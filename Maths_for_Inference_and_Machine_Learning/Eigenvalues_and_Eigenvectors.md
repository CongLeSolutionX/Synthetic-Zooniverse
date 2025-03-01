---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Eigenvalues and Eigenvectors
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## A Diagram Structure



```mermaid
---
title: Eigenvalues and Eigenvectors
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
    A[Eigenvalues and Eigenvectors] --> B{Definition}
    B --> C[Eigenvector]
    C --> D(A vector x such that Ax = λx)
    D --> E("A is a square matrix")
    D --> F("λ is a scalar, the eigenvalue")

    B --> G[Eigenvalue]
    G --> H("A scalar λ that satisfies det(A − λI) = 0")
    H --> I("A is a square matrix")
    H --> J("I is the identity matrix")

    subgraph Example
        B -- Example:<br>A = [[2, 1], [1, 2]] --> K
        K -- x = [1, 1] --> L
        L -- λ = 3 --> M
        K -- x = [-1, 1] --> N
        N -- λ = 1 --> O
    end

    subgraph Properties
        B --> P{Properties of Eigenvalues and Eigenvectors}
        P --> Q[Real Eigenvalues and Eigenvectors]
        P --> R[Eigenvectors Corresponding to Distinct Eigenvalues are Orthogonal]
        P --> S[Eigenvalues and Eigenvectors are Critical in Decomposition]

        Q -- Example:<br>Symmetric matrices<br>(e.g., covariance matrices) --> T("Always have real eigenvalues and eigenvectors")
        R -- Example:<br>PCA, SVD, and other matrix decompositions --> U("Crucial for linear transformations and dimensionality reduction")
        S -- Example:<br>Spectral Graph Theory, Machine Learning Algorithms --> V("Basis for understanding complex data structures and algorithms");
    end

    subgraph Summary
        B --> AA["Computational Aspects"]
        AA --> AB("Eigenvalues and eigenvectors are often computed numerically, not always analytically, as solving a polynomial equation")
        AA --> AC("Eigenanalysis algorithms like the QR algorithm are often employed for efficiency")
        AA --> AD("Libraries such as NumPy (Python) and LAPACK (C++) provide optimized routines for eigenvalue and eigenvector computations")
    end

```





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---