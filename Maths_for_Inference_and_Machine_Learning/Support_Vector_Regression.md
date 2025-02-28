---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Support Vector Regression
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Support Vector Regression - A Diagram Structure


```mermaid
---
title: Support Vector Regression (SVR)
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
    A["Support Vector Regression<br>(SVR)"] --> B{Core Concepts}
    B --> C(Linear Regression with Margin)
    C --> CA[Traditional linear regression aims to minimize the sum of squared errors between predicted and actual values.]

    B --> D(Non-Linear Mapping)
    D --> DA[SVR uses a non-linear mapping φ to transform data into a higher-dimensional feature space.]
    
    B --> E(ε-Insensitive Loss Function)
    E --> EA[SVR introduces an ε-insensitive loss function.]
    EA --> E1["Data points within a tube of width 2ε around the regression line are considered correctly predicted, without incurring a penalty (error)."]

    B --> F(Regularization)
    F --> FA["SVR incorporates a regularization term (e.g.,  ||w||<sup>2</sup>) to control model complexity and prevent overfitting."]

    subgraph SVR_Optimization["SVR Optimization"]
        B --> G(Optimization Problem)
        G --> GA[SVR's optimization problem aims to minimize a combined cost function.]
        GA --> G1[This cost function includes the regularization term, the ε-insensitive loss for points outside the tube, and a penalty term for points far from the tube.]
        G --> GB(Primal Form)
        GB --> G1["Minimize ||w||<sup>2</sup> + C Σ ξ<sub>i</sub>"]
        GB --> G2["subject to |y<sub>i</sub> - (w<sup>T</sup>φ(x<sub>i</sub>) + b)| ≤ ε + ξ<sub>i</sub>, ξ<sub>i</sub> ≥ 0"]
        G --> GC(Dual Form)
        GC --> G3[Minimize α<sup>T</sup>Kα - 1<sup>T</sup>α]
        GC --> G4["subject to 0 ≤ α<sub>i</sub> ≤ C, ∑ y<sub>i</sub>α<sub>i</sub> = 0"]
        GC --> G5["where K is the kernel matrix (K<sub>ij</sub> = k(x<sub>i</sub>, x<sub>j</sub>) = φ(x<sub>i</sub>)<sup>T</sup>φ(x<sub>j</sub>))"]
    end
    
    subgraph SVR_Summary["SVR Summary"]
        F --> FB[Key Parameters]
        FB --> FB1["C (cost of error), ε (width of the tube), and kernel function (k) control the regression quality"]
    end
    
    
    subgraph SVR_Application["SVR Application"]
        B --> H(Kernel Trick)
        H --> HA[The kernel trick enables efficient computations in the high-dimensional feature space without explicitly calculating φ]
    end
    
    subgraph SVR_Decision_Function["SVR Decision Function"]
        B --> I(Decision Function)
        I --> IA[The decision function for SVR is similar to that of SVM, but instead of classifying, it predicts continuous values]
        IA --> I1["Predictions are calculated using the support vectors and the kernel function, with an offset (b)"]
    end
    
```

---

### Explanation and Considerationss

* **Core Concepts (B):**  This is the top-level grouping of the key elements that define SVR.

* **Linear Regression with Margin (C):**  Illustrates the foundation in traditional linear regression, showing how SVR builds upon it.

* **Non-linear Mapping (D):**  SVR's capability to handle non-linear data relationships is highlighted.  It maps input data into a higher-dimensional space via a mapping function (φ).

* **ε-Insensitive Loss Function (E):** Shows how SVR defines an error function that tolerates deviations within a certain margin.  The error doesn't incur a penalty if the point falls within the `ε` tube.

* **Regularization (F):** This is a crucial component that prevents overfitting. The added regularization term (e.g., L<sub>2</sub> norm) controls the complexity of the SVR model.

* **Optimization Problem (G):** This subgraph breaks down the optimization problem into primal and dual forms.  Key components of the optimization, like the kernel matrix, are shown.

* **Kernel Trick (H):** Explains the essential idea behind how SVR efficiently handles high-dimensional feature spaces without needing to compute the mapping φ directly.

* **Decision Function (I):**  Describes how SVR computes predictions using support vectors and the kernel function, demonstrating its ability to predict continuous values rather than classifying data into discrete categories.

* **Key Parameters (FB):**  Highlights the crucial parameters that affect the quality and complexity of the SVR model.

* **Application (SVR_Application):** Showcases the use cases of SVR, connecting it to real-world problems.

---

### Diagram Style Considerations

* **Clarity:** Use clear node labels and concise descriptions.
* **Hierarchy:** Employ subgraphs to organize related concepts and clarify the structure.
* **Visual Connections:** Use clear edges to show relationships between concepts.
* **Mathematical Precision:**  Include mathematical expressions (like the cost function formulas) where appropriate.
* **Emphasis on Key Concepts:** Clearly highlight the core ideas, such as the ε-insensitive loss and the kernel trick.


This improved diagram more accurately reflects the key components of SVR and provides a clearer structure for understanding the method. Remember to tailor specific nodes and edges to reflect the specific details of the document being visualized.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---