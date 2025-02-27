---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://www.doc.ic.ac.uk/~dfg/ProbabilisticInference/InferenceAndMachineLearningNotes.pdf"
---



# Feature Engineering
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Feature Engineering Diagram Structure


```mermaid
---
title: Feature Engineering Diagram Structure
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
    A[Feature Engineering] --> B{Types of Feature Engineering}
    B --> C(Extraction)
    B --> D(Transformation)
    B --> E(Combination)
    
    subgraph Feature_Extraction["Feature Extraction"]
    style Feature_Extraction fill:#cf22,stroke:#333,stroke-width:2px
        C --> CA(Creating new features from existing ones)
        CA -- Example:<br>Calculating ratios or differences --> CB
        CA -- Example:<br>Binning numerical data --> CC
        CA -- Example:<br>Extracting text features<br>(e.g., TF-IDF, word counts) --> CD
        CA -- Example:<br>Using domain expertise --> CE
    end

    subgraph Feature_Transformation["Feature Transformation"]
    style Feature_Transformation fill:#cc22,stroke:#333,stroke-width:2px
        D --> DA(Modifying existing features)
        DA -- Example:<br>Scaling numerical features<br>(e.g., Min-Max, Z-score) --> DB
        DA -- Example:<br>Log transformation --> DC
        DA -- Example:<br>One-hot encoding categorical features --> DD
        DA -- Example:<br>Normalization --> DE
        DA -- Example:<br>Feature selection<br>(e.g., using filter methods or wrapper methods) --> DF
    end

    subgraph Feature_Combination["Feature Combination"]
    style Feature_Combination fill:#cdd2,stroke:#333,stroke-width:2px
        E --> EA(Combining extracted and transformed features)
        EA -- Example:<br>Concatenating different features --> EB
        EA -- Example:<br>Creating interaction terms<br>(e.g., x1 * x2) --> EC
        EA -- Example:<br>Combining categorical and numerical features --> ED
    end
    
    subgraph Summary["Summary"]
    style Summary fill:#cddf9,stroke:#333,stroke-width:2px
        C --> CC1[Reducing dimensionality]
        C --> CC2[Improving model performance]
        C --> CC3[Handling non-linear relationships]
        D --> DD1[Improving model performance]
        D --> DD2[Addressing data distributions]
        E --> EE1[Creating more comprehensive features]
        E --> EE2[Capturing complex interactions]
    end
    
```

---


### Explanation

* **Feature Engineering:** This is the overarching concept.
* **Types of Feature Engineering:** The core strategies are broken down into three main categories: Extraction, Transformation, and Combination.
* **Feature Extraction:** This focuses on creating new features from existing ones.  Examples include calculating ratios, differences, binning numerical data, or extracting text features like TF-IDF.  The examples are meant to be illustrative, and you can add more as needed, relevant to the specific context of your application.
* **Feature Transformation:** This involves modifying existing features.  Examples include scaling (Min-Max, Z-score), log transformations, one-hot encoding, normalization, and feature selection.  Feature selection is important to reduce irrelevant or redundant features, improving model performance.
* **Feature Combination:** This focuses on combining extracted and transformed features to create more comprehensive and expressive features. Examples include concatenating features, creating interaction terms, and combining categorical and numerical features.  This is vital for capturing complex relationships between variables that might be missed using only individual features.
* **Summary:** The bottom subgraph highlights the overarching benefits of feature engineering in machine learning tasks. It emphasizes that feature engineering can reduce dimensionality, enhance model performance, and effectively handle complex relationships in data.


### How to use this diagram in different contexts

* **Specific Data:**  For a specific dataset, you can add more detailed examples within each category that are relevant to the data's characteristics (e.g., if you are dealing with images, feature engineering might involve creating edge or corner detectors).
* **Algorithms:** Include specific algorithms that benefit from specific feature engineering techniques. For example, you could note that one-hot encoding is frequently used with decision trees.
* **Applications:** Connect the diagram to specific applications (e.g., image recognition, natural language processing, etc.) to illustrate how feature engineering is used in different domains.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---