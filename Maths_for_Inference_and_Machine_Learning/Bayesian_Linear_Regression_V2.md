---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Bayesian Linear Regression
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Bayesian Linear Regression - A Diagram Structure


```mermaid
---
title: Bayesian Linear Regression
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
    A[Bayesian Linear Regression] --> B{Model}
    B -- "Inputs<br>(x<sub>1</sub>, ..., x<sub>N</sub>)" --> C[Data]
    B -- "Outputs<br>(y<sub>1</sub>, ..., y<sub>N</sub>)" --> C
    B -- "Parameters<br>(θ)" --> D[Parameters]
    D -- "Prior Distribution<br>(θ ~ N(m<sub>0</sub>, S<sub>0</sub>))" --> E[Prior]
    
    subgraph Model_Details
        C --> F[Observations]
        F -- "Noise<br>(ϵ ~ N(0, σ<sup>2</sup>I))" --> G[Noise]
        F -- "Linear Transformation<br>(y = Φθ + ϵ)" --> H[Linear Transformation]
        H --> I["Likelihood<br>(y | θ, X, σ<sup>2</sup>)"]
        I -- "Bayes' Theorem" --> J["Posterior<br>(θ | X, y)"]
    end
    
    subgraph Calculation_of_Posterior["Calculation of Posterior"]
        J -- "Marginal Likelihood<br>(p(y | X))" --> K[Marginal Likelihood]
        K -- "Integration over θ" --> L[Integration]
        E --> L
        I --> L
        L --> J
    
    J -- "Closed-Form Solution" --> M["Closed-Form Posterior"]
        M -- Mean (m<sub>N</sub>) --> N1[Mean]
        M -- "Covariance<br>(S<sub>N</sub>)" --> N2[Covariance]
        
    N1 -- Derivation --> N1_1[Equation]
        N2 -- Derivation --> N2_1[Equation]

    end

    subgraph Prediction_and_Inference["Prediction and Inference"]
        M --> O[Prediction]
        O -- "Test Location<br>(x*)" --> P[Test Location]
        P -- "Feature Vector<br>(φ(x*))" --> Q[Feature Vector]
        O -- "Posterior Distribution<br>(θ | X, y)" --> R[Posterior]
        Q --> R

        O -- "Predictive Distribution<br>(y* | X, y, x*)" --> S[Predictive Distribution]
        S -- Derivation --> T[Equation]
        
        R --> T
        Q --> T
        G --> T
        T -- Mean (φ*(x*)m<sub>N</sub>) --> U1[Predictive Mean]
        T -- Variance (φ*(x*)S<sub>N</sub>φ*(x*) + σ<sup>2</sup>) --> U2[Predictive Variance]
    end
    
```


---

### Explanation of the Diagram

* **Nodes:** Represent key concepts and variables.  'Data', 'Parameters', 'Prior', 'Likelihood', 'Posterior', 'Marginal Likelihood', 'Predictive Distribution' are core nodes.  The diagram shows how these concepts relate.

* **Edges:** Indicate relationships and dependencies.  For example, an edge from 'Data' to 'Linear Transformation' shows the input to the model.  Edges to 'Likelihood' and 'Posterior' show how these relate to the data and prior.

* **Subgraphs:** Group related calculations or aspects of the model.  This improves readability by organizing the flow of information.

* **Equations:** While not fully written out, the diagram includes placeholders for equations (`N(m<sub>0</sub>, S<sub>0</sub>)`) to show the mathematical formulation.  This is crucial to convey the mathematical foundation.

* **Prediction and Inference:** The subgraph focuses on how the model makes predictions at a new data point (x*).  It highlights the predictive mean and variance, which are calculated using the posterior parameters and noise variance.

---


### Key Concepts Conveyed

* **Bayesian Approach:** The diagram explicitly shows the use of a prior distribution over parameters and how that influences the posterior and predictions.

* **Linear Model:** The model is explicitly a linear model using feature vectors Φ.

* **Gaussian Distributions:** The prior, likelihood, and posterior are all Gaussian distributions, making calculations tractable.

* **Conditional Dependence:** The diagram visualizes how observations depend on parameters and noise.


This diagram provides a more visual and comprehensive representation of Bayesian Linear Regression, clearly illustrating the relationships between concepts and the mathematical formulations involved.  It's designed to be more accessible to someone trying to understand the concept than a purely textual explanation.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---