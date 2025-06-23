---
created: 2025-06-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ggml-org/media
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExMWxxaTBpM2VvY20zOXJhZzI2enVwcHZoNGhkeXlmZ2FwdGp5NnFkNyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3oEduIl1GryVXv22ly/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# media repo project
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
title: "media repo project"
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
flowchart TB
    %% Actors
    %% User["User"]:::user
User@{ img: "https://raw.githubusercontent.com/CongLeSolutionX/CongLeSolutionX/refs/heads/main/assets/images/My-meme-and-question-marks-open-book-old-characters-background.png", label: "...👀.User.📖...", pos: "b", w: 200, h: 150, constraint: "off" }
    User:::user

    %% Documentation
    doc["<b>README.md</b>"]:::doc
    gitignore1["<b>.gitignore</b>"]:::doc
    gitignore2["<b>cards/.gitignore</b>"]:::doc

    subgraph CLI_Entry_Scripts["CLI Entry Scripts"]
    style CLI_Entry_Scripts fill:#F2F2,stroke:#333,stroke-width:1px, color: #FFFF
        script1["<b>llama.cpp-feature-cache-reuse.sh</b>"]:::script
        script2["<b>llama.cpp-feature-speculative-decoding.sh</b>"]:::script
        script3["<b>llama.cpp-model-gemma-3-test.sh</b>"]:::script
        script4["<b>llama.cpp-model-nomic-embed-text-v2.sh</b>"]:::script
        script5["<b>llama.cpp-model-qwen-3.sh</b>"]:::script
    end

    common["<b>common.sh</b>"]:::script

    subgraph llama_cpp_Engine["llama.cpp Engine"]
    style llama_cpp_Engine fill:#BFF2,stroke:#333,stroke-width:1px, color: #FFFF
      engine["llama.cpp binary + models"]:::engine
    end

    %% Assets
    subgraph Assets["Assets"]
    style Assets fill:#22BB,stroke:#333,stroke-width:1px, color: #FFFF
        fonts["Fonts"]:::asset
        logo["Logo"]:::asset
    end

    composer["Image Composer<br/>(ImageMagick)"]:::process
    output["Output:<br/><b>output.png</b>"]:::output
    sync["Sync to ggml org"]:::sync

    %% Flow
    User -->|runs| script1
    User -->|runs| script2
    User -->|runs| script3
    User -->|runs| script4
    User -->|runs| script5

    script1 -->|"sources <b>common.sh</b>"| common
    script2 --> common
    script3 --> common
    script4 --> common
    script5 --> common

    common -->|"invokes"| engine
    engine -->|"stdout text"| common

    common -->|"renders image"| composer
    fonts --> composer
    logo --> composer

    composer -->|"writes"| output
    output -->|"triggers"| sync

    %% Documentation links
    User --- doc
    doc --- gitignore1
    doc --- gitignore2

    %% Click Events
    click script1 "https://github.com/ggml-org/media/blob/master/cards/llama.cpp-feature-cache-reuse.sh"
    click script2 "https://github.com/ggml-org/media/blob/master/cards/llama.cpp-feature-speculative-decoding.sh"
    click script3 "https://github.com/ggml-org/media/blob/master/cards/llama.cpp-model-gemma-3-test.sh"
    click script4 "https://github.com/ggml-org/media/blob/master/cards/llama.cpp-model-nomic-embed-text-v2.sh"
    click script5 "https://github.com/ggml-org/media/blob/master/cards/llama.cpp-model-qwen-3.sh"
    click common "https://github.com/ggml-org/media/blob/master/cards/common.sh"
    click fonts "https://github.com/ggml-org/media/tree/master/fonts/ProFontWinTweaked/"
    click logo "https://github.com/ggml-org/media/tree/master/logo/"
    click sync "https://github.com/ggml-org/media/blob/master/scripts/sync-to-ggml-org.sh"
    click doc "https://github.com/ggml-org/media/blob/master/README.md"
    click gitignore1 "https://github.com/ggml-org/media/blob/master/.gitignore"
    click gitignore2 "https://github.com/ggml-org/media/blob/master/cards/.gitignore"

    %% Styles
    classDef user fill:#eef2,stroke:#333,stroke-width:1px
    classDef script fill:#ddf2,stroke:#333,stroke-width:1px
    classDef engine fill:#cfc2,stroke:#333,stroke-width:1px
    classDef asset fill:#fcf2,stroke:#333,stroke-width:1px
    classDef process fill:#ff92,stroke:#333,stroke-width:1px
    classDef output fill:#fc92,stroke:#333,stroke-width:1px
    classDef sync fill:#9cf2,stroke:#333,stroke-width:1px
    classDef doc fill:#eee2,stroke:#333,stroke-width:1px

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
