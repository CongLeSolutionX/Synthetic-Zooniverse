---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2501.09223"
---



# Problem Decomposition
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
title: Problem Decomposition
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
    subgraph Problem_Decomposition["Problem Decomposition"]
        A[Problem Decomposition] --> B(Sub-problem Generation)
        B --> C(Decomposition Strategies)
        
        subgraph Decomposition_Strategies["Decomposition Strategies"]
            C --> C1(Manual Outline)
            C --> C2(LLM-Generated Outline)
            C --> C3(Iterative Subproblem Generation)
            C --> C4(Divide-and-Conquer Algorithms)
            C --> C5(Dynamic Sub-problem Generation)
        end
        
        B --> D(Sub-problem Solving)
        D --> E(Sequential Solving)
        D --> F(Parallel Solving)
        D --> G(Sub-problem Decomposition)
        
        subgraph Subproblem_Solving_Details["Subproblem Solving Details"]
            E --> E1(LLM as Solver)
            E --> E2(External Tools as Solvers)
            E --> E3(Recursive Solving)
            E --> E4(Integrating Retrieval Systems)
            F --> F1(Parallel LLM Runs)
            F --> F2(Parallel External Tool Calls)
            G --> G1(Further Decomposing Sub-problems)
            
        end
        
        %% subgraph Problem_Decomposition_Relationship
        %% B -- Methods for Generation of subproblems. --> D -- Methods for solving subproblems.
    
        %%     B -- LLM-based approach --> D -- LLMs solve sub-problems
        
        
        %%     C5 --Dynamically generating sub-problems --> D -- Solving subproblems based on the results of the previous steps
        %% end
    end

```


----

### Explanation of the Diagram

* **Problem Decomposition:**  The top-level node represents the overarching concept of decomposing a complex problem into smaller, more manageable sub-problems.
* **Sub-problem Generation (B):** This node focuses on the methods used to identify and create these smaller sub-problems.  It branches out into various strategies like manual outlining, using LLMs to generate outlines, iterative generation, divide-and-conquer approaches, and dynamically generating sub-problems based on prior results.
* **Sub-problem Solving (D):** This node focuses on the methods used to tackle the generated sub-problems. It branches into different types of solving approaches like sequential (one at a time), parallel (multiple sub-problems concurrently), recursive decomposition, and incorporating external resources like information retrieval systems (e.g., RAG).
* **Relationship (within the subgraph) and Connections (between subgraphs):**  The diagram explicitly shows the links and flow of information. For example, you can visually see that LLM-based approaches to sub-problem generation (e.g., asking an LLM to generate an outline) often lead directly to LLMs solving these sub-problems (e.g., using the generated outline to produce content for each section).  The connection between dynamic sub-problem generation and solving highlights that the solution to a sub-problem informs the next sub-problem to be tackled.  This crucial relationship is central to the concept of problem decomposition, where solutions are not predetermined in advance.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---