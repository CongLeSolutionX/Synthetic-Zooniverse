---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Gaussian Distribution
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
title: Gaussian Distribution
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
    A[Gaussian Distribution] --> B{Properties}
    B --> C(Mean)
    B --> D(Variance)
    B --> E(Covariance Matrix)
    B --> F(Density Function)
    
    subgraph Univariate_Gaussian["Univariate Gaussian"]
        C --> CA[µ]
        D --> DB[σ²]
        F --> FC["1 / (σ√(2π)) * exp(-(x-µ)² / (2σ²))"]
        
        
        %% note right of CA
        %% Mean of the distribution
        %% end note
        
        %% note right of DB
        %% Variance (spread) of the distribution
        %% end note

        %% note right of FC
        %% Probability density function;
        %% Gives the probability density at a particular value x.
        %% end note

    end
    
    subgraph Multivariate_Gaussian["Multivariate Gaussian"]
        C --> CB["µ (Vector)"]
        D --> DD["Σ (Matrix)"]
        F --> FD["(2π)^(-D/2) * |Σ|^(-1/2) * exp(-(x-µ)^T Σ^(-1) (x-µ)/2)"]
    
        %% note right of CB
        %% Mean vector of the distribution.
        %% end note
    
        %% note right of DD
        %% Covariance matrix of the distribution;
        %% Describes the relationships and variances between multiple dimensions.
        %% end note
    
        %% note right of FD
        %% Probability density function for multiple dimensions.
        %% end note
    end

    subgraph Relationships["Relationships"]
        C --> CC[Describes the center of the distribution]
        D --> DC[Describes the spread of the distribution]
        E --> EE[Describes the correlations between dimensions]
        F --> FF[Provides the probability density at any point]
        %% note bottom
        %% The density function is crucial for calculating probabilities of events and
        %% for sampling from the distribution.
        %% end note
    end
    
```


---

### Explanation

This Mermaid diagram visualizes the Gaussian distribution, separating the univariate and multivariate cases.  It clearly highlights the key properties (mean, variance, covariance matrix, and density function) and their roles in defining the distribution.  The use of subgraphs clarifies the difference in representation for single and multiple dimensions.  Annotations provide additional context for each property, making the visualization more informative.  The inclusion of "Relationships" subgraph further emphasizes the interplay between the properties and the interpretation of the distribution. This structure can easily be adapted for different probabilistic distributions or statistical models by replacing the specific nodes and connections.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---