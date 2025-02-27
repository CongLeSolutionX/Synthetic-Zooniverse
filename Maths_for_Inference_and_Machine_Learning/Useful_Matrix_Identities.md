---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Useful Matrix Identities
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
title: Useful Matrix Identities
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
    A[Useful Matrix Identities] --> B{General Form};
    B --> C(Inverse of a Sum)
    C --> CA[" (A + UCV)^−1 = A^−1 − A^−1U(C^−1 + VA^−1U)^−1VA^−1 "]
    
    B --> D(Woodbury Matrix Identity);
    D --> DA[" (A + UCV)^−1 = A^−1 − A^−1U(C^−1 + VA^−1U)^−1VA^−1 "]

    B --> E(Kailath Inverse);
    E --> EA["(A + BC)^−1 = A^−1 − A^−1B(C + BA^−1B)^−1BA^−1 "]
    
    B --> F{Specific Cases and Applications}

    F --> FA("In machine learning, these identities are crucial for computationally efficient calculations. For instance, the Woodbury matrix identity is frequently used to compute the inverse of a matrix that is updated by adding a rank-one matrix (often in the context of Bayesian linear regression or other situations with incremental data)")

    F --> FB("Careful attention to the conditions of the matrices (invertibility, symmetry, etc.) is required. For example, the Woodbury identity only holds if A is invertible, and the inverse (C^−1 + VA^−1U) needs to be well-defined, which requires that C is also invertible")

    F --> FC(These identities often appear in matrix derivations, where you need to differentiate expressions involving matrix inverses or sums of matrices. For example, you might find that differentiating the trace of a matrix product necessitates the application of these identities to avoid cumbersome and possibly error-prone manual derivations)

```

-----


### Explanation and Considerations


*   **General Form (B):** The diagram highlights the general structure of the matrix identities.  The `subgraph` and `style` are used to organize and give emphasis to the general ideas.

*   **Specific Cases (F):** The `subgraph` and its connected nodes (`FA`, `FB`, and `FC`) provide crucial contextual information about the practical usage and importance of these identities in machine learning and related fields.  It points out crucial conditions and considerations when applying these identities.


*   **Detailed Identities (C, D, E):** These are the core matrix identities.  They are presented in a clear, concise format suitable for reference.  Note that the diagram structure allows for easy expansion with additional, more specific cases if needed.


-----


### Important Considerations for Diagrams


* **Contextualization:** The diagram should be supplemented with explanations of *why* these identities are important.  Mention specific scenarios in machine learning where they are frequently used (Bayesian methods, matrix inversions in large datasets, etc.).

* **Conditions:**  Highlight the necessary conditions for each identity to hold (e.g., invertibility, symmetry).  This is critical for proper application.

* **Applications:** Connect the identities to practical applications in machine learning, like linear regression, Bayesian inference, and dimensionality reduction.

* **Computational Efficiency:** Explain how these identities lead to computational efficiency improvements (e.g., avoiding direct matrix inversions in large datasets).




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---