---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2405.04324"
---



# Feed Forward Network Component within the Transformer Architecture
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Feed Forward Network - A Diagrammatic Guide 


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
    A["Feed Forward Network<br>(FFN)"] --> B{Components}
    style A fill:#ccf3,stroke:#333,stroke-width:2px
    B --> C[Linear Layer 1]
    B --> D{Activation Function}
    B --> E[Linear Layer 2]
    D --> F[SwiGLU]
    D --> G[GELU]

    C -- "Input:<br>Output from Attention Block" --> D
    D --  "Output:<br>To Linear Layer 2" --> E
    F -- "Used in:<br>Granite-3B-Code, Granite-8B-Code" --> E
    G -- "Used in:<br>Granite-20B-Code, Granite-34B-Code" --> E
    E -- "Output:<br>To Subsequent Layer" --> H
    H[Output of FFN]
    

    subgraph SwiGLU_Details["SwiGLU Details"]
    F -- swish(x) = x * sigmoid(x) --> I[Swish Activation]
    I --> J["GLU (Gated Linear Unit)"]
    end
    
    subgraph GELU_Details["GELU Details"]
    G -- GELU(x) = x * Φ(x) --> K["Gaussian Error Linear Unit"]
    K -- Φ(x): Standard Normal CDF --> L["CDF Details"]
    end
    
```

Key elements:

*   **FFN as the Central Node:** Highlights that we are focusing on this specific part of the Transformer.
*   **Components (Linear Layers, Activation Function):** Sub-nodes that break down the FFN.
*   **Activation Function Variation:** Notes that the activation function differs based on the model size (SwiGLU for smaller, GELU for larger).
*   **Data Flow:** Clear arrows showing how data moves through the FFN.
*   **Annotations (Model Usage):** Specifies which activation function is used in each model.

Here's a semantic breakdown of the diagram:

1.  **Feed Forward Network (FFN):**
    *   This component is the heart of the diagram, representing a key element of the Granite Code Models. It's a distinct processing block within each transformer layer.

2.  **Components:**
    *   These are the building blocks of the FFN. The "Linear Layer 1" applies an affine transformation to the input, and the "Linear Layer 2" maps the result of the activation function back to the expected output dimensions. The activation function introduces non-linearity.

3.  **Activation Functions (SwiGLU, GELU):**
    *   The choice of activation function depends on the model size, with SwiGLU used in smaller models (3B, 8B) and GELU in larger models (20B, 34B). SwiGLU (Swish-Gated Linear Unit) is computationally efficient, while GELU (Gaussian Error Linear Unit) can better capture complex data patterns.
*   **Data Flow:**
    *   Clear arrows indicate the flow of data: from the output of the attention block to the first linear layer, through the activation function, into the second linear layer, and then to the subsequent layer.
*   **Model Usage:**
    *   Labels indicate which activation function is used in each Granite Code Model. This emphasizes the architectural differences.





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---