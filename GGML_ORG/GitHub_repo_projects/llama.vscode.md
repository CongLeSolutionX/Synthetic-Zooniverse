---
created: 2025-06-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ggml-org/llama.vscode
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExcHBhZjRleGY4ajJrbnFpY2FjNWt2MG80czlzaHA1Y3QxNGQzZTJlaCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3o8doRPFzhzAVkW9NK/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# llama.vscode repo project
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
title: "llama.vscode repo project"
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
    'flowchart': { 'htmlLabels': true, 'curve': 'bumpY' },
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
flowchart LR
  %% Global Entities
  Editor["VS Code Editor Host"]:::external

  subgraph Extension_Host_Process["Extension Host Process"]
  style Extension_Host_Process fill:#F2F2,stroke:#333,stroke-width:1px, color: #FFFF
  direction TB
    subgraph Orchestration_Layer["Orchestration Layer"]
    style Orchestration_Layer fill:#FFD2,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
      ExtensionDispatcher["Command & Event Dispatcher"]:::frontend
      Application["Orchestration /<br/> Dependency Injection"]:::frontend
      Architect["Architect /<br/> Factory Setup"]:::frontend
    end

    subgraph UI_Integrator_Layer["UI Integrators"]
    style UI_Integrator_Layer fill:#2D22,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
      Menu["Context Menu Commands"]:::frontend
      Statusbar["Status Bar Updates"]:::frontend
      TextEditor["Inline Suggestions & Keybindings"]:::frontend
    end

    
    subgraph Context_Manager_Layer["Context Manager"]
    style Context_Manager_Layer fill:#DB22,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
      ChatContext["Primary Context<br/>(chat-context)"]:::backend
      ExtraContext["Additional Context<br/>(extra-context)"]:::backend
    end

    subgraph Completion_Engine_Layer["Completion Engine"]
    style Completion_Engine_Layer fill:#BCF2,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
      ChatWithAI["High-level Chat Interface"]:::backend
      Completion["Core Completion Logic"]:::backend
      LlamaServer["HTTP Interface to llama.cpp"]:::backend
    end

    subgraph Supporting_Services["Supporting Services"]
    style Supporting_Services fill:#CFF2,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
      Configuration["Configuration & Toggles"]:::service
      Prompts["Prompt Templates"]:::service
      Translations["Localization /<br/> Translations"]:::service
      Utils["General Utilities"]:::service
      LRUCache["In-memory LRU Cache"]:::service
      Logger["Logging Utilities"]:::service
    end

    %% Tests
    Tests["Extension Tests"]:::service
  end

  %% External Service
  LlamaCPP["llama.cpp Server<br/>(HTTP :8080)"]:::external

  %% Connections - Dynamic Flow
  Editor -->|"onType/<br/>onCompletion"| ExtensionDispatcher
  ExtensionDispatcher -->|"init services"| Application
  Application -->|"wires"| Architect

  Architect --> ChatContext
  Architect --> ExtraContext
  Architect --> ChatWithAI
  Architect --> Completion
  Architect --> LlamaServer
  Architect --> Configuration
  Architect --> Prompts
  Architect --> Translations
  Architect --> Utils
  Architect --> LRUCache
  Architect --> Logger
  Architect --> Menu
  Architect --> Statusbar
  Architect --> TextEditor

  ChatContext --> ChatWithAI
  ExtraContext --> ChatWithAI

  ChatWithAI --> Completion
  Completion --> LlamaServer
  LlamaServer -->|HTTP request| LlamaCPP
  LlamaCPP -->|token stream| LlamaServer
  LlamaServer -->|response| Completion
  Completion -->|CompletionItems| TextEditor

  TextEditor -->|render suggestions| Editor
  Statusbar -->|update metrics| Editor
  Menu -->|commands| Editor

  %% Supporting Services usage
  Completion --> Configuration
  Completion --> Prompts
  ChatWithAI --> Prompts
  ChatWithAI --> LRUCache
  ChatWithAI --> Logger
  ChatContext --> Utils
  ExtraContext --> Utils

  %% Tests dependency
  Tests --> ExtensionDispatcher
  Tests --> ChatWithAI
  Tests --> Completion

  %% Click Events
  click ExtensionDispatcher "https://github.com/ggml-org/llama.vscode/blob/master/src/extension.ts"
  click Application "https://github.com/ggml-org/llama.vscode/blob/master/src/application.ts"
  click Architect "https://github.com/ggml-org/llama.vscode/blob/master/src/architect.ts"
  click ChatContext "https://github.com/ggml-org/llama.vscode/blob/master/src/chat-context.ts"
  click ExtraContext "https://github.com/ggml-org/llama.vscode/blob/master/src/extra-context.ts"
  click ChatWithAI "https://github.com/ggml-org/llama.vscode/blob/master/src/chat-with-ai.ts"
  click Completion "https://github.com/ggml-org/llama.vscode/blob/master/src/completion.ts"
  click LlamaServer "https://github.com/ggml-org/llama.vscode/blob/master/src/llama-server.ts"
  click Menu "https://github.com/ggml-org/llama.vscode/blob/master/src/menu.ts"
  click Statusbar "https://github.com/ggml-org/llama.vscode/blob/master/src/statusbar.ts"
  click TextEditor "https://github.com/ggml-org/llama.vscode/blob/master/src/text-editor.ts"
  click Configuration "https://github.com/ggml-org/llama.vscode/blob/master/src/configuration.ts"
  click Prompts "https://github.com/ggml-org/llama.vscode/blob/master/src/prompts.ts"
  click Translations "https://github.com/ggml-org/llama.vscode/blob/master/src/translations.ts"
  click Utils "https://github.com/ggml-org/llama.vscode/blob/master/src/utils.ts"
  click LRUCache "https://github.com/ggml-org/llama.vscode/blob/master/src/lru-cache.ts"
  click Logger "https://github.com/ggml-org/llama.vscode/blob/master/src/logger.ts"
  click Tests "https://github.com/ggml-org/llama.vscode/blob/master/src/test/extension.test.ts"

  %% Styles
  classDef frontend fill:#BEF2,stroke:#333,stroke-width:1px
  classDef backend fill:#C6C9,stroke:#333,stroke-width:1px
  classDef service fill:#F9C2,stroke:#333,stroke-width:1px
  classDef external fill:#C2BC,stroke:#333,stroke-width:1px

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
