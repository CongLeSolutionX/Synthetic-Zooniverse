---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Completing the Squares
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Completing the Squares - A Diagram Structure


```mermaid
---
title: Completing the Squares
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
    A[Completing the Squares] --> B{Mathematical Technique}
    B --> C{Purpose}
    C --> CA["Simplify complex expressions, often quadratic forms, to a recognizable standard form (e.g., a Gaussian distribution)"]
    C --> CB[Allows for easy analysis and manipulation of expressions, frequently appearing in probabilistic models, optimization, and calculus]
    
    B --> D{Application in Probabilistic Models}
    D --> DA[Deriving posterior distributions, especially in Bayesian linear regression]
    D --> DB[Calculating marginal likelihoods in Bayesian model selection]
    D --> DC[Simplifying integrals and enabling closed-form solutions]
    
    B --> E{Steps}
    E --> EA[Identify Quadratic Form]
    EA --> EAA[The expression to be simplified must include a quadratic form in the variable of interest]
    E --> EB[Complete the Square]
    EB --> EBA["Use algebraic manipulation to rewrite the expression in the form (variable - constant)<sup>2</sup> + constant"]
    E --> EC[Isolate Terms]
    EC --> ECA[Group terms depending on the variable to be solved and isolate constants]

    E --> ED[Simplify & Rearrange]
    ED --> EDA[Organize terms to resemble a standard distribution form, like a Gaussian distribution]
    ED --> EDB[Apply algebraic operations like factoring, completing the square, and expanding]

    E --> EE[Recognize Standard Form]
    EE --> EEA[The simplified expression should resemble a standard distribution like Gaussian. Then, the mean and variance or other related parameters can be extracted]
    EE --> EEB[If the expression doesn't directly match a standard form, further simplification or rearrangement might be necessary]
    
    subgraph Example_Bayesian_Linear_Regression["Example Bayesian Linear Regression"]
        B --> BF{"Illustrative Example (Bayesian Linear Regression)"}
        BF --> BFA["Consider a log-posterior with quadratic terms in θ"]
        BFA --> BFAB["Rewrite the expression using completing the square to isolate quadratic terms and a constant value depending on θ"]
        BFA --> BFAC["Match the coefficients of the quadratic form with those of a Gaussian distribution, revealing the mean (m<sub>N</sub>) and covariance (S<sub>N</sub>) of the posterior distribution over parameters θ"]
    end
    
```

---

### Explanation of the Diagram

The diagram illustrates the technique of completing the squares, focusing on its mathematical foundation, application in probabilistic models, and the step-by-step procedure involved. The example subgraph highlights the direct application in the context of Bayesian Linear Regression.

* **Nodes:**  Represent key concepts and steps in the process.
* **Subgraphs:**  Provide focused examples within a broader context (e.g., Bayesian Linear Regression).
* **Arrows:** Indicate the relationships and flow of information between concepts.

This detailed diagram helps clarify the purpose, application, and procedure of completing the squares, particularly its role in deriving posterior distributions in Bayesian Linear Regression.  This structure can be adapted to other contexts by changing the illustrative example and adjusting the specific nodes and arrows. Remember to add annotations, equations, and formulas to make the diagram more descriptive and insightful.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---