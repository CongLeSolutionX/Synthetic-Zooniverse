---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Positive and Negative Deﬁnite Matrices
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
title: Positive and Negative Definite Matrices
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
    A[Positive and Negative Definite Matrices] --> B{Definition}
    B --> C(Positive Definite)
    C --> CA[∀ x ∈ ℝ<sup>n</sup>, x<sup>T</sup>Ax > 0]
    
    B --> D(Negative Definite)
    D --> DA[∀ x ∈ ℝ<sup>n</sup>, x<sup>T</sup>Ax < 0]

    B --> E(Positive Semi-Definite)
    E --> EA[∀ x ∈ ℝ<sup>n</sup>, x<sup>T</sup>Ax ≥ 0]
    
    B --> F(Negative Semi-Definite)
    F --> FA[∀ x ∈ ℝ<sup>n</sup>, x<sup>T</sup>Ax ≤ 0]
    
    subgraph Example_Matrices
    C --> CA1["Example: A = [[2, 1], [1, 2]]"]
    D --> DA1["Example: A = [[-2, -1], [-1, -2]]"]
    E --> EA1["Example: A = [[1, 0], [0, 0]]"]
    F --> FA1["Example: A = [[-1, 0], [0, 0]]"]

    
    CA1 --> CA2["x<sup>T</sup>Ax = 2x<sub>1</sub><sup>2</sup> + 2x<sub>1</sub>x<sub>2</sub> + 2x<sub>2</sub><sup>2</sup> > 0"]
    DA1 --> DA2["x<sup>T</sup>Ax = -2x<sub>1</sub><sup>2</sup> - 2x<sub>1</sub>x<sub>2</sub> - 2x<sub>2</sub><sup>2</sup> < 0"]
    EA1 --> EA2["x<sup>T</sup>Ax = x<sub>1</sub><sup>2</sup> ≥ 0"]
    FA1 --> FA2["x<sup>T</sup>Ax = -x<sub>1</sub><sup>2</sup> ≤ 0"]

    
    subgraph Properties
        C --> CP["All eigenvalues are positive"]
        D --> DP["All eigenvalues are negative"]
        E --> EP["All eigenvalues are non-negative"]
        F --> FP["All eigenvalues are non-positive"]

        C -- Related to --> CS[Eigenvalues > 0]
        D -- Related to --> DS[Eigenvalues < 0]
        E -- Related to --> ES[Eigenvalues ≥ 0]
        F -- Related to --> FS["Eigenvalues ≤ 0"]
    end
    end
    
```

---


### Explanation

* **Definition (B):** This node represents the fundamental criteria for classifying matrices.
* **Positive Definite (C):** This node details the condition for a positive definite matrix:  For *every* non-zero vector x in n-dimensional space, the quadratic form x<sup>T</sup>Ax must be greater than zero.  The example shows a 2x2 positive definite matrix and demonstrates how to evaluate the condition.
* **Negative Definite (D):** Similarly, this node defines a negative definite matrix where the quadratic form is always negative for any non-zero vector x.
* **Positive Semi-Definite (E):**  This node describes the condition where the quadratic form is non-negative for any vector x, including zero.
* **Negative Semi-Definite (F):** This node defines matrices where the quadratic form is always non-positive.
* **Properties (subgraph):** This subgraph highlights the critical link between eigenvalues and the definiteness. Positive definite matrices have all positive eigenvalues, negative definite matrices have all negative eigenvalues, and so on.  The example evaluations (CA2, DA2, etc.) explicitly demonstrate how to check the definiteness conditions for example matrices.

---


### Important Considerations

* **Vectors:** The diagram emphasizes the role of vectors (x ∈ ℝ<sup>n</sup>) in the definiteness criteria.
* **Quadratic Forms:** The crucial concept is the evaluation of quadratic forms (x<sup>T</sup>Ax) for different vectors x.
* **Eigenvalues:** The strong connection between eigenvalues and definiteness is highlighted, with direct links to the properties of eigenvalues being positive, negative, or zero.
* **Examples:**  Explicit examples are provided (e.g., the 2x2 matrices) to illustrate the concepts concretely.


This diagram provides a structured and visual way to understand the properties of positive and negative definite matrices, linking the abstract mathematical definitions to practical evaluations. Remember to tailor the examples to the specific dimensionality and context you need.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---