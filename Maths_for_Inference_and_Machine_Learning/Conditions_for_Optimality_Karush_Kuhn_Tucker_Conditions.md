---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Conditions for Optimality (Karush-Kuhn-Tucker Conditions)
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Conditions for Optimality - A Diagram Structure


```mermaid
---
title: Conditions for Optimality (Karush-Kuhn-Tucker Conditions)
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
    A[Conditions for Optimality] --> B(Karush-Kuhn-Tucker Conditions)
    B --> C{Feasibility}
    C -- w and a are feasible --> CA["g(w) ≤ 0 and a ≥ 0"]
    
    B --> D{Complementary Slackness}
    D -- ag(w) = 0 --> DA["The constraint g(w) affects the optimal solution only if it's active (g(w) = 0).<br>If the optimal solution is inside the feasible region defined by g(w) ≤ 0, then a = 0;<br>otherwise, a > 0, and the constraint is active"]
    
    B --> E{Stationarity}
    E -- ∇<sub>w</sub>L(w, a) = 0 --> EA[The gradient of the Lagrangian function L with respect to the primal variable w is zero at the optimal solution];
    
    B --> F{Primal and Dual Solutions};
    F -- d<sup>*</sup> = p<sup>*</sup> --> FA["The solution to the dual problem (maximizing the minimum Lagrangian)<br>equals the solution to the primal problem (minimizing the function subject to constraints),<br>under certain conditions (convexity and linearity of the constraints)"]
    
    subgraph Conditions_Explanation["Conditions Explanation"]
        C --> CB["g(w) ≤ 0  Indicates constraints on the primal variable 'w'"]
        C --> CC["a ≥ 0 Indicates non-negativity of the Lagrange multipliers"]
        D --> DD["ag(w) = 0  Implies that either the constraint is inactive (a=0) or the constraint is active (g(w)=0)"]
        E --> EE["∇<sub>w</sub>L(w, a) = 0<br>This is the standard stationarity condition for optimality"]
        
        F --> FF["d<sup>*</sup> = p<sup>*</sup>  Indicates the equality of primal and dual optimal solutions"]
    end
    
```


---

### Explanation

The Karush-Kuhn-Tucker (KKT) conditions provide necessary and sufficient conditions for optimality in constrained optimization problems.  The diagram illustrates these conditions in a structured way, showing the relationships between feasibility, complementary slackness, and stationarity conditions, and how they relate to the primal and dual solutions.

* **Feasibility (C):**  This condition ensures that the chosen values for the primal variables (`w`) and Lagrange multipliers (`a`) are valid within the constraints defined by the problem.  This is critical, as solutions outside these constraints are not valid.

* **Complementary Slackness (D):** This condition is key for understanding when a constraint actively influences the solution. If the multiplier `a` is zero, the constraint is not binding (inactive) at the optimal solution.  If `a` is positive, the constraint is active (binding), and thus must be satisfied with equality.

* **Stationarity (E):** This standard condition ensures that the gradient of the Lagrangian (`∇<sub>w</sub>L(w, a)`) is zero at the optimal point.  This means the function is not changing in the direction of the primal variables at the optimal point, satisfying the necessary condition for a minimum or maximum.

* **Primal and Dual Solutions (F):** This condition states that under specific convexity conditions and linear constraints, the solutions to the primal and dual problems are equal.  This is a crucial result in optimization, as the dual problem is sometimes easier to solve than the primal, allowing the use of efficient algorithms for its solution.


This diagram provides a concise and visual representation of the KKT conditions, highlighting their importance for finding optimal solutions in constrained optimization problems.  It is suitable for both theoretical understanding and practical application, especially when applying KKT conditions in situations involving Support Vector Machines (SVMs).



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---