---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original Source: "https://arxiv.org/pdf/2412.19437"
---



# Multi-Head Latent Attention (MLA) Architecture
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Multi-Head Latent Attention (MLA) Architecture - A Diagrammatic Guide



```mermaid
---
title: "DeepSeek-V3 Technical Report"
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
    "graph": { "htmlLabels": false, 'curve': 'cardinal' },
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
    subgraph MLA_Architecture["Multi-Head Latent Attention (MLA) Architecture"]
        A["Multi-Head Latent Attention (MLA)"] --> B{Input}
        B --> C("h<sub>t</sub>")
        C --> D("Embedding Dimension (d)")
        C --> E("Number of Attention Heads (n<sub>h</sub>)")
        C --> F("Dimension per Head (d<sub>h</sub>)")
        
        
        B --> G("Low-rank Joint Compression")

        G --> H("Down-Projection Matrix (W<sub>DKV</sub>)")
        H --> I("Compressed Latent Vector (c<sub>KV</sub><sup>t</sup>)")
        I --> J("KV Compression Dimension (d<sub>c</sub>)")
        
        G --> K("Up-Projection Matrix (W<sub>U</sub><sup>K</sup>)")
        K --> L("Key")
        
        G --> M("Up-Projection Matrix (W<sub>U</sub><sup>V</sup>)")
        M --> N("Value")
        
        B --> O("RoPE")
        O --> P("Decoupled Key (k<sup>R</sup><sub>t,i</sub>)")
        O --> Q("Decoupled Key Matrix (W<sub>KR</sub>)")

        L --> R("Concatenation (k<sup>C</sup><sub>t,i</sub>)")
        N --> S("Concatenation (v<sup>C</sup><sub>t,i</sub>)")
        
        R --> T("Attention Queries (q<sub>t,i</sub>)")
        S --> U("Attention Values (v<sub>j,i</sub>)")
        
        T --> V("Softmax")
        V --> W("Attention Output (o<sub>t,i</sub>)")
        W --> X("Output Projection Matrix (W<sub>O</sub>)")
        X --> Y("Final Attention Output (u<sub>t</sub>)")
    end
    
    subgraph Summary["Summary"]
        Y -- d --> Z("d<sub>h</sub> * n<sub>h</sub>")
        Z -- d<sub>c</sub> --> AA("d<sub>c</sub> << d<sub>h</sub> * n<sub>h</sub>")

    end
    
```



---


### Explanation

This Mermaid diagram visualizes the Multi-Head Latent Attention (MLA) architecture, aligning with the provided text.

* **Input (B):**  The attention input for the 𝑡-th token (h<sub>t</sub>).
* **Low-rank Joint Compression (G):** This is a core step.  It represents the process of reducing the dimensionality of keys and values.
* **Matrices (H, K, M):** Show the down-projection and up-projection matrices, crucial for the low-rank compression.
* **Compressed Latent Vectors (I):** The compressed representation of keys and values.
* **Rotary Position Embedding (RoPE) (O):**  Explicitly shows RoPE as a separate operation applied to the keys.
* **Decoupled Keys/Values (P,Q):** Shows the decoupled keys and values generated via RoPE.
* **Concatenation (R,S):** Represents the concatenation of the compressed latent vectors and RoPE-embedded keys and values.
* **Attention Queries (T), Attention Values (U):** The diagram highlights the queries and values used in the attention calculation.
* **Softmax (V):** The core attention step where the similarity between queries and keys is calculated.
* **Output Projection (X):** The final transformation of the attention outputs.
* **Final Attention Output (Y):** The output of the MLA mechanism, which is a crucial input to the next layer.
* **Summary (AA):** A small subgraph to emphasize the crucial dimension reduction achieved by MLA (d<sub>c</sub> << d<sub>h</sub> * n<sub>h</sub>).

**Important Considerations for Further Detail:**

* **Inline Equations:**  Include equations (1) through (11) from the original text as inline equations within the relevant nodes for precise representation.  This will add clarity.
* **Visual Cues:** Use colors (e.g., different shades of blue for different vectors) to differentiate the different vectors and matrices.
* **Layer Numbers:** Include layer numbers (e.g., 'Attention Layer L') to explicitly relate this component to the overall network architecture.
* **Connections:**  Clearly show the connections between the different components, such as the flow of input (h<sub>t</sub>) and the production of the output (u<sub>t</sub>).




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---