---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Data Preprocessing Techniques
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
title: Data Preprocessing Diagram Structure
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
    A[Data Preprocessing] --> B{Types of Preprocessing}
    
    subgraph Centering["Centering"]
    style Centering fill:#cf555,stroke:#333,stroke-width:1px
        B -- Centering --> C[Data Centering]
        C --> CA(Subtract Mean)
        CA --> CB[Compute Mean]
        CB --> CC[Original Data]
        CB --> CD[Mean Value]
        C --> CE[Centered Data]
        style C fill:#ccf2,stroke:#333,stroke-width:1px
    end

    subgraph Scaling["Scaling"]
    style Scaling fill:#2219,stroke:#333,stroke-width:1px
        B -- Scaling --> D[Data Scaling]
        D --> DA(Min-Max Scaling)
        DA --> DB[Find Min, Max Values]
        DA --> DC[Scaled Data]
        style D fill:#ccf2,stroke:#333,stroke-width:1px
    end
    
    subgraph Normalization["Normalization"]
    style Normalization fill:#2219,stroke:#333,stroke-width:1px
        B -- Normalization --> E[Data Normalization]
        E --> EA(Z-Score Normalization)
        EA --> EB[Compute Mean and Standard Deviation]
        EA --> EC[Normalized Data]
        style E fill:#ccf5,stroke:#333,stroke-width:1px
    end
        
    subgraph Handling_Missing_Values["Handling Missing Values"]
    style Handling_Missing_Values fill:#2219,stroke:#333,stroke-width:1px
        B -- Handling Missing Values --> F[Missing Value Imputation]
        F --> FA(Mean/Median/Mode Imputation)
        FA --> FB[Replace Missing Values]
        style F fill:#ccf2,stroke:#333,stroke-width:1px
    end

    subgraph Feature_Selection["Feature Selection"]
    style Feature_Selection fill:#2219,stroke:#333,stroke-width:1px
        B -- Feature Selection --> G[Feature Selection]
        G --> GA(Filter Methods)
        GA --> GB[Select Relevant Features]
        style G fill:#ccf2,stroke:#333,stroke-width:1px
    end
    
    subgraph Feature_Transformation["Feature Transformation"]
    style Feature_Transformation fill:#2219,stroke:#333,stroke-width:1px
        B -- Feature Transformation --> H[Feature Transformation]
        H --> HA(Polynomial Transformation)
        HA --> HB[Transform Data]
        style H fill:#ccf2,stroke:#333,stroke-width:1px
    end

    subgraph Outlier_Removal["Outlier Removal"]
    style Outlier_Removal fill:#2219,stroke:#333,stroke-width:1px
        B -- Outlier Removal --> I[Outlier Removal]
        I --> IA(Z-Score Method)
        IA --> IB[Identify and remove outliers]
        style I fill:#ccf2,stroke:#333,stroke-width:1px
    end
    

    subgraph Summary["Summary"]
    style Summary fill:#f555,stroke:#333,stroke-width:1px
        B -- Summary --> J[Preprocessed Data]
        J --> JA[Improved Data Quality]
        J --> JB[Enhanced Model Performance]
    end

```

----


### Explanation of Diagram

*   **Nodes:** The diagram uses nodes to represent different types of preprocessing steps (centering, scaling, normalization, missing value imputation, feature selection, feature transformation, and outlier removal).
*   **Subgraphs:** Each preprocessing type is enclosed in a subgraph for better organization.
*   **Edges:** Directed edges connect the steps of preprocessing, showing the flow from raw data to preprocessed data.  For example, 'Data Centering' connects to 'Compute Mean' and then to 'Centered Data'.
*   **Detailing:** The subgraph detail shows more about the steps involved in each technique. For example, 'Data Centering' details steps like computing the mean and subtracting it from each data point.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---