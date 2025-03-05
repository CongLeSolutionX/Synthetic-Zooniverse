---
created: 2025-03-04 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2312.11805"
---



# Decoder-Only Transformers Architecture
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Decoder-Only Transformers Architecture - A Diagrammatic Guide 



```mermaid
---
title: "Gemini: A Family of Highly Capable Multimodal Models - Google DeepMind"
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
    A[Decoder-Only Transformer Architecture] --> B{Key Components}
    style A fill:#a3ae,stroke:#333,stroke-width:1px

    B --> C[Self-Attention Mechanism]:::detail
    style C fill:#a2fa,stroke:#333,stroke-width:1px
    C --> CA[Allows the model to weigh the importance of different parts of the input sequence]:::takeaway
    C --> CB[Enables parallel processing of the entire input sequence]:::takeaway

    B --> D[Feedforward Neural Networks]:::detail
    style D fill:#a2fa,stroke:#333,stroke-width:1px
    D --> DA[Apply non-linear transformations to the output of the attention mechanism]:::takeaway
    D --> DB[Enhance the model's ability to learn complex patterns]:::takeaway

    B --> E[Residual Connections]:::detail
    style E fill:#a2da,stroke:#333,stroke-width:1px
    E --> EA[Allow for easier flow of information through the network]:::takeaway
    E --> EB[Help to mitigate the vanishing gradient problem]:::takeaway

    B --> F[Layer Normalization]:::detail
    style F fill:#a2da,stroke:#333,stroke-width:1px
    F --> FA[Stabilizes training and improves generalization performance]:::takeaway
    
    A --> G{Gemini Enhancements}
    style G fill:#a3ae,stroke:#333,stroke-width:1px
    G --> GA[Architecture Improvements]:::detail
        style GA fill:#f2fa,stroke:#333,stroke-width:1px
        GA --> GAA[Optimized for stable training at scale]:::takeaway
        GA --> GAB[Enables 32k context length]:::takeaway
    G --> GB[Model Optimization]:::detail
         style GB fill:#f2fa,stroke:#333,stroke-width:1px
         GB --> GBA["Optimized inference on Google's Tensor Processing Units (TPUs)"]:::takeaway
         GB --> GBB[Multi-query attention]:::takeaway
    
 classDef takeaway fill:#f2b2,stroke:#333,stroke-width:1px
 classDef detail fill:#f2f2,stroke:#333,stroke-width:1px
 class C,D,E,F,GA,GB detail
 class CA,CB,DA,DB,EA,EB,FA,FB,GAA,GAB,GBA,GBB takeaway
 
```

----


### Key improvements and explanations

*   **Focus on Decoder-Only:** The diagram is explicitly centered on the "Decoder-Only Transformer Architecture," as requested.
*   **Hierarchical Structure:**  Key components of the decoder (Self-Attention, Feedforward Networks, etc.) are clearly outlined as sub-nodes.
*   **Gemini Enhancements:** The specific improvements made in the Gemini models (optimized for TPUs, long context length, etc.) are highlighted separately.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---