---
created: 2025-06-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ggml-org/llama.cpp
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExdDc1azN0YnQ5bnN6bnFiNWpjM2ZlMGpoMGdyYWY4NjRoY3Jtemg0MiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zxt9AHjMEOtGM/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# llama.cpp repo project
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
title: "llama.cpp repo project"
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
    'flowchart': { 'htmlLabels': true, 'curve': 'monotoneY' },
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
flowchart TD
    %% Llama_logo@{ img: "https://raw.githubusercontent.com/meta-llama/llama3/refs/heads/main/Llama3_Repo.jpeg", label: "..🃏..🎲..🀄..", pos: "b", w: 300, h: 250, constraint: "on" }

    %% Logo@{ img: "https://pbs.twimg.com/profile_images/1913581839987380224/8X6G4lfs_400x400.jpg", label: "..🪚..🛠️..📚..", pos: "b", w: 200, h: 150, constraint: "on" }
    
    %% Public API
    A["llama.cpp <br/>(Public API)"]:::api

    %% Llama_logo ~~~ A
    %% Logo ~~~ Chat_and_Context


    %% I/O & Model Representation Layer
    subgraph I_O_and_Model["I/O & Model"]
    style I_O_and_Model fill:#004085,stroke:#6C3483,stroke-width:3px, color: #FFFF
    direction TB
      B1["llama-model-loader"]:::io
      B2["llama-model-saver"]:::io
      B3["llama-mmap"]:::io
      B4["llama-io"]:::io
      B5["llama-model"]:::model
      B6["llama-hparams"]:::model
      B7["llama-cparams"]:::model
      B8["llama-vocab"]:::model
    end

    %% Execution & Backends Layer
    subgraph Execution_and_Backends["Execution & Backends"]
    style Execution_and_Backends fill:#155724,stroke:#856404,stroke-width:1px, color: #FFFF
    direction TB
      C1["llama-graph"]:::exec
      C2["llama-arch <<Backend Interface>>"]:::exec
      C3["llama-adapter"]:::exec
      C4["llama-batch"]:::exec
    end

    %% Memory & Cache
    subgraph Memory_and_Cache["Memory & Cache"]
    style Memory_and_Cache fill:#0c5460,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
      D1["llama-memory"]:::cache
      D2["llama-kv-cache"]:::cache
    end

    %% Quantization & Sampling Layer
    subgraph Quant_and_Sampling["Quant & Sampling"]
    style Quant_and_Sampling fill:#856404,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
      E1["llama-quant"]:::quant
      E2["llama-sampling"]:::quant
    end

    %% Chat & Context Layer
    subgraph Chat_and_Context["Chat & Context"]
    style Chat_and_Context fill:#6f42c1,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
      F1["llama-chat"]:::chat
      F2["llama-context"]:::chat
    end

    %% Utilities Layer
    subgraph Utilities["Utilities"]
    style Utilities fill:#6c757d,stroke:#333,stroke-width:2px, color: #FFFF
    direction TB
      G1["unicode"]:::util
      G2["unicode-data"]:::util
      G3["llama-grammar"]:::util
    end

    %% Flow connections
    A -->|"calls load GGUF"| B1
    A --> B3
    B1 --> B5
    B3 --> B5
    B4 --> B5
    B5 --> C1
    C1 --> C2
    C2 --> C4
    C1 --> C3
    C4 --> D1
    C4 --> D2
    D2 --> C1
    C2 --> E1
    C1 --> E2
    E2 --> D2
    E2 --> F2
    F2 --> C1
    F1 --> F2
    F1 --> E2
    E2 --> G3
    G3 --> A

    %% Click Events
    click A "https://github.com/ggml-org/llama.cpp/blob/master/src/llama.cpp"
    click B1 "https://github.com/ggml-org/llama.cpp/blob/master/src/llama-model-loader.cpp"
    click B2 "https://github.com/ggml-org/llama.cpp/blob/master/src/llama-model-saver.cpp"
    click B3 "https://github.com/ggml-org/llama.cpp/blob/master/src/llama-mmap.cpp"
    click B4 "https://github.com/ggml-org/llama.cpp/blob/master/src/llama-io.cpp"
    click B5 "https://github.com/ggml-org/llama.cpp/blob/master/src/llama-model.cpp"
    click B6 "https://github.com/ggml-org/llama.cpp/blob/master/src/llama-hparams.cpp"
    click B7 "https://github.com/ggml-org/llama.cpp/blob/master/src/llama-cparams.cpp"
    click B8 "https://github.com/ggml-org/llama.cpp/blob/master/src/llama-vocab.cpp"
    click C1 "https://github.com/ggml-org/llama.cpp/blob/master/src/llama-graph.cpp"
    click C2 "https://github.com/ggml-org/llama.cpp/blob/master/src/llama-arch.cpp"
    click C3 "https://github.com/ggml-org/llama.cpp/blob/master/src/llama-adapter.cpp"
    click C4 "https://github.com/ggml-org/llama.cpp/blob/master/src/llama-batch.cpp"
    click D1 "https://github.com/ggml-org/llama.cpp/blob/master/src/llama-memory.cpp"
    click D2 "https://github.com/ggml-org/llama.cpp/blob/master/src/llama-kv-cache.cpp"
    click E1 "https://github.com/ggml-org/llama.cpp/blob/master/src/llama-quant.cpp"
    click E2 "https://github.com/ggml-org/llama.cpp/blob/master/src/llama-sampling.cpp"
    click F1 "https://github.com/ggml-org/llama.cpp/blob/master/src/llama-chat.cpp"
    click F2 "https://github.com/ggml-org/llama.cpp/blob/master/src/llama-context.cpp"
    click G1 "https://github.com/ggml-org/llama.cpp/blob/master/src/unicode.cpp"
    click G2 "https://github.com/ggml-org/llama.cpp/blob/master/src/unicode-data.cpp"
    click G3 "https://github.com/ggml-org/llama.cpp/blob/master/src/llama-grammar.cpp"

    %% Styles
    classDef api fill:#62cc,stroke:#62cc,stroke-width:1px,color:#F8B229
    classDef io fill:#005cbf,stroke:#485,stroke-width:3px,color:#F8B229
    classDef model fill:#004085,stroke:#004085,stroke-width:3px,color:#F8B229
    classDef exec fill:#155724,stroke:#22BB,stroke-width:4px,color:#F8B229
    classDef cache fill:#0c5460,stroke:#541,stroke-width:3px,color:#F8B229
    classDef quant fill:#5229,stroke:#f0ad4e,stroke-width:1px,color:#F8B229
    classDef chat fill:#4b0082,stroke:#6f42c1,stroke-width:2px,color:#F8B229
    classDef util fill:#343a40,stroke:#6c757d,stroke-width:1px,color:#F8B229

```

---

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
