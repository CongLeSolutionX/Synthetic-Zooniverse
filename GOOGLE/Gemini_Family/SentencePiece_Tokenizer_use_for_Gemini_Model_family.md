---
created: 2025-03-04 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2312.11805"
---



# SentencePiece Tokenizer used for Gemini Model family
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## SentencePiece Tokenizer used for Gemini Model family - A Diagrammatic Guide 


```mermaid
---
title: "Gemini: A Family of Highly Capable Multimodal Models - Google DeepMind"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
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
graph TD
    A[Gemini Model Family] --> B{Text Processing}
    style A fill:#a3ae,stroke:#333,stroke-width:1px
    B --> C[Tokenizer]
    style C fill:#a2da,stroke:#333,stroke-width:1px
    C --> CA[SentencePiece Tokenizer]:::detail
    class CA fill:#f2bf,stroke:#333,stroke-width:1px
    CA --> CB[Used for tokenizing text data]:::takeaway
    CA --> CC[Trained on a large sample of the entire training corpus]:::detail
    CA --> CD[Improves inferred vocabulary]:::detail
    CA --> CE[Benefits model quality]:::detail
    CA --> CF[Benefits training and inference speed]:::detail
   
   
 classDef takeaway fill:#f2b3,stroke:#333,stroke-width:1px
 classDef detail fill:#f2f3,stroke:#333,stroke-width:1px
 
```

----

### Key elements

*   **Focus:** The diagram focuses specifically on the SentencePiece Tokenizer within the Gemini Model Family.
*   **Concise Structure:** Uses the requested hierarchical structure to present the information.
*   **Highlighting Key Points:** Marks the key takeaway - that the SentencePiece Tokenizer is used for processing text data - for easy understanding.
*   **Additional Details:** Includes nodes for improving inferred vocabulary, model quality, and training/inference speed.







---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---