---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Symmetric Matrices
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Symmetric Matrices - A Diagram Structure



```mermaid
---
title: Symmetric Matrices
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
    A[Symmetric Matrices] --> B{Definition}
    B --> C[Symmetric Property]
    C --> D["A = A<sup>T</sup>"]
    
    subgraph Example_Symmetric_Matrix["Example Symmetric Matrix"]
        D -- Example:  A =  [ 1  2 ]
                        [ 2  3 ] --> E
    end
    
    B --> E1[Real Eigenvalues]
    B --> E2[Orthogonal Eigenvectors]
    
    subgraph Eigenvalue_Example["Eigenvalue Example"]
    E1 -- Example:  λ<sub>1</sub> = 2,  λ<sub>2</sub> = 4, corresponding eigenvectors are u<sub>1</sub>, u<sub>2</sub>
                    u<sub>1</sub><sup>T</sup> u<sub>2</sub> = 0  --> F
    end

    
    B --> E3[Eigendecomposition]
    E3 --> G["A = QΛQ<sup>-1</sup>"]
    G -- Q: Orthogonal matrix of eigenvectors --> H
    G -- Λ: Diagonal matrix of eigenvalues --> I
    
    B --> E4[Singularity]
    E4 --> J["If rank(A) = r < n, then n-r eigenvectors correspond to zero eigenvalues"]
    J --> K["Qr: n x r matrix of non-zero eigenvectors; Λr: r x r diagonal matrix of non-zero eigenvalues"]
    
```

---

### Explanation

This Mermaid diagram represents the key properties and characteristics of symmetric matrices.  It's designed to be easily understood and provides concrete examples to illustrate the concepts.

* **Definition:** The diagram starts by defining a symmetric matrix as a square matrix equal to its transpose.
* **Eigenvalues and Eigenvectors:** It highlights that symmetric matrices have real eigenvalues and orthogonal eigenvectors.  The example illustrates these points.
* **Eigendecomposition:** The diagram shows the eigendecomposition formula (`A = QΛQ<sup>-1</sup>`).  It visually connects the matrix `A` with the orthogonal matrix of eigenvectors (`Q`) and the diagonal matrix of eigenvalues (`Λ`).
* **Singularity:** The diagram addresses the case where a symmetric matrix is singular (rank less than its dimension). It defines the components (`Qr` and `Λr`) of the eigendecomposition in the singular case.

This diagram is designed to be intuitive and easy to follow, clearly illustrating the relationship between the definition of a symmetric matrix and its important properties regarding eigenvalues, eigenvectors, and eigendecomposition.  It also incorporates the concept of singularity, which is crucial for understanding the limitations of applying certain operations.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---