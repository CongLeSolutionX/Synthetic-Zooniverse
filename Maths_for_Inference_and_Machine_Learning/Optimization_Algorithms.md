---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Optimization Algorithms (Beyond Gradient Descent)
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Optimization Algorithms Visualization


```mermaid
---
title: Optimization Algorithms
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
    A[Optimization Algorithms] --> B(Beyond Gradient Descent)
    B --> C(Conjugate Gradient Descent)
    C --> D{Algorithm Characteristics}
    D --> DA[Faster Convergence for Certain Problems]
    D --> DB[Suitable for solving linear systems]
    D --> DC[Often uses preconditioning]
    
    B --> E(Stochastic Approximation Algorithms)
    E --> F{Algorithm Characteristics}
    F --> FA[Approximates the gradient using subsets of data]
    F --> FB[Faster for large datasets]
    F --> FC[Can be noisy, but often converges with appropriate learning rate schedules]
    F --> FD[Examples:<br>RMSProp, AdaGrad, Adam]
    
    B --> G(Newton's Method)
    G --> H{Algorithm Characteristics}
    H --> HA["Uses second-order derivatives<br>(Hessian)"]
    H --> HB[Generally faster than first-order methods for well-behaved functions]
    H --> HC[Requires computation of Hessian, which can be expensive]
    H --> HD[Can be unstable for ill-conditioned problems]
    
    B --> I(Quasi-Newton Methods)
    I --> J{Algorithm Characteristics}
    J --> JA[Approximates the Hessian]
    J --> JB[Balances speed and efficiency compared to Newton's method]
    J --> JC[Often used in large-scale optimization problems]
    J --> JD[Examples:<br>BFGS, L-BFGS]

    B --> K(Gradient Descent with Momentum)
    K --> L{Algorithm Characteristics}
    L --> LA[Smoothes out erratic updates]
    L --> LB[Dampens oscillations]
    L --> LC[Often used in conjunction with other methods, like stochastic gradient descent]

    subgraph Summary["Summary"]
    style Summary fill:#cfc3,stroke:#333,stroke-width:2px
        D --> DD[Mathematical foundation for inference]
        D --> DE[Computational efficiency for specific cases]
        
        F --> FF[Mathematical foundation for inference]
        F --> FG[Scalability for large datasets]
        
        H --> HH[Mathematical foundation for inference]
        H --> HI[Computational efficiency for specific cases]
        
        J --> JJ[Mathematical foundation for inference]
        J --> JK[Approximations improve efficiency]
        
        L --> LL[Mathematical foundation for inference]
        L --> LM[Smoothing enhances convergence]
    end
    
```


### Explanation of the Diagram

* **Nodes:** The diagram uses nodes to represent specific optimization algorithms, such as 'Conjugate Gradient Descent', 'Stochastic Approximation Algorithms', 'Newton's Method', 'Quasi-Newton Methods', and 'Gradient Descent with Momentum'.
* **Subgraphs:** Subgraphs are used for grouping related characteristics.  This enhances readability and structure.
* **Edges:** Directed edges link algorithms to their key characteristics. This visually represents the connections between the algorithm and the properties it exhibits.
* **Summary Subgraph:** This subgraph highlights the key themes and applications that tie together the different optimization methods.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---