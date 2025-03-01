---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2501.09223"
---



# Tool Use in LLMs
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
title: Tool Use in LLMs
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
    subgraph Tool_Use_in_LLMs["Tool Use in LLMs"]
        A[Tool Use] --> B(Concept)
        B --> C(Problem)
        C --> C1(LLMs Lack Direct Knowledge Access)
        C --> C2(Need for External Data/Tools)
        C --> C3(Integrating External Tools)
        
        B --> D(Methods)
        D --> D1(Calling External APIs)
        D --> D2("Retrieval-Augmented Generation (RAG)")
        D --> D3(Tool Use as Problem Decomposition)
        
        subgraph API_Calling_Details["API Calling Details"]
            D1 --> D11(LLMs generating calls)
            D1 --> D12("Format for calls e.g., {tool: web-search, query: '...'}")
            D1 --> D13(Execution and incorporation of results)
            D1 --> D14(Handling potential errors in calls)
        end
        
        subgraph RAG_Details["RAG Details"]
            D2 --> D21(Retrieval Systems)
            D2 --> D22(Retrieval Strategies e.g., vector databases, search engines)
            D2 --> D23(Combining retrieved information with LLM input)
            D2 --> D24(Handling unreliable or irrelevant retrieved data)
            D2 --> D25(Control over use of external data)
        end
        
        subgraph Problem_Decomposition["Problem Decomposition"]
            D3 --> D31(LLM handles parts of the problem)
            D3 --> D32(External systems handle other parts)
            D3 --> D33(Example: math problems, API calls)
        end
        
        B --> E(Fine-tuning)
        E --> E1(Annotating data with tool use commands)
        E --> E2(Adapting models for tool use)
        E --> E3(Managing potential issues like over-reliance on tools)
        
        subgraph FineTuning_Details["Fine-Tuning Details"]
            E1 --> E11(Defining markers or commands)
            E1 --> E12(Using labeled data for training)
            E1 --> E13(Handling diverse types of external tool usage)
        end
    end
    style A fill:#ccf5,stroke:#333,stroke-width:1px;
    style B fill:#ccf5,stroke:#333,stroke-width:1px;
    style C fill:#ccf5,stroke:#333,stroke-width:1px;
    style D fill:#ccf5,stroke:#333,stroke-width:1px;
    style E fill:#ccf5,stroke:#333,stroke-width:1px;
    
```


----

### Explanation


This Mermaid graph visually represents the key concepts of "Tool Use" in large language models (LLMs). It's a more detailed breakdown of the "Tool Use" aspect from the previous response, showing the underlying problem, methods for tool integration, and the fine-tuning considerations involved.

*   **Subgraphs:**  Each subgraph (e.g., API Calling Details, RAG Details) helps organize related aspects of tool use.
*   **Nodes:**  Nodes (e.g., Problem, Methods, Fine-tuning) represent different categories within the topic.  The nodes under each category provide further granularity.
*   **Arrows:**  Arrows connect the concepts and ideas, showing relationships between different parts of tool use.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---