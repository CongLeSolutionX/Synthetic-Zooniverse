---
created: 2025-06-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ggml-org/ci
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExaDV0NjhoMjFmMTU4bmk5OXZvdDRrNXR6MHNhenZ4c3UyaGUxYnpqbSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/52FJTR5RaZ15dlzwqF/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# ci repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes (<ins>sometimes, entertainment purposes</ins>), personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


----

```mermaid
---
title: "ci repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
  look: handDrawn
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'American Typewriter, monospace',
    'logLevel': 'fatal',
    'themeVariables': {
      'primaryColor': '#22BB',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#E2F1',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '20px'
    }
  }
}%%
flowchart TB
    %% Bootstrap phase
    subgraph Bootstrap_and_Provisioning["Bootstrap & Provisioning"]
    direction TB
        Setup["Bootstrap Scripts"]:::infra
    end

    %% Infrastructure layer
    subgraph Docker_Hosts["Docker Hosts<br/>(VMs)"]
    direction TB
        subgraph Runner_Pool["Runner Pool"]
        direction TB
            Runner["GitHub-Runner Container"]:::container
            ModelDL["Model-Downloader Container"]:::container
        end
    end

    %% Core orchestrator
    CI_Orchestrator["CI Orchestrator Service"]:::service

    %% External services
    subgraph GitHub["GitHub"]
    direction TB
        GitHubAPI["GitHub API"]:::external
        GitHubRepos["GitHub Repositories"]:::external
    end

    %% Data flows
    Setup -->|boots and configures| Docker_Hosts
    CI_Orchestrator -->|polls for commits| GitHubAPI
    GitHubAPI -->|notifies of new commits| CI_Orchestrator
    CI_Orchestrator -->|schedules job| Runner
    Runner -->|if needed invokes| ModelDL
    Runner -->|pushes logs/results| GitHubAPI
    CI_Orchestrator -->|updates commit status| GitHubAPI

    %% Click events
    click CI_Orchestrator "https://github.com/ggml-org/ci/tree/master/images/github-runners-manager/"
    click Runner "https://github.com/ggml-org/ci/tree/master/images/github-runner/"
    click ModelDL "https://github.com/ggml-org/ci/tree/master/images/llama.cpp-model-downloader/"

    %% Styles
    classDef service fill:#D0E8FF,stroke:#005B9F,color:#000;
    classDef container fill:#B3DFFF,stroke:#007ACC,color:#000;
    classDef external fill:#DFFFE0,stroke:#1A7F1A,color:#000;
    classDef infra fill:#F0F0F0,stroke:#888888,color:#000;
    class CI_Orchestrator service
    class Runner,ModelDL container
    class GitHubAPI,GitHubRepos external
    class Setup infra

```

------

```mermaid
---
title: "❓...CongLeSolutionX....❓"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%{
  init: {
    'flowchart': { 'htmlLabels': false },
    'fontFamily': 'Bradley Hand',
    'themeVariables': {
      'primaryColor': '#fc82',
      'primaryTextColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#5229',
      'secondaryTextColor': '#6C3483',
      'lineColor': '#F8B229',
      'fontSize': '20px'
    }
  }
}%%
flowchart LR
  My_Meme@{ img: "https://raw.githubusercontent.com/CongLeSolutionX/CongLeSolutionX/refs/heads/main/assets/images/My-meme-and-question-marks-open-book-old-characters-background.png", label: "..🙉..👀..📖..", pos: "b", w: 200, h: 150, constraint: "off" }

  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote@{ shape: braces, label: "..👀..<br/>A suit 🕴️ <br/> or<br/>a stack of proof 🗂️ <br/>❓<br/>💭 Where should your attention truly be 💬<br/>❓..."}

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  animatingEdge@{ animate: true }

```

---
><b>Licenses</b>:
>
>- <b>MIT License</b>:  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
>- <b>Creative Commons Attribution-ShareAlike 4.0 International</b>: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) [![CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/88x31.png)](https://creativecommons.org/licenses/by-sa/4.0/) - Legal details in [LICENSE-CC-BY-SA-4.0](THE_PAST/LICENSE-CC-BY-SA-4.0) and at [Creative Commons official site](https://creativecommons.org/licenses/by-sa/4.0/).
>
---
