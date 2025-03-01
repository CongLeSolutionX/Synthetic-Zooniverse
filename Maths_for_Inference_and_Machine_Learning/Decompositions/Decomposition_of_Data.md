---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Decomposition of Data
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Decomposition of Data - A Diagram Structure


```mermaid
---
title: Decomposition of Data
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
    A[Decomposition of Data] --> B{Methods}
    B --> C(Matrix Decompositions)
    B --> D(Feature Extraction Techniques)
    B --> E(Dimensionality Reduction)
    
    subgraph Matrix_Decompositions["Matrix Decompositions"]
        C --> CA(Eigen-decomposition)
        CA --> CA1["A = QΛQ<sup>-1</sup>"]
        CA --> CA2["Useful for symmetric matrices"]
        CA --> CA3["Applicable for finding principal components<br>(PCA)" ]
    
        C --> CB(QR decomposition)
        CB --> CB1["A = QR"]
        CB --> CB2["Useful for solving linear systems and orthogonal basis"]
        CB --> CB3["Crucial for Gram-Schmidt process"]
    
        C --> CC("Singular Value Decomposition<br>(SVD)")
        CC --> CC1["A = UΣV<sup>T</sup>"]
        CC --> CC2["Useful for dimensionality reduction, rank determination, and data whitening"]
        CC --> CC3["Closely related to PCA"]
    end
    
    subgraph Feature_Extraction_Techniques["Feature Extraction Techniques"]
        D --> DA("Principal Component Analysis<br>(PCA)")
        DA --> DA1["Maximizes variance of projected data"]
        DA --> DA2["Finds principal axes (eigenvectors) of data's covariance matrix"]
        DA --> DA3["Employs eigen-decomposition"]
    
        D --> DB("Linear Discriminant Analysis<br>(LDA)")
        DB --> DB1["Maximizes separability between classes"]
        DB --> DB2["Minimizes variability within classes"]
        DB --> DB3["Utilizes generalized eigenvalue problem"]
        DB --> DB4["Employs within-class and between-class scatter matrices"]
    end
    
    subgraph Dimensionality_Reduction["Dimensionality Reduction"]
        E --> EA(Rank Reduction)
        EA --> EA1["Keeping only significant singular values and vectors<br>(SVD)"]
        EA --> EA2["Reduces computational burden by eliminating noise and redundancy"]
    
        E --> EB(Data Whitening/Spherering)
        EB --> EB1["Normalizes data to have unit variance"]
        EB --> EB2["Facilitates applying other algorithms effectively"]
    end
    
```

----


### Explanation

This diagram visually decomposes the process of "Decomposition of Data" into its constituent parts.  It's organized using subgraphs for better clarity.  Each section (matrix decompositions, feature extraction, dimensionality reduction) is broken down into specific techniques with their respective uses and connections to mathematical concepts.  The use of inline equations enhances the diagram's semantic richness.  For example, the QR decomposition, SVD, and PCA are shown with their respective mathematical representations.  This structure provides a comprehensive view of how different methods contribute to data decomposition. Remember to adapt the specific content (equations and details) to match the document section you want to illustrate.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---