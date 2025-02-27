---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Probabilistic Distributions
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
title: Probabilistic Distributions
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
    subgraph Probabilistic_Distributions["Probabilistic Distributions"]
        A["Probability Distributions"] --> B("Continuous Distributions")
        B --> C(Gaussian/Normal)
        C --> D{"Mean (µ), Covariance (Σ)"}
        C --> E["p(x|µ, Σ) = (2π)^(-D/2) |Σ|^(-1/2) exp(-(x-µ)^T Σ^(-1) (x-µ)/2)"]
        
        B --> F(Bernoulli)
        F --> G{"Parameter (µ)"}
        F --> H["p(x|µ) = µ^x(1-µ)^(1-x)"]
        
        B --> I(Binomial)
        I --> J{"Parameters (N, µ)"}
        I --> K["p(m|N,µ) = (N choose m) µ^m (1-µ)^(N-m)"]

        B --> L(Beta)
        L --> M{"Parameters (α, β)"}
        L --> N["p(µ|α,β) = (Γ(α+β))/(Γ(α)Γ(β)) µ^(α-1)(1-µ)^(β-1)"]

        B --> O(Gamma)
        O --> P{"Parameters (a, b)"}
        O --> Q["p(τ|a,b) = (b^a)/(Γ(a)) τ^(a-1) exp(-bτ)"]
        
        B --> R(Wishart)
        R --> S{"Parameters (Σ, ν)"}
        R --> T["p(W|Σ,ν) = B|Σ|^(ν-D-1)/2 exp(-tr(W^(-1)Σ)/2)"]
        
        B --> U(Uniform)
        U --> V{"Parameters (a, b)"}
        U --> W["p(x) = 1/(b-a) if a<=x<=b"]
    
    end
    
```


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---