---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Maximum Likelihood for Probabilistic PCA
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Maximum Likelihood for Probabilistic PCA - A Diagram Structure


```mermaid
---
title: Maximum Likelihood for Probabilistic PCA
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
    subgraph Probabilistic_PCA["Probabilistic PCA"]
        A[Probabilistic PCA] --> B{Model Formulation}
        B -- Equation: x<sub>i</sub> = Wy<sub>i</sub> + μ + e<sub>i</sub> --> C[Variables]
        C --> C1[x<sub>i</sub>]
        C --> C2[y<sub>i</sub>]
        C --> C3[W]
        C --> C4[μ]
        C --> C5[e<sub>i</sub>]
        
        C1 -- i.i.d. Gaussian distributed input vector --> C1a["N(0, Σ)"]
        C2 -- Zero-mean Gaussian --> C2a["N(0, I)"]
        C5 -- i.i.d. Gaussian noise --> C5a["N(0, σ<sup>2</sup>I)"]

        C3 -- d x q matrix, projection matrix --> C3a[Orthogonal basis]
        C4 -- q-dimensional mean vector --> C4a[Centroid of the projected data]

        
        B --> D{Conditional Probabilities}
        D -- Equation:<br>p(x<sub>i</sub>|y<sub>i</sub>, W, σ) = N(x<sub>i</sub>|Wy<sub>i</sub> + μ, σ<sup>2</sup>I) --> E
        D -- Equation:<br>p(y<sub>i</sub>) = N(y<sub>i</sub>|0, I) --> F


        D -- Equation:<br>p(x<sub>i</sub>|W, σ) = ∫<sub>y<sub>i</sub></sub> p(x<sub>i</sub>|y<sub>i</sub>, W, σ) p(y<sub>i</sub>) dy<sub>i</sub> --> G[Marginal Distribution]


        G --> H{Maximum Likelihood Estimation}
        H -- Objective:<br>θ<sub>o</sub> = arg max<sub>θ</sub> ln p(x<sub>1</sub>, ..., x<sub>n</sub>|θ) --> I[Likelihood Function]
        
        I --> J[Log-likelihood of each data point]
        J -- Equation:<br>ln p(x<sub>i</sub>|θ) --> K[Parameter Estimation]

        K --> L[Solving for Parameters]
        L -- Equation:<br>∇<sub>θ</sub>L(θ) = 0 (finding optimal W, μ, σ<sup>2</sup>) --> M[Optimal Parameters]

        M --> N[Result]
        N -- Optimal parameters<br>(W, μ, σ<sup>2</sup>) --> O[Model Trained]


        subgraph Notes["Notes"]
            E -- Note:<br>N(x|μ, Σ) is the multivariate Gaussian distribution. --> E1
            F -- Note:<br>I is the identity matrix. --> F1
            C5a -- Note:<br>σ<sup>2</sup>I represents the variance of the noise. --> C5b
            G -- Note:<br>Integrating out y<sub>i</sub> finds the marginal distribution of x<sub>i</sub>, given the parameters. --> G1

            O -- Note:  The resulting model allows for dimensionality reduction, data generation, and modeling class-conditional densities. --> O1
        end
    end
    
```


---

### Explanation of the Diagram

* **Subgraph `Probabilistic PCA`:** This encapsulates the entire Probabilistic PCA model.
* **Node `A`:**  The overall Probabilistic PCA model.
* **Node `C` and connected nodes:**  Define the variables involved in the PPCA model.  The links illustrate the distributions they follow and their role in the model.
* **Node `B`:**  Showcases the core equation and how it relates to the variables.
* **Node `D`:** Shows the conditional and marginal distributions in mathematical equations.
* **Node `G`:** Showcases the mathematical equation of the marginal distribution.
* **Node `H`:**  Defines the core goal of the Maximum Likelihood Estimation.
* **Node `I`:** Shows the likelihood function of the PPCA model.
* **Node `J`:** Shows the log-likelihood function of the PPCA model.
* **Node `K`:** Shows how the optimal parameters are estimated from the likelihood function.
* **Node `L`:** Shows how the parameters are solved using differentiation.
* **Node `M`:** Shows the final results.
* **Subgraph `Notes`:** This provides crucial explanations for the notation and mathematical concepts used in the model.  The notes are essential for understanding the meaning of the nodes and edges.


This diagram provides a visual representation of the Probabilistic PCA model and the associated maximum likelihood estimation process, aligning with the structure suggested in the previous response. Remember to fill in specific equations and variable names as appropriate for your specific use case.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---