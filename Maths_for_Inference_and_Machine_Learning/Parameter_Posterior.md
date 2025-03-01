---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Parameter Posterior
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Parameter Posterior - A Diagram Structure


```mermaid
---
title: Parameter Posterior
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
    subgraph Parameter_Posterior["Parameter Posterior"]
        A[Parameter Posterior] --> B{Concept}
        B --> C[Represents the probability distribution over the parameters of a model, given observed data.]
        B --> D[Provides a complete description of the uncertainty associated with the parameter values.]
        B --> E[Crucial for Bayesian inference and prediction.]
        
        subgraph Bayesian_Inference["Bayesian Inference"]
            C --> CA[Derived from Bayes' Theorem, combining the prior probability distribution over parameters and the likelihood function of the observed data.]
            CA --> CB[Prior: Our initial beliefs about the parameter values.]
            CA --> CC[Likelihood:<br>How well the observed data is explained by different parameter values.]
        end
        
        subgraph Calculation_Methods["Calculation Methods"]
            B --> DA[Calculated by integrating the likelihood function over all possible parameter values, weighted by the prior distribution]
            DA --> DB[Requires calculating the marginal likelihood, or evidence.]
            DA --> DC[Marginal Likelihood:<br>A normalizing constant that ensures the posterior integrates to 1]
        end
        
        subgraph Example_Linear_Regression["Example Linear Regression"]
            B --> EA[In Linear Regression, the parameter posterior is a Gaussian distribution]
            EA --> EB[Mean and covariance of this Gaussian distribution contain information about the uncertainty in the parameter estimates, and this information is essential for making predictions]
            EA --> EC["The mean of the posterior often coincides with the maximum a posteriori (MAP) estimate"]
        end
    end
    
```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---