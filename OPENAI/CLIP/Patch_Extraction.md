---
created: 2025-03-10 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2103.00020"
---



# Patch Extraction
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




While "Patch Extraction" isn't a central theme in the CLIP paper, it is implicitly involved in several aspects of the model and can be represented effectively using the previously outlined structure. Here's how:

```mermaid
---
title: "CLIP - Learning Transferable Visual Models From Natural Language Supervision"
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
    A[Patch Extraction in CLIP] --> B{Core Role & Context};

    subgraph Image_Encoding["Image Encoding"]
    style Image_Encoding fill:#f2b4,stroke:#333,stroke-width:1px;
        B --> C["Vision Transformer (ViT)"]
        C --> CA[Patch Extraction];
        CA --> CAA[Image divided into fixed-size patches];
        CA --> CAB[ViT-B/32: 32x32 patches];
        CA --> CAC[ViT-B/16: 16x16 patches];
        CA --> CAD[ViT-L/14: 14x14 patches];
        C --> CB[Linear Projection];
        CB --> CBA[Patch embeddings projected];
        C --> CC[Transformer Layers];
        CC --> CCA[Process patch embeddings to learn relationships];
    end

    subgraph Augmentation["Augmentation"]
    style Augmentation fill:#a2f3,stroke:#333,stroke-width:1px;
        B --> D[Data Augmentation];
        D --> DA[Random Square Crop];
        DA --> DAA[Crop extracted from resized images];
        D --> DB[Resizing];
        DB --> DBA[Upscaling and Downscaling];
    end

    subgraph Relevance_to_CLIP["Relevance to CLIP"]
    style Relevance_to_CLIP fill:#f2a3,stroke:#333,stroke-width:1px;
        B --> E[Key Aspects];
        E --> EA[ViT architecture relies on patch-based image representation];
        E --> EB[Patch size influences receptive field and computation];
        E --> EC[Random cropping used as a key augmentation technique];
    end

    subgraph Technical_Implications["Technical Implications"]
    style Technical_Implications fill:#a2a2,stroke:#333,stroke-width:1px;
        B --> F[Computational Cost];
        F --> FA[Smaller patches -> more tokens -> increased computation];
        B --> G[Receptive Field];
        G --> GA[Patch size influences what ViT learns];
        B --> H[Augmentation Importance];
        H --> HA[Random cropping aids in generalization];
    end
    
```

---


### Key improvements and explanations

*   **Focus on Patch Extraction:** The diagram centers around patch extraction as a specific element.
*   **ViT Details:** Provides information about patch sizes in the ViT.
*   **Contextualization:** Describes how patch extraction relates to the broader CLIP architecture and goals.
*   **Technical Considerations:** Outlines how patch extraction affects computation and receptive field.
*   **Augmentation Link:** connects with the Augmentation element.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---