---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Triangular Matrices
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
title: Triangular Matrices
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
    A[Triangular Matrices] --> B{Types}
    B --> C(Lower Triangular)
    B --> D(Upper Triangular)
    B --> E(Diagonal Matrix)

    C --> CA{Entries Above Main Diagonal = 0}
    D --> DA{Entries Below Main Diagonal = 0}
    E --> EA{Entries Above and Below Main Diagonal = 0}
    
    subgraph Example_Lower_Triangular
    C -- Example: --> CF[
        1  0  0
        2  3  0
        4  5  6
    ]
    end
    
    subgraph Example_Upper_Triangular
    D -- Example: --> DF[
        1  2  4
        0  3  5
        0  0  6
    ]
    end
    
    subgraph Example_Diagonal_Matrix
    E -- Example: --> EF[
        1  0  0
        0  3  0
        0  0  6
    ]
    end


    subgraph Properties
    C --> CP[Properties]
    CP --> CPA[Sum/Product of Lower Triangular Matrices = Lower Triangular]
    CP --> CPB[Sum/Product of Upper Triangular Matrices = Upper Triangular]
    CP --> CPC[Inverse of Invertible Upper/Lower Triangular Matrices = Upper/Lower Triangular]
    CP --> CPD[Product of a Triangular Matrix by a Constant = Triangular]
    CP --> CPE[Transpose of Upper Triangular = Lower Triangular, Vice Versa]
    CP --> CPF[Determinant = Product of Diagonal Entries]
    CP --> CPG[Diagonal Entries = Eigenvalues]
    
    D --> DP[Properties]
    DP --> DPA[Sum/Product of Upper Triangular Matrices = Upper Triangular]
    DP --> DPB[Sum/Product of Lower Triangular Matrices = Lower Triangular]
    DP --> DPC[Inverse of Invertible Upper/Lower Triangular Matrices = Upper/Lower Triangular]
    DP --> DPD[Product of a Triangular Matrix by a Constant = Triangular]
    DP --> DPE[Transpose of Upper Triangular = Lower Triangular, Vice Versa]
    DP --> DPF[Determinant = Product of Diagonal Entries]
    DP --> DPG[Diagonal Entries = Eigenvalues]

    E --> EP[Properties]
    EP --> EPA[Sum/Product of Diagonal Matrices = Diagonal]
    EP --> EPB[Inverse of Invertible Diagonal Matrices = Diagonal]
    EP --> EPC[Product of a Diagonal Matrix by a Constant = Diagonal]
    EP --> EPD[Determinant = Product of Diagonal Entries]
    EP --> EPG[Diagonal Entries = Eigenvalues]

    
    subgraph Applications
        C --> AP[Applications]
        AP --> APA[Efficient Computations]
        AP --> APB[Solving Linear Systems]
        AP --> APC[Eigenvalue Computations]
    end
    
    subgraph TriangularMatrix_vs_GeneralMatrices
        C --> TMG[Difference]
        TMG --> TMGA["Triangular matrices have specific properties for matrix operations that make computations more efficient than general matrices"]
    end
end

```

----

### Explanation

This Mermaid diagram visually represents triangular matrices (lower, upper, and diagonal) with their defining characteristics, key properties, and some illustrative applications.  It's structured to clearly show how these matrices differ from general matrices and why they are important in computational contexts.  It emphasizes the specific computational advantages offered by triangular matrices, such as efficient matrix multiplication and inversion, and ties this to their applications in solving linear systems and eigenvalue computations. The diagram includes example matrices to clarify the concept of the entries being zero above or below the main diagonal. It also includes a summary subgraph of the properties of each triangular matrix type.  Finally, it includes a subgraph comparing triangular matrices against general matrices, highlighting the specific benefits that triangular matrices offer. This structure provides a more comprehensive understanding of the concept. Remember that "properties" and "applications" in the diagram are just starting points, and specific examples from your original material should be integrated for greater detail.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---