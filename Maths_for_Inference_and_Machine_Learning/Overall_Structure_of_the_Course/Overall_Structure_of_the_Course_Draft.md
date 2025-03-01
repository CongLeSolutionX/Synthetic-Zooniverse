---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Overall Structure of the Course  - Draft
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
title: Mathematics for Inference and Machine Learning
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
    A[Mathematics for Inference and Machine Learning] --> B(Linear Regression);
    B --> C{Probabilistic Foundations};
    B --> D{Mathematical Tools};
    B --> E{Learning & Inference};
    B --> F[Bayesian Linear Regression];
    B --> G(Feature Extraction);
    B --> H(Support Vector Machines);
    
    subgraph Appendices
        A --> K[Appendices];
    end

    C --> CA(Probability Distributions);
    CA --> CAB(Discrete Distributions);
    CA --> CAC(Continuous Distributions);
    CA --> CAD(Gaussian Distributions);
    CA --> CAE(Multivariate Gaussians);
     CA --> CAF(Conditional Distributions);
    C --> CB(Statistical Concepts);
    CB --> CBB(Means & Covariances);
    CB --> CBC(Independence & Conditional Independence);
    CB --> CBD(Conjugacy);
    
    D --> DA(Vector Calculus);
    DA --> DAB(Partial Derivatives);
    DA --> DAC(Gradients);
    DA --> DAD(Jacobian);
    DA --> DAE(Taylor Series & Linearization);
    D --> DB(Matrix Decompositions);
    DB --> DBB(Eigen-decomposition);
    DB --> DBC(QR decomposition);
    DB --> DBD("Singular Value Decomposition (SVD)");
    
    E --> EA(Parameter Estimation);
    EA --> EAB("Maximum Likelihood Estimation (MLE)");
    EA --> EAC(MLE with Features);
    EA --> EAD(Properties of MLE);
    EA --> EAE(Overfitting);
    EA --> EAF(Regularization);
    EA --> EAG("Maximum-A-Posterior Estimation (MAP)");
    E --> EB(Optimization Algorithms);
    EB --> EBB(Gradient Descent);
    EB --> EBC(Gradient Descent Variants);
    EB --> EBD("Stochastic Gradient Descent (SGD)");
    EB --> EBE(Stepsize Strategies);
    EB --> EBF(Momentum);
    E --> EC(Model Selection);
    EC --> ECB(Cross-Validation);
    EC --> ECC(Bayesian Model Selection);
    EC --> ECD(Bayes Factors);


    F --> FA(Prior & Posterior Distributions);
    F --> FB(Prediction & Inference);
    F --> FC(Marginal Likelihood);

    G --> GA(PCA);
    GA --> GAB(Statistical Perspective);
    GA --> GAC(Reconstruction Perspective);
    GA --> GAD(Computational Aspects);
    G --> GB("Linear Discriminant Analysis (LDA)");
    G --> GC(Kernel Methods);
    G --> GCD(Kernel PCA);
    G --> GCE(Kernel LDA);


    H --> HA(Support Vector Classiﬁcation);
    HA --> HAB(Linear Separating Hyperplanes);
    HA --> HAC(Lagrangian Duality);
    HA --> HAD(KKT Conditions);
    HA --> HAE(Dual Problem);
    HA --> HAF(Mapping to Higher Dimensions);
    H --> HB(Support Vector Regression);
    H --> HC(Kernel Trick);
    
    K --> KA(Vectors & Matrices);
    K --> KB(Vector Operations);
    K --> KC(Matrix Operations);
    K --> KD(Norms);
    K --> KE(Determinants & Inverses);
    K --> KF(Eigenvalues & Eigenvectors);
    K --> KG(Special Matrices);
```


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---