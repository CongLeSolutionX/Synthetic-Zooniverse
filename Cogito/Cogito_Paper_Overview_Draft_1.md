---
created: 2025-03-04 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2501.18653"
---



# Cogito, ergo sum: A Neurobiologically-Inspired Cognition-Memory-Growth
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Cogito - A Diagrammatic Guide 


### I. Overall System Architecture

This section will describe the core architecture with primary components like:

*   Planner
*   Coder
*   Debugger
*   Super-Role
*   Hippocampus-like Memory

```mermaid
---
title: "Cogito, ergo sum: A Neurobiologically-Inspired Cognition-Memory-Growth"
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
    "graph": { "htmlLabels": false, 'curve': 'natural' },
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
    A[Cogito System] --> B{Agent Roles}
    B --> C[Planner]
    B --> D[Coder]
    B --> E[Debugger]
    A --> F[Super-Role]
    A --> G[Hippocampus-like Memory Module]

    subgraph Agent_Roles["Agent Roles"]
        C --> C1(Outlines step-by-step strategy)
        C1 --> C2(Considers edge cases and performance)
        D --> D1(Translates plan into functional code)
        E --> E1(Analyzes traceback feedback)
        E1 --> E2(Identifies and corrects errors)
    end

    subgraph Super_Role_Functionality["Super Role Functionality"]
        F --> F1(Evolves from Debugger to Coder to Planner)
        F1 --> F2(Accumulates knowledge and cognitive skills)
        F2 --> F3(Solves problems independently)
        F3 --> F4(Iteratively refines solutions)
    end

    subgraph Memory_Module["Memory Module"]
        G --> G1["Dentate Gyrus<br>(DG)"]
        G --> G2["Cornu Ammonis<br>(CA)"]
        G1 --> G1a(Formation of new memories)
        G1 --> G1b(Processes large volume of information)
        G2 --> G2a[CA1]
        G2 --> G2b[CA2]
        G2 --> G2c[CA3]
        G2 --> G2d[CA4]
        G2a --> G2aa(Storage and retrieval of initial responses)
        G2b --> G2bb(Personalization module)
        G2c --> G2cc(Stores code versions and error tracebacks)
        G2d --> G2dd(Stores final correct result)
    end

    style A fill:#f9f3,stroke:#333,stroke-width:2px
    style F fill:#a2f3,stroke:#333,stroke-width:1px
    
```

---


### II. Workflow

This section describes the sequence of actions of the Cogito System.

```mermaid
---
title: "Cogito, ergo sum: A Neurobiologically-Inspired Cognition-Memory-Growth"
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
    "graph": { "htmlLabels": false, 'curve': 'natural' },
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
    A[Cogito Workflow] --> B{Reverse Sequence}
    B --> C[Debugging]
    B --> D[Coding]
    B --> E[Planning]

    subgraph Iterative_Process["Iterative Process"]
        C --> F(Code Analysis and Correction)
        D --> G(Providing Initial Solutions)
        E --> H(Optimizing Strategies)
        H --> I(Super-Role Provides Final Answer)
        I --> C
    
    style F fill:#ccf3,stroke:#333,stroke-width:1px
    style G fill:#ccf3,stroke:#333,stroke-width:1px
    style H fill:#ccf3,stroke:#333,stroke-width:1px
    end
    
```


---


### III. Hippocampus-Inspired Memory

Detailing the different regions of the memory module.

```mermaid
---
title: "Cogito, ergo sum: A Neurobiologically-Inspired Cognition-Memory-Growth"
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
    "graph": { "htmlLabels": false, 'curve': 'natural' },
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
    A["Hippocampus-like Memory"] --> B{"Regions"}
    B --> C["Dentate Gyrus<br>(DG)"]
    B --> D["Cornu Ammonis<br>(CA)"]

    subgraph DG_Functionality["DG Functionality"]
        C --> C1(Formation of new memories)
        C --> C2(Processes large volume of information)
    end

    subgraph CA_Regions["CA Regions"]
        D --> D1[CA1]
        D --> D2[CA2]
        D --> D3[CA3]
        D --> D4[CA4]
    end

    subgraph CA1_Functionality["CA1 Functionality"]
        D1 --> D1a(Storage and retrieval of initial responses)
        D1 --> D1b(Long-term memory access)
    end

    subgraph CA2_Functionality["CA2 Functionality"]
        D2 --> D2a(Personalization module)
        D2 --> D2b(Understands user's coding style)
    end

    subgraph CA3_Functionality["CA3 Functionality"]
        D3 --> D3a(Stores code versions)
        D3 --> D3b(Stores error tracebacks)
        D3 --> D3c(Facilitates quick recall)
    end

    subgraph CA4_Functionality["CA4 Functionality"]
        D4 --> D4a(Stores final correct result)
        D4 --> D4b(Accessible for similar tasks)
    end
    
    style A fill:#a2f3,stroke:#333,stroke-width:1px
    
```


---


### IV. Agent Collaboration Settings

Illustrating agent weights and how the best answers are selected.

```mermaid
---
title: "Cogito, ergo sum: A Neurobiologically-Inspired Cognition-Memory-Growth"
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
    "graph": { "htmlLabels": false, 'curve': 'natural' },
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
    A[Agent Collaboration] --> B{Initial Weights}
    B --> C[Planner: 0.4]
    B --> D[Coder: 0.4]
    B --> E[Debugger: 0.3]

    A --> F{Importance Score}
    F --> G(Evaluate answers)
    G --> H(Assign importance score)
    H --> I(Multiply by initial weight)

    A --> J{Dynamic Selection}
    J --> K(Reintroduce two random roles in each group)
    K --> L(Prevents over-committing to incorrect answers)
    
    style A fill:#af23,stroke:#333,stroke-width:1px
    
```

----


### V. Results and Performance

Summarizing the quantitative results and comparisons to baselines. (This might be better presented as a table, but a graph could highlight key trends).

```mermaid
---
title: "Cogito, ergo sum: A Neurobiologically-Inspired Cognition-Memory-Growth"
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
    "graph": { "htmlLabels": false, 'curve': 'natural' },
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
    A["Experimental Results"] --> B{"Performance Metrics"}
    B --> C["Pass@k"]
    B --> D["Token Consumption"]
    B --> E["API Calls"]

    A --> F{Datasets}
    F --> G[HumanEval]
    F --> H[MBPP]
    F --> I[APPS]
    F --> J[xCodeEval]
    F --> K[CodeContest]
    F --> L[EvalPlus]
    
```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---