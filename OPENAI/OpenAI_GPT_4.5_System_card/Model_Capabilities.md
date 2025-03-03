---
created: 2025-03-02 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://cdn.openai.com/gpt-4-5-system-card-2272025.pdf"
---



# Model Capabilities
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Model Capabilities - A Diagrammatic Guide 



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
    subgraph Model_Capabilities["Model Capabilities"]
        B{Model Overview}
        B --> L[Model Capabilities]
        L --> L1[Scaling Unsupervised Learning]
        L --> L2["Enhanced Chain-of-Thought Reasoning"]
        L --> L3[Improved Steerability & Understanding of Nuance]
        L --> L4[Enhanced Emotional Intelligence]
        L --> L5[Improved Aesthetic Intuition & Creativity]
        L --> L6[Robust Conversational Capabilities]
        L --> L7[World Knowledge]
        L --> L8[Improved Writing Ability]
        L --> L9[Reduced Hallucinations]
        L --> L10["Multilingual Proficiency<br>(evident from MMLU results)"]

        L1 --> L1a[Increased world model accuracy]
        L1 --> L1b[Decreased hallucination rates]
        L1 --> L1c[Improved associative thinking]

        L2 --> L2a[Ability to tackle complex STEM or logic problems]
        L2 --> L2b[Thinking before responding]

        L3 --> L3a[Improved response to user intent]
        L3 --> L3b[Better handling of nuanced queries]

        L4 --> L4a[Adaptive responses to emotionally charged queries]
        L4 --> L4b["Provides advice, diffuses frustration, or actively listens"]
        L4 --> L4c[Improved understanding of human intent]

        L5 --> L5a[Improved creative writing and design support]
        L5 --> L5b[Stronger aesthetic intuition]
        L5 --> L5c[Increased creative potential]

        L6 --> L6a[Enhanced ability to maintain coherent conversations]
        L6 --> L6b[Handles complex or nuanced dialogues]
        L6 --> L6c[Smooth and natural conversations]
    
        L7 --> L7a[Access to a vast amount of world knowledge through diverse data]

        L8 --> L8a[Better quality and structure in generated text]
        L8 --> L8b[Improved ability to adapt to different writing styles]

        L9 --> L9a[Reduced instances of fabricated information]
        L9 --> L9b[Reduced false or misleading responses]
    
    end

```


---


### Explanation of Changes and Additions

This revised `Model_Capabilities` subgraph directly reflects the capabilities described in the original document, linking each to specific sub-elements where appropriate.

* **More Specific and Detailed Nodes:** The nodes are now more specific, avoiding vague terms like "Improved Capabilities" and instead highlighting *what* aspects of capability were improved. For instance, 'Scaling Unsupervised Learning' is now broken down into more concrete elements like 'Increased world model accuracy', 'Decreased hallucination rates', and 'Improved associative thinking.'
* **Direct Connections to Supporting Information:** Connections are made between the core capabilities and the supporting details in the original document.  For example, 'Multilingual Proficiency' is explicitly linked to the MMLU evaluation results.
* **Clearer Relationship Representation:** The use of arrows makes the connections between the core capabilities and their sub-elements explicit and easy to understand.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---