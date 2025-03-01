---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# The Two Class Case
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## The Two Class Case - A Diagram Structure


```mermaid
---
title: The two class case
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
    A[Linear Discriminant Analysis] --> B{Two-Class Case}
    B --> C(Within-Class Variance Minimization)
    C --> CA(Minimize Variability within Each Class)
    C --> CB["σ²<sub>y(c1)</sub> + σ²<sub>y(c2)</sub> is minimized"]

    B --> D(Between-Class Variance Maximization)
    D --> DA(Maximize Distance Between Class Means)
    D --> DB["(µ<sub>y(c1)</sub> - µ<sub>y(c2)</sub>)² is maximized"]

    subgraph Optimization_Goal["Optimization Goal"]
        C --> E["Find Projection Vector w"]
        E --> EA["Project data onto vector w"]
        E --> EB["y<sub>i</sub> = w<sup>T</sup>x<sub>i</sub>"]
        
        D --> F["Maximize Separability"]
        F --> FA["Maximize distance between projected class means"]
        
        E --> G[Optimization Problem]
        G --> GA["Maximize (µ<sub>y(c1)</sub> - µ<sub>y(c2)</sub>)² / (σ²<sub>y(c1)</sub> + σ²<sub>y(c2)</sub>)"]
        G --> GB["subject to: w<sup>T</sup>w = 1 (unit vector constraint)"]
    end

    
    subgraph Within_Class_Variance["Within Class Variance"]
        CA --> H[Within-Class Scatter Matrix]
        H --> HA["S<sub>w</sub> = S<sub>1</sub> + S<sub>2</sub>"]
        H --> HB["S<sub>j</sub> = (1/N<sub>c<sub>j</sub></sub>) Σ<sub>x<sub>i</sub>∈c<sub>j</sub></sub> (x<sub>i</sub> - µ(c<sub>j</sub>))(x<sub>i</sub> - µ(c<sub>j</sub>))<sup>T</sup>"]
        H --> HC["S<sub>1</sub> for class c<sub>1</sub>, S<sub>2</sub> for class c<sub>2</sub>"]
    end
    
    subgraph Between_Class_Variance["Between Class Variance"]
        DA --> I[Between-Class Scatter Matrix]
        I --> IA["S<sub>b</sub> = (µ(c<sub>1</sub>) - µ(c<sub>2</sub>))(µ(c<sub>1</sub>) - µ(c<sub>2</sub>))<sup>T</sup>"]
        I --> IB["µ(c<sub>1</sub>) is the mean of class c<sub>1</sub>, µ(c<sub>2</sub>) is the mean of class c<sub>2</sub>"]
    end

    
    subgraph Solution["Solution"]
        G --> J[Generalized Eigenvalue Problem]
        J --> JA["S<sub>w</sub><sup>-1</sup>S<sub>b</sub>w = λw"]
        J --> JB["w is the optimal projection vector"]
        J --> JC["w ∝ S<sub>w</sub><sup>-1</sup>(µ(c<sub>1</sub>) - µ(c<sub>2</sub>))"]
    end
    
```

---


### Explanation

This diagram illustrates the two-class case of Linear Discriminant Analysis (LDA). It breaks down the key concepts into logical components and visually represents how the optimization problem arises from minimizing within-class variance and maximizing between-class variance.

* **Within-Class Variance Minimization:** The goal is to minimize the variability within each class, as measured by the within-class scatter matrix (S<sub>w</sub>), which combines the scatter matrices for each class (S<sub>1</sub> and S<sub>2</sub>).

* **Between-Class Variance Maximization:** The aim is to maximize the distance between the projected class means, as captured by the between-class scatter matrix (S<sub>b</sub>).

* **Optimization Problem:**  The core optimization problem is to find the projection vector (w) that maximizes the ratio of between-class variance to within-class variance. The constraint ensures the projection vector has unit length.

* **Generalized Eigenvalue Problem:** The solution to this optimization problem is obtained through solving a generalized eigenvalue problem involving S<sub>w</sub><sup>-1</sup>S<sub>b</sub>.

* **Optimal Projection Vector:** The optimal projection vector (w) is a solution to this generalized eigenvalue problem, and is proportional to the inverse of the within-class scatter matrix times the difference between the class means.

The diagram visually connects these concepts through arrows, making it easier to understand the overall process of finding the optimal projection for LDA in the two-class scenario. The inclusion of relevant formulas and annotations makes the diagram more complete and understandable.





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---