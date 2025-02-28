---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Link between SVD and PCA
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Link between SVD and PCA - A Diagram Structure


```mermaid
---
title: Link between SVD and PCA
config:
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
    subgraph SVD_PCA_Relationship["SVD PCA Relationship"]
        A["Singular Value Decomposition<br>(SVD)"] --> B{"Relationship"}
        B --> C["Principal Component Analysis<br>(PCA)"]
        C --> D{"Principal Components"}
        D --  are the eigenvectors of the covariance matrix --> E["Covariance Matrix<br>(XX<sup>T</sup>)"]
        E -- is the outer product of the data matrix with its transpose --> F["Data Matrix<br>(X)"]
        F -- X = UΣV<sup>T</sup> --> G["SVD Decomposition"]
        G -- "left singular vectors<br>(U)" --> D
        G -- "singular values<br>(Σ)" --> H{"Squared Singular Values"}
        H --  are the eigenvalues of the covariance matrix --> E
    end
    
    subgraph Summary["Summary"]
        D --> I[Dimensionality Reduction]
        I --> J{SVD and PCA achieve dimensionality reduction}
        J --  by projecting data onto the principal components --> K[Principal Components]
        K --  which correspond to the largest singular values --> L[Largest Singular Values]
        
        D --> M[Feature Extraction]
        M --> N{SVD and PCA extract features}
        N -- by projecting data onto the principal components --> O[Principal Components]
        O -- which capture most of the variance in the data --> P[Variance in Data]
    end
    
    
    subgraph Example_Data_Projection["Example Data Projection"]
        F --> Q[Data Projection]
        Q --> R["New feature space<br>(Y)"]
        R --  Y = U<sup>T</sup>X --> S{Project data onto principal axes}
    end

```

---

### Explaination


This diagram illustrates the relationship between SVD and PCA.  The core idea is that the principal components found by PCA are directly related to the singular vectors of the SVD of the data matrix.  The diagram highlights that the covariance matrix (XX<sup>T</sup>) is central to both, and how the SVD decomposition of the data matrix leads directly to the principal components and their corresponding eigenvalues.  Crucially, it also emphasizes how both methods achieve dimensionality reduction by projecting data onto these principal components. The example data projection part showcases how the projection actually works in practice.  Finally, the summary section captures the key takeaway of both techniques in terms of dimensionality reduction and feature extraction.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---