---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Matrix Determinant
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
title: Matrix Determinant
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
    A[Matrix Determinant] --> B{Definition}
    B --> C[Formal Definition]
    C --> D(Laplace Expansion)
    D --> E["det(A) = Σ<sub>j=1</sub><sup>n</sup> (-1)<sup>i+j</sup> a<sub>ij</sub> M<sub>ij</sub>"]
    E -- a<sub>ij</sub> --> F[Element at row i, column j]
    E -- M<sub>ij</sub> --> G[Minor of a<sub>ij</sub>]
    
    subgraph Explanation
        G --> G1[Minor of a<sub>ij</sub> is the determinant of the submatrix formed by removing row i and column j]
    
        G1 --> G2[Example:<br>if A is a 3x3 matrix, M<sub>12</sub> is the 2x2 determinant formed by removing row 1 and column 2]
        
        E --> H[Example]
        H --> I[A = ]
        I --> I1[−2 2 −3]
        I --> I2[−1 1 3]
        I --> I3[0 −1 2]

        H --> J["det(A) = (-1)<sup>1+2</sup> * 2 * det(M<sub>12</sub>) + (-1)<sup>2+2</sup> * 1 * det(M<sub>22</sub>) + (-1)<sup>3+2</sup> * (−1) * det(M<sub>32</sub>)"]
    
        J --> K["Step-by-step calculations to find det(M<sub>12</sub>), det(M<sub>22</sub>), det(M<sub>32</sub>)"]
        K --> L["Result:<br>det(A) = 18"]
    
        subgraph Properties
            B --> B1{Properties}
            B1 --> B2["det(I) = 1"]
            B1 --> B3["det(A) = det(A<sup>T</sup>)"]
            B1 --> B4["det(AB) = det(A)det(B)"]
            B1 --> B5["det(cA) = c<sup>n</sup>det(A)"]
            B1 --> B6["det(triangular matrix) = product of diagonal elements"]
            B1 --> B7["det(A) = product of eigenvalues of A"]
            B1 --> B8["det(A) = 0 if A is singular"]

            B1 --> B9["Examples:<br>det(Identity), det(Upper Triangular), det(Lower Triangular) with annotations"]
        end
    
        subgraph Application
            B --> B10{Applications}
            B10 --> B11[Invertibility Tests]
            B10 --> B12["Solving Linear Systems<br>(determinant of coefficient matrix)"]
            B10 --> B13["Eigenvalue Calculations (characteristic polynomial)"]
            B10 --> B14["Matrix Rank Determination (det(A) = 0 for rank-deficient matrices)"]
            B10 --> B15[Linear transformations and geometric properties of matrices]
        end
    end

```

----

### Explanation

This Mermaid graph visually outlines the definition and properties of a matrix determinant.  It uses a combination of nodes and subgraphs to organize the information logically.  The graph directly addresses the core concepts by:


*   **Defining the Determinant:** It starts with the definition of the determinant and uses Laplace expansion as the method for its calculation.
*   **Visualizing the Laplace Expansion:** The diagram shows the components of the Laplace expansion—the elements (a<sub>ij</sub>) and their corresponding minors (M<sub>ij</sub>)—clearly.
*   **Providing an Example:**  A concrete example (a 3x3 matrix) with step-by-step calculations demonstrates the calculation process.
*   **Highlighting Properties:**  Subgraph 'Properties' clearly displays important properties of determinants, including their connection to invertibility, eigenvalues, and matrix rank.
*   **Emphasizing Applications:**  Subgraph 'Applications' connects the determinant to practical use cases in linear algebra and machine learning.


This structure allows for a comprehensive understanding of matrix determinants, their calculations, and their applications.  To use this diagram for other types of matrices, simply update the matrix elements and their minors in the example section. Remember to provide concrete numerical examples to make the illustration more informative.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---