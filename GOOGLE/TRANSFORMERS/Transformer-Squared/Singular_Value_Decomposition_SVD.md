---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2501.06252"
---



# Singular Value Decomposition (SVD)
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Singular Value Decomposition - A Diagrammatic Guide 



```mermaid
---
title: "Transformer-Squared: Self-Adaptive LLMs"
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
    "graph": { "htmlLabels": false, 'curve': 'linear' },
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
    subgraph SVD["Singular Value Decomposition<br>(SVD)"]
        A[SVD] --> B{Decomposition}
        B --> C(Weight Matrix W)
        C --> D(U)
        C --> E(Σ)
        C --> F("V<sup>T<sup>")
        
        D -- semi-orthogonal matrix  --> D1
        E -- diagonal matrix of singular values<br>(σ<sub>i<sub>) --> E1
        F -- semi-orthogonal matrix --> F1
        
        subgraph Mathematical_Representation["Mathematical Representation"]
            D1 -- "U = [u<sub>1<sub>, u<sub>2<sub>, ..., u<sub>m<sub>]"  --> D2
            E1 -- "Σ = diag{σ<sub>1<sub>, σ<sub>2<sub>, ..., σ<sub>p<sub>}" --> E2
            F1 -- "V<sup>T<sup> = [v<sub>1<sub>, v<sub>2</sub>, ..., v<sub>n<sub>]<sup>T<sup>" --> F2
            
            C --> G(W = U Σ V<sup>T<sup>)
            G -- formula representing decomposition --> G1

            %% Ordering of singular values
            G1 -- σ<sub>1<sub> ≥ σ<sub>2<sub> ≥ ... ≥ σ<sub>p<sub>  --> G2
        end
        
        subgraph Vector_Matrix_Operations["Vector-Matrix Operations"]
            C --> H{Linear Operation}
            H --> I["y = Σ<sub>i=1<sub><sup>r<sup> σ<sub>i<sub> u<sub>i<sub>v<sub>i<sub><sup>T<sup> x"]
            I -- orthogonal contributions --> I1
            I -- singular values modulate contribution --> I2
    
        end

        subgraph Applications["Applications"]
            A --> J{Applications}
            J --> K[Dimensionality Reduction]
            J --> L[Feature Extraction]
            J --> M[Model Approximation]
            
            K --> K1["Discarding minor singular components<br>(noise)"]
            K --> K2[Approximating with top-r singular vectors]
            L --> L1[Capturing variance]
            L --> L2[Identifying principal components]
            M --> M1[Reducing model complexity]
            M --> M2[Efficient storage and computation]
        end
    end
    
```

----

### Explanation of the Diagram

The diagram uses a hierarchical structure to illustrate the key components and applications of Singular Value Decomposition (SVD) within the context of large language model (LLM) fine-tuning.

* **Weight Matrix (W):** The diagram starts with the weight matrix (W) of a neural network layer as the central object. SVD decomposes this matrix.
* **SVD Decomposition:**  The core of the diagram visually represents the decomposition of the weight matrix (W) into three components:  U, Σ, and V<sup>T</sup>.  Key attributes (e.g., semi-orthogonal matrices, diagonal matrix of singular values) are explicitly labeled to highlight their mathematical characteristics.
* **Mathematical Representation:**  This subgraph further clarifies the mathematical form of the decomposition.  It shows how the weight matrix is expressed as the product of U, Σ, and V<sup>T</sup>. The crucial ordering of singular values (σ<sub>i</sub>) is also noted, emphasizing the inherent ordering and importance of these values.
* **Vector-Matrix Operations:**  This subgraph emphasizes that applying the weight matrix to an input vector (x) can be decomposed into a sum of independent terms. This emphasizes the orthogonal contributions of each singular component and the modulating role of singular values.
* **Applications:** This subgraph highlights the practical applications of SVD in LLM fine-tuning, especially focusing on dimensionality reduction, feature extraction, and model approximation.  It clarifies how discarding minor components, approximating with the top singular vectors, and capturing variance are crucial aspects.


This structured diagram effectively encapsulates the core concepts of SVD and its applicability to large language models, as discussed in the original text. Note that this diagram is an *abstract* representation; further details can be added with specific mathematical equations or references to the original text.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---