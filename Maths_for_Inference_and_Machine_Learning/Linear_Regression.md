---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Linear Regression
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---

## A Diagram Structure for Linear Regression



```mermaid
---
title: Linear Regression Diagram Structure
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
    A[Linear Regression] --> B{Model Formulation};
    B -- Inputs (x) --> C[x<sub>1</sub>];
    B -- Inputs (x) --> C1[x<sub>2</sub>];
    B -- Inputs (x) --> C2[...x<sub>N</sub>];
    B -- Outputs (y) --> D[y<sub>1</sub>];
    B -- Outputs (y) --> D1[y<sub>2</sub>];
    B -- Outputs (y) --> D2[...y<sub>N</sub>];
    B -- Parameters (θ) --> E[θ<sub>1</sub>];
    B -- Parameters (θ) --> E1[θ<sub>2</sub>];
    B -- Parameters (θ) --> E2[...θ<sub>D</sub>];
    B -- Noise (ϵ) --> F[ϵ<sub>1</sub>];
    B -- Noise (ϵ) --> F1[ϵ<sub>2</sub>];
    B -- Noise (ϵ) --> F2[...ϵ<sub>N</sub>];


    subgraph Model_Equation
        C --> G("x<sub>i</sub> ∈ R<sup>D</sup>");
        D --> H("y<sub>i</sub> ∈ R");
        E --> I("θ ∈ R<sup>D</sup>");
        F --> J("(ϵ) ∼ N(0, σ<sup>2</sup>)");
        I --> K("y<sub>i</sub> = x<sub>i</sub><sup>T</sup>θ + ϵ<sub>i</sub>");
    end

    subgraph Parameter_Estimation
        B --> L{Parameter Learning};
        L -- Maximum Likelihood Estimation --> M["arg max<sub>θ</sub> p(y|X, θ)"]
        L -- Maximum A Posteriori Estimation --> N["arg max<sub>θ</sub> p(θ|y, X)"]
    end


    subgraph Data_Dependence
        M --> O["p(y|X, θ)"]
        M --> O1["p(y<sub>i</sub>|x<sub>i</sub>, θ)"]
        O --> P[Likelihood Function]
        O1 --> P1[Factorizes over data points]
        N --> Q["p(θ|y,X)"]
        N --> Q1["p(θ)"]
        Q --> R[Posterior Distribution]

    end

    subgraph Likelihood_Example
        O1 --> S[Gaussian Likelihood];
        S --> T("p(y<sub>i</sub>|x<sub>i</sub>, θ) = (2πσ<sup>2</sup>)<sup>-1/2</sup> exp(-(y<sub>i</sub> - x<sub>i</sub><sup>T</sup>θ)<sup>2</sup> / 2σ<sup>2</sup>)");
    end
    
    
    subgraph Gradient_Descent
        L --> U[Gradient Descent];
        U --> V[Minimizing Negative Log-Likelihood];
        V --> W("L(θ) = -log p(y|X, θ)");
        
        W --> X[Minimizing Error Function];
        X --> Y["L(θ) = Σ<sub>i=1</sub><sup>N</sup> (y<sub>i</sub> - x<sub>i</sub><sup>T</sup>θ)<sup>2</sup> / 2σ<sup>2</sup>"];
    end
    
```


**Explanation:**

This Mermaid diagram visually represents the components of a linear regression model, its parameter estimation methods, and the mathematical underpinnings.  It connects the various elements (inputs, outputs, parameters, noise) and shows their relationships. The use of subgraphs enhances readability and organization. The equations are included for direct reference.


* **Nodes:**  Represent entities like variables, functions, and estimation methods.  The diagram includes nodes for inputs (x<sub>i</sub>), outputs (y<sub>i</sub>), parameters (θ<sub>i</sub>), and the noise term (ϵ<sub>i</sub>).
* **Edges:** Indicate relationships. For example, an edge connecting 'x<sub>i</sub>' to 'y<sub>i</sub>' represents the input-output relationship.
* **Subgraphs:** Organize related concepts, like the model equation, parameter estimation, or the likelihood example.
* **Equations:**  The diagram incorporates the essential equations of linear regression, including the model itself (y<sub>i</sub> = x<sub>i</sub><sup>T</sup>θ + ϵ<sub>i</sub>) and the likelihood function for a Gaussian noise model. This clarifies the mathematical basis of the model.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---