---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Lagrangian Duality
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Lagrangian Duality - A Diagram Structure

```mermaid
---
title: Lagrangian Duality
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
    A[Lagrangian Duality] --> B{Core Idea}
    B --> C[Constrained Optimization]
    C --> D(Primal Problem)
    D --> DA["Minimize a function<br>(f(w))"]
    D --> DB["Subject to constraints<br>(g(w) ≤ 0)"]
    
    B --> E(Dual Problem)
    E --> EA["Maximize a function (a function of Lagrange multipliers)"]
    E --> EB["Subject to constraints on the Lagrange multipliers<br>(e.g., a ≥ 0)"]
    
    subgraph Primal_Dual_Relationship
        D --> F{Equivalent, but potentially easier to solve}
        F --> G(Dual Solution)
        G --> GA[Often has a simpler form than the primal problem]
        G --> GB[Especially useful when constraints are linear]
    
        E --> H{Under certain conditions}
        H --> I[Primal = Dual]
        I --> IA["e.g., f(w) is convex, g(w) is affine"]
    end
    
    subgraph Lagrangian_Formulation
        B --> J[Lagrangian Function]
        J --> JA["f(w) + a * g(w)"]
        JA -- a: Lagrange multiplier --> JB[Weight on the constraint]
        JB --> J1[Maximize with respect to 'a']
        J1 --> J2[Ensures constraint is satisfied implicitly]
        J1 --> J3[Allows for easier computation in some cases]
    end
    
    
    subgraph Key_Conditions_Optimality
        B --> K{Conditions for Optimality}
        K --> KA["Feasibility of (w, a)"]
        KA --> KAB["Constraints satisfied,<br>i.e., g(w) ≤ 0, a ≥ 0"]
        K --> KB[Complementary Slackness]
        KB --> KBA["a*g(w) = 0"]
        KBA -- Importance --> KBB[If constraint not binding, multiplier = 0;<br>If binding, constraint holds with equality]
    end
    
    
    subgraph Example_Illustration
        B --> L["Illustration:<br>p(a,b,c) = p(c|a,b)p(b|a)p(a)"]
        L --> LA[Directed Edges:<br>Relationships]
        L --> LB[Nodes:<br>Variables a,b,c]
        L --> LC["Factors:<br>p(c|a,b), p(b|a), p(a)"]
    end
    
    
    subgraph Summary_Diagram
        C --> M[Applications in ML]
        M --> MA["Support Vector Machines<br>(SVMs)"]
        M --> MB[Finding optimal hyperplanes]
        M --> MC[Kernel Methods]
        M --> MD[More efficient computations]
    end

```





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---