---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Thin SVD
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Thin SVD - A Diagram Structure



```mermaid
---
title: Thin SVD
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
graph TD
    A[Thin SVD] --> B{Definition}
    B --> C[Matrix Decomposition]
    C --> D[A ∈ R<sup>m×n</sup>]
    
    subgraph SVD_Decomposition["SVD Decomposition"]
        D -- m ≥ n --> E[A = U<sub>1</sub>Σ<sub>1</sub>V<sub>T</sub><sup>1</sup>]
        E -- U<sub>1</sub> = [u<sub>1</sub>, ..., u<sub>n</sub>]  ∈ R<sup>m×n</sup> --> F
        E -- Σ<sub>1</sub> = diag(σ<sub>1</sub>, ..., σ<sub>n</sub>) ∈ R<sup>n×n</sup> --> G
        E -- V<sub>1</sub><sup>T</sup> = [v<sub>1</sub>, ..., v<sub>n</sub>]<sup>T</sup> ∈ R<sup>n×n</sup> --> H
    
        F -- u<sub>i</sub> are left singular vectors --> I
        G -- σ<sub>i</sub> are singular values --> J
        H -- v<sub>i</sub> are right singular vectors --> K
    end
    
    subgraph Summary["Summary"]
        E -- Key Properties --> L
        L -- U<sub>1</sub><sup>T</sup>U<sub>1</sub> = I<sub>n</sub> --> M
        L -- V<sub>1</sub><sup>T</sup>V<sub>1</sub> = I<sub>n</sub> --> N
        L -- rank(A) = n --> O
        L -- A = ∑<sub>i=1</sub><sup>n</sup> σ<sub>i</sub>u<sub>i</sub>v<sub>i</sub><sup>T</sup> --> P
    end
    
```


---

### Explanation

This Mermaid diagram depicts Thin SVD, focusing on its core definition as a matrix decomposition.

* **A (Thin SVD):** The main topic.
* **B (Definition):**  Indicates that Thin SVD is a specific case of SVD.
* **C (Matrix Decomposition):**  Highlights the core concept that Thin SVD decomposes a matrix.
* **D (A ∈ R<sup>m×n</sup>):**  Specifies the input matrix is of size m x n.  Crucially, it emphasizes the condition m ≥ n.
* **E (A = U<sub>1</sub>Σ<sub>1</sub>V<sub>T</sub><sup>1</sup>):** This shows the core decomposition formula, emphasizing the subscripts on U, Σ, and V to denote the thin variant.
* **F, G, H (Left Singular Vectors, Singular Values, Right Singular Vectors):** Clearly identifies the components of the decomposition and their significance (singular values are on the diagonal of Σ).
* **I, J, K (Descriptions of Components):** Provides a concise description of the components to help readers understand the diagram's elements.
* **L (Key Properties):**  A subgraph to explicitly show the critical properties that distinguish the thin SVD.
* **M, N, O (Key Properties Details):**  Explains the important properties specific to thin SVD, including orthogonality of U<sub>1</sub> and V<sub>1</sub>, and the rank of A being equal to n.
* **P (Expansion):** Shows the summation form of the decomposition, which helps visualize how the individual components contribute to the entire matrix.

----

### Key Improvements and Considerations

* **Clarity:** Uses clear labels and concise descriptions.
* **Specificity:** Employs precise mathematical notation (e.g., R<sup>m×n</sup>, diag(...)) for accuracy.
* **Structure:** Organizes the information logically to guide the reader through the concept.
* **Conditions:** Explicitly shows that Thin SVD applies when *m ≥ n*.

This improved diagram is more focused and informative, helping to clarify the core concept of Thin SVD. Remember that in a real-world application, you would need to provide more specific context about how Thin SVD is used and why.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---