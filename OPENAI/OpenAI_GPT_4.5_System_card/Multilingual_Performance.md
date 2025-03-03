---
created: 2025-03-02 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://cdn.openai.com/gpt-4-5-system-card-2272025.pdf"
---



# Multilingual Performance
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Multilingual Performance - A Diagrammatic Guide 



```mermaid
---
title: "OpenAI GPT-4.5 System Card"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "graph": { "htmlLabels": false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
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
    subgraph Multilingual_Performance["Multilingual Performance"]
        A[Multilingual Performance Evaluation] --> B{"GPT-4.5 Evaluation"}
        B --> C[MMLU Dataset]
        C --> D[Translated Test Set]
        D --> E[14 Languages]

        E -- Arabic --> F(0.8598)
        E -- Bengali --> G(0.8477)
        E -- Chinese (Simplified) --> H(0.8695)
        E -- English (not translated) --> I(0.896)
        E -- French --> J(0.8782)
        E -- German --> K(0.8532)
        E -- Hindi --> L(0.8777)
        E -- Indonesian --> M(0.8603)
        E -- Italian --> N(0.8722)
        E -- Japanese --> O(0.8693)
        E -- Korean --> P(0.8693)
        E -- Portuguese (Brazil) --> Q(0.8789)
        E -- Spanish --> R(0.8840)
        E -- Swahili --> S(0.8199)
        E -- Yoruba --> T(0.6818)

    end
    
```

---


### Explanation

This Mermaid diagram specifically visualizes the multilingual performance evaluation of GPT-4.5.

* **Multilingual Performance Evaluation (A):**  The top-level node representing the overall evaluation.
* **MMLU Dataset (C):** The dataset used for the multilingual evaluation.
* **Translated Test Set (D):** The test set within the MMLU dataset, specifically translated for this evaluation.
* **14 Languages (E):** The languages included in the translated test set, each represented by a node.
* **Scores (F-T):**  The performance score (accuracy) of GPT-4.5 on the translated test set for each of the 14 languages.  These scores are directly taken from Table 16 in the original document.

---


### Important Considerations

* **Clarity and Focus:** The diagram is focused solely on the multilingual performance evaluation results.
* **Data Representation:** The numerical scores are explicitly displayed for each language. This directly reflects the information provided in the original data.
* **Conciseness:** The diagram avoids unnecessary complexity while retaining the core information.


This diagram effectively visualizes the multilingual performance of GPT-4.5, highlighting the scores achieved for each language in the MMLU evaluation.  Remember, this diagram relies on the accuracy of the scores from the original source document.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---