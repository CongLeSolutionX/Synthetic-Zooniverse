---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Statistical Properties for Machine Learning
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Statistical Properties Diagram for Machine Learning


```mermaid
---
title: Statistical Properties for Machine Learning
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
    A[Statistical Properties] --> B(Mean)
    B --> BA{Definition}
    BA --> BA1["Expected value of a random variable"]
    BA --> BA2["Average value of the distribution"]
    BA --> BA3["Σx = ∫x p(x) dx"]

    A --> C(Variance)
    C --> CA{Definition}
    CA --> CA1["Measure of dispersion around the mean"]
    CA --> CA2["Average squared deviation from the mean"]
    CA --> CA3["σ^2 = ∫ (x - μ)^2 p(x) dx"]

    A --> D(Covariance)
    D --> DA{Definition}
    DA --> DA1["Measure of linear relationship between two random variables"]
    DA --> DA2["Average product of the deviations from their respective means"]
    DA --> DA3["Cov(x, y) = ∫ (x - μx)(y - μy) p(x, y) dx dy"]

    A --> E(Correlation)
    E --> EA{Definition}
    EA --> EA1["Standardized measure of linear relationship"]
    EA --> EA2["Ranges from -1 to +1"]
    EA --> EA3["Corr(x, y) = Cov(x, y) / (σx σy)"]
    
    A --> F(Standard Deviation)
    F --> FA{Definition}
    FA --> FA1["Square root of the variance"]
    FA --> FA2["Measure of dispersion in the same units as the data"]
    FA --> FA3["σ = √σ^2"]

    A --> G(Probability Density Function)
    G --> GA{Definition}
    GA --> GA1["Function describing the relative likelihood of a variable taking on a given value"]
    GA --> GA2["Area under the curve = 1"]
    GA --> GA3["p(x): Describes the probability of a random variable 'x' taking on different values"]

    A --> H(Cumulative Distribution Function)
    H --> HA{Definition}
    HA --> HA1["Describes the probability that a random variable is less than or equal to a given value"]
    HA --> HA2["P(x ≤ a) = ∫(-∞, a) p(x) dx"]
    HA --> HA3["Useful for quantiles and percentiles"]
    
    subgraph Summary["Summary"]
    style Summary fill:#cfc3,stroke:#333,stroke-width:2px
        A --> AA["Key Concepts"]
        AA --> AA1["Mean:<br>Central tendency"]
        AA --> AA2["Variance:<br>Dispersion"]
        AA --> AA3["Covariance:<br>Relationship"]
        AA --> AA4["Standard Deviation:<br>Dispersion in original units"]
        AA --> AA5["Probability Density Function:<br>Describes the probability of a random variable taking on a given value"]
        AA --> AA6["Cumulative Distribution Function:<br>Probability that a random variable is less than or equal to a given value"]
    end

```

---


### Explanation and Considerations

* **Clarity and Conciseness:** The diagram focuses on the core definitions and emphasizes the key mathematical expressions for each property.  Avoids unnecessary details.
* **Consistency:** Uses consistent formatting for nodes (e.g., curly braces for definitions).
* **Completeness:** Includes all the listed statistical properties (mean, variance, covariance, correlation, standard deviation, probability density function, and cumulative distribution function).
* **Context:** The diagram uses text labels, particularly in the {Definition} boxes, to explain the meaning of each concept.  The mathematical formulas provide a concrete expression of each statistical property.
* **Hierarchical Structure:** The subgraph "Summary" provides a concise overview of the key concepts and their roles.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---