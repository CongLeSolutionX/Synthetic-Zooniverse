---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://azure.microsoft.com/en-us/blog/empowering-innovation-the-next-generation-of-the-phi-family/"
---




# The Next Generation of the Phi Family
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---

## The Next Generation of the Phi Family - A Diagrammatic Guide




```mermaid
---
title: "The Next Generation of the Phi Family by Microsoft"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "flowchart": { "htmlLabels": false, 'curve': 'linear' },
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
    subgraph Phi_Models["Phi Models"]
    style Phi_Models fill:#f235,stroke:#333,stroke-width:2px
        A[Phi-4-Multimodal] --> B{Multimodality}
        B --> C[Speech]
        B --> D[Vision]
        B --> E[Text]
        
        A --> F[Unified Architecture]
        F --> G[Mixture-of-LoRAs]
        
        A --> H[Performance]
        H --> I[Speech Recognition]
        H --> J[Speech Translation]
        H --> K[Summarization]
        H --> L[Visual Reasoning]

        A --> M[Deployment]
        M --> N[Mobile Devices]
        M --> O[Edge Computing]

        A --> P[Vocabulary]
        A --> Q[Multilingual Support]
        
        A --> R(Benchmark Comparisons)
        R --> S["Bar Chart: Phi-4-Multimodal vs. Other Models (Speech)"]
        R --> T["Bar Chart: Phi-4-Multimodal vs. Other Models (Vision)"]

        A1[Phi-4-Mini] --> B1{Text-Based Tasks}
        B1 --> C1[Reasoning]
        B1 --> D1[Math]
        B1 --> E1[Coding]
        B1 --> F1[Instruction Following]
        B1 --> G1[Function Calling]
        
        A1 --> H1[Performance]
        H1 --> I1[Bar Chart: Phi-4-Mini vs. Other Models]
        
        A1 --> J1[Architecture]
        J1 --> K1[Dense Transformer]
        J1 --> L1[Decoder-Only]
        J1 --> M1[Grouped Query Attention]
        J1 --> N1[Shared Input-Output Embeddings]
        J1 --> O1[Large Vocabulary]
        A1 --> P1[Deployment]
        P1 --> Q1[Mobile Devices]
        P1 --> R1[Edge Computing]
        P1 --> S1[ONNX Runtime]

        subgraph Security_Safety["Security Safety"]
        style Security_Safety fill:#529,stroke:#333,stroke-width:2px
            A --> T[Security & Safety Testing]
            T --> U["Microsoft AI Red Team (AIRT)"]
            T --> V["Risk Identification Toolkit (PyRIT)"]
            T --> W[Multilingual Probing]
            T --> X[Security Evaluations]
        end
        
        subgraph Use_Cases["Use Cases"]
        style Use_Cases fill:#22f2,stroke:#333,stroke-width:2px
            A --> Y[Use Cases]
            Y --> Z[Device Integration]
            Y --> AA[Automotive AI]
            Y --> BB[Financial Services]
        end
    
        subgraph Customization["Customization"]
        style Customization fill:#122f2,stroke:#333,stroke-width:2px
            A --> CC[Customization]
            CC --> DD["Fine-tuning"]
            CC --> EE["Cross-Platform Support"]
        end
    end
    
```


----


### Explanation

This Mermaid graph uses a subgraph structure to group related concepts, making the diagram more organized and readable. It visualizes the core features of both models, highlighting the relationships between different aspects (e.g., the multimodality of Phi-4-multimodal). The graph also incorporates benchmarking data using bar charts, and illustrates the different architectures of the models.  The addition of subgraphs for Security & Safety Testing, Use Cases, and Customization improve clarity and focus.  Remember, you can add specific data points (e.g., parameter counts) to the nodes for more detail, and add specific examples of use cases to nodes Z, AA, and BB.  Adjust the diagram as needed to fit your desired level of detail. Note that the graph is quite large and could be broken down further into more specialized diagrams.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---