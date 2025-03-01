---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# The Dual Problem
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## The Dual Problem - A Diagram Structure


```mermaid
---
title: The Dual Problem
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
    A[The Dual Problem] --> B{Optimization Problem}
    B --> C[Primal Problem]
    C --> D["min f(w) subject to g(w) ≤ 0"]

    B --> E[Dual Problem]
    E --> F["max L(w, a) subject to a ≥ 0"]
    F --> FA["L(w, a) = f(w) + a * g(w)"]

    subgraph Explanation
        F -- Constraints on a --> GA[a ≥ 0]
        F -- Objective Function L --> GB["L(w, a)"]
        GB --> GBC["f(w) + a * g(w)"]
    end

    subgraph Equivalence
        C -- Primal Problem --> CA["Finds w that minimizes f(w) given constraint g(w) ≤ 0"]
        E -- Dual Problem --> EB["Finds a that maximizes L(w,a) given constraint a ≥ 0"]
        CA --> CB["Equivalent solutions for convex f(w) and affine g(w)"]
        EB --> EB1["Equivalent solutions for convex f(w) and affine g(w)"]
    end
    
    subgraph Summary
        B --> BB[Constrained Optimization]
        BB --> BB1["Lagrangian Duality"]
        BB --> BB2["Primal and Dual Problems"]
        BB --> BB3["Equivalent solutions under certain conditions<br>(Convexity, Affineness)"]
        BB --> BB4["Duality gap for non-convex functions"]
    end
    
```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---