---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2405.04324"
---



# The GELU (Gaussian Error Linear Units) activation function
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## GELU - A Diagrammatic Guide 

Here's a Mermaid diagram focusing specifically on the GELU (Gaussian Error Linear Units) activation function, based on the information from the original document:

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
    A[GELU Activation Function] --> B{Context}
    B --> C["Used in Larger Granite Models<br>(20B, 34B)"]
    B --> D[Replaces SwiGLU in Smaller Models]
    B --> E[MLP Block Component]
    
    C --> F[More Complex Architectures]
    D --> G[Smaller Architectures]
    E --> H[Part of FeedForward Network in Transformer]
    
    A --> I{Mathematical Definition}
    I --> J["Approximation:<br> 0.5x(1 + tanh[√(2/π) * (x + 0.044715x³)])"]
    I --> K["Exact:<br> x * Φ(x) , Φ(x) <br>is the CDF of the Standard Normal Distribution"]

    style A fill:#ccf3,stroke:#333,stroke-width:2px
    
```

---


### Explanation

*   **Node A ("GELU Activation Function"):** This is the central concept.
*   **Node B ("Context"):** This central node shows the overall purpose of the GELU activation function.
*   **Nodes C & D:** specify the models that the GELU activation function applies to.
*   **Node E:** specifies the component of the larger architecture that the GELU is used for.
*   **Node I:** is the mathematical definition of the function that will be useful. 




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---