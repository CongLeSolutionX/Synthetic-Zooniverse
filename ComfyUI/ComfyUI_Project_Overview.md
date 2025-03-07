---
created: 2025-03-07 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://github.com/comfyanonymous/ComfyUI/blob/master/README.md"
---



# Overview ComfyUI Project
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## ComfyUI Project - A Diagrammatic Guide






```mermaid
---
title: "CHANGE_ME_DADDY"
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
      'lineColor': '#F8B229'
    }
  }
}%%
flowchart TD
    %% User Interaction
    USR["User"]:::external

    %% Frontend Layer
    subgraph "Frontend Layer"
        FE["Frontend (web)"]:::frontend
    end

    %% Backend Services
    subgraph "Backend Services"
        AS["API Server"]:::backend
        APS["Application Services"]:::backend
        MM["Model Manager Implementation"]:::backend
    end

    %% Execution Engine
    subgraph "Execution Engine"
        CE["Core Execution Engine (comfy)"]:::execution
        GP["Graph Processing (comfy_execution)"]:::execution
    end

    %% Model Management
    subgraph "Model Management"
        MS["Models Storage (models)"]:::storage
    end

    %% CI/CD and Integrations
    subgraph "CI/CD & Integrations"
        CI["CI/CD Scripts (.ci)"]:::cicd
        GH["GitHub Workflows (.github)"]:::cicd
    end

    %% Additional Tools and Utilities
    subgraph "Additional Tools & Utilities"
        TST["Tests"]:::tools
        NB["Notebooks"]:::tools
        SE["Script Examples"]:::tools
        UT["Utils"]:::tools
    end

    %% Data Flow Connections
    USR -->|"initiates"| FE
    FE -->|"API_call"| AS
    AS -->|"triggers"| APS
    APS -->|"executes"| CE
    CE -->|"processes_graph"| GP
    APS -->|"manages_models"| MM
    MM -->|"loads_models"| MS
    CE -->|"fetches_models"| MS

    %% CI/CD Integration (dashed to indicate external support)
    CI -.-> APS
    GH -.-> APS

    %% Styles
    classDef frontend fill:#cce5f,stroke:#004085,stroke-width:2px;
    classDef backend fill:#d4eda,stroke:#155724,stroke-width:2px;
    classDef execution fill:#fff3d,stroke:#856404,stroke-width:2px;
    classDef storage fill:#f8d7a,stroke:#721c24,stroke-width:2px;
    classDef cicd fill:#d1ec1,stroke:#0c5460,stroke-width:2px;
    classDef tools fill:#e2e35,stroke:#6c757d,stroke-width:2px;
    classDef external fill:#ffeea,stroke:#856404,stroke-width:2px;

    %% Click Events
    click FE "https://github.com/comfyanonymous/comfyui/tree/master/web"
    click AS "https://github.com/comfyanonymous/comfyui/tree/master/api_server"
    click APS "https://github.com/comfyanonymous/comfyui/tree/master/app"
    click CE "https://github.com/comfyanonymous/comfyui/tree/master/comfy"
    click GP "https://github.com/comfyanonymous/comfyui/tree/master/comfy_execution"
    click MS "https://github.com/comfyanonymous/comfyui/tree/master/models"
    click MM "https://github.com/comfyanonymous/comfyui/blob/master/app/model_manager.py"
    click CI "https://github.com/comfyanonymous/comfyui/blob/master/.ci"
    click GH "https://github.com/comfyanonymous/comfyui/blob/master/.github"
    click TST "https://github.com/comfyanonymous/comfyui/tree/master/tests"
    click NB "https://github.com/comfyanonymous/comfyui/tree/master/notebooks"
    click SE "https://github.com/comfyanonymous/comfyui/tree/master/script_examples"
    click UT "https://github.com/comfyanonymous/comfyui/tree/master/utils"
     
```





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---