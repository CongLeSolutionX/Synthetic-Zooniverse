---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Scalar Products
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
title: Scalar Products
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
    A[Scalar Products] --> B{Definition}
    B --> C[Bilinear Mapping]
    C --> CA(β : V × V → R)
    
    subgraph Properties
        C --> CB[Symmetric]
        CB --> CB1["β(x, y) = β(y, x)"]
        C --> CC[Positive Definite]
        CC --> CC1["β(x, x) > 0  for all x ≠ 0"]
        CC --> CC2["β(0, 0) = 0"]
    end

    B --> D[Scalar Product/Dot Product/Inner Product]
    D --> DA["(V, <·, ·>) is a Euclidean Vector Space"]
    
    subgraph Examples
        D --> DB["Standard Scalar Product (ℝ<sup>n</sup>)"]
        DB --> DB1["<x, y> = x<sup>T</sup>y = Σ<sub>i=1</sub><sup>n</sup> x<sub>i</sub>y<sub>i</sub>"]
        D --> DC["Alternative Scalar Product (ℝ<sup>2</sup>)"]
        DC --> DC1["<x, y> = x<sub>1</sub>y<sub>1</sub> - (x<sub>1</sub>y<sub>2</sub> + x<sub>2</sub>y<sub>1</sub>) + 2x<sub>2</sub>y<sub>2</sub>"]
    end

    subgraph Applications
        D --> DD[Lengths, Distances, and Orthogonality]
        DD --> DDA["(Norm) ||x|| = √<x, x>"]
        DD --> DDB["Distance d(x, y) = ||x - y||"]
        DD --> DDC["Orthogonality x ⊥ y ⇔ <x, y> = 0"]
    end

    subgraph CauchySchwarz
        D --> DE[Cauchy-Schwarz Inequality]
        DE --> DEA["| <x, y> | ≤ ||x|| ||y||"]
    end
    subgraph  Minkowski
        D --> DF[Minkowski Inequality]
        DF --> DFA["||x + y|| ≤ ||x|| + ||y||"]
    end

    subgraph Angles
        D --> DG[Angles between Vectors]
        DG --> DGA["Cosine of Angle ω = <x, y> / (||x|| ||y||)"]
        DG --> DGB["Unique angle ω ∈ [0, π)"]
    end
    
    subgraph Further_Applications
        D --> DH[Kernel Methods]
        DH --> DHA["Important in kernel methods for implicit computation in feature spaces"]
        DH --> DHB["Used in Gaussian processes for probabilistic regression"]
        DH --> DHC["Crucial in Krylov subspace methods for linear systems"]
    end

```

----

### Explanation

This Mermaid diagram visually represents the concept of scalar products.  It's structured to show the definition, properties, examples, and applications of scalar products in a vector space.  Key components are:

*   **Definition:** The diagram starts by defining scalar products as a specific type of bilinear mapping. It highlights the crucial properties of symmetry and positive definiteness.

*   **Properties:** It clearly outlines the symmetric and positive definite properties, which are essential for a scalar product.

*   **Examples:** It provides concrete examples of scalar products, including the standard dot product in R<sup>n</sup> and a more complex example in R<sup>2</sup>. This makes the abstract concept more concrete.

*   **Applications:** It shows how scalar products are fundamental for calculating lengths, distances, and orthogonality in vector spaces. This section is further expanded to highlight their role in various machine learning techniques like kernel methods and Gaussian processes.


*   **Cauchy-Schwarz and Minkowski Inequalities:** These important inequalities are highlighted, showing their relation to scalar products.

*   **Angles between vectors:** The diagram shows how the scalar product can be used to find the cosine of the angle between two vectors.

This detailed representation helps in understanding the concept's various aspects and its importance in various mathematical and computational contexts. Remember that you can adapt this diagram to specific examples or equations from your reference material. Remember to include the relevant mathematical equations inline or as annotations in the graph for clarity and context.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---