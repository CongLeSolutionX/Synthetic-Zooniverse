---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2405.04324"
---



# Model Architecture of the Granite Code Models
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Model Architecture of the Granite Code Models - A Diagrammatic Guide 


```mermaid
---
title: "IBM - Granite Code Models - Model Architecture"
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
    "graph": { "htmlLabels": true, 'curve': 'linear' },
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
    A[Transformer Decoder] --> B{Granite Code Models};
    style B fill:#ccf3,stroke:#333,stroke-width:2px

    B --> C[Granite-3B-Code]
    C -- Size: 3B Parameters --> C

    B --> D[Granite-8B-Code]
     D -- Size: 8B Parameters --> D

    B --> E[Granite-20B-Code]
     E -- Size: 20B Parameters --> E

    B --> F[Granite-34B-Code]
     F -- Size: 34B Parameters --> F

    C --> C1[RoPE Embedding]
    C --> C2[MHA]
    C --> C3[RMSNorm]
    C --> C4[SwiGLU]
    C -- Context Length: 2048 --> C1
    C1 --> C5[Positional Embedding]
    C2 --> C6[Attention Mechanism]
    C3 --> C7[Normalization Layer]
    C4 --> C8[Activation Function]

    D --> D1[GQA]
    D --> D2[RMSNorm]
    D --> D3[SwiGLU]
     D -- Context Length: 4096 --> D1
    D1 --> D4[Attention Mechanism]
    D2 --> D5[Normalization Layer]
    D3 --> D6[Activation Function]

    E --> E1[MQA]
    E --> E2[LayerNorm]
    E --> E3[GELU]
     E -- Context Length: 8192 --> E1
    E1 --> E4[Attention Mechanism]
    E2 --> E5[Normalization Layer]
    E3 --> E6[Activation Function]

   F --> F1[MQA]
    F --> F2[LayerNorm]
    F --> F3[GELU]
     F -- Context Length: 8192 --> F1
     F -- "Depth Upscaling from 20B" --> F

    F1 --> F4[Attention Mechanism]
    F2 --> F5[Normalization Layer]
    F3 --> F6[Activation Function]
    
```

---


Key elements:

*   `Transformer Decoder`: the base architecture of all the models
*   Four Models Sizes: The diagram clearly indicates the sizes of all four models.
*   Components: The components are listed in the respective models.
*   Annotation: The key aspects of each component are listed in the diagrams.

This representation provides a concise overview of the model architectures, highlighting the key differences between each size variant.





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---