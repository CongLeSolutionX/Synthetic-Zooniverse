---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2501.09223"
---


# Zero-shot In-context Learning
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


```mermaid
---
title: Zero-Shot In-context Learning
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
    subgraph ZeroShot_InContext_Learning["Zero-Shot In-context Learning"]
        A[Zero-Shot In-Context Learning] --> B{Core Idea}
        B -- Directly applying pre-trained LLMs to new, unseen tasks --> C(No training or tuning on task-specific data)
        B -- LLMs have learned general language knowledge during pre-training --> D(Activating this knowledge for new tasks)
        B -- Effective for quick adaptation to new problems --> E(Without task-specific adjustments)

        subgraph ZeroShot_Example["ZeroShot Example"]
            C --> C1{No explicit task-specific demonstrations}
            C --> C2{LLMs rely on pre-trained knowledge}
            
            D --> D1{Prompt Engineering is key to activating this knowledge}
            D --> D2{Properly-crafted prompts guide LLMs towards solving the task}
        end
        
        subgraph Practical_ZeroShot_Example["Practical ZeroShot Example"]
            A --> A1['Task': 'Translation']
            A1 --> A2['Source language': 'English']
            A2 --> A3['Target language': 'Chinese']
            A3 --> A4['Style': 'Formal text']
            A4 --> A5["'Template': 'Translate the following sentence: {*sentence*}'"]
            A5 --> A6["'Input': 'She don't like going to the park.'"]
            A6 --> A7["'Output': '*Correct Translation*'"]

            A --> A8['Task': 'Grammar Correction']
            A8 --> A9["'Input': 'She don't like going to the park.'"]
            A9 --> A10["'Output': '*Corrected Sentence*'"]
        end
    end
    
```

----

### Explanation

* **Zero-Shot In-Context Learning (A):** This subgraph encapsulates the overall concept.
* **Core Idea (B):**  This node highlights the fundamental idea: directly applying a pre-trained LLM to a new task without any further training or tuning on that specific task.  It leverages the general knowledge learned during pre-training.
* **No training or tuning on task-specific data (C):**  Zero-shot learning avoids any need for task-specific data.
* **Activating this knowledge for new tasks (D):** This is crucial; the general knowledge must be "activated" by the right prompt.  Proper prompt engineering is essential.
* **Effective for quick adaptation to new problems (E):**  This summarizes the practical benefit.
* **Zero-Shot Example (subgraph ZeroShot_Example):**  This subgraph further illustrates the concept.
* **Practical Zero-Shot Example (subgraph Practical_ZeroShot_Example):** This subgraph demonstrates the core steps involved in a zero-shot learning use case, including a translation task and grammar correction, and how a suitable prompt guides the LLM to produce the expected output.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---