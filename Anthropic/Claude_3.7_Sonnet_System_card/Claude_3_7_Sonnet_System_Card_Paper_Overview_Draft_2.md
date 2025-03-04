---
created: 2025-03-04 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://assets.anthropic.com/m/785e231869ea8b3b/original/claude-3-7-sonnet-system-card.pdf"
---



# Claude 3.7 Sonnet System Card Paper Overview
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Claude 3.7 Sonnet System Card Paper Overview - A Diagrammatic Guide 



These diagrams below  provide a visual summary of the problem formulation for Claude 3.7 Sonnet, highlighting the core challenges, the relationships between components, and the key steps in the responsible scaling policy.

---



### Diagram 1: Core Challenges

This diagram visualizes the main challenges Anthropic is addressing with Claude 3.7 Sonnet.

```mermaid
---
title: "Claude 3.7 Sonnet System Card by Anthropic"
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
graph LR
    A["Claude 3.7 Sonnet:<br>Core Challenges"] --> B{"Safety & Ethical Considerations"}
    style A fill:#a2da,stroke:#333,stroke-width:1px
    B --> C[Reducing Harms]
    B --> D[Transparency & Trust]
    B --> E[Responsible Scaling]
    B --> F[Appropriate Harmlessness]
    
    C --> C1[Minimize Misuse]
    C --> C2[Ensure Child Safety]
    C --> C3[Mitigate Bias]
    C --> C4[Prevent Prompt Injection]
    C --> C5[Maintain Faithfulness]

    D --> D1[Provide Reasoning Insights]
    D --> D2[Enable Quality Evaluation]
    D --> D3[Support Safety Research]

    E --> E1[Manage AI Risks]
    E --> E2[Meet ASL Requirements]
    E --> E3[Monitor & Respond]

    F --> F1[Handle Ambiguous Requests]
    F --> F2[Provide Safe, Helpful Responses]
    F --> F3[Reduce Unnecessary Refusals]
    
    linkStyle 0 stroke-width:2px,stroke:#333
    
```


### Explanation

*   **Purpose:** This diagram summarizes the core challenges related to the development and deployment of Claude 3.7 Sonnet.
*   **Nodes:** The main node "Claude 3.7 Sonnet: Core Challenges" is connected to the four main challenge areas (Reducing Harms, Transparency & Trust, Responsible Scaling, and Appropriate Harmlessness).
*   **Sub-Nodes:** Each challenge area is further broken down into more specific sub-challenges.
*   **Style:** The style ensures easy visual interpretation of the challenges.

---

### Diagram 2: Dependencies and Relationships

This diagram emphasizes the dependencies and relationships between the various aspects of the problem formulation.

```mermaid
---
title: "Claude 3.7 Sonnet System Card by Anthropic"
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
graph LR
    A[Claude 3.7 Sonnet] --> B{Problem Formulation}
    style A fill:#a2da,stroke:#333,stroke-width:1px
    B --> C[Training Data & Process]:::detail
    B --> D[Extended Thinking Mode]:::detail
    B --> E[Evaluation Methods]:::detail
    B --> F[Safeguards & Mitigations]:::detail
    
    C --> C1[Proprietary Mix]
    C --> C2[Data Cleaning & Filtering]
    C --> C3[Focus on Helpfulness, Harmlessness, Honesty]

    D --> D1[Step-by-Step Reasoning]
    D --> D2[Toggleable User Control]
    D --> D3[Mathematical Problems, Complex Analyses]

    E --> E1[Automated Testing]
    E --> E2[Expert Red Teaming]
    E --> E3[Uplift Studies]

    F --> F1[Harmlessness Training]
    F --> F2[System Prompt Updates]
    F --> F3[Classifier Interventions]
    F --> F4[Usage Policy Enforcement]

    linkStyle 0 stroke-width:2px,stroke:#333
    classDef detail fill:#f9f3,stroke:#333,stroke-width:1px,stroke-dasharray:5 5
    
```



### Explanation

*   **Purpose:** To showcase the relationship between the different components.
*   **Nodes:**  The main node is "Claude 3.7 Sonnet", which branches out to the main aspects of the document (Training Data, Extended Thinking, Evaluation Methods, and Safeguards).
*   **Sub-Nodes:** Each aspect is further broken down into its key components.
*   **Style:** The style allows for an easy visual interpretation of the relationship between topics.

---

### Diagram 3: Responsible Scaling Policy (RSP) Flow

This diagram visualizes the RSP and how the ASL is determined.

```mermaid
---
title: "Claude 3.7 Sonnet System Card by Anthropic"
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
    A["Responsible Scaling Policy (RSP)"] --> B{"Evaluation Stages"}
    style A fill:#a2da,stroke:#333,stroke-width:1px
    B --> C["Domain-Specific Knowledge Testing"]
    B --> D["Capability Assessments<br>(Benchmarks)"]
    B --> E["Expert Red Teaming"]
    B --> F["Iterative Feedback<br>(FRT & AST)"]

    F --> G{"ASL Determination"}
    G --> H["RSO & CEO Review"]
    G --> I["Board of Directors"]
    G --> J["Long-Term Benefit Trust<br>(LTBT)"]

    H & I & J --> K{"Safety Measures"}
    K --> L["Monitoring Systems"]
    K --> M["Incident Response Protocols"]

    L & M --> N["Release Decision"]
    
    linkStyle 0 stroke-width:2px,stroke:#333
    
```



### Explanation

*   **Purpose:** Shows the process behind the RSP and the steps taken.
*   **Nodes:**  The main node is the "Responsible Scaling Policy (RSP)", which goes through evaluation stages and finally a release decision is made.
*   **Style:** The style allows for an easy visual interpretation of the process.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---