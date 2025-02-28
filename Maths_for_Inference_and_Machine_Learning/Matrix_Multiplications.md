---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Matrix Multiplications
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Matrix Multiplications - A Diagram Structure

```mermaid
---
title: Matrix Multiplication
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
    A[Matrix Multiplication] --> B{Types}
    B --> C(Matrix-Vector Multiplication)
    B --> D(Matrix-Matrix Multiplication)

    subgraph Matrix_Vector_Multiplication["Matrix-Vector Multiplication"]
        C --> CA(Input Matrix)
        C --> CB(Input Vector)
        C --> CC(Output Vector)
        CA --> CC1["A = [a<sub>1</sub>, a<sub>2</sub>, ..., a<sub>n</sub>]"]
        CB --> CC2["x = [x<sub>1</sub>, x<sub>2</sub>, ..., x<sub>m</sub>]<sup>T</sup>"]
        CC --> CC3["Ax = [a<sub>1</sub><sup>T</sup>x, a<sub>2</sub><sup>T</sup>x, ..., a<sub>n</sub><sup>T</sup>x]<sup>T</sup>"]
    
    
        
    end

    subgraph Matrix_Matrix_Multiplication["Matrix-Matrix Multiplication"]
        D --> DA(Input Matrix A);
        D --> DB(Input Matrix B);
        D --> DC(Output Matrix C);
        DA --> DC1["A = [a<sub>1</sub>, a<sub>2</sub>, ..., a<sub>n</sub>]"]
        DB --> DC2["B = [b<sub>1</sub>, b<sub>2</sub>, ..., b<sub>m</sub>]"]
        DC --> DC3["C = [A b<sub>1</sub>, A b<sub>2</sub>, ..., A b<sub>m</sub>]"]
        
    end

    subgraph Summary
        C --> C1[Ax = b]
        D --> D1[A * B = C]
        
        %% C1 -- Computes the linear combination of columns of A using components of x;
        %% D1 -- Computes the linear combination of columns of B using rows of A;
        
    end
    
    style A fill:#a2c5,stroke:#333,stroke-width:2px
    style C fill:#e5d9,stroke:#333,stroke-width:1px
    style D fill:#e5d9,stroke:#333,stroke-width:1px
    
```

----


### Explanation

The Mermaid diagram illustrates two key types of matrix multiplications: matrix-vector and matrix-matrix.

* **Matrix-Vector Multiplication (Ax = b):**
    * **Input Matrix (A):**  Represented as a collection of column vectors (a<sub>1</sub>, a<sub>2</sub>, ..., a<sub>n</sub>).
    * **Input Vector (x):** A column vector of appropriate dimensions ([x<sub>1</sub>, x<sub>2</sub>, ..., x<sub>m</sub>]<sup>T</sup>) for the multiplication to be valid.
    * **Output Vector (b):**  The result of the multiplication, a column vector where each element is a dot product of a row of A with x ([a<sub>1</sub><sup>T</sup>x, a<sub>2</sub><sup>T</sup>x, ..., a<sub>n</sub><sup>T</sup>x]<sup>T</sup>).  This illustrates the core operation: computing the linear combination of columns of A using components of x.

* **Matrix-Matrix Multiplication (A * B = C):**
    * **Input Matrix A:**  Again, represented as a collection of column vectors ([a<sub>1</sub>, a<sub>2</sub>, ..., a<sub>n</sub>]).
    * **Input Matrix B:**  A matrix of appropriate dimensions for multiplication ([b<sub>1</sub>, b<sub>2</sub>, ..., b<sub>m</sub>])
    * **Output Matrix C:** The result of the multiplication, a matrix where each column is a matrix-vector multiplication of A with a column vector of B ([A b<sub>1</sub>, A b<sub>2</sub>, ..., A b<sub>m</sub>]). This depicts the key concept of computing a linear combination of columns of B using rows of A to produce each column of C.

* **Summary subgraph:**  The summary subgraph visually connects the two types of multiplications to the equations that represent them (`Ax = b` for matrix-vector and `A * B = C` for matrix-matrix).  It further describes the fundamental operations involved in each type, highlighting the computation as a linear combination of column vectors for matrix-vector multiplication and of column vectors of B using rows of A for matrix-matrix multiplication.

This structured diagram effectively captures the core concepts of matrix multiplication, their types, and the underlying calculations.  It's ready to be adapted to more specific use cases if required. Remember to replace the example vector and matrix values with the actual values you want to visualize.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---