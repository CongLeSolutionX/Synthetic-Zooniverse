---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# SVM Dual Problem
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## SVM Dual Problem - A Diagram Structure



```mermaid
---
title: SVM Dual Problem
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
    A[SVM Dual Problem] --> B{Primal Problem Formulation}
    B --> C(Minimizing a Quadratic Function)
    C --> CA[Minimize 1/2 * w<sup>T</sup>w]
    
    B --> D(Subject to Linear Constraints)
    D --> DA["y<sub>i</sub>(w<sup>T</sup>x<sub>i</sub> + b) ≥ 1"]
    D --> DB["for i = 1, ..., n"]
    
    
    subgraph Dual_Problem_Derivation["Dual Problem Derivation"]
        B --> E(Introduce Lagrangian)
        E --> EA["L(w, b, α) = 1/2 * w<sup>T</sup>w - Σ<sub>i=1</sub><sup>n</sup> α<sub>i</sub>(y<sub>i</sub>(w<sup>T</sup>x<sub>i</sub> + b) - 1)"]
        EA -- α<sub>i</sub> --> EB["Lagrange Multipliers"]

        E --> F(Optimizing the Lagrangian)
        F --> FA["∂L/∂w = w - Σ<sub>i=1</sub><sup>n</sup> α<sub>i</sub>y<sub>i</sub>x<sub>i</sub> = 0"]
        FA -- w --> FB["w = Σ<sub>i=1</sub><sup>n</sup> α<sub>i</sub>y<sub>i</sub>x<sub>i</sub>"]
        
        F --> FC["∂L/∂b = Σ<sub>i=1</sub><sup>n</sup> α<sub>i</sub>y<sub>i</sub> = 0"]
        FC -- b --> FD["Σ<sub>i=1</sub><sup>n</sup> α<sub>i</sub>y<sub>i</sub> = 0"]
    
        F --> G(Substituting w into the Lagrangian)
        G --> GA["L(α) = Σ<sub>i=1</sub><sup>n</sup> α<sub>i</sub> - 1/2 * Σ<sub>i=1</sub><sup>n</sup> Σ<sub>j=1</sub><sup>n</sup> α<sub>i</sub>α<sub>j</sub>y<sub>i</sub>y<sub>j</sub>x<sub>i</sub><sup>T</sup>x<sub>j</sub>"]
        
        G --> H(Dual Problem)
        H --> HA["Maximize L(α) = Σ<sub>i=1</sub><sup>n</sup> α<sub>i</sub> - 1/2 * Σ<sub>i=1</sub><sup>n</sup> Σ<sub>j=1</sub><sup>n</sup> α<sub>i</sub>α<sub>j</sub>y<sub>i</sub>y<sub>j</sub>k(x<sub>i</sub>, x<sub>j</sub>)"]
        
        HA -- α<sub>i</sub> --> HB["Subject to"]
        HB --> HC["α<sub>i</sub> ≥ 0"]
        HB --> HD["Σ<sub>i=1</sub><sup>n</sup> α<sub>i</sub>y<sub>i</sub> = 0"]
    end
    
```


---

### Explanation

* **Primal Problem Formulation (B):**  The initial SVM problem is to minimize a quadratic function (1/2 * w<sup>T</sup>w) subject to linear constraints (y<sub>i</sub>(w<sup>T</sup>x<sub>i</sub> + b) ≥ 1 for each training example (x<sub>i</sub>, y<sub>i</sub>)).

* **Introduce Lagrangian (E):** A Lagrangian function is constructed, combining the objective function and the constraints.  Lagrange multipliers (α<sub>i</sub>) are introduced to handle the constraints.

* **Optimizing the Lagrangian (F):** The partial derivatives of the Lagrangian with respect to w and b are set to zero.  Solving these yields expressions for w and b in terms of the Lagrange multipliers.

* **Substituting and Dual Problem (G & H):** Substituting the expressions for w and b (from step F) back into the Lagrangian function gives a function of only the Lagrange multipliers (α<sub>i</sub>).  This new function represents the dual problem: to maximize the Lagrangian with respect to α<sub>i</sub>, subject to the constraints that α<sub>i</sub> ≥ 0 and Σ<sub>i=1</sub><sup>n</sup> α<sub>i</sub>y<sub>i</sub> = 0.

---

### Key Concepts Illustrated

* **Lagrangian Duality:** The diagram illustrates the transformation from the primal problem to the dual problem.
* **Lagrange Multipliers:**  The role of Lagrange multipliers (α<sub>i</sub>) in handling the constraints is highlighted.
* **Kernel Trick (implicitly):** The diagram uses `k(x<sub>i</sub>, x<sub>j</sub>)`  (kernel function), which is crucial for handling non-linearly separable data, but the diagram does not explicitly showcase the kernel trick itself.


This diagram provides a clear and structured view of the derivation of the SVM dual problem, incorporating the concepts of Lagrangian duality and the role of constraints.  It highlights the mathematical transformations and connections between the primal and dual formulations. Remember to replace the generic kernel function `k(x<sub>i</sub>, x<sub>j</sub>)` with the specific kernel being used in the context of the document.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---