---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Computing the Marginal Likelihood
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Computing the Marginal Likelihood - A Diagram Structure


```mermaid
---
title: Computing the Marginal Likelihood
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
    A["Computing the Marginal Likelihood"] --> B{"Problem Context"}
    B --> C["Bayesian Linear Regression"]
    C --> D("Generative Model")

    subgraph Generative_Model["Generative Model"]
        D -- θ ~ N(m<sub>0</sub>, S<sub>0</sub>) --> E[Prior]
        D -- y<sub>i</sub> | x<sub>i</sub>, θ ~ N(Φ<sub>i</sub>θ, σ<sup>2</sup>I) --> F[Likelihood]
        D -- x<sub>i</sub>, y<sub>i</sub> --> G[Observations]
    end

    subgraph Marginal_Likelihood_Calculation["Marginal Likelihood Calculation"]
        G --> H["Marginal Likelihood, p(y|X)"]
        H --> I[Definition]
        I -- p(y|X) = ∫ p(y|X, θ)p(θ) dθ --> J[Integration over Parameters]
    
        J --> K[Resulting Distribution]
        K -- p(y|X) ~ N(m<sub>N</sub>, S<sub>N</sub>) --> L[Multivariate Gaussian]
    
        L -- m<sub>N</sub> = S<sub>N</sub>(S<sub>0</sub>m<sub>0</sub> + σ<sup>−2</sup>Φ<sup>T</sup>y) --> M[Mean]
        L -- S<sub>N</sub> = (S<sub>0</sub> + σ<sup>−2</sup>Φ<sup>T</sup>Φ)<sup>−1</sup> --> N[Covariance]
    end
    
    subgraph Gaussian_Product_Property["Gaussian Product Property"]
        F --> FF[Product of Gaussians is a Gaussian]
        FF --> FF1["p(y|X) = p(y|X, θ) p(θ) is an unnormalized Gaussian distribution"]
        FF --> FF2["p(θ) = prior over parameters"]
        FF --> FF3["p(y|X, θ) = likelihood for the data"]
    end

```

---


### Explanation

This diagram visualizes the process of computing the marginal likelihood in the context of Bayesian linear regression.  It clearly outlines the generative model and the steps involved in the calculation.


*   **Problem Context:** The diagram starts by highlighting that we're dealing with Bayesian linear regression.
*   **Generative Model:**  This section emphasizes the key components of the generative model. The prior on the parameters (θ), the likelihood of the data given the parameters, and the observed data (x<sub>i</sub>, y<sub>i</sub>) are crucial elements.
*   **Marginal Likelihood Calculation:** The section explicitly shows the mathematical definition of the marginal likelihood (p(y|X)), highlighting the integration over all possible parameter values (θ).
*   **Resulting Distribution:**  The key takeaway is that the marginal likelihood itself follows a multivariate Gaussian distribution (N(m<sub>N</sub>, S<sub>N</sub>)).
*   **Mean and Covariance:**  The diagram explicitly shows how the mean (m<sub>N</sub>) and covariance (S<sub>N</sub>) of the resulting Gaussian are calculated.
*   **Gaussian Product Property:** This subgraph highlights the crucial property that a product of two Gaussian distributions results in another Gaussian distribution. This property is essential for the closed-form solution.

---

### Important Considerations

*   **Notations:** The diagram uses variables like θ, m<sub>0</sub>, S<sub>0</sub>, Φ, σ<sup>2</sup>, x<sub>i</sub>, y<sub>i</sub> to reflect the notations from the original text. These are important for understanding the specific mathematical details.
*   **Relationships:** The diagram shows how the various components (prior, likelihood, observations) relate to the final calculation of the marginal likelihood.
*   **Mathematical Formulation:** The diagram connects the mathematical definition of the marginal likelihood (integration) to the resulting Gaussian distribution. This clarifies the connection between the probabilistic model and the computational step.

This revised diagram provides a more structured and visual representation of computing the marginal likelihood in Bayesian linear regression, making the process easier to understand. Remember that the specific mathematical expressions and their derivation are critical components that are implied but not explicitly shown in the diagram for clarity.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---