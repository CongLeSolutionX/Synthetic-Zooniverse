---
created: 2025-03-10 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2103.00020"
---



# CLIP - Learning Transferable Visual Models From Natural Language Supervision
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
title: "The CLIP Paper - Learning Transferable Visual Models From Natural Language Supervision"
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
    A[CLIP: Contrastive Language-Image Pre-training] --> B{Core Concepts};
    
    subgraph Model_Architecture ["Model Architecture"]
    style Model_Architecture fill:#f2b3,stroke:#333,stroke-width:1px;
        B --> C[Image Encoder];
        C --> CA["ResNet (RN50, RN101, RN50x{4,16,64})"]
        C --> CB["Vision Transformer (ViT-B/32, ViT-B/16, ViT-L/14)"]
        C --> CC["Attention Pooling (Replaces Avg Pooling)"]
        B --> D[Text Encoder];
        D --> DA["Transformer (12-layer, 512-wide, 8-head)"]
        D --> DB["BPE Representation (49,152 vocab)"]
        B --> E[Joint Embedding Space];
        E --> EA["Linear Projection (Image & Text Features)"]
        E --> EB["Cosine Similarity (Image & Text Embeddings)"]
    end
    
    subgraph Training_Process ["Training Process"]
    style Training_Process fill:#a2fa,stroke:#333,stroke-width:1px;
        B --> F["Dataset: 400M (Image, Text) Pairs (WIT)"]
        F --> FA[Publicly Available Internet Data];
        F --> FB[500K Queries for Broad Coverage];
        B --> G["Objective: Contrastive Loss"]
        G --> GA["Predict Correct (Image, Text) Pairings"]
        G --> GB[Minimize Similarity of Incorrect Pairings];
        B --> H[Optimization];
        H --> HA[Adam Optimizer];
        H --> HB[Weight Decay Regularization];
        H --> HC[Cosine Learning Rate Schedule];
        H --> HD["Large Minibatch Size (32,768)"]
        H --> HE[Mixed Precision Training];
    end
    
    subgraph Zero_Shot_Transfer ["Zero-Shot Transfer"]
    style Zero_Shot_Transfer fill:#f2aa,stroke:#333,stroke-width:1px;
        B --> I[Create Dataset Classiﬁer];
        I --> IA["Embed Class Names/Descriptions (Text Encoder)"]
        I --> IB["Zero-Shot Linear Classiﬁer (Synthesized)"]
        B --> J[Zero-Shot Prediction];
        J --> JA["Cosine Similarity (Image Embeddings & Classiﬁer)"]
        J --> JB["Predict Most Probable (Image, Text) Pair"]
    end
    
    subgraph Evaluation_Metrics ["Evaluation & Metrics"]
    style Evaluation_Metrics fill:#a2aa,stroke:#333,stroke-width:1px;
        B --> K[Benchmarks];
        K --> KA[>30 Computer Vision Datasets];
        K --> KB[OCR, Action Recognition, Geo-localization, Fine-Grained Classiﬁcation];
        B --> L[Metrics];
        L --> LA[Zero-Shot Accuracy];
        L --> LB[Linear Probe Performance];
        L --> LC[Robustness to Distribution Shift];
        L --> LD[Human Performance Comparison];
    end
    
    subgraph Key_Findings ["Key Findings"]
    style Key_Findings fill:#f2fa,stroke:#333,stroke-width:1px;
        B --> M[Performance];
        M --> MA[Matches ResNet-50 on ImageNet Zero-Shot];
        M --> MB[Competitive with Task-Specific Supervised Models];
        B --> N[Efficiency];
        N --> NA[Efficient Learning from Natural Language Supervision];
        N --> NB[Zero-Shot Transfer Efficiency];
        B --> O[Robustness];
        O --> OA[Robust to Natural Distribution Shift];
        O --> OB[Reduces Robustness Gap vs. ImageNet Models];
    end
    
    subgraph Broader_Impacts ["Broader Impacts & Limitations"]
    style Broader_Impacts fill:#a2af,stroke:#333,stroke-width:1px;
        B --> P[Bias & Fairness];
        P --> PA["Potential for Social Biases (FairFace)"]
        P --> PB[Importance of Class Design];
        B --> Q[Surveillance];
        Q --> QA[Enables Bespoke Surveillance Applications];
        Q --> QB[Reduces Skill Requirements for Building Such Applications];
        B --> R[Limitations];
        R --> RA[Weakness on Complex Tasks];
        R --> RB[OCR Performance Variability];
        R --> RC["Limited Flexibility (Compared to Image Captioning)"]
    end
    
```

---

### Key improvements and explanations:

*   **Clear Categorization:**  The diagram is now organized into major sections like Model Architecture, Training Process, Zero-Shot Transfer, Evaluation Metrics, and Broader Impacts & Limitations, making it easier to understand the flow of information.

*   **Detailed Subgraphs:** Each major section is further broken down into subgraphs, providing a hierarchical view of the key components.

*   **Emphasis on Relationships:**  Edges are used to explicitly show the relationships between different aspects of the CLIP model and the data.

*   **Mathematical Concepts:**  Incorporate the actual mathematical notation used in the paper. This provides more context and information.

*   **Specific Examples:** When possible, include concrete examples from the CLIP paper (e.g., specific ResNet and ViT architectures).

*   **Concise Labels:**  Use clear and concise labels for nodes and edges.

*   **Color-coding:** Apply color-coding to help distinguish between different types of information or concepts.

*   **Bias & Limitations Highlighted:** The section on "Broader Impacts & Limitations" is included.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---