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
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExZW8yNXMybzE4YnM4bzE3Zjhjc2xjaWF4OWtkdXVxdDAxbnBqMG9rMSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/12qq4Em3MVuwJW/giphy.gif)
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
> The materials are intended for 👨‍🎓 <ins>educational purposes</ins> 👨‍🎓 (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), 📖 <ins> personal study </ins> 📖, and 🔖 <ins> reference </ins> 🔖.
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
  look: handDrawn
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
      'secondaryColor': '#222',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '15px'
    }
  }
}%%
flowchart TD
    %% User Trigger
    A["User Repo Workflow<br/>(<b>.yml</b>)"]:::project
    A -->|"(1) trigger:<br/>push/tag"| B["GitHub Actions Runner"]:::github

    %% Action Execution Flow
    B -->|"(2) load metadata"| C["<b>action.yml</b>"]:::project
    C -->|"(3) exec bundle"| D["<b>dist/index.js</b>"]:::project
    D -->|"invokes"| E["<b>@actions/core</b>"]:::project
    D -->|"calls"| F["<b>src/main.js</b>"]:::project
    F -->|"reads inputs"| E
    F -->|"delegates to"| G["<b>src/create-release.js</b>"]:::project

    %% Release Logic
    G -->|"<code>GET /repos/:owner/:repo/tags</code>"| H["GitHub REST API"]:::external
    G -->|"compute tag<br/>(semver)"| I["semver"]:::project
    G -->|"<code>POST /repos/:owner/:repo/releases</code>"| H
    G -->|"set outputs"| J["Runner exposes outputs"]:::github
    J -->|"available to"| K["Subsequent Steps<br/>(<b>upload-release-asset</b>)"]:::github

    subgraph CI_Test_Pipeline["CI/Test Pipeline"]
    style CI_Test_Pipeline fill:#F2F2,stroke:#333,stroke-width:1px, color: #FFFF
        CI1["<b>.github/workflows/ci.yml</b>"]:::project
        CI2["<b>tests/create-release.test.js</b>"]:::project
        CI3["<b>package.json</b>"]:::project
        CI4["<b>package-lock.json</b>"]:::project
    end

    CI1 -->|"runs tests via npm test"| CI2
    CI2 -->|"validates logic"| F
    CI1 -->|"uses deps"| CI3
    CI1 -->|"locks deps"| CI4

    subgraph Legend["Legend"]
    style Legend fill:#22BB,stroke:#333,stroke-width:1px, color: #FFFF
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
    classDef github fill:#004085,stroke:#004085
    classDef project fill:#155724,stroke:#155724
    classDef external fill:#856404,stroke:#856404
    classDef ci fill:#657d,stroke:#6c757d
    
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
