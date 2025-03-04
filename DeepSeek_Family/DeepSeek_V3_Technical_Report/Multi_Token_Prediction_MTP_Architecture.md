---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original Source: "https://arxiv.org/pdf/2412.19437"
---



# Multi-Token Prediction (MTP) Architecture
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Multi-Token Prediction (MTP) Architecture - A Diagrammatic Guide


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
    subgraph MTP_Architecture["Multi-Token Prediction (MTP) Architecture"]
        A["MTP Module k"] --> B("Shared Embedding Layer Emb(·)")
        A --> C("Shared Output Head OutHead(·)")
        A --> D("Transformer Block TRM<sub>k</sub>(·)")
        A --> E("Linear Projection Matrix M<sub>k</sub>")
        B --> F("Input Token Representation h<sub>i</sub><sup>k-1</sup>")
        B --> G("Embedding of Token t<sub>i+k</sub>")
        F -- h<sub>i</sub><sup>k-1</sup> --> H("RMSNorm(h<sub>i</sub><sup>k-1</sup>)")
        G -- "Emb(t<sub>i+k</sub>)" --> I("RMSNorm(Emb(t<sub>i+k</sub>))")
        H --> J("Concatenation")
        I --> J

        J --> K("h'<sub>i</sub><sup>k</sup>")
        K --> L("TRM<sub>k</sub>(h'<sub>i</sub><sup>k</sup>)")
        L --> M("h<sub>i</sub><sup>k</sup>")
        M --> N("Output Head OutHead(·)")
        N --> O("Prediction Probability Distribution P<sub>k</sub><sup>i+k+1</sup>")
        O -- "P<sub>k</sub><sup>i+k+1</sup>" --> P("Cross-Entropy Loss L<sub>k</sub><sup>MTP</sup>")
    end
    
```



---

### Explanation of the MTP Module (k)

* **Shared Embedding Layer (Emb(·))**: This layer is shared across all MTP modules and the main model. It converts input tokens into vector representations of a fixed dimension (d).
* **Shared Output Head (OutHead(·))**:  Also shared, this layer maps the output of the MTP module to logits (raw scores) for the vocabulary, and then applies the Softmax function to compute the probability distribution for the k-th additional predicted token.
* **Transformer Block (TRM<sub>k</sub>(·))**: A standard Transformer block, operating on the combined representation at each prediction depth.
* **Linear Projection Matrix (M<sub>k</sub>):** A matrix that linearly projects the combined representation from the (k-1)th and kth depths.
* **Input Token Representation (h<sub>i</sub><sup>k-1</sup>):**  The hidden state representation of the i-th input token at the (k-1)th prediction depth.  This is the output of the main model or the previous MTP module.
* **Embedding of Token (Emb(t<sub>i+k</sub>))**: The embedding of the (i+k)-th token.
* **RMSNorm Operations:**  Normalization operations (RMSNorm) applied to both the input token representation and the embedded token at each step.
* **Concatenation:** The outputs of the RMSNorm operations are concatenated to create the combined representation (h'<sub>i</sub><sup>k</sup>).
* **Output Representation (h<sub>i</sub><sup>k</sup>):** The output representation of the i-th token at the kth prediction depth after passing through the Transformer block.
* **Prediction Probability Distribution (P<sub>k</sub><sup>i+k+1</sup>):** The probability distribution over the vocabulary for the (i+k+1)th token.

* **Cross-Entropy Loss (L<sub>k</sub><sup>MTP</sup>):**  The cross-entropy loss associated with predicting the k-th additional token for a given input token at a given prediction depth.

---

### Key Relationships

* **Shared Resources:** The embedding layer and output head are shared across all modules. This is a significant aspect of the architecture.
* **Sequential Prediction:** The graph emphasizes the sequential nature of the MTP process, with each module (k) building on the previous one's output.
* **Causal Chain:**  Each MTP module maintains the causal chain of predictions, differing from the independent prediction method used in some prior work.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---