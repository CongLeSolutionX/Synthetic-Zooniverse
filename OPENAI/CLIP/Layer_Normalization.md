---
created: 2025-03-10 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2103.00020"
---



# Layer Normalization
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
    A["Layer Normalization<br>(LayerNorm)"] --> B{"Concept & Application in CLIP"}

    subgraph Definition["Definition"]
    style Definition fill:#f2b4,stroke:#333,stroke-width:1px
        B --> C[Normalization Technique]
        C --> CA[Normalizes Activations Within a Layer]
        C --> CB[Computes Mean & Variance Across Features]
        C --> CC[Independent of Batch Size]
    end

    subgraph Equation["Equation"]
    style Equation fill:#a2fa,stroke:#333,stroke-width:1px
        B --> D[Normalization Step]
        D --> DA["$$\begin{aligned}y = \frac{x - E[x]}{\sqrt{Var[x] + \epsilon}} * \gamma + \beta \end{aligned}$$"]
        DA --> DAA["x: Input to the layer"]
        DA --> DAB["E[x]: Mean of x"]
        DA --> DAC["Var[x]: Variance of x"]
        DA --> DAD["γ: Scale Parameter<br>(Learned)"]
        DA --> DAE["β: Bias Parameter<br>(Learned)"]
        DA --> DAF["ϵ: Small Constant for Numerical Stability"]
    end

    subgraph Role_in_CLIP["Role in CLIP"]
    style Role_in_CLIP fill:#f2aa,stroke:#333,stroke-width:1px
        B --> E[ViT Image Encoder]
        E --> EA[Applied to Combined Patch & Position Embeddings]
        E --> EB[Added Before Transformer Layers]
        B --> F[Text Encoder]
        F --> FA[Applied After Transformer's Highest Layer]
        F --> FB["Feature Representation of Text (at [EOS] Token)"]
    end

    subgraph Justification["Justification"]
    style Justification fill:#a2aa,stroke:#333,stroke-width:1px
        B --> G[Stabilizes Training]
        G --> GA[Improved Performance]
        G --> GB[Enables Larger Batch Sizes]
        B --> H[Benefits for Transformers]
        H --> HA[Well-suited for Attention-Based Models]
        H --> HB[Reduces Internal Covariate Shift]
    end

```

---


### Key improvements and explanations

*   **Mathematical Foundation:** The LaTeX equation makes the diagram technically precise and clear. The equation is then broken down, so that you can expect to see the terms that come out of the equation.
*   **Specific Application in CLIP:**  The visual representation of the different parts of LayerNorm is given, which are taken from the text.

This version creates a more structured explanation of Layer Normalization within the context of CLIP, and it focuses on the properties that are important to explain the role and purpose of this function.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---