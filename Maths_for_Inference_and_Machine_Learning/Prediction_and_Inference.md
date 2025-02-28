---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Prediction and Inference
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Prediction and Inference - A Diagram Structure



```mermaid
---
title: Prediction and Inference
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
    subgraph Prediction_and_Inference["Prediction and Inference"]
        A[Prediction and Inference] --> B(Bayesian Linear Regression)
        B --> C{Inference using Posterior Distributions}
        C --> CA[Posterior predictive distribution]
        CA --> CB["p(y*|X, y, x*) = ∫ p(y*|x*, θ)p(θ|X, y)dθ"]
        CB --> CC["p(y*|x*, θ) : Likelihood of the predicted output given parameters θ at test location x*"]
        CB --> CD["p(θ|X, y) : Posterior distribution of parameters θ given training data X and y"]

        C --> CE[Marginal Likelihood]
        CE --> CF["p(y|X) = ∫ p(y|X, θ)p(θ)dθ"]
        CE --> CG[Normalization constant]

        C --> CH[Predictive Mean]
        CH --> CI["E[y*|X, y, x*] = φ*(x*)E[θ|X, y]"]
        CH --> CJ["φ*(x*) : Feature vector for test input x*"]
        
        C --> CK[Predictive Variance]
        CK --> CL["V[y*|X, y, x*] = φ*(x*)V[θ|X, y] + σ^2"]
        CK --> CM[σ^2 : Noise variance]

        C --> CN[Uncertainty due to Parameters]
        CN --> CO[SN : Posterior covariance matrix]
        
        C --> CP[Uncertainty due to Noise]
        CP --> CQ[σ^2 : Noise variance]
    end
    
```

---

### Explanation

This Mermaid diagram visualizes the process of prediction and inference in Bayesian Linear Regression, following a structure similar to the previous examples.

* **Prediction and Inference (Subgraph):**  Encompasses the entire process.
* **Bayesian Linear Regression (Node B):**  The model under consideration.
* **Inference using Posterior Distributions (Node C):**  The core idea is using the posterior distribution to make predictions.
* **Posterior predictive distribution (Node CA):** This is the primary outcome of the inference process.
* **Marginal Likelihood (Node CE):** The normalizing constant that ensures the posterior integrates to 1.
* **Predictive Mean (Node CH):** The expected value of the prediction, calculated by averaging over the posterior distribution of parameters.
* **Predictive Variance (Node CK):** The variability associated with the prediction, considering both the parameter uncertainty and the noise.  The noise variance (σ^2) and posterior covariance of the parameters (SN) are clearly distinguished as contributing factors to the overall uncertainty.
* **Uncertainty due to Parameters (Node CN):**  This part emphasizes the role of the posterior parameter uncertainty in the prediction variance.
* **Uncertainty due to Noise (Node CP):**  This part highlights the impact of the noise variance on the prediction variance.

---


### Key Relationships and Concepts Illustrated

* **Bayes' Theorem:** Implicitly illustrated through the equation for the posterior predictive distribution and marginal likelihood.
* **Integration:** The process of integrating over the posterior parameter distribution (θ) is visually represented.
* **Mean and Variance:** The diagram clearly depicts how the predictive mean and variance are derived from the posterior distribution.
* **Uncertainty Quantification:**  The diagram explicitly shows how uncertainty in parameters and noise contributes to the overall uncertainty in predictions.


This diagram, like the previous ones, can be further expanded by adding more specific details about the components, such as particular equations and formulas for calculating the predictive mean and variance or linking these concepts to related sections of the original document.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---