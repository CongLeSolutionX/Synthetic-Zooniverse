---
created: 2025-06-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/zendesk/action-create-release
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExcGN5bjVmMmlyZzF3MDh6dW9kd3hjNnZvb3l5anMxMXFlNmt6a2R1ZCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/xT39CSrbCLKaQJ2MqQ/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# zendesk - action-create-release repo project
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
title: "zendesk - action-create-release repo project"
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
flowchart TD
    %% User Trigger
    A["User Repo Workflow (.yml)"]:::project
    A -->|"(1) trigger: push/tag"| B["GitHub Actions Runner"]:::github

    %% Action Execution Flow
    B -->|"(2) load metadata"| C["action.yml"]:::project
    C -->|"(3) exec bundle"| D["dist/index.js"]:::project
    D -->|"invokes"| E["@actions/core"]:::project
    D -->|"calls"| F["src/main.js"]:::project
    F -->|"reads inputs"| E
    F -->|"delegates to"| G["src/create-release.js"]:::project

    %% Release Logic
    G -->|"GET /repos/:owner/:repo/tags"| H["GitHub REST API"]:::external
    G -->|"compute tag (semver)"| I["semver"]:::project
    G -->|"POST /repos/:owner/:repo/releases"| H
    G -->|"set outputs"| J["Runner exposes outputs"]:::github
    J -->|"available to"| K["Subsequent Steps (upload-release-asset)"]:::github

    %% CI/Test Pipeline
    subgraph "CI / Test Pipeline"
        CI1[".github/workflows/ci.yml"]:::project
        CI2["tests/create-release.test.js"]:::project
        CI3["package.json"]:::project
        CI4["package-lock.json"]:::project
    end
    CI1 -->|"runs tests via npm test"| CI2
    CI2 -->|"validates logic"| F
    CI1 -->|"uses deps"| CI3
    CI1 -->|"locks deps"| CI4

    %% Legend
    subgraph Legend
        L1["GitHub-managed Components"]:::github
        L2["Project Artifacts"]:::project
        L3["External Services"]:::external
        L4["CI/Test Steps"]:::ci
    end

    %% Click Events
    click C "https://github.com/zendesk/action-create-release/blob/master/action.yml"
    click D "https://github.com/zendesk/action-create-release/blob/master/dist/index.js"
    click F "https://github.com/zendesk/action-create-release/blob/master/src/main.js"
    click G "https://github.com/zendesk/action-create-release/blob/master/src/create-release.js"
    click CI2 "https://github.com/zendesk/action-create-release/blob/master/tests/create-release.test.js"
    click CI1 "https://github.com/zendesk/action-create-release/blob/master/.github/workflows/ci.yml"
    click CI3 "https://github.com/zendesk/action-create-release/blob/master/package.json"
    click CI4 "https://github.com/zendesk/action-create-release/blob/master/package-lock.json"

    %% Styles
    classDef github fill:#cce5ff,stroke:#004085,color:#004085;
    classDef project fill:#d4edda,stroke:#155724,color:#155724;
    classDef external fill:#fff3cd,stroke:#856404,color:#856404;
    classDef ci fill:#e2e3e5,stroke:#6c757d,color:#6c757d;
    class Legend,L1,L2,L3,L4 ci
    class L1 github
    class L2 project
    class L3 external
    class L4 ci
```

----

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
