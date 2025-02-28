---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Support Vector Classiﬁcation
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Support Vector Classiﬁcation - A Diagram Structure




```mermaid
---
title: Support Vector Classification
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
    A[Support Vector Classification] --> B{Problem Formulation}
    B --> C(Linear Separating Hyperplane)
    C --> D(Data Points)
    D --> DA(x<sub>1</sub>, y<sub>1</sub>)
    D --> DB(x<sub>2</sub>, y<sub>2</sub>)
    ...
    D --> DN(x<sub>N</sub>, y<sub>N</sub>)

    C --> E(Margin Maximization)
    E --> EA(Maximize Distance Between Classes)
    E --> EB(wTx + b = ±1)
    
    subgraph Optimization_Problem["Optimization Problem"]
        E --> F(Primal Problem Formulation)
        F --> FA(min<sub>w,b</sub> 1/2 w<sup>T</sup>w)
        F --> FB("subject to y<sub>i</sub>(w<sup>T</sup>x<sub>i</sub> + b) ≥ 1,  i = 1, ..., N")
    end
    
    subgraph Lagrangian_Duality["Lagrangian Duality"]
        F --> G(Lagrangian Formulation)
        G --> GA("L(w, b, α) = 1/2 w<sup>T</sup>w - Σ<sub>i=1</sub><sup>N</sup> α<sub>i</sub>(y<sub>i</sub>(w<sup>T</sup>x<sub>i</sub> + b) - 1)")
        G --> GB(α<sub>i</sub> ≥ 0)
        G --> GC(Dual Problem Formulation)
        GC --> GCA(max<sub>α</sub> Σ<sub>i=1</sub><sup>N</sup> α<sub>i</sub> - 1/2 Σ<sub>i=1</sub><sup>N</sup> Σ<sub>j=1</sub><sup>N</sup> α<sub>i</sub> α<sub>j</sub> y<sub>i</sub> y<sub>j</sub> x<sub>i</sub><sup>T</sup>x<sub>j</sub>)
        GC --> GCB(subject to Σ<sub>i=1</sub><sup>N</sup> α<sub>i</sub> y<sub>i</sub> = 0,  α<sub>i</sub> ≥ 0)
        G --> GD(KKT Conditions)
        GD --> GDA("α<sub>i</sub>(y<sub>i</sub>(w<sup>T</sup>x<sub>i</sub> + b) - 1) = 0")
        GD --> GDB(w = Σ<sub>i=1</sub><sup>N</sup> α<sub>i</sub> y<sub>i</sub> x<sub>i</sub>)
        GD --> GDC(Σ<sub>i=1</sub><sup>N</sup> α<sub>i</sub> y<sub>i</sub> = 0)
    end
    
    subgraph Solution_and_Decision_Function["Solution and Decision Function"]
        GC --> H(Solution)
        H --> HA(Optimal α<sub>i</sub> Values)
        H --> HB(Compute w using α<sub>i</sub>)
        H --> HC(Choose b from support vectors)
        H --> HD("Decision Function: f(x) = sign(w<sup>T</sup>x + b)")
    end
    
    subgraph Support_Vectors["Support Vectors"]
        H --> I(Support Vectors)
        I --> IA("Data points that lie on the margin (y<sub>i</sub>(w<sup>T</sup>x<sub>i</sub> + b) = 1)")
        I --> IB(Crucial for decision function)
    end

```

---


### Explanation of the Diagram

* **Problem Formulation (Node B):**  Defines the core objective of finding a linear hyperplane that maximizes the margin between two classes of data points.
* **Data Points (Node D):**  Illustrates the input data (x<sub>i</sub>, y<sub>i</sub>) pairs where x<sub>i</sub> are data points and y<sub>i</sub> are their associated labels (+1 or -1).
* **Margin Maximization (Node E):** Highlights the key idea of maximizing the distance between the separating hyperplane and the closest data points from each class.
* **Primal Problem Formulation (Node F):**  Shows the mathematical representation of the optimization problem to find the optimal hyperplane (w, b) that minimizes 1/2 w<sup>T</sup>w.
* **Lagrangian Formulation (Node G):**  Introduces the Lagrangian function, incorporating the constraints into the objective function using Lagrange multipliers (α<sub>i</sub>).
* **KKT Conditions (Node GD):**  Specifies the Karush-Kuhn-Tucker conditions, necessary for optimality, which relate the Lagrange multipliers (α<sub>i</sub>) to the data points.
* **Support Vectors (Node I):**  Emphasizes the crucial role of support vectors (data points on the margin) in determining the separating hyperplane and the decision function.
* **Solution and Decision Function (Node H):**  Describes how the optimal solution (w, b) is obtained from the dual problem and how it's used in the decision function to classify new data points.
* **Dual Problem Formulation (Node GC):** Shows the dual problem formulation for easier computation, using the kernel trick (k(x<sub>i</sub>, x<sub>j</sub>) = x<sub>i</sub><sup>T</sup>x<sub>j</sub>) to compute inner products efficiently in higher-dimensional spaces (although not explicitly mentioned here, this is implicit if the data aren't linearly separable).

This diagram provides a structured overview of Support Vector Classification, highlighting the core concepts and their mathematical representations.  It's designed to be easily adaptable and extendable to illustrate further details as needed.  Remember to replace placeholders like x<sub>1</sub>, x<sub>2</sub>, ..., with specific data points if you are illustrating a particular example.





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---