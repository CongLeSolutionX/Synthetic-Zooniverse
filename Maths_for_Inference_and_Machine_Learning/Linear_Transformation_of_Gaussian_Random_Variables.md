---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Linear Transformation of Gaussian Random Variables
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Linear Transformation of Gaussian Random Variables - A Diagram Structure


```mermaid
---
title: Linear Transformation of Gaussian Random Variables
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
    A[Linear Transformation] --> B{Gaussian Random Variable}
    B -- x ~ N(μ, Σ) --> C[x ∈ ℝ<sup>D</sup>]
    
    subgraph Transformation_Process["Transformation Process"]
        C -- y = Ax + b --> D[y ∈ ℝ<sup>E</sup>]
        D -- A ∈ ℝ<sup>E×D</sup> --> E[Matrix Transformation]
        D -- b ∈ ℝ<sup>E</sup> --> F[Translation Vector]
        E --> G{Properties of A}
        G -- Invertible --> H["y ~ N(Aμ + b, AΣA<sup>T</sup>)"]
    
        G -- Non-invertible --> I["y ~ Distribution with potentially non-zero covariance"]
    end
    
    subgraph Implications["Implications"]
        H -- Resulting Gaussian --> J[Mean]
        J --> JA[Aμ + b]
        H -- Resulting Gaussian --> K[Covariance]
        K --> KA[AΣA<sup>T</sup>]
    end
    
    I -- Resulting Distribution --> L[More Complex Distribution]
    L -- Implications --> M[Potential for Rank Reduction/Noise Filtering]
    L --> N[Further Analysis]
    
```

----


### Explanation

This diagram illustrates the linear transformation of a Gaussian random variable.

* **Gaussian Random Variable (B):**  A random variable `x` in `ℝ<sup>D</sup>` is distributed according to a multivariate Gaussian distribution with mean vector `μ` and covariance matrix `Σ`.  This is represented by the node `x ~ N(μ, Σ)`.

* **Transformation (D):**  The variable `x` is linearly transformed into `y` using a matrix `A` and a translation vector `b`.  The transformation is shown as `y = Ax + b`.  Crucially, the diagram highlights both the matrix `A` and the vector `b` as distinct components of the transformation.

* **Matrix Transformation (E):** The role of the matrix `A` in performing the transformation is emphasized.  This is a critical step in understanding the effect of the transformation on the original distribution.

* **Translation Vector (F):**  The translation vector `b` is explicitly represented as contributing to the transformation.

* **Properties of A (G):**  The diagram distinguishes between the cases where the transformation matrix `A` is invertible and non-invertible.

    * **Invertible (H):** If `A` is invertible, the resulting transformed variable `y` also follows a Gaussian distribution, but with a transformed mean and covariance. The specific formula, `y ~ N(Aμ + b, AΣA<sup>T</sup>)`, is displayed.

    * **Non-invertible (I):** If `A` is non-invertible, the resulting distribution is more complex, with implications for potential rank reduction or noise filtering (as singular values may be lost or reduced), and potentially requiring further analysis.


* **Implications (H, I):** The resulting Gaussian distribution's mean (J) and covariance (K) are clearly derived from the original mean and covariance and the transformation matrix.


This diagram provides a structured overview of the process, highlighting the critical characteristics of the transformation matrix `A` and the resulting distribution of `y`.  It also makes clear the distinctions between invertible and non-invertible transformations and the implications of those distinctions.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---