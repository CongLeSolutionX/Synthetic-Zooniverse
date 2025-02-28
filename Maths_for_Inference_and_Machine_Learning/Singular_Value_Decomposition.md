---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Singular Value Decomposition
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Singular Value Decomposition - A Diagram Structure




```mermaid
---
title: Singular Value Decomposition
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
    A["Singular Value Decomposition (SVD)"] --> B{Definition}
    B -- Matrix Decomposition --> C(A ∈ R<sup>m×n</sup>)
    B -- Orthogonal Matrices --> C1(U ∈ R<sup>m×m</sup>, V ∈ R<sup>n×n</sup>)
    B -- Singular Values --> C2(Σ ∈ R<sup>m×n</sup>)
    C --> D[A = UΣV<sup>T</sup>]
    
    subgraph SVD_Components["SVD Components"]
        C1 --> E(U<sup>T</sup>U = I<sub>m</sub>)
        C1 --> F(V<sup>T</sup>V = I<sub>n</sub>)
        C2 --> G("Σ = diag(σ<sub>1</sub>, σ<sub>2</sub>, ..., σ<sub>p</sub>)")
        G -- σ<sub>i</sub>  --> H[Singular Values]
        G -- σ<sub>1</sub> ≥ σ<sub>2</sub> ≥ ... ≥ σ<sub>p</sub> ≥ 0 --> I[Ordered Singular Values]
        G -- p = min(m, n) --> J[Dimension of Σ]

        E -- columns of U --> K[Left Singular Vectors]
        F -- columns of V --> L[Right Singular Vectors]
    
    end
    
    subgraph SVD_Applications["SVD Applications"]
        D --> M[Rank Reduction]
        M --> N[Dimensionality Reduction]
        D --> O[Data Compression]
        D --> P[Solving Linear Systems]
        D --> Q[Feature Extraction]
        D --> R["Finding Principal Components (PCA)"]
    end
    
    subgraph SVD_Formulae["SVD Formulae"]
        D --> S["Rank(A) = r"]
        S -- r --> T[Number of Non-Zero Singular Values]
        S -- r --> U["rank(A) = r"]
        S -- r --> V[σ<sub>1</sub> ≥ σ<sub>2</sub> ≥ ... ≥ σ<sub>r</sub> > 0]

        D --> W[Null Space]
        W -- Null Space --> X["span{v<sub>r+1</sub>, v<sub>r+2</sub>, ..., v<sub>n</sub>}"]
        D --> Y[Range/Column Space]
        Y -- Range/Column Space --> Z["span{u<sub>1</sub>, u<sub>2</sub>, ..., u<sub>r</sub>}"]

        D --> AA[A = Σ<sub>i=1</sub><sup>r</sup> σ<sub>i</sub>u<sub>i</sub>v<sub>i</sub><sup>T</sup>]
    end

```

---

### Explanation and Considerations

* **`A[Singular Value Decomposition (SVD)]`**:  This is the main node, representing the overall concept.
* **`B{Definition}`**:  Indicates the purpose of the diagram.
* **`C(A ∈ R<sup>m×n</sup>)`**:  A matrix A with dimensions m x n.
* **`C1(U ∈ R<sup>m×m</sup>, V ∈ R<sup>n×n</sup>)`**: Orthogonal matrices U (m x m) and V (n x n).  Critically, they are orthogonal.  The `E` and `F` nodes further explain the orthogonality properties.
* **`C2(Σ ∈ R<sup>m×n</sup>)`**:  The singular value matrix Σ.  Crucially, it's a diagonal matrix.  Nodes `G`, `H`, and `I` elaborate on this.
* **`D[A = UΣV<sup>T</sup>]`**: The core equation for SVD, showing the relationship between the matrix A and its decomposition.
* **`SVD_Components` subgraph**:  Explores the key components of the SVD decomposition, emphasizing the relationships between matrices.
* **`SVD_Applications` subgraph**:  Highlights the practical applications of SVD in various contexts.
* **`SVD_Formulae` subgraph**:  Connects the core equation to more detailed mathematical properties, such as rank, null space, and range.

---


### Key Concepts Illustrated

* **Orthogonality:** The diagram emphasizes the orthogonality of the columns of U and V, which is a defining characteristic of the decomposition.
* **Singular Values:** The diagram clearly defines singular values (σ<sub>i</sub>) as the diagonal elements of Σ.
* **Left and Right Singular Vectors:**  The diagram labels the columns of U and V as left and right singular vectors, respectively.
* **Rank, Null Space, and Range:**  The connections to the mathematical properties like rank, null space, and range make the diagram informative for a deeper understanding of SVD's impact on the structure of a matrix.

This diagram, following the structure and concepts in the previous response, effectively represents the core components and applications of Singular Value Decomposition. Remember to tailor the specific detail and connections to the context of your intended audience.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---