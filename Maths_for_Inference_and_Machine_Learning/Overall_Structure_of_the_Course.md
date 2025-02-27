---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Overall Structure of the Course
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---

## Mathematics for Inference and Machine Learning - A Diagrammatic Overview
```mermaid
---
title: Overall Structure of the Course
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
    A["Mathematics for Inference and Machine Learning"] --> B("Linear Regression")
    B --> C{"Probabilities"}
    B --> D{"Vector Calculus"}
    B --> E{"Parameter Estimation"}
    B --> F{"Gradient Descent"}
    B --> G{"Model Selection & Cross-Validation"}
    B --> H["Bayesian Linear Regression"]
    
    subgraph Feature_Extraction["Feature Extraction"]
        B --> I("Feature Extraction")
    end
    subgraph Support_Vector_Machines["Support Vector Machines"]
        I --> J("Support Vector Machines")
    end
    subgraph Appendices["Appendices"]
        A --> K["Appendices"]
    end

    C --> CA("Probability Density Functions")
    C --> CB("Means & Covariances")
    C --> CC("Statistical Independence")
    C --> CD("Basic Probability Distributions")
    C --> CE("Conjugacy")
    
    D --> DA("Partial Differentiation")
    D --> DB("Gradients")
    D --> DC("Jacobian")
    D --> DD("Linearization & Taylor Series")
    
    E --> EA("Maximum Likelihood Estimation")
    E --> EB("Overfitting")
    E --> EC("Regularization")
    E --> ED("Maximum-A-Posterior Estimation")
    
    F --> FA("Gradient Descent Algorithm")
    F --> FB("Stepsize")
    F --> FC("Momentum")
    F --> FD("Stochastic Gradient Descent")
    
    G --> GA(Cross-Validation)
    G --> GB(Bayesian Model Selection)
    G --> GC(Bayes Factors)
    
    H --> HA(Gaussian Prior)
    H --> HB(Parameter Posterior)
    H --> HC("Prediction & Inference")

    I --> IA("Eigen-decomposition")
    I --> IB(QR decomposition)
    I --> IC(SVD)
    I --> ID(PCA)
    I --> IE(LDA)
    I --> IF(Kernel Methods)

    J --> JA(Support Vector Classiﬁcation)
    J --> JB(Mapping to Higher Dimensions)
    J --> JC(Dual Problem)
    J --> JD(Support Vector Regression)

    K --> KA(Vector/Matrix Preliminaries)
    K --> KB(Scalar Products)
    K --> KC(Useful Matrix Identities)

    click A "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf" "Inference and Machine Learning Notes - Click to see the original lecture notes"
```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---