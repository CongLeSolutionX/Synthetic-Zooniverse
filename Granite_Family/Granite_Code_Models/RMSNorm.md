---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2405.04324"
---



# RMSNorm
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## RMSNorm - A Diagrammatic Guide 

The diagram below illustrates the context of RMSNorm (Root Mean Square Layer Normalization) technique within the "Granite Code Models" architecture. It prioritizes a conceptual understanding of its role and benefit. If the user asks for further mathematical explanation, that can be addressed as well.




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
graph TD
    A[Normalization Techniques] --> B{RMSNorm}
    B --> C[Granite-3B-Code]
    B --> D[Granite-8B-Code]
    B --> E[Computational Efficiency]
    E --> F[Replaces LayerNorm]
    F --> G[Reduces Training Time]

    style B fill:#ccf3,stroke:#333,stroke-width:2px
    B -- Used in --> C
    B -- Used in --> D
    B -- (Zhang & Sennrich, 2019) --> A
    
```

----


### Explanation

*   **Central Concept:** `RMSNorm` (Root Mean Square Layer Normalization) is highlighted as the primary focus.
*   **Usage:** The connections to `Granite-3B-Code` and `Granite-8B-Code` show where RMSNorm is employed within the model family.
*   **Benefits:** The connections to `Computational Efficiency` and `Replaces LayerNorm` explain the main motivation for choosing RMSNorm.
*   **Reference:**  The source of RMSNorm is cited as (Zhang & Sennrich, 2019)
*   **Style**: Node fill-style added to the central concept.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---