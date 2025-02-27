---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Trace Operator
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
title: Trace Operator
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
    A[Trace Operator] --> B{Definition}
    B --> C(Definition)
    C --> D["tr(A): A ∈ Rn×n → R"]
    D --> E["tr(A) = ∑<sub>i=1</sub><sup>n</sup> a<sub>ii</sub>"]
    
    subgraph Properties_of_Trace
        E --> F{Properties}
        F --> FA["tr(A + B) = tr(A) + tr(B)"]
        F --> FB["tr(cA) = c * tr(A) for all scalars c ∈ R"]
        F --> FC["tr(A) = tr(A<sup>T</sup>)"]
        F --> FD["tr(AB) = tr(BA)"]
        F --> FE["tr(ABCD) = tr(BCDA) = tr(DABC) = tr(CDAB)"]
        F --> FF["If A is an n × n matrix and λ<sub>1</sub>, ..., λ<sub>n</sub> are its eigenvalues, then ∑<sub>i</sub> λ<sub>i</sub> = tr(A)"]
        F --> FG["||A||<sub>F</sub><sup>2</sup> = tr(A<sup>T</sup>A)" ]
    end
    
    subgraph Examples
        E --> H{Examples}
        H --> HA["Let A = a 2x2 matrix:"]
        HA --> H1["A = [a<sub>11</sub>, a<sub>12</sub>; a<sub>21</sub>, a<sub>22</sub>]"]
        HA --> H2["tr(A) = a<sub>11</sub> + a<sub>22</sub>"]
        H --> HB["Let A be an n×n identity matrix I<sub>n</sub>"]
        HB --> HB1["tr(I<sub>n</sub>) = n"]
        H --> HC["Let A be a diagonal matrix with eigenvalues λ<sub>1</sub>, λ<sub>2</sub>, ..., λ<sub>n</sub>"]
        HC --> HC1["A = diag(λ<sub>1</sub>, λ<sub>2</sub>, ..., λ<sub>n</sub>)"]
        HC --> HC2["tr(A) = λ<sub>1</sub> + λ<sub>2</sub> + ... + λ<sub>n</sub>"]
    end
    
```

----

### Explanation and Considerations

* **Definition:** The Trace Operator is defined as the sum of the elements on the main diagonal of a square matrix.  The notation `∑<sub>i=1</sub><sup>n</sup> a<sub>ii</sub>` clearly shows this summation process.

* **Properties:**  The diagram outlines several important properties of the trace operator, including linearity, symmetry, and its relationship to matrix multiplication and eigenvalues. This is crucial for understanding how the trace operator behaves in various mathematical contexts.

* **Examples:**  The examples illustrate the application of the trace operator to different types of matrices (2x2, identity, diagonal), making the concept more concrete and accessible.


----

### Important Notes

* **Matrix Notation:** The use of subscripts and superscripts (e.g., a<sub>ij</sub>, A<sup>T</sup>) accurately represents matrix elements and transposes, which is essential for clarity.
* **Mathematical Symbols:**  The use of mathematical symbols like summation (∑), and matrix notation (`tr(A)`) is standard and ensures that the diagram conveys the mathematical meaning accurately.
* **Diagram Structure:** The hierarchical structure of the diagram, using subgraphs, clarifies the relationships between the different aspects of the trace operator (definition, properties, examples).


This Mermaid diagram provides a complete visual representation of the trace operator, covering its definition, properties, and illustrative examples, making it easier to understand and remember.  It accurately reflects the mathematical concepts involved.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---