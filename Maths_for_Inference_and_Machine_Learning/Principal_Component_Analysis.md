---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Principal Component Analysis
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Principal Component Analysis - A Diagram Structure



```mermaid
---
title: Principal Component Analysis
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
    A["Principal Component Analysis<br>(PCA)"] --> B{Concepts}
    B -- Data Representation --> C[Data Matrix]
    C -- Example --> D("X = [x<sub>1</sub>, x<sub>2</sub>, ..., x<sub>n</sub>]")
    D -- Dimensions --> E[d]
    D -- Samples --> F[n]
    B -- Data Centering --> G[Mean Subtraction]
    G --> H[Centered Data Matrix]
    H -- Example --> I("X̄ = [x̄<sub>1</sub>, x̄<sub>2</sub>, ..., x̄<sub>n</sub>]")
    B -- Covariance Matrix --> J["Covariance Matrix (Σ)"]
    J --> K["Σ = (1/n) * X̄X̄<sup>T</sup>"]
    B -- Eigenvalue Decomposition --> L["Eigenvalue Decomposition (Σ)"]
    L --> M[Σ = UΛU<sup>T</sup>]
    M -- Eigenvectors --> N["Principal Components (U)"]
    M -- Eigenvalues --> O["Variances along Principal Components (Λ)"]
    B -- Dimensionality Reduction --> P[Feature Selection]
    P --> Q["Selecting top d eigenvectors (U<sub>d</sub>)"]
    P --> R[Projecting Data onto Principal Components]
    R --> S["Reduced Dimensionality Data Matrix (Y)"]
    S -- Example --> T(Y = U<sub>d</sub><sup>T</sup>X̄)
    B -- Whitening/Spherin --> U[Whitening Transformation]
    U --> V["Σ<sub>w</sub> = I (Identity Matrix)"]
    U --> W["Whitening Matrix (W)"]
    W --> X[W = UΛ<sup>-1/2</sup>]
    B -- Reconstruction --> Y[Reconstruction]
    Y --> Z["˜x<sub>i</sub> = W * (W<sup>T</sup> * W)<sup>-1</sup> * W<sup>T</sup> * x<sub>i</sub>"]
    B -- Statistical Perspective --> AA[Maximize Variance]
    AA --> AB[Maximizing w<sup>T</sup>Σw subject to w<sup>T</sup>w = 1]
    B -- Reconstruction Perspective --> BB[Minimize Reconstruction Error]
    BB --> BC["Minimizing ||X - ˜X||<sub>F</sub><sup>2</sup>"]

    subgraph Statistical_Interpretation["Statistical Interpretation"]
    style Statistical_Interpretation fill:#c254,stroke:#333,stroke-width:2px
        C --> CC(Scatter Matrix)
        CC -- Example --> CD(Σ = X̄X̄<sup>T</sup>)
        CC -- Explanation --> CE(Maximizes variance of projected data)
    end

    subgraph Dimensionality_Reduction["Dimensionality Reduction"]
    style Dimensionality_Reduction fill:#c215,stroke:#333,stroke-width:2px
        P --> PF[Reduced Dimensionality Data]
        PF -- Example --> PG(Y = U<sub>d</sub><sup>T</sup>X̄)
    end

    subgraph Whitening["Whitening"]
    style Whitening fill:#c915,stroke:#333,stroke-width:2px
        U --> UF(Whitened Data)
        UF -- Example --> UG(Σ<sub>w</sub> = I)
    end
  
    subgraph Computational_Aspects["Computational Aspects"]
    style Computational_Aspects fill:#c815,stroke:#333,stroke-width:2px
        P --> PI[Computational Cost]
        PI --> PJ["O(n*d<sup>2</sup>) or O(n*d)"]
    end
    
    subgraph SVD_Connection["SVD Connection"]
    style SVD_Connection fill:#c635,stroke:#333,stroke-width:2px
        X --> XM[SVD Connection]
        XM --> XN[SVD yields principal components and eigenvalues]
    end

classDef Style_for_concept_1 fill:#cf43,stroke:#333,stroke-width:2px
class C Style_for_concept_1

classDef Style_for_concept_4 fill:#c639,stroke:#333,stroke-width:2px
class G Style_for_concept_4

classDef Style_for_concept_5 fill:#c925,stroke:#333,stroke-width:2px
class J Style_for_concept_5

classDef Style_for_concept_6 fill:#cf24,stroke:#333,stroke-width:2px
class L Style_for_concept_6

classDef Style_for_concept_2 fill:#c13,stroke:#333,stroke-width:2px
class P Style_for_concept_2

classDef Style_for_concept_3 fill:#c63,stroke:#333,stroke-width:2px
class U Style_for_concept_3


classDef Style_for_concept_7 fill:#ccc4,stroke:#333,stroke-width:2px
class Y Style_for_concept_7

classDef Style_for_concept_8 fill:#c155,stroke:#333,stroke-width:2px
class AA Style_for_concept_8

classDef Style_for_concept_9 fill:#c455,stroke:#333,stroke-width:2px
class BB Style_for_concept_9

```


---


### Explanation of the Diagram

This Mermaid diagram illustrates the key concepts of Principal Component Analysis (PCA).  It visually connects the input data matrix, data centering, covariance matrix calculation, eigenvalue decomposition, feature selection (dimensionality reduction), and the concept of whitening. It also includes examples to show the application of the formulas in a practical setting.  The subgraphs provide further contextual explanation and highlight the computational aspects. The diagram emphasizes the duality between the statistical and reconstruction perspectives.  The notation used closely follows the common usage in linear algebra and statistical machine learning.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---