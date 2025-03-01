---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Matrix Pseudo-Inverse
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
title: Matrix Pseudo-Inverse
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
    A[Matrix Pseudo-Inverse] --> B{Definitions}
    B --> C(Full Column Rank)
    C --> D["A<sup>†</sup> = (A<sup>T</sup>A)<sup>−1</sup>A<sup>T</sup>"]
    
    B --> E(Full Row Rank)
    E --> F["A<sup>†</sup> = A<sup>T</sup>(AA<sup>T</sup>)<sup>−1</sup>"]
    
    B --> G(Square and Invertible)
    G --> H["A<sup>†</sup> = A<sup>−1</sup>"]
    
    subgraph Summary
        C --> CA[Conditions for Full Column Rank]
        CA --> CA1["rank(A) = n, n ≤ m"]
        CA --> CA2[A<sup>T</sup>A is invertible]
        CA --> CA3["A<sup>†</sup>A = I (left inverse)"]
        
        E --> EA[Conditions for Full Row Rank]
        EA --> EA1["rank(A) = m, m ≤ n"]
        EA --> EA2[AA<sup>T</sup> is invertible]
        EA --> EA3["AA<sup>†</sup> = I (right inverse)"]

        G --> GA[Conditions for Square and Invertible]
        GA --> GA1[A is square]
        GA --> GA2[A is invertible]
        GA --> GA3["A<sup>†</sup> = A<sup>−1</sup>"]
    end
    
```

----


### Explanation

The diagram shows the matrix pseudo-inverse (A<sup>†</sup>) as a generalization of the inverse, applicable in cases where the matrix isn't square or invertible.  It's defined differently depending on whether the matrix has full column rank or full row rank.  A square, invertible matrix's pseudo-inverse is simply its regular inverse.


*   **Full Column Rank (C):**  If a matrix has full column rank (meaning the number of linearly independent columns equals the number of columns, and the number of columns is less than or equal to the number of rows), its pseudo-inverse is calculated using the formula `A<sup>†</sup> = (A<sup>T</sup>A)<sup>−1</sup>A<sup>T</sup>`. This ensures a left inverse (A<sup>†</sup>A = I).

*   **Full Row Rank (E):** If a matrix has full row rank (meaning the number of linearly independent rows equals the number of rows, and the number of rows is less than or equal to the number of columns), its pseudo-inverse is given by the formula `A<sup>†</sup> = A<sup>T</sup>(AA<sup>T</sup>)<sup>−1</sup>`. This ensures a right inverse (AA<sup>†</sup> = I).

*   **Square and Invertible (G):**  If the matrix is square and invertible, its pseudo-inverse is simply its inverse (A<sup>†</sup> = A<sup>−1</sup>). This is a special case where the two formulas above reduce to a single one.

The `Summary` subgraph clarifies the conditions that must hold for each case, linking the conditions (full column rank, full row rank, or square and invertible) to the appropriate formula for calculating the pseudo-inverse.  This diagram effectively visualizes the different scenarios and the corresponding calculations.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---