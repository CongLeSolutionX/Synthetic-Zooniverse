---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Parameter Estimation MLE MAP Diagram
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
title: Parameter Estimation MLE MAP Diagram
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
    A["Parameter Estimation<br>(MLE, MAP)"] --> B{"Methods"}
    B --> C(Maximum Likelihood Estimation)
    B --> D(Maximum A Posteriori Estimation)
    
    subgraph MLE_Details["MLE Details"]
    style MLE_Details fill:#f933,stroke:#333,stroke-width:1px
        C --> CA(Finding optimal parameters)
        CA --> CB{Maximize Likelihood}
        CB -- p(y|X, θ) --> CC[Likelihood function]
        CA --> CD{"Data Set (D)"}
        CA --> CE{"Parameters (θ)"}
        CA --> CF(Numerical Optimization)
        CF --> CG[Gradient Ascent/Descent]
        CG --> CH("log p(y|X, θ)")
        CH --> CI[Log-Likelihood]
        
        
        subgraph MLE_Example["MLE Example"]
          CI -- Linear Regression --> CJ["p(y|x,θ) = Gaussian"]
          CJ -- Noise --> CK["ϵ ∼ N(0, σ<sup>2</sup>)"]
          CJ -- Data --> CL[y = Φθ + ϵ]
          CJ -- Parameters --> CM[θ]
          CJ --> CN["1/2σ<sup>2</sup>(y - Φθ)<sup>2</sup>"]
          CN --> CO[Minimization of negative log-likelihood]
        end
    end
    
    subgraph MAP_Details["MAP Details"]
    style MAP_Details fill:#f133,stroke:#333,stroke-width:1px
        D --> DA(Finding optimal parameters)
        DA --> DB{Maximize Posterior}
        DB -- p(θ|X, y) --> DC[Posterior Distribution]
        DA --> DD{"Data Set (D)"}
        DA --> DE{"Parameters (θ)"}
        DA --> DF{"Prior Distribution (p(θ))"}
        DA --> DG[Numerical Optimization]
        DG --> DH[Gradient Ascent/Descent]
        DH --> DI["log p(θ|X, y)"]
        DI --> DJ[Log-Posterior]
        
        subgraph MAP_Example["MAP Example"]
          DJ -- Linear Regression --> DK["p(θ) = Gaussian"]
          DK -- Mean --> DL[m<sub>0</sub>]
          DK -- Variance --> DM[S<sub>0</sub>]
          DJ -- Likelihood --> DN["p(y|x,θ) = Gaussian"]
          DN -- Noise --> DO["ϵ ∼ N(0, σ<sup>2</sup>)"]
          DN -- Data --> DP[y = Φθ + ϵ]
          DN -- Parameters --> DQ[θ]
          DJ --> DR["1/2σ<sup>2</sup>(y - Φθ)<sup>2</sup> + 1/2b<sup>2</sup>θ<sup>2</sup>"]
          DR --> DS[Minimization of negative log-posterior]
        end
    end

    subgraph Summary["Summary"]
      C --> CA1["θ* = arg max<sub>θ</sub> p(y|X, θ)"]
      D --> DA1["θ*<sub>MAP</sub> = arg max<sub>θ</sub> p(θ|X, y)"]
    end
    
%% classDef Style_for_MLE fill:#f935,stroke:#333,stroke-width:1px;
```


**Explanation:**

This Mermaid diagram provides a more structured and detailed view of parameter estimation using MLE and MAP.  It incorporates the following key elements:

* **MLE (Maximum Likelihood Estimation):**  Focuses on maximizing the likelihood of the observed data given the parameters.  It includes a subgraph detailing how this works in the context of linear regression with Gaussian noise.  Includes a key equation summarizing the process.
* **MAP (Maximum A Posteriori Estimation):**  Emphasizes maximizing the posterior distribution, which considers both the likelihood of the data and a prior distribution on the parameters.  A dedicated subgraph illustrates the MAP process for linear regression with a Gaussian prior.  Includes a key equation.
* **Data and Parameters:** Clear representation of the data set (D) and the parameters (θ) as crucial inputs for both methods.
* **Numerical Optimization:**  Highlights the use of numerical optimization techniques (gradient ascent/descent) for finding the optimal parameters.
* **Likelihood and Posterior:** Distinguishes the likelihood function (p(y|X, θ)) and the posterior distribution (p(θ|X, y)).
* **Log-Likelihood and Log-Posterior:** Explicitly shows the use of log-likelihood and log-posterior for numerical stability and computation.
* **Linear Regression Examples:** The diagrams incorporate examples of linear regression to illustrate how MLE and MAP work in practice with Gaussian data.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---