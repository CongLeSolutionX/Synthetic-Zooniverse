---
created: 2025-03-10 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2103.00020"
---



# Vision Transformer Family
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
title: "Vision Transformer Family"
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
graph LR
    A["Vision Transformer (ViT) Family"] --> B{Core Characteristics}

    subgraph General_Architecture["General Architecture"]
    style General_Architecture fill:#f2b3,stroke:#333,stroke-width:1px;
        B --> C[Patch Extraction];
        C --> CA[Image Divided into Fixed-Size Patches];
        C --> CB[Linear Embedding of Patches];
        B --> D[Transformer Encoder];
        D --> DA[Multiple Layers of Self-Attention and Feedforward Networks];
        D --> DB[Layer Normalization];
        D --> DC[Positional Embeddings Added];
        B --> E[Classification Head];
        E --> EA["MLP Head (Multilayer Perceptron)"]
        E --> EB["Linear Projection"]
    end

    subgraph Training["Training Details"]
    style Training fill:#a2fa,stroke:#333,stroke-width:1px;
        B --> F[Datasets];
        F --> FA["ImageNet-21K<br>(Used in Original ViT)"]
        F --> FB["CLIP Dataset<br>(400M Image-Text Pairs)"]
        B --> G["Training Objectives"]
        G --> GA["Supervised Classification<br>(ImageNet)"]
        G --> GB["Contrastive Learning<br>(CLIP)"]
        B --> H["Optimization"]
        H --> HA["Adam Optimizer"]
        H --> HB["Weight Decay Regularization"]
        H --> HC["Cosine Learning Rate Schedule"]
        H --> HD["High Resolution Finetuning"]
        HD --> HDA["Used on ViT-L/14@336px (336 Pixel Resolution)"]
    end

    subgraph Model_Variants["Model Variants<br>(CLIP)"]
    style Model_Variants fill:#f2aa,stroke:#333,stroke-width:1px
        B --> I["ViT-B/32"]
        I --> IA["Base Model"]
        I --> IB["32x32 Patch Size"]
        B --> J["ViT-B/16"]
        J --> JA["Base Model"]
        J --> JB["16x16 Patch Size"]
        B --> K["ViT-L/14"]
        K --> KA["Larger Model"]
        K --> KB["14x14 Patch Size"]
        B --> L["ViT-L/14@336px"]
        L --> LA["Largest Model"]
        L --> LB["Pre-trained at 224px, Fine-tuned at 336px"]
        L --> LC["Best Performance in CLIP"]
    end

    subgraph Distinguishing_Features["Distinguishing Features in CLIP"]
    style Distinguishing_Features fill:#a2a3,stroke:#333,stroke-width:1px;
        B --> M["Learned Joint Embedding"]
        M --> MA["Dot Product with Text Embeddings"]
        B --> N["Contrastive Learning Objective"]
        N --> NA["Direct Optimization of Image-Text Similarity"]
        B --> O["Robust Zero-Shot Performance"]
        O --> OA["Generalizes to Various Tasks via Natural Language"]
    end

    subgraph Performance_Notes["Performance Notes"]
    style Performance_Notes fill:#a2f3,stroke:#333,stroke-width:1px
        B --> P["ViTs vs. ResNets"]
        P --> PA["ViTs More Compute Efficient than ResNets<br>(CLIP)"]
        P --> PB["Reaches Higher Overall Performance"]
        B --> Q["CLIP Limitations"]
        Q --> QA["Struggles with Complex, Abstract Tasks"]
        Q --> QB["Requires Large Scale Data"]
    end
    
```

---


### Explanations

*   **Distinguishing Features:** Added a specific section on the unique characteristics of Vision Transformers when used within CLIP, focusing on the dot product with text embeddings and the contrastive learning objective.
*   **Concrete Examples:** included patch size and other distinguishing properties.
*   **Highlights Key Results:** More direct mention of how the performance and efficiency compares to ResNet architectures.
*   **Clearer Organization:** Reorganized for better flow and readability.

This structure provides a complete and detailed overview of the Vision Transformer family within the context of the CLIP paper. It outlines the core characteristics, training details, different model variants, and performance highlights.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---