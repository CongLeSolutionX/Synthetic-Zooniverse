---
created: 2025-03-10 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2103.00020"
---



# Image Encoder
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## A Diagrammatic Guide 


```mermaid
---
title: "Image Encoder"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "graph": { "htmlLabels": false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph TD
    A[Image Encoder] --> B{Architectures};
    
    subgraph ResNet_Encoder ["ResNet-Based Encoder"]
    style ResNet_Encoder fill:#f2b3,stroke:#333,stroke-width:1px;
        B --> C["ResNet (RN50, RN101, RN50x{4, 16, 64})"]
        C --> CA["Modifications: ResNet-D Improvements (He et al., 2019)"]
        C --> CB["Anti-Aliased Rect-2 Blur Pooling (Zhang, 2019)"]
        C --> CC["Attention Pooling (Replaces Global Avg Pooling)"]
        CC --> CCA[Multi-Head QKV Attention];
        CC --> CCB[Query Conditioned on Global Average-Pooled Image Features];
        C --> CD["Output: Image Representation (I_f)"]
    end
    
    subgraph Vision_Transformer_Encoder ["Vision Transformer Encoder"]
    style Vision_Transformer_Encoder fill:#a2f3,stroke:#333,stroke-width:1px;
        B --> D["Vision Transformer (ViT-B/32, ViT-B/16, ViT-L/14, ViT-L/14@336px) (Dosovitskiy et al., 2020)"]
        D --> DA[Minor Modification: Additional Layer Normalization];
        DA --> DAA[Combined Patch & Position Embeddings];
        D --> DB[Slightly Different Initialization Scheme];
        D --> DC["Output: Image Representation (I_f)"]
    end
    
```
----


### Key breakdown

*   **ResNet-Based Encoder:**  The nodes describe the architectural elements.
*   **Vision Transformer Encoder:**  Again, details the main features.

This provides a concise visual representation of the Image Encoder component of CLIP, ready for integration into a larger diagram or for standalone use. The annotations clarify the specific improvements and modifications from other research to fully capture the context.





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---