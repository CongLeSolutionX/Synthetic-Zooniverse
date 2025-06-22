---
created: 2025-06-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ggml-org/whisper.cpp
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExaTFnNnAyemJrdDRpMnFib2ZlNXJ3bmEwZnk5NWZ3aDc2azhxdzR0bSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/ggREjp7UHSmnaL6e1p/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# whisper.cpp repo project
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
title: "whisper.cpp repo project"
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
flowchart TD
    subgraph Front_ends_and_Integrations["Front-ends & Integrations"]
    style Front_ends_and_Integrations fill:#F2F2,stroke:#333,stroke-width:1px, color: #FFFF
        FE_CLI["CLI Tools"]:::frontend
        FE_Bindings["Language Bindings"]:::frontend
        FE_Mobile["Mobile Apps"]:::frontend
        FE_Others["Other Examples"]:::frontend
    end

    FE_CLI --> Core
    FE_Bindings --> Core
    FE_Mobile --> Core
    FE_Others --> Core

    subgraph Whisper_Core_Library["Whisper Core Library"]
    style Whisper_Core_Library fill:#22F2,stroke:#333,stroke-width:1px, color: #FFFF
        Core["Whisper Core Library"]:::core
    end

    Core --> Backend

    subgraph ggml_Backend["ggml Backend"]
    style ggml_Backend fill:#22BB,stroke:#333,stroke-width:1px, color: #FFFF
        Backend["ggml Backend"]:::backend
    end

    Backend --> ComputeSplit{"Dispatch Based On Build Flags"}

    subgraph Compute_Engines["Compute Engines"]
    style Compute_Engines fill:#2BB,stroke:#333,stroke-width:1px, color: #FFFF
        CE_CPU["CPU Intrinsics"]:::compute
        CE_CUDA["CUDA/cuBLAS"]:::compute
        CE_Vulkan["Vulkan GPU"]:::compute
        CE_Metal["Metal /<br/> Core ML"]:::compute
        CE_OpenVINO["OpenVINO"]:::compute
        CE_CANN["CANN<br/>(Ascend)"]:::compute
    end

    ComputeSplit --> CE_CPU
    ComputeSplit --> CE_CUDA
    ComputeSplit --> CE_Vulkan
    ComputeSplit --> CE_Metal
    ComputeSplit --> CE_OpenVINO
    ComputeSplit --> CE_CANN

    CE_CPU --> Backend
    CE_CUDA --> Backend
    CE_Vulkan --> Backend
    CE_Metal --> Backend
    CE_OpenVINO --> Backend
    CE_CANN --> Backend

    subgraph Model_Artifacts_and_Conversion["Model Artifacts & Conversion"]
    style Model_Artifacts_and_Conversion fill:#299D,stroke:#333,stroke-width:1px, color: #FFFF
        ModelsNode["Model Storage & Conversion"]:::models
    end

    ModelsNode -.-> Core

    subgraph Build_and_CI_Infrastructure["Build & CI Infrastructure"]
    style Build_and_CI_Infrastructure fill:#DD22,stroke:#333,stroke-width:1px, color: #FFFF
        CI["Build & CI"]:::ci
    end

    CI --> Core
    CI --> Backend
    CI --> FE_CLI

    classDef core fill:#AD86,stroke:#000
    classDef backend fill:#EE22,stroke:#000
    classDef compute fill:#B2BF,stroke:#000
    classDef frontend fill:#DAD2,stroke:#000
    classDef models fill:#22B,stroke:#000
    classDef ci fill:#D3D3,stroke:#000

    click Core "https://github.com/ggml-org/whisper.cpp/blob/master/include/whisper.h"
    click Core "https://github.com/ggml-org/whisper.cpp/blob/master/src/whisper.cpp"
    click Core "https://github.com/ggml-org/whisper.cpp/blob/master/src/whisper-arch.h"
    click Core "https://github.com/ggml-org/whisper.cpp/blob/master/src/CMakeLists.txt"
    click Backend "https://github.com/ggml-org/whisper.cpp/blob/master/ggml/include/ggml.h"
    click Backend "https://github.com/ggml-org/whisper.cpp/blob/master/ggml/src/ggml.c"
    click Backend "https://github.com/ggml-org/whisper.cpp/blob/master/ggml/src/ggml-backend.cpp"
    click Backend "https://github.com/ggml-org/whisper.cpp/blob/master/ggml/src/ggml-backend-reg.cpp"
    click Backend "https://github.com/ggml-org/whisper.cpp/blob/master/ggml/src/ggml-impl.h"
    click CE_CPU "https://github.com/ggml-org/whisper.cpp/tree/master/ggml/src/ggml-cpu"
    click CE_CUDA "https://github.com/ggml-org/whisper.cpp/tree/master/ggml/src/ggml-cuda"
    click CE_Vulkan "https://github.com/ggml-org/whisper.cpp/tree/master/ggml/src/ggml-vulkan"
    click CE_Metal "https://github.com/ggml-org/whisper.cpp/tree/master/ggml/src/ggml-metal"
    click CE_OpenVINO "https://github.com/ggml-org/whisper.cpp/tree/master/ggml/src/ggml-opencl"
    click CE_CANN "https://github.com/ggml-org/whisper.cpp/tree/master/ggml/src/ggml-cann"
    click FE_CLI "https://github.com/ggml-org/whisper.cpp/blob/master/examples/cli/cli.cpp"
    click FE_Bindings "https://github.com/ggml-org/whisper.cpp/tree/master/bindings/go"
    click FE_Mobile "https://github.com/ggml-org/whisper.cpp/blob/master/examples/whisper.objc"
    click FE_Others "https://github.com/ggml-org/whisper.cpp/blob/master/examples/lsp/lsp.cpp"
    click ModelsNode "https://github.com/ggml-org/whisper.cpp/blob/master/models/convert-h5-to-ggml.py"
    click CI "https://github.com/ggml-org/whisper.cpp/blob/master/CMakeLists.txt"
    click CI "https://github.com/ggml-org/whisper.cpp/tree/master/Makefile"
    click CI "https://github.com/ggml-org/whisper.cpp/tree/master/.devops/"
    click CI "https://github.com/ggml-org/whisper.cpp/tree/master/.github/workflows/"
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
