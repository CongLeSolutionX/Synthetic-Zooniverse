---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Beta Distribution
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
title: Beta Distribution
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
    A[Beta Distribution] --> B{Definition}
    B -- Continuous distribution over the interval [0, 1] --> C
    C -- Parameterized by α > 0 and β > 0 --> D
    D -- Probability Density Function --> E["p(µ|α, β) = Γ(α + β) / (Γ(α)Γ(β)) * µ<sup>α−1</sup> * (1 − µ)<sup>β−1</sup>"]
    E -- where: --> F
    F -- µ is the variable --> G[µ]
    F -- α is the shape parameter --> H[α]
    F -- β is the shape parameter --> I[β]
    F -- Γ is the gamma function --> J["Γ(t) = ∫<sub>0</sub><sup>∞</sup> x<sup>t−1</sup>e<sup>−x</sup>dx"]
    
    subgraph Example_Relationships["Example Relationships"]
        C -- Special Cases --> K
        K -- α = 1, β = 1 --> L["Uniform Distribution U[0, 1]"]
        K -- α, β < 1 --> M["Bimodal distribution with spikes at 0 and 1"]
        K -- α, β > 1 --> N["Unimodal distribution"]
        K -- α = β --> O["Unimodal, symmetric, centered at 0.5"]
    end
    
    subgraph Summary["Summary"]
        C --> P[Mean]
        P --> P1["E[µ] = α / (α + β)"]
        C --> Q[Variance]
        Q --> Q1["V[µ] = αβ / (α + β)<sup>2</sup>(α + β + 1)"]
    end
    
```

----


This Mermaid diagram visually represents the Beta distribution, highlighting its key characteristics, parameters, and relationships to other distributions.  It also summarizes important properties like mean and variance. The diagram effectively encapsulates the core concepts for understanding the Beta distribution. Remember that the diagram can be further customized based on the specific context or further details needed to be highlighted.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---