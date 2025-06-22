---
created: 2025-06-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/jlumbroso/free-disk-space
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExZmd2OHpkYmJvM3Mxc2p3aHdjOTE5cTYwMXVxbW9qc3hoZ244ZXRkaiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/TsO3cLxeE8DNsztZyv/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# jlumbroso - free-disk-space repo project
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


---

```mermaid
---
title: "jlumbroso - free-disk-space repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'linear'},
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#22BB',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EEF2',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '15px'
    }
  }
}%%
flowchart TB
    %% Global Layers
    subgraph User_Configuration["User Configuration"]
        Workflow["GitHub Actions Workflow"]:::config
        ActionDef["Action Definition<br/>(action.yml)"]:::config
    end

    subgraph "Host Environment"
        Runner["Ubuntu Runner VM"]:::host
    end

    subgraph Clean_up_Engine["Clean-up Engine"]
    direction TB
        ModulesGroup["Clean-up Modules"]:::engine
        subgraph Clean_up_engine[" "]
        direction TB
            Android["Android libs cleanup"]:::module
            Dotnet[".NET cleanup"]:::module
            Haskell["Haskell cleanup"]:::module
            Large["Large packages cleanup"]:::module
            Toolcache["Tool cache cleanup"]:::module
            Swap["Swap cleanup"]:::module
        end
        Aggregator["Aggregate Free-Space Metrics"]:::log
    end

    DocsGroup["Project Documentation & License"]:::doc
    README["README.md"]:::doc
    License["LICENSE"]:::doc

    %% Connections
    Workflow -->|"trigger event"| Runner
    Runner -->|"reads action.yml"| ActionDef
    ActionDef -->|"input flags"| ModulesGroup
    ModulesGroup --> Android
    ModulesGroup --> Dotnet
    ModulesGroup --> Haskell
    ModulesGroup --> Large
    ModulesGroup --> Toolcache
    ModulesGroup --> Swap
    Android -->|"shell commands"| Aggregator
    Dotnet -->|"shell commands"| Aggregator
    Haskell -->|"shell commands"| Aggregator
    Large -->|"shell commands"| Aggregator
    Toolcache -->|"shell commands"| Aggregator
    Swap -->|"shell commands"| Aggregator
    Aggregator -->|"console output"| DocsGroup

    %% Click Events
    click Workflow "https://github.com/jlumbroso/free-disk-space/blob/main/.github/workflows/test.yml"
    click ActionDef "https://github.com/jlumbroso/free-disk-space/blob/main/action.yml"
    click README "https://github.com/jlumbroso/free-disk-space/blob/main/README.md"
    click License "https://github.com/jlumbroso/free-disk-space/tree/main/LICENSE"

    %% Styles
    classDef config fill:#a8e6cf,stroke:#333,stroke-width:1px
    classDef host fill:#ccc,stroke:#333,stroke-width:1px
    classDef engine fill:#dcedc1,stroke:#333,stroke-width:1px
    classDef module fill:#84b6f4,stroke:#333,stroke-width:1px
    classDef log fill:#ffd97d,stroke:#333,stroke-width:1px
    classDef doc fill:#ffaaa5,stroke:#333,stroke-width:1px
```

-----

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
