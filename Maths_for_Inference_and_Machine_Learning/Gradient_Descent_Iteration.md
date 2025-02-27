---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Gradient Descent Iteration Breakdown
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


Applying the "Decomposition of Complex Concepts" strategy to Gradient Descent.

## A Single Iteration of Gradient Descent

A flowchart detailing the steps in a single iteration of gradient descent, emphasizing the inputs and outputs at each step:

```mermaid
---
title: A Single Iteration of Gradient Descent
config:
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
    A["Start Iteration"] --> B{"Current Parameter Vector<br>(θ<sub>i</sub>)"}
    B -- θ<sub>i</sub> --> C["Calculate Gradient<br>(∇L(θ<sub>i</sub>))"]
    C -- ∇L(θ<sub>i</sub>) --> D{"Compute Step Size<br>(γ<sub>i</sub>)"}
    D -- γ<sub>i</sub> --> E["Update Parameter Vector<br>(θ<sub>i+1</sub>)"]
    E -- θ<sub>i+1</sub> --> F["Check Convergence Condition?"]
    F -- Yes --> G["End Iteration"]
    F -- No --> A

    style B fill:#f9f5,stroke:#333,stroke-width:1px
    style C fill:#ccf5,stroke:#333,stroke-width:1px
    style D fill:#ccf5,stroke:#333,stroke-width:1px
    style E fill:#f9f5,stroke:#333,stroke-width:1px
    style F fill:#ccf5,stroke:#333,stroke-width:1px
    style G fill:#f9f5,stroke:#333,stroke-width:1px

```

DOI: [10.13140/RG.2.2.26078.14404](http://dx.doi.org/10.13140/RG.2.2.26078.14404)



### Explanation of Nodes and Connections

* **Start Iteration (A):** The beginning of an iteration cycle.
* **Current Parameter Vector (θ<sub>i</sub>) (B):** The current estimate of the parameters at the start of the iteration.
* **Calculate Gradient (∇L(θ<sub>i</sub>)) (C):** Computes the gradient of the loss function (L) with respect to the parameters at the current point.  This step requires calculating partial derivatives. Annotate this node with the formula for the gradient: ∇L(θ<sub>i</sub>) = ... (where ... represents the actual calculation).
* **Compute Step Size (γ<sub>i</sub>) (D):** Determines the magnitude of the update step. The formula used for calculating the step size should be shown here (e.g., a fixed learning rate or a dynamically adjusted one).  Annotate with the formula: γ<sub>i</sub> = ...
* **Update Parameter Vector (θ<sub>i+1</sub>) (E):** Updates the parameter vector based on the calculated gradient and step size.  Show the formula: θ<sub>i+1</sub> = θ<sub>i</sub> - γ<sub>i</sub>∇L(θ<sub>i</sub>).
* **Check Convergence Condition? (F):** Checks if the algorithm has converged to a solution (e.g., if the change in the parameter vector is below a certain threshold or if the loss function value stops decreasing significantly).
* **End Iteration (G):** The end of the iteration if the convergence condition is met.

---


## Multiple Iterations of Gradient Descent

An alternative diagram (for visualizing multiple iterations).

```mermaid
---
title: Multiple Iterations of Gradient Descent
config:
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
    subgraph Iteration 1
        A1[θ<sub>0</sub>] --> C1["∇L(θ<sub>0</sub>)"] --> D1[γ<sub>0</sub>] --> E1[θ<sub>1</sub>]
    end

    subgraph Iteration 2
        A2[θ<sub>1</sub>] --> C2["∇L(θ<sub>1</sub>)"] --> D2[γ<sub>1</sub>] --> E2[θ<sub>2</sub>]
    end

    subgraph Iteration 3
        A3[θ<sub>2</sub>] --> C3["∇L(θ<sub>2</sub>)"] --> D3[γ<sub>2</sub>] --> E3[θ<sub>3</sub>]
    end

    ...

    style A1 fill:#f9f5,stroke:#333,stroke-width:1px
    style C1 fill:#ccf5,stroke:#333,stroke-width:1px
    style D1 fill:#ccf5,stroke:#333,stroke-width:1px
    style E1 fill:#f9f5,stroke:#333,stroke-width:1px
    
```


This second diagram shows multiple iterations and how the parameter vector updates through the steps.  The subgraphs help visualize each iteration distinctly.  Further iterations can be added as necessary.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---