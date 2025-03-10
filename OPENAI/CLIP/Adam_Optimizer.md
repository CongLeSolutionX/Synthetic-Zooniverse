---
created: 2025-03-10 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2103.00020"
---



# Adam Optimizer
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
    A[Adam Optimizer] --> B{Core Aspects};
    style A fill:#ccf3,stroke:#333,stroke-width:1px

    B --> C[Algorithm Type];
    C --> CA[First-Order Optimization];
    C --> CB["Stochastic Gradient Descent (SGD) Variant"]

    B --> D[Purpose];
    D --> DA[Update Model Parameters];
    D --> DB[Minimize Loss Function];

    B --> E[Key Features];
    E --> EA[Adaptive Learning Rates];
    EA --> EAA[Individual Learning Rate for Each Parameter];
    EA --> EAB[Based on Estimates of 1st and 2nd Moments of Gradients];
    E --> EB[Momentum];
    EB --> EBA[Incorporates Past Gradients to Smooth Updates]
    E --> EC[Bias Correction]
    EC --> ECA[Corrects for Initialization Bias in Moment Estimates]

    B --> F[Parameters]
    F --> FA["Learning Rate (α): Overall Step Size"]
    F --> FB["β1: Exponential Decay Rate for 1st Moment Estimates<br>(Defaults to 0.9)"]
    F --> FC["β2: Exponential Decay Rate for 2nd Moment Estimates<br>(Defaults to 0.999 or 0.98 in CLIP)"]
    F --> FD["Epsilon (ϵ): Small Constant for Numerical Stability<br>(10^-8 or 10^-6 in CLIP)"]
    F --> FE["Weight Decay (λ): Regularization<br>(0.2 in CLIP)"]

    B --> G[CLIP Specifics]
    G --> GA["Decoupled Weight Decay Regularization<br>(Loshchilov & Hutter, 2017)"]
    G --> GB["Used on Weights<br>(Excluding Gains and Biases)"]
    G --> GC["Beta 2 Adjusted for ViT models<br>(0.98)"]
    G --> GD["Epsilon Adjusted for ViT models<br>(10^-6)"]

    B --> H["Relevant Equations<br>(Conceptual)"]
    H --> HA["m_t = β1 * m_{t-1} + (1 - β1) * g_t <br>(1st Moment Estimate)"]
    H --> HB["v_t = β2 * v_{t-1} + (1 - β2) * g_t^2<br>(2nd Moment Estimate)"]
    H --> HC["m_hat_t = m_t / (1 - β1^t)<br>(Bias Correction)"]
    H --> HD["v_hat_t = v_t / (1 - β2^t)<br>(Bias Correction)"]
    H --> HE["θ_t = θ_{t-1} - α * m_hat_t / (sqrt(v_hat_t) + ϵ)<br>(Parameter Update)"]
    H --> HF["Where g_t is gradient, θ_t is parameter vector at time t"]
    
```


DOI:[10.13140/RG.2.2.21352.17924](http://dx.doi.org/10.13140/RG.2.2.21352.17924)


---


### Key points and explanations

*   **Core Aspects:** This section defines the core aspects of Adam and its relationship to other optimizers.
*   **Key Features:** Adaptive learning rates and momentum are highlighted as defining features.
*   **Parameters:** The parameters with commonly used default values and CLIP specific tunings are explicitly provided.
*   **CLIP Specifics:** Any modifications used in CLIP are highlighted.
*   **Relevant Equations:** Core equations for the algorithm are shown, however, are kept at a high-level.

This structure allows you to break down the complexities of the Adam optimizer in a concise visual summary. Remember to balance visual clarity with technical accuracy.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---