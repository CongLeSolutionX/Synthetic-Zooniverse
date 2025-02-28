---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Eigen-decomposition
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Eigen-decomposition - A Diagram Structure


```mermaid
---
title: Eigen-decomposition
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
    A[Eigen-decomposition] --> B{Concept}
    B --> C[Matrices and Eigenvalues]
    C --> D[Definition]
    D --> D1["For a square matrix A ∈ R<sup>n×n</sup>, an eigenvector x is a non-zero vector that, when multiplied by A, results in a scalar multiple of itself."]
    D --> D2["The scalar multiple is called the eigenvalue λ, and this relationship is represented as Ax = λx."]
    
    B --> E[Eigenvalues and Eigenvectors]
    E --> E1["Eigenvalues are the roots of the characteristic polynomial, det(A − λI) = 0."]
    E --> E2["Each eigenvalue has a corresponding eigenvector that satisfies the equation Ax = λx."]

    B --> F[Decomposition]
    F --> F1["A square matrix A can be decomposed into a product of three matrices."]
    F --> F2["A = QΛQ<sup>-1</sup>, where Q is a matrix whose columns are the orthonormal eigenvectors of A, and Λ is a diagonal matrix containing the corresponding eigenvalues."]

    B --> G[Properties]
    G --> G1["If A is symmetric, then its eigenvectors are orthogonal."]
    G --> G2["Eigenvectors corresponding to distinct eigenvalues are orthogonal."]
    G --> G3["Q is an orthogonal matrix, meaning Q<sup>T</sup>Q = QQ<sup>T</sup> = I (the identity matrix)." ]
    
    subgraph Example["Example"]
        F --> FA[Example: A = QΛQ<sup>-1</sup>]
        FA --> FB[Q = matrix of eigenvectors]
        FA --> FC[Λ = diagonal matrix of eigenvalues]
        FA --> FD[Example of how to calculate eigenvalues]
        FA --> FE[Proof of A = QΛQ<sup>-1</sup>]
    end

    
    subgraph Additional_Considerations["Additional Considerations"]
        B --> BA[Singular Matrices]
        BA --> BA1["If a matrix is singular (rank < n), some eigenvalues are zero.  The decomposition still holds, but with zero eigenvalues"]
        BA --> BA2["Eigenvectors corresponding to zero eigenvalues span the null space of the matrix"]

        B --> BB[Complex Eigenvalues]
        BB --> BB1["For non-symmetric matrices, eigenvalues and eigenvectors can be complex."]
        BB --> BB2["Focus on real eigenvalues in the context of symmetric matrices"]

        B --> BC[Computational Aspects]
        BC --> BC1["Eigen-decomposition is used in many algorithms for dimensionality reduction (e.g., PCA) and solving linear equations."]
        BC --> BC2["Numerical methods like the QR algorithm are often used to compute eigenvalues and eigenvectors"]
    end
    
```

---


### Explaination

This diagram uses the "Concept", "Eigenvalues and Eigenvectors", "Decomposition", "Properties", and "Additional Considerations" as logical groupings to illustrate the key elements of eigen-decomposition.  It also includes placeholders for illustrating how to calculate eigenvalues and eigenvectors. Remember to replace the placeholder examples with the specific details relevant to the context of your application.  Feel free to expand on the "Example" subgraph to illustrate specific computations.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---