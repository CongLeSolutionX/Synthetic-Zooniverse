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


The diagrams below provide a detailed overview of the Cogito system, its workflow, memory module, agent collaboration, and experimental results. They are structured to align with the main concepts presented in the document.


----


### I. Overall System Architecture

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
    A["Cogito System"] --> B{"Agent Roles"}
    A --> F["Super-Role"]:::superrole
    A --> G["Hippocampus-like Memory Module"]:::memory

    subgraph Agent_Roles["Agent Roles"]
    style Agent_Roles fill:#f9f2,stroke:#333,stroke-width:1px
        B --> C[Planner]:::planner
        B --> D[Coder]:::coder
        B --> E[Debugger]:::debugger
    end

    subgraph Super_Role_Functionality["Super-Role Functionality"]
    style Super_Role_Functionality fill:#f2f2,stroke:#333,stroke-width:1px
        F --> F1(Evolves through Roles)
        F1 --> F2(Accumulates Knowledge)
        F2 --> F3(Solves Problems)
        F3 --> F4(Refines Solutions)
    end

    subgraph Memory_Module["Memory Module"]
    style Memory_Module fill:#a2a2,stroke:#333,stroke-width:1px
        G --> G1["Dentate Gyrus<br>(DG)"]:::dg
        G --> G2["Cornu Ammonis<br>(CA)"]:::ca
    end

    subgraph DG_Functionality["DG Functionality"]
    style DG_Functionality fill:#ffc2,stroke:#333,stroke-width:1px
        G1 --> G1a(New Memories)
        G1 --> G1b(Processes Information)
    end

    subgraph CA_Regions["CA Regions"]
     style CA_Regions fill:#ff21,stroke:#333,stroke-width:1px
        G2 --> G2a[CA1]:::ca1
        G2 --> G2b[CA2]:::ca2
        G2 --> G2c[CA3]:::ca3
        G2 --> G2d[CA4]:::ca4
    end

    C --> C1(Step-by-Step Strategy)
    C1 --> C2(Edge Cases & Performance)
    D --> D1(Translates Plan to Code)
    E --> E1(Analyzes Traceback)
    E1 --> E2(Corrects Errors)
    G2a --> G2aa(Initial Responses)
    G2b --> G2bb(Personalization)
    G2c --> G2cc(Code & Tracebacks)
    G2d --> G2dd(Final Results)

    classDef superrole fill:#f2aa,stroke:#333,stroke-width:1px
    classDef memory fill:#aaf2,stroke:#333,stroke-width:1px
    classDef planner fill:#aaf2,stroke:#333,stroke-width:1px
    classDef coder fill:#afa2,stroke:#333,stroke-width:1px
    classDef debugger fill:#faa2,stroke:#333,stroke-width:1px
    classDef dg fill:#eee2,stroke:#333,stroke-width:1px
    classDef ca fill:#eee2,stroke:#333,stroke-width:1px
    classDef ca1 fill:#eee2,stroke:#333,stroke-width:1px
    classDef ca2 fill:#eee2,stroke:#333,stroke-width:1px
    classDef ca3 fill:#eee2,stroke:#333,stroke-width:1px
    classDef ca4 fill:#eee2,stroke:#333,stroke-width:1px

    style A fill:#a2da,stroke:#333,stroke-width:2px
    
```

----

### II. Workflow

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
    A["Cogito Workflow"] --> B{Reverse Sequence}:::reverse
    B --> C[Debugging]:::phase
    B --> D[Coding]:::phase
    B --> E[Planning]:::phase

    subgraph Iterative_Process["Iterative Process"]
        style Iterative_Process fill:#eff3,stroke:#333,stroke-width:1px
        C --> F("Code Analysis & Correction")
        D --> G(Providing Solutions)
        E --> H(Optimizing Strategies)
        H --> I(Super-Role Provides Answer)
        I -- Iterates --> C
    end

    classDef reverse fill:#f2aa,stroke:#333,stroke-width:1px
    classDef phase fill:#f2f3,stroke:#333,stroke-width:1px
    
```

---


### III. Hippocampus-Inspired Memory

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
    A["Hippocampus-like Memory"] --> B{"Regions"}:::regions
    B --> C["Dentate Gyrus<br>(DG)"]:::dg
    B --> D["Cornu Ammonis<br>(CA)"]:::ca

    subgraph DG_Functionality["DG Functionality"]
        style DG_Functionality fill:#f2c2,stroke:#333,stroke-width:1px;
        C --> C1(New Memories)
        C --> C2(Information Processing)
    end

    subgraph CA_Regions["CA Regions"]
        style CA_Regions fill:#ff22,stroke:#333,stroke-width:1px
        D --> D1[CA1]:::ca1
        D --> D2[CA2]:::ca2
        D --> D3[CA3]:::ca3
        D --> D4[CA4]:::ca4
    end

    D1 --> D1a(Initial Responses)
    D1 --> D1b(Long-term Access)
    D2 --> D2a(Personalization)
    D2 --> D2b(Coding Style)
    D3 --> D3a(Code Versions)
    D3 --> D3b(Error Tracebacks)
    D3 --> D3c(Quick Recall)
    D4 --> D4a(Final Results)
    D4 --> D4b(Similar Tasks)

    classDef regions fill:#aaf3,stroke:#333,stroke-width:1px
    classDef dg fill:#afa3,stroke:#333,stroke-width:1px
    classDef ca fill:#faa3,stroke:#333,stroke-width:1px
    classDef ca1 fill:#f2f3,stroke:#333,stroke-width:1px
    classDef ca2 fill:#f2f3,stroke:#333,stroke-width:1px
    classDef ca3 fill:#f2f3,stroke:#333,stroke-width:1px
    classDef ca4 fill:#f2f3,stroke:#333,stroke-width:1px
    style A fill:#afa3,stroke:#333,stroke-width:2px
    
```


---


### IV. Agent Collaboration Settings

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
graph TD
    A[Agent Collaboration] --> B{Initial Weights}:::weights
    B --> C[Planner: 0.4]:::planner
    B --> D[Coder: 0.4]:::coder
    B --> E[Debugger: 0.3]:::debugger

    A --> F{Importance Score}:::importance
    F --> G(Evaluate Answers)
    G --> H(Assign Score)
    H --> I(Multiply by Weight)

    A --> J{Dynamic Selection}:::dynamic
    J --> K(Reintroduce Random Roles)
    K --> L(Prevents Over-Commitment)

    classDef weights fill:#f242,stroke:#333,stroke-width:1px
    classDef importance fill:#f242,stroke:#333,stroke-width:1px
    classDef dynamic fill:#f242,stroke:#333,stroke-width:1px
    classDef planner fill:#af22,stroke:#333,stroke-width:1px
    classDef coder fill:#af22,stroke:#333,stroke-width:1px
    classDef debugger fill:#fa22,stroke:#333,stroke-width:1px
    style A fill:#ff22,stroke:#333,stroke-width:2px
    
```


----

### V. Results and Performance

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
    A[Experimental Results] --> B{Performance Metrics}:::metrics
    B --> C["Pass@k"]:::pass
    B --> D[Token Consumption]:::token
    B --> E[API Calls]:::api

    A --> F{Datasets}:::datasets
    F --> G[HumanEval]:::simple
    F --> H[MBPP]:::simple
    F --> L[EvalPlus]:::simple
    F --> I[APPS]:::complex
    F --> J[xCodeEval]:::complex
    F --> K[CodeContest]:::complex

    classDef metrics fill:#f232,stroke:#333,stroke-width:1px
    classDef datasets fill:#f232,stroke:#333,stroke-width:1px
    classDef pass fill:#aaf3,stroke:#333,stroke-width:1px
    classDef token fill:#afa3,stroke:#333,stroke-width:1px
    classDef api fill:#faa3,stroke:#333,stroke-width:1px
    classDef simple fill:#ddd3,stroke:#333,stroke-width:1px
    classDef complex fill:#eee3,stroke:#333,stroke-width:1px
    style A fill:#afa3,stroke:#333,stroke-width:2px
    
```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---