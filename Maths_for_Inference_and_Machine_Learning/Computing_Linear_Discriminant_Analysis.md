---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---


# Computing Linear Discriminant Analysis
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Computing Linear Discriminant Analysis - A Diagram Structure


```mermaid
---
title: Computing Linear Discriminant Analysis
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
    A["Computing Linear Discriminant Analysis<br>(LDA)"] --> B{Input Data}
    B --> C(Training Data)
    C --> CA("X = [x<sub>1</sub>, x<sub>2</sub>, ..., x<sub>n</sub>]")
    CA -- "Features<br>(F-dimensional)" --> CB("y = [y<sub>1</sub>, y<sub>2</sub>, ..., y<sub>n</sub>]")
    CB -- "Class Labels<br>(C classes)" --> CC(C)
    
    subgraph Data_Preprocessing["Data Preprocessing"]
        C --> D(Data Centering)
        D --> DA("Compute mean μ = (1/n) * Σx<sub>i</sub>")
        D --> DB(Center each data point x<sub>i</sub> = x<sub>i</sub> - μ)
    end
    
    subgraph LDA_Calculation["LDA Calculation"]
        D --> E("Within-Class Scatter Matrix<br>(Sw)")
        E --> EA("Compute within-class scatter for each class")
        EA -- "Class c<sub>j</sub>" --> EB("S<sub>j</sub> = (1/N<sub>cj</sub>) * Σ<sub>x ∈ c<sub>j</sub></sub> (x - μ<sub>c<sub>j</sub></sub>)(x - μ<sub>c<sub>j</sub></sub>)<sup>T</sup>")
        E --> EC(Sw = Σ<sub>j=1</sub><sup>C</sup> S<sub>j</sub>)

        D --> F("Between-Class Scatter Matrix (Sb)")
        F --> FA(Compute mean μ<sub>c<sub>j</sub></sub> for each class)
        F --> FB("Sb = Σ<sub>j=1</sub><sup>C</sup> N<sub>c<sub>j</sub></sub>(μ<sub>c<sub>j</sub></sub> - μ)(μ<sub>c<sub>j</sub></sub> - μ)<sup>T</sup>")

        EC --> G(Generalized Eigenvalue Problem)
        G --> GA("Solve SbW = SwWΛ")
        GA -- "W<br>(Projection Matrix)" --> GB("Select eigenvectors corresponding to largest eigenvalues")
        GB -- "W<sub>d</sub> <br>(d dimensions)" --> GC("Dimensionality Reduction")
        GC --> GD(Transform data X = W<sub>d</sub>X)
    end
    
    subgraph Output_and_Further_Steps["Output and Further Steps"]
        GD --> H(Reduced Data)
        H -- d-dimensional data --> HA("Y = [y<sub>1</sub>, y<sub>2</sub>, ..., y<sub>d</sub>]")
        H -- "Projection Matrix W<sub>d</sub>" --> HB(Further Analysis/Classification)
        H --> HC(Kernel LDA)
        HC -- Non-linear Transformation --> HD(Feature Space)
    end

```


----

### Explanation

This Mermaid diagram visualizes the steps involved in computing Linear Discriminant Analysis (LDA).  It's structured to mirror the key components and calculations in a way that's easy to follow.

*   **Input Data (X, y, C):**  The input data `X` is a matrix of features, `y` is a vector of class labels, and `C` is the number of classes.
*   **Data Preprocessing:** The data is centered to remove the effect of the mean.
*   **Scatter Matrices (Sw, Sb):** The within-class scatter matrix (`Sw`) and between-class scatter matrix (`Sb`) are calculated.  These matrices capture the variance within and between the classes.
*   **Generalized Eigenvalue Problem:**  The core of LDA is solving the generalized eigenvalue problem `SbW = SwWΛ`.  This equation finds the projection matrix `W` that maximizes the separation between classes while minimizing the variance within each class.
*   **Eigenvector Selection:** The eigenvectors corresponding to the largest eigenvalues of `Sw<sup>-1</sup>Sb` are selected to form the projection matrix `W<sub>d</sub>`, reducing the dimensionality to `d`.
*   **Dimensionality Reduction:** The input data `X` is projected onto the lower-dimensional space using `W<sub>d</sub>`. This results in a new data set `Y` in `d` dimensions.
*   **Output and Further Steps:** The diagram includes `Kernel LDA` as an extension, indicating the applicability of non-linear transformations.

-----


### Key Improvements

*   **Clearer Structure:**  The diagram is more organized with distinct subgraphs for preprocessing and LDA calculation.
*   **Mathematical Representation:**  Uses mathematical notation (`x<sub>i</sub>`, `μ`, `S<sub>j</sub>`, `W<sub>d</sub>`) to clearly convey the computations.
*   **Focus on Key Concepts:** Highlights the core steps (data centering, scatter matrices, eigenvalue problem) crucial to understanding LDA.
*   **Connections:** Shows clear connections between input data, preprocessing, calculations, and the resulting reduced data.


This diagram is a more robust visual representation of the LDA process compared to a simple flowchart, offering a better understanding of the mathematical steps involved.  It's ready to be adapted further to incorporate more detailed mathematical formulas if needed. Remember to replace the example variables with the actual ones from your original text if you are aiming to use it as a visual representation of a specific problem.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---