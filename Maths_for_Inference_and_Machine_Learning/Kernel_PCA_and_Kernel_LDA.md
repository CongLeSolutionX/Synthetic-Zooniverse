---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Kernel PCA and Kernel LDA
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Kernel PCA and Kernel LDA - A Diagram Structure


```mermaid
---
title: Maximum Likelihood for Probabilistic PCA
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
    A[Kernel Methods] --> B(Kernel PCA)
    B --> C{"Input Space <br>(X)"}
    C --> CA[x<sub>1</sub>, x<sub>2</sub>, ..., x<sub>n</sub>]
    B --> D("Feature Mapping<br>(φ)")
    D --> DA["φ(x<sub>1</sub>), φ(x<sub>2</sub>), ..., φ(x<sub>n</sub>)"]
    D --> DB[φ: R<sup>F</sup> → H]
    
    B --> E(Kernel Trick)
    E --> EA["φ(x<sub>i</sub>)<sup>T</sup>φ(x<sub>j</sub>) = k(x<sub>i</sub>, x<sub>j</sub>)"]
    E --> EB[k: Kernel Function]
    
    B --> F("Kernel Matrix<br>(K)")
    F --> FA["K = [k(x<sub>i</sub>, x<sub>j</sub>)]"]

    B --> G(PCA in Feature Space)
    G --> GA[Principal Components in H]
    
    B --> H(Dimensionality Reduction in H)

    subgraph Kernel_PCA_Example["Kernel PCA Example"]
        B -- Example:  k(x,y) = exp(-||x-y||<sup>2</sup> / 2σ<sup>2</sup>)  --> I
        I -- x --> J[x]
        I -- y --> K[y]
        I -- k(x,y) --> L["k(x,y) = exp(-||x-y||<sup>2</sup> / 2σ<sup>2</sup>)"]
    end

    A --> I1(Kernel LDA)
    I1 --> C1{"Input Space<br>(X)"}
    C1 --> C1A[x<sub>1</sub>, x<sub>2</sub>, ..., x<sub>n</sub>]
    I1 --> D1("Feature Mapping (φ)")
    D1 --> D1A["φ(x<sub>1</sub>), φ(x<sub>2</sub>), ..., φ(x<sub>n</sub>)"]
    D1 --> D1B[φ: R<sup>F</sup> → H]
    
    I1 --> E1(Kernel Trick)
    E1 --> E1A["φ(x<sub>i</sub>)<sup>T</sup>φ(x<sub>j</sub>) = k(x<sub>i</sub>, x<sub>j</sub>)"]
    E1 --> E1B[k: Kernel Function]
    
    I1 --> F1("Kernel Matrix<br>(K)")
    F1 --> F1A["K = [k(x<sub>i</sub>, x<sub>j</sub>)]"]

    I1 --> G1(LDA in Feature Space)
    G1 --> G1A[Principal Components in H]
    
    I1 --> H1(Dimensionality Reduction in H)
    I1 --> I1I{"Class Labels<br>(y)"}
    I1I --> I1IA[y<sub>1</sub>, y<sub>2</sub>, ..., y<sub>n</sub>]

    subgraph Summary["Summary"]
        I1 -- Key difference:<br>LDA leverages class labels. --> I1S
        I1S -- Handles non-linearly separable data in a higher-dimensional space. --> I1S1
        I1S1 -- Critical:<br>Kernel trick allows computation without explicit φ. --> I1S2
    end
    
```

---

### Explanation

This diagram illustrates Kernel PCA and Kernel LDA, highlighting their shared structure and the crucial differences.

* **Kernel PCA:**  Starts with data in the input space (X).  A feature mapping (φ) transforms the data into a higher-dimensional feature space (H).  The kernel trick allows calculation of inner products in the feature space (φ(x<sub>i</sub>)<sup>T</sup>φ(x<sub>j</sub>) = k(x<sub>i</sub>, x<sub>j</sub>)) without explicitly computing φ. A kernel matrix (K) is formed using these kernel values. Finally, the diagram depicts how standard PCA techniques are applied within the feature space to derive principal components for dimensionality reduction.

* **Kernel LDA:**  Similar to Kernel PCA, it begins with input data (X) and uses the feature mapping (φ) to transform into a higher-dimensional feature space (H).  The crucial difference lies in the incorporation of class labels (y). This aspect is explicitly called out in the summary subgraph, which emphasizes that Kernel LDA takes advantage of class labels for dimensionality reduction that works in non-linear spaces.  The kernel trick simplifies calculations, allowing dimensionality reduction without needing to explicitly know the feature mapping.

* **Key Difference:** The crucial difference between Kernel PCA and Kernel LDA is that Kernel LDA uses class labels to optimize the dimensionality reduction to be better suited for classification tasks. Kernel PCA only aims to maximize variance, whereas Kernel LDA aims to maximize class separation while minimizing within-class variance.

* **Summary:** The summary subgraph emphasizes the core concepts: the ability to handle non-linearly separable data by transforming to a higher-dimensional feature space and the use of the kernel trick to effectively perform computations within this space without explicit calculation of the feature mapping.


This diagram provides a structured and visual understanding of the key steps and differences between these two kernel methods. Remember to tailor the specific kernel functions (like the example Gaussian RBF kernel) and the types of data used to match the specific application you're visualizing.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---