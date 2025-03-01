---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Preliminaries on Vectors and Matrices
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Preliminaries on Vectors and Matrices - A Diagram Structure



```mermaid
---
title: Preliminaries on Vectors and Matrices
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
    A[Preliminaries on Vectors and Matrices] --> B{Vectors}
    B --> C[Column Vector]
    C --> D("x = [x<sub>1</sub>, x<sub>2</sub>, ..., x<sub>n</sub>]<sup>T</sup>")
    C --> E[Geometric Interpretation]
    E --> F(Magnitude/Norm)
    E --> G(Inner Product/Dot Product)
    G --> H("x<sup>T</sup>y = Σx<sub>i</sub>y<sub>i</sub>")
    F --> I("||x|| = √(x<sup>T</sup>x)")

    B --> C1[Row Vector]
    C1 --> D1("x = [x<sub>1</sub>, x<sub>2</sub>, ..., x<sub>n</sub>]")

    A --> B2{Matrices}
    B2 --> C2[Definition]
    C2 --> D2("A = [a<sub>ij</sub>] ∈ R<sup>m×n</sup>")
    C2 --> E2[Representation]
    E2 --> F2("A = [a<sub>1</sub>, a<sub>2</sub>, ..., a<sub>n</sub>], where a<sub>i</sub> are column vectors")
    E2 --> G2("A = [a<sub>1</sub><sup>T</sup>, a<sub>2</sub><sup>T</sup>, ..., a<sub>m</sub><sup>T</sup>]<sup>T</sup>, where a<sub>i</sub><sup>T</sup> are row vectors")


    A --> B3{Matrix Operations}
    B3 --> C3[Matrix Multiplication]
    C3 --> D3("A ∈ R<sup>m×n</sup>, B ∈ R<sup>n×p</sup>  → AB ∈ R<sup>m×p</sup>")
    C3 --> E3("Element-wise multiplication: (AB)<sub>ij</sub> = Σ<sub>k</sub> a<sub>ik</sub>b<sub>kj</sub>")
    C3 --> F3("Matrix-vector multiplication")
    B3 --> C4[Matrix Transposition]
    C4 --> D4("A<sup>T</sup> = [a<sub>ji</sub>] ∈ R<sup>n×m</sup>")

    A --> B4{Matrix Norms}
    B4 --> C5[Frobenius Norm]
    C5 --> D5("||A||<sub>F</sub> = √Σ<sub>i,j</sub> a<sub>ij</sub><sup>2</sup>")
    B4 --> C6[Induced p-norms]
    C6 --> D6("||A||<sub>p</sub> = sup<sub>x≠0</sub> ||Ax||<sub>p</sub> / ||x||<sub>p</sub>")


    subgraph Summary["Summary"]
        B --> BB[Key Concepts]
        BB --> BB1[Vectors, Matrices, Norms]
        BB --> BB2[Linear Transformations, Operations]
        BB --> BB3[Scalar Products, Projections]
    end

    subgraph Additional_Details["Additional Details"]
        E --> EE[Applications]
        EE --> EE1[Geometric Interpretations of Vectors]
        EE --> EE2[Computations in Machine Learning]
        EE --> EE3[Solving Linear Systems]

        D2 --> DD[Common Uses]
        DD --> DD1[Data Representation, Preprocessing, Linear Algebra]
        DD --> DD2[Coordinate Transformations, Basis Changes]
    end

```

---

### Explanation

This Mermaid diagram visually represents the "Preliminaries on Vectors and Matrices" section. It uses nodes and relationships to clarify the definitions and key concepts.  Each subgraph helps organize related information.

*   **Vectors:** Defines column and row vectors, shows the relationship between their geometric interpretations (magnitude/norm), and inner products.
*   **Matrices:** Explains matrix definition, common representations (column/row vector formats), and the significance of matrix multiplication.
*   **Matrix Operations:** Includes matrix transposition, highlighting its purpose and how it affects the representation of data.
*   **Matrix Norms:** Introduces the Frobenius norm and induced p-norms, emphasizing their role in measuring the magnitude of matrices.
*   **Summary:** Summarizes the overall structure of the concepts.
*   **Additional Details:** Expands on the applications of these concepts, making the content more practical and less abstract.


This structured diagram effectively encapsulates the core information, offering a visual roadmap for understanding the preliminaries. Remember that this is a general structure; you'd need to tailor it further with specific details from the document.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---