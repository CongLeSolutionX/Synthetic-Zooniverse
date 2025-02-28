---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Model
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Model - A Diagram Structure


```mermaid
---
title: Model
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
    A[Model] --> B(Linear Regression)
    B --> C{Parametric Models}
    C --> CA[y = Φθ + ϵ]
    
    subgraph Linear_Regression_Components["Linear Regression Components"]
        CA -- θ --> CB[Parameters]
        CA -- Φ --> CC[Feature Transformation]
        CA -- ϵ --> CD[Noise]
    end
    
    A --> D(Bayesian Linear Regression)
    D --> E{Probabilistic Models}
    E --> EA["θ ∼ N(m<sub>0</sub>, S<sub>0</sub>)"]
    E --> EB["y | Φθ ∼ N(0, σ<sup>2</sup>I)"]
    
    subgraph Bayesian_Components["Bayesian Components"]
        EA -- m<sub>0</sub> --> EC[Prior Mean]
        EA -- S<sub>0</sub> --> ED[Prior Covariance]
        EB -- σ<sup>2</sup> --> EE[Noise Variance]
    end
    
    A --> F(Polynomial Regression)
    F --> G{Non-linear Models}
    G --> GA["y = φ(x)θ + ϵ"]
    
    subgraph Polynomial_Components["Polynomial Components"]
        GA -- φ(x) --> GB[Nonlinear Features]
        GA -- θ --> GC[Parameters]
        GA -- ϵ --> GD[Noise]
    end
    
    A --> H(Support Vector Machines)
    H --> I{Classiﬁcation/Regression}
    I --> IA[Linear Separating Hyperplane]
    
    subgraph SVM_Components["SVM Components"]
        IA -- w --> IB[Weights]
        IA -- b --> IC[Bias]
    end
    
    I --> ID[Non-linear Mappings]
    ID --> IE["φ(x)"]
    
    I --> IF[Dual Optimization Problem]
    IF --> IG[α]
    
    
    subgraph Summary["Summary"]
        C -- Summary: --> CC1[Parameterization of the regression function]
        CC1 --> CC2["Function Classes<br>(e.g., polynomials)"]
        CC1 --> CC3["Parametrization choices<br>(e.g., degree of the polynomial)"]
    
        E -- Summary: --> EE1[Prior on parameters]
        EE1 --> EE2[Gaussian Prior]
        EE1 --> EE3[Uncertainty in parameters]
    
        G -- Summary: --> GG1[Nonlinear Feature Extraction]
        GG1 --> GG2[Kernel Functions]
        GG1 --> GG3[Feature Space]

        H -- Summary: --> HH1[Maximizing the Margin]
        HH1 --> HH2[Dual Optimization]
        HH1 --> HH3[Support Vectors]
    end
    
```

---

### Explanation

This diagram provides a structured overview of different models, categorizing them by their core characteristics.  Each model is represented by a node, and subgraphs detail the key components within each model type.  The diagram is adaptable, allowing you to add more details or specific aspects of each model.  It uses a consistent visual language to represent models and their components.  Importantly, the diagram highlights the relationship between linear and non-linear models.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---