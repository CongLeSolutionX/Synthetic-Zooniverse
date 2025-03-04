---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original Source: "https://arxiv.org/pdf/2412.19437"
---



# DualPipe Pipeline Parallelism During Training for DeepSeek V3
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## DualPipe Pipeline - A Diagrammatic Guide


```mermaid
---
title: "DeepSeek-V3 Technical Report"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "graph": { "htmlLabels": false, 'curve': 'cardinal' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#f529',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    subgraph DualPipe_Pipeline["DualPipe Pipeline"]
        A[DualPipe] --> B(Forward Chunk)
        A --> C(Backward Chunk)
        B --> D{Attention}
        B --> E{"All-to-All Dispatch"}
        B --> F{MLP}
        B --> G{"All-to-All Combine"}
        C --> H{"Attention<br>(Backward for Input)"}
        C --> I{"Attention<br>(Backward for Weights)"}
        C --> J{"MLP<br>(Backward)"}
        C --> K{PP Communication}
        C --> L{Barrier}
        D --> Da(Compute Attention on input)
        D --> Db(Accumulate attention output)
        E --> Ea(Dispatch to experts across nodes)
        E --> Eb("Handle communication with InfiniBand (IB) and NVLink")
        F --> Fa(Compute MLP on token representations)
        F --> Fb(Accumulate MLP outputs)
        G --> Ga(Combine results from experts)
        G --> Gb("Receive results via IB/NVLink")
        H --> Ha(Compute attention gradients based on input)
        H --> Hb(Backward pass for input part)
        I --> Ia(Compute attention gradients based on weights)
        I --> Ib(Backward pass for weight part)
        J --> Ja(Compute MLP gradients)
        J --> Jb(Backward pass for MLP)
        K --> Ka("Inter-node communication via PP")
        K --> Kb("Overlapping with forward/backward computation")
        L --> La("Synchronization point for forward/backward chunks")
        
        classDef Style_for_Group_Elements_1 fill:#ccf3,stroke:#333,stroke-width:1px
        class D,H,I,J Style_for_Group_Elements_1

        classDef Style_for_Group_Elements_2 fill:#cf33,stroke:#333,stroke-width:1px
        class E,G,K Style_for_Group_Elements_2

        classDef Style_for_Group_Elements_3 fill:#2f33,stroke:#333,stroke-width:1px
        class F,J Style_for_Group_Elements_3
        
    end
    
    B -.-> B1(Micro-Batch 1)
    B -.-> B2(Micro-Batch 2)
    C -.-> C1(Micro-Batch 1)
    C -.-> C2(Micro-Batch 2)

    subgraph Micro_Batch_1_Overlap["Micro Batch 1 Overlap"]
        B1 --> D1[Compute]
        B1 --> E1[Dispatch]
        B1 --> F1[Compute MLP]
        B1 --> G1[Combine]
    end
    
    subgraph Micro_Batch_2_Overlap["Micro Batch 2 Overlap"]
        B2 --> D2[Compute]
        B2 --> E2[Dispatch]
        B2 --> F2[Compute MLP]
        B2 --> G2[Combine]
        
        C1 --> H1[Compute]
        C1 --> I1[Compute]
        C1 --> J1[Compute]
        C1 --> K1[Communication]
        C1 --> L1[Barrier]
    end
    
    C2 --> H2[Compute]
    C2 --> I2[Compute]
    C2 --> J2[Compute]
    C2 --> K2[Communication]
    C2 --> L2[Barrier]
    
```



-----

### Explanation

This Mermaid diagram visualizes the DualPipe pipeline during training for DeepSeek-V3.  It's designed to illustrate the overlapping of computation and communication across forward and backward chunks of the pipeline.

* **Subgraphs:**  The `DualPipe_Pipeline` subgraph encapsulates the core structure.  The `Micro_Batch_1_Overlap` and `Micro_Batch_2_Overlap` subgraphs illustrate the crucial aspect of processing multiple micro-batches concurrently.

* **Nodes:** The diagram uses boxes for pipeline stages (`Attention`, `All-to-All Dispatch`, `MLP`, `All-to-All Combine`, and for backward chunks the specific backward phases).  Nodes like `Micro-Batch 1` and `Micro-Batch 2` show the processing of multiple micro-batches in parallel.

* **Edges:** Directed edges show the data flow through the pipeline stages.  Note the overlapping of forward and backward computation/communication, indicated by arrows connecting stages between micro-batches 1 and 2. This highlights the key feature of DualPipe's design.  The `Barrier` nodes represent synchronization points.

* **Emphasis on Overlap:** The arrangement of edges connecting the forward and backward chunks within each micro-batch shows the overlapping operations (e.g., attention computation with backward communication).  The style differentiates the stages to make the overlap clear.

* **Communication Handling:**  Nodes like `All-to-All Dispatch` and `All-to-All Combine` are highlighted, indicating that communication operations are also handled concurrently with computation.

This diagram provides a visual representation of how DualPipe, through its overlapping mechanisms, aims to reduce the training time and enhance the efficiency of the DeepSeek-V3 model.  To further enhance the diagram, you could include figures to illustrate the timing of operations or tables detailing the resources allocated to each task (e.g., number of SMs, bandwidths used).  Remember to add text annotations to the boxes to clarify the specific operations performed in each stage.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---