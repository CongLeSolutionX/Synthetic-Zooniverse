---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Matrix Decompositions
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Matrix Decompositions - A Diagram Structure


```mermaid
---
title: Matrix Decompositions
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
    A[Matrix Decompositions] --> B(Eigen-decomposition)
    B --> C{Square Matrix, A ∈ R<sup>n×n</sup>}
    C --> D[Eigenvalues, λ<sub>i</sub>]
    C --> E[Eigenvectors, q<sub>i</sub>]
    C --> F[Linearly Independent Eigenvectors]
    B --> G[Factorization]
    G --> H["A = QΛQ<sup>-1</sup>"]
    
    subgraph Eigen_Decomposition_Example["Eigen Decomposition Example"]
     H -- Example: --> I["A = [[2, 1], [1, 2]]"]
        I -- Eigenvalues: --> J["λ<sub>1</sub> = 1, λ<sub>2</sub> = 3"]
        I -- Eigenvectors: --> K["q<sub>1</sub> = [1, 1]<sup>T</sup>, q<sub>2</sub> = [-1, 1]<sup>T</sup>"]
        I -- Q: --> L["Q = [[1, -1], [1, 1]]"]
        I -- Λ: --> M["Λ = [[1, 0], [0, 3]]"]
    end

    A --> B1(QR decomposition)
    B1 --> C1{Real Square Matrix, A ∈ R<sup>n×n</sup>}
    B1 --> G1[Orthogonal Matrix, Q]
    B1 --> H1[Upper Triangular Matrix, R]
    B1 --> I1[Factorization]
    I1 --> J1["A = QR"]

    subgraph QR_Decomposition_Example["QR Decomposition Example"]
        J1 -- Example: --> K1["A = [[1, 2], [3, 4]]"]
        K1 -- Q: --> L1["Q = ... (Orthogonal Matrix)"]
        K1 -- R: --> M1["R = ... (Upper Triangular Matrix)"]
    end
    
    A --> B2("Singular Value Decomposition (SVD)")
    B2 --> C2{Matrix, A ∈ R<sup>m×n</sup>}
    B2 --> D2[Orthogonal Matrices, U, V]
    B2 --> E2[Singular Values, σ<sub>i</sub>]
    B2 --> F2[Factorization]
    F2 --> G2["A = UΣV<sup>T</sup>"]
    
    subgraph SVD_Example["SVD Example"]
        G2 -- Example: --> H2["A = [[1, 2], [3, 4]]"]
        H2 -- U: --> I2["U = ... (Orthogonal Matrix)"]
        H2 -- Σ: --> J2["Σ = ... (Diagonal Matrix of Singular Values)"]
        H2 -- V<sup>T</sup>: --> K2["V<sup>T</sup> = ... (Orthogonal Matrix)"]
    end
    
    A --> B3(Cholesky Decomposition)
    B3 --> C3{Symmetric Positive Definite Matrix, A ∈ R<sup>n×n</sup>}
    B3 --> D3[Lower Triangular Matrix, L]
    B3 --> E3[Factorization]
    E3 --> F3["A = LL<sup>T</sup>"]
    
    subgraph Cholesky_Decomposition_Example["Cholesky Decomposition Example"]
        F3 -- Example: --> I3["A = [[4, 12], [12, 52]]"]
        I3 -- L: --> J3["L = ... (Lower Triangular Matrix)"]
    end
    
    A --> B4(LU Decomposition)
    B4 --> C4{Matrix, A ∈ R<sup>m×n</sup>}
    B4 --> D4[Lower Triangular Matrix, L]
    B4 --> E4[Upper Triangular Matrix, U]
    B4 --> F4[Permutation Matrix, P]
    F4 --> G4["PA = LU"]
    
```

---


### Explanation and Considerations

* **Eigen-decomposition:** Decomposes a square matrix into eigenvectors and eigenvalues.  Crucial for understanding the fundamental properties of a matrix, such as its rank and linear transformations.
* **QR decomposition:** Decomposes a matrix into an orthogonal matrix (Q) and an upper triangular matrix (R).  Used for solving linear systems, generating orthogonal bases, and eigenvalue computations.
* **Singular Value Decomposition (SVD):** Decomposes any matrix into three matrices (U, Σ, V<sup>T</sup>).  Fundamental for dimensionality reduction, finding low-rank approximations, and understanding a matrix's rank, null space, and range.
* **Cholesky Decomposition:** Decomposes a symmetric positive-definite matrix into a lower triangular matrix (L) and its transpose (L<sup>T</sup>).  Important for solving systems of linear equations and various computations in statistics and machine learning.
* **LU Decomposition:** Decomposes a matrix into a lower triangular matrix (L), an upper triangular matrix (U), and a permutation matrix (P).  Used for solving systems of linear equations, calculating determinants, and more.


### Illustrative Examples

The subgraphs provide example matrices and their decomposed parts to make the concepts concrete.  Each subgraph is designed to show a typical decomposition example.

**Diagram Organization:**

The diagram uses subgraphs for illustrative examples to break down each type of decomposition. This helps in presenting the concept in a structured and clear manner.


**How to Use for Further Analysis:**

This diagram can be expanded to include specific algorithms (e.g., Gram-Schmidt process for QR), properties (e.g., symmetry, positive definiteness), and applications (e.g., dimensionality reduction with SVD, solving linear systems with LU).  You can tailor the specific examples to match your needs.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---