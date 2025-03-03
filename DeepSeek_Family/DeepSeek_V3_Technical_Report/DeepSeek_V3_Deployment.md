---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original Source: "https://arxiv.org/pdf/2412.19437"
---


# DeepSeek V3 Deployment
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## DeepSeek V3 Deployment - A Diagrammatic Guide



```mermaid
---
title: "DeepSeek-V3 Technical Report"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "graph": { "htmlLabels": false, 'curve': 'linear' },
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
    subgraph DeepSeek_V3_Deployment["DeepSeek V3 Deployment"]
        A[DeepSeek-V3 Deployment] --> B(Prefilling)
        A --> C(Decoding)

    end
    
    subgraph Prefilling["Prefilling"]
        B(Prefilling) --> B1(Compute Resources)
        B --> B2(Expert Parallelism)
        B --> B3(Communication Strategy)
        B --> B4(Micro-batch Overlap)
        
        B1 --> B1a(4 nodes with 32 GPUs)
        B1 --> B1b(NVLink and InfiniBand)
        B2 --> B2a(32-way EP)
        B2 --> B2b("Redundant Experts (32)")
        B3 --> B3a(IB for inter-node, NVLink for intra-node)
        B3 --> B3b(Token Dispatch to 4 nodes)
        B4 --> B4a(Simultaneous attention/MoE for 2 micro-batches)
        
    end
    
    subgraph Decoding["Decoding"]
        C(Decoding) --> C1(Compute Resources)
        C --> C2(Expert Parallelism)
        C --> C3(Communication Strategy)
        C --> C4(Micro-batch Overlap)
        
        C1 --> C1a(40 nodes with 320 GPUs)
        C1 --> C1b(NVLink and InfiniBand)
        C2 --> C2a("320-way EP (1 expert per GPU)")
        C2 --> C2b("Redundant Experts (64 GPUs)")
        C3 --> C3a(Direct point-to-point IB transfers)
        C3 --> C3b(IBGDA technology)
        C4 --> C4a(Simultaneous attention/MoE for 2 micro-batches)
        
    end

    B1a --> B1b[Interconnects]
    B2a --> B2b[Redundancy for Load Balancing]
    B3a --> B3b[Optimized Communication]
    B4a --> B4b[Overlap for efficiency]
    C1a --> C1b[Interconnects]
    C2a --> C2b[Redundancy for Load Balancing]
    C3a --> C3b[Low Latency Transfers]
    C4a --> C4b[Overlap for efficiency]
    
```

---


### Explanation

This Mermaid diagram visualizes the DeepSeek-V3 deployment strategy, highlighting the differences between prefilling and decoding.  It's organized into two main subgraphs: "Prefilling" and "Decoding". Each subgraph focuses on the specific resource allocation, expert parallelism, and communication strategy employed for each stage.

* **Subgraphs:** This structure clearly separates the two deployment stages, making it easier to compare the differences and similarities in their strategies.

* **Nodes:** Each box represents a key component or concept related to the deployment. For example, "Compute Resources" details the number of nodes and GPUs.  "Expert Parallelism" specifies the number of experts per GPU. "Communication Strategy" illustrates the methods used for inter-node and intra-node communication.

* **Arrows:** Connect related components, showing the flow of data and the relationship between different parts of the deployment. For example, arrows connect "Compute Resources" to "Expert Parallelism" to illustrate that the hardware supports the parallel processing of experts.

* **Detailed Components:**  The subgraphs further break down the key components and the techniques used for efficient deployment. This provides a more granular understanding of the strategies used.

* **Overlap:**  The diagram highlights the key optimization of overlapping computations and communications within a stage, and between the stages, as a key factor in boosting efficiency. This is a vital aspect for reducing latency and improving throughput.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---