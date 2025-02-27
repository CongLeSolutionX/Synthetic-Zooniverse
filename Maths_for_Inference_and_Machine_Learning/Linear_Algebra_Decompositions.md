---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Linear Algebra Decompositions
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Linear Algebra Decompositions Overview


```mermaid
---
title: Linear Algebra Decompositions (Beyond QR and SVD)
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%{
  init: {
    'fontFamily': 'verdana',
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
    A["Linear Algebra Decompositions"] --> B("Eigenvalue Decomposition")
    B --> C{"Nodes and Relationships"}
    
    subgraph Eigenvalue_Decomposition_Example["Eigenvalue Decomposition Example"]
    style Eigenvalue_Decomposition_Example fill:#c951,stroke:#333,stroke-width:2px
        C -- Example:<br>A = QΛQ<sup>-1</sup> --> D
        D -- Matrix A --> E[A]
        D -- Eigenvectors Q --> F[Q]
        D -- Eigenvalues Λ --> G[Λ]
        D -- Inverse of Q --> H[Q<sup>-1</sup>]
    end
    
    A --> B1(LU Decomposition)
    B1 --> C1{Nodes and Relationships}
    
    subgraph LU_Decomposition_Example["LU Decomposition Example"]
    style LU_Decomposition_Example fill:#c955,stroke:#333,stroke-width:2px
        C1 -- Example:<br>A = LU --> D1
        D1 -- Matrix A --> E1[A]
        D1 -- Lower Triangular Matrix L --> F1[L]
        D1 -- Upper Triangular Matrix U --> G1[U]
    end
    
    A --> B2(Cholesky Decomposition)
    B2 --> C2{Nodes and Relationships}
    
    subgraph Cholesky_Decomposition_Example["Cholesky Decomposition Example"]
    style Cholesky_Decomposition_Example fill:#c555,stroke:#333,stroke-width:2px
        C2 -- Example:<br>A = LLT --> D2
        D2 -- Matrix A --> E2[A]
        D2 -- Lower Triangular Matrix L --> F2[L]
    end

    A --> B3(QR Decomposition)
    B3 --> C3{Nodes and Relationships}
    
    subgraph QR_Decomposition_Example["QR Decomposition Example"]
    style QR_Decomposition_Example fill:#c255,stroke:#333,stroke-width:2px
        C3 -- Example:<br>A = QR --> D3
        D3 -- Matrix A --> E3[A]
        D3 -- Orthogonal Matrix Q --> F3[Q]
        D3 -- Upper Triangular Matrix R --> G3[R]
    end
    
    A --> B4("Singular Value Decomposition<br>(SVD)")
    B4 --> C4{Nodes and Relationships}
    
    subgraph SVD_Decomposition_Example["SVD Decomposition Example"]
    style SVD_Decomposition_Example fill:#c299,stroke:#333,stroke-width:2px
        C4 -- Example:<br>A = UΣV<sup>T</sup> --> D4
        D4 -- Matrix A --> E4[A]
        D4 -- Left Singular Vectors U --> F4[U]
        D4 -- Singular Values Σ --> G4[Σ]
        D4 -- Right Singular Vectors V --> H4[V]
    end
   
    
    subgraph Summary["Summary"]
    style Summary fill:#cfc3,stroke:#333,stroke-width:2px
        C --> CC[Mathematical Relationships]
        CC --> CC1[Factorizations and decompositions are crucial for computational efficiency and understanding matrix properties]
        CC --> CC2[Eigenvalues and eigenvectors reveal essential information about the matrix's behavior and structure, important for dimensionality reduction]
        CC --> CC3[Decompositions allow for algorithms that can reduce the cost of matrix calculations, enabling operations on larger matrices and systems]
    end

    classDef Style_for_Cholesky_Decomposition fill:#c555,stroke:#333,stroke-width:2px
    class B2 Style_for_Cholesky_Decomposition

    classDef Style_for_LU_Decomposition fill:#c955,stroke:#333,stroke-width:2px
    class B1 Style_for_LU_Decomposition

    classDef Style_for_Eigenvalue_Decomposition fill:#c951,stroke:#333,stroke-width:2px
    class B Style_for_Eigenvalue_Decomposition

    classDef Style_for_QR_Decomposition fill:#c255,stroke:#333,stroke-width:2px
    class B3 Style_for_QR_Decomposition

    classDef Style_for_SVD_Decomposition fill:#c299,stroke:#333,stroke-width:2px
    class B4 Style_for_SVD_Decomposition
    
```


### Explanation and Considerations


This Mermaid diagram extends the structure to incorporate `Eigenvalue Decomposition`, `LU Decomposition`, `Cholesky Decomposition`, and a comprehensive summary.

* **Nodes:** Each decomposition method (`Eigenvalue`, `LU`, `Cholesky`, `QR`, `SVD`) is represented as a node, with sub-graphs illustrating specific examples.  Matrices (A, Q, Λ, L, U, Σ, R) are depicted as separate nodes, and the relationships between them are crucial.
* **Relationships:** Arrows (directed and undirected) connect the relevant nodes, illustrating how the various decompositions relate to one another and the original matrix.
* **Context:**  The summary subgraph emphasizes the *why* behind these decompositions.  It highlights their importance in computational efficiency, revealing matrix properties, and enabling more complex calculations.
* **Visual Clarity:** The color-coded subgraphs enhance readability and allow for quick identification of each decomposition method.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---