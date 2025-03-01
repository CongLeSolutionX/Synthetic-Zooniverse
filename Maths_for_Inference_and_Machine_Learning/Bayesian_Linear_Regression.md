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


## A Diagram Structure


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
graph LR
    subgraph Bayesian_Linear_Regression["Bayesian Linear Regression"]
    style Bayesian_Linear_Regression fill:#cfc3,stroke:#333,stroke-width:2px
        A[Bayesian Linear Regression] --> B{Model}
        B --> C(Generative Process)
        C --> CA(Inputs)
        CA --> CB["'x<sub>1</sub>', 'x<sub>2</sub>', ..., 'x<sub>N</sub>'"]
        C --> CC(Outputs)
        CC --> CD["'y<sub>1</sub>', 'y<sub>2</sub>', ..., 'y<sub>N</sub>'"]
        C --> CE(Parameters)
        CE --> CF["'θ<sub>1</sub>', 'θ<sub>2</sub>', ..., 'θ<sub>D</sub>'"]
        C --> CG(Noise)
        CG --> CH["ϵ"]
        C --> CI(Prior Distribution)
        CI --> CJ["θ ~ N(m<sub>0</sub>, S<sub>0</sub>)" ]
        C --> CK(Likelihood Function)
        CK --> CL["y<sub>i</sub>|x<sub>i</sub>, θ ~ N(x<sub>i</sub><sup>T</sup>θ, σ<sup>2</sup>I)" ]

        C --> CM(Posterior Distribution)
        CM --> CN["θ|X, y ~ N(m<sub>N</sub>, S<sub>N</sub>)"]

        C --> CO{Inference Steps}
        CO -- Bayes' Theorem --> CP["p(θ|X, y) = p(y|X, θ)p(θ) / p(y|X)"]
        CO -- Closed-Form Solution --> CQ[Derivation for Posterior]
        CQ --> CR["m<sub>N</sub> = S<sub>N</sub>(S<sub>0</sub>m<sub>0</sub> + σ<sup>-2</sup>Φ<sup>T</sup>y)"]
        CQ --> CS["S<sub>N</sub> = (S<sub>0</sub> + σ<sup>-2</sup>Φ<sup>T</sup>Φ)<sup>-1</sup>"]
    end
    
    subgraph Inference_Details["Inference Details"]
    style Inference_Details fill:#cff1,stroke:#333,stroke-width:2px
        CQ --> CT[Closed-form Expression]
        CT --> CU["p(θ|X, y) = N(m<sub>N</sub>, S<sub>N</sub>)" ]
        CT --> CV["m<sub>N</sub> : Posterior mean of θ"]
        CT --> CW["S<sub>N</sub> : Posterior covariance matrix of θ"]
        CQ --> CX[Key to Efficient Computation]
        CX --> CY["Kernel Trick (Optional)"]
        CY --> CZ["Efficiently compute inner products in high-dimensional space without explicitly mapping"]
    end
    
    subgraph Prediction_Stage["Prediction Stage"]
    style Prediction_Stage fill:#ccc2,stroke:#333,stroke-width:2px
        A --> D{Prediction}
        D --> DA(Test Input)
        DA --> DB["x*"]
        D --> DC(Predictive Distribution)
        DC --> DD["y* ~ N(m*, S*)"]
        D --> DE{Prediction Steps}
        DE -- Integration over θ --> DF["m* = φ*(x*)<sup>T</sup>m<sub>N</sub> and S* = φ*(x*)<sup>T</sup>S<sub>N</sub>φ*(x*) + σ<sup>2</sup>"]
        
    end
    
```

DOI: [10.13140/RG.2.2.24400.42244](http://dx.doi.org/10.13140/RG.2.2.24400.42244)


---

### Explanation

* **Generative Process (C):** Shows how data are generated.  The model assumes inputs (`x<sub>i</sub>`) and outputs (`y<sub>i</sub>`) are related through a linear transformation (`x<sub>i</sub><sup>T</sup>θ`) plus Gaussian noise (`ϵ`).
* **Prior Distribution (CI):** Represents the initial belief about the parameters θ, modeled as a Gaussian distribution `N(m<sub>0</sub>, S<sub>0</sub>)`.
* **Likelihood Function (CK):**  Defines the probability of observing the outputs (`y<sub>i</sub>`) given the inputs (`x<sub>i</sub>`) and parameters (`θ`).  Modeled as a Gaussian distribution `N(x<sub>i</sub><sup>T</sup>θ, σ<sup>2</sup>I)`.
* **Posterior Distribution (CM):** The updated belief about the parameters after observing the data.  Calculated using Bayes' theorem and shown as a Gaussian `N(m<sub>N</sub>, S<sub>N</sub>)`.  Crucially, the posterior mean (`m<sub>N</sub>`) and covariance (`S<sub>N</sub>`) are derived in closed form.
* **Inference Steps (CO):** Shows the key steps in obtaining the posterior:  applying Bayes' theorem and deriving the closed-form expression for the posterior parameters.
* **Closed-Form Expression (CT):** Explains the result of the inference process, that the posterior is a Gaussian distribution with specific mean and covariance.
* **Prediction Stage (D):** Shows how to predict the output for a new, unseen input (`x*`). The key step is integration over the posterior parameters, resulting in a predictive distribution.

**Important Considerations:**

* **Notation:** The diagram uses standard mathematical notation for probability distributions (e.g., `N(μ, Σ)` for a Gaussian distribution with mean μ and covariance Σ).  Using superscripts to indicate transpose is crucial for clarity, as is using * to denote variables in the prediction step.
* **Closed-form Solutions:** The diagram highlights that the posterior distribution has a closed-form expression, a critical aspect of Bayesian Linear Regression.
* **Kernels (Optional):** The diagram includes a possible path for the kernel trick if applicable.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---