---
created: 2025-03-10 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2103.00020"
---



# Optimization Methods
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
    A["CLIP Optimization Methods"] --> B{Core Techniques}

    subgraph Core_Components["Optimization Techniques"]
    style Core_Components fill:#f2b2,stroke:#333,stroke-width:1px;
        B --> C[Optimizer]
        C --> CA[Adam Optimizer]
        CA --> CAA[Rationale:<br>Widely Used, Efﬁcient]
        C --> CB[Decoupled Weight Decay]
        CB --> CBA[Regularization applied to Weights, Not Gains/Biases]
        B --> D[Learning Rate Schedule]
        D --> DA[Cosine Decay Schedule]
        DA --> DAA[Reduces Learning Rate Over Training]
        B --> E[Temperature Optimization]
        E --> EA["Learnable Temperature Parameter<br>(τ)"]
        EA --> EAA[Initialized as Log-Parameterized Multiplicative Scalar]
        EA --> EAB[Clipped to Prevent Logit Scaling > 100]
        B --> F[Large Minibatch Size]
        F --> FA["Size:<br>32,768"]
        FA --> FAA["Rationale:<br>Improved Training Stability"]
        B --> G[Mixed Precision Training]
        G --> GA["Data Type:<br>FP16"]
        GA --> GAA["Rationale:<br>Accelerates Training, Saves Memory"]
        B --> H[Memory Savings Techniques]
        H --> HA[Gradient Checkpointing]
        H --> HB[Half-Precision Adam Statistics]
        H --> HC[Half-Precision Stochastically Rounded Text Encoder Weights]
        B --> I[Distributed Training]
        I --> IA[Embedding Similarities Sharded Across GPUs]
        IA --> IAA["Rationale:<br>Reduced Memory Footprint Per GPU"]
    end
    
```

DOI: [10.13140/RG.2.2.11285.84962](http://dx.doi.org/10.13140/RG.2.2.11285.84962)


---



### Key explanations

*   **Adam Optimizer:**  The most important and widely used optimization approach in the study. The Adam optimizer is an algorithm for ﬁrst-order gradient-based optimization of stochastic objective functions, based on adaptive estimates of lower-order moments.
*   **Decoupled Weight Decay Regularization:**  Addresses how the regularization is applied to the weights. Regularization techniques, such as weight decay, aim to prevent overfitting by adding a penalty term to the loss function. This helps in generalization.
*   **Cosine Learning Rate Schedule:** This schedule reduces the learning rate during training. Cosine annealing refers to a learning rate schedule that follows the cosine function. In this scheme, the learning rate starts at a maximum value and then decreases following a cosine curve.
*   **Temperature Optimization:** Learnable Temperature Parameter (τ) - a parameter of the softmax function that controls the steepness of the probability distribution.
*   **Large Minibatch Size** (32,768)
*   **Mixed Precision Training**
*   **Memory Savings Techniques:** Techniques to reduce memory requirements during training.

This structured visual summary captures the essential optimization techniques employed in CLIP.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---