---
created: 2025-06-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ggml-org/ggml
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




# ggml repo project
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
title: "ggml repo project"
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
    %% Build-time flow
    subgraph "Build System"
        direction TB
        CMakeLists["CMakeLists.txt"]:::tool
        CMakeDir["cmake/"]:::tool
    end

    subgraph "Core Tensor Engine"
        direction TB
        GGML_C["ggml.c"]:::core
        GGML_ALLOC["ggml-alloc.c"]:::core
        GGML_BACKEND_CPP["ggml-backend.cpp"]:::core
        GGML_REG["ggml-backend-reg.cpp"]:::core
        GGML_OPT["ggml-opt.cpp"]:::core
        GGML_QUANTS["ggml-quants.c/.h"]:::core
        GGUF["gguf.cpp"]:::core
        HDR_GGML["ggml.h"]:::core
        HDR_ALLOC["ggml-alloc.h"]:::core
    end

    subgraph "Backend Modules"
        direction TB
        CPU["CPU Backend<br/>(src/ggml-cpu/)"]:::backend
        BLAS["BLAS Backend<br/>(src/ggml-blas/)"]:::backend
        CUDA["CUDA Backend<br/>(src/ggml-cuda/)"]:::backend
        METAL["Metal Backend<br/>(src/ggml-metal/)"]:::backend
        VULKAN["Vulkan Backend<br/>(src/ggml-vulkan/)"]:::backend
        OPENCL["OpenCL Backend<br/>(src/ggml-opencl/)"]:::backend
        SYCL["SYCL Backend<br/>(src/ggml-sycl/)"]:::backend
        CANN["CANN Backend<br/>(src/ggml-cann/)"]:::backend
        KOMPUTE["Kompute Backend<br/>(src/ggml-kompute/)"]:::backend
    end

    subgraph "Public API & Headers"
        direction TB
        PublicAPI["Public API<br/>(include/*.h)"]:::api
    end

    subgraph "Language Bindings"
        direction TB
        PythonBindings["Python CFFI Bindings"]:::api
    end

    subgraph "Client Applications"
        direction TB
        Examples["Example Applications<br/>(examples/)"]:::api
    end

    subgraph "Tools & Tests"
        direction TB
        Scripts["scripts/"]:::tool
        Tests["tests/"]:::tool
        RPC["RPC Module<br/>(src/ggml-rpc/)"]:::tool
    end

    %% Artifacts
    LIB["libggml<br/>(static/shared)"]:::core

    %% Build relationships
    CMakeLists -->|configures & compiles| GGML_C
    CMakeLists --> GGML_ALLOC
    CMakeLists --> GGML_BACKEND_CPP
    CMakeLists --> GGML_REG
    CMakeLists --> GGML_OPT
    CMakeLists --> GGML_QUANTS
    CMakeLists --> GGUF
    CMakeLists --> CPU
    CMakeLists --> BLAS
    CMakeLists --> CUDA
    CMakeLists --> METAL
    CMakeLists --> VULKAN
    CMakeLists --> OPENCL
    CMakeLists --> SYCL
    CMakeLists --> CANN
    CMakeLists --> KOMPUTE
    CMakeLists --> LIB
    CMakeLists -->|uses| CMakeDir

    %% Runtime relationships
    Examples -->|link to| LIB
    PythonBindings -->|loads via CFFI| LIB
    Scripts -->|model conversion| LIB
    RPC -->|wraps calls| LIB
    Tests -->|unit test| LIB

    Examples -->|calls| PublicAPI
    PythonBindings -->|calls| PublicAPI
    RPC -->|calls| PublicAPI

    PublicAPI -->|dispatch to| GGML_C
    PublicAPI --> GGML_ALLOC
    PublicAPI --> GGUF

    GGML_C -->|backend registration| GGML_REG
    GGML_REG --> CPU
    GGML_REG --> BLAS
    GGML_REG --> CUDA
    GGML_REG --> METAL
    GGML_REG --> VULKAN
    GGML_REG --> OPENCL
    GGML_REG --> SYCL
    GGML_REG --> CANN
    GGML_REG --> KOMPUTE

    %% Styles
    classDef core fill:#ADD8E6,stroke:#000
    classDef backend fill:#90EE90,stroke:#000
    classDef api fill:#FFA500,stroke:#000
    classDef tool fill:#D3D3D3,stroke:#000

    %% Click Events
    click CMakeLists "https://github.com/ggml-org/ggml/blob/master/CMakeLists.txt"
    click CMakeDir "https://github.com/ggml-org/ggml/tree/master/cmake/"
    click GGML_C "https://github.com/ggml-org/ggml/blob/master/src/ggml.c"
    click GGML_ALLOC "https://github.com/ggml-org/ggml/blob/master/src/ggml-alloc.c"
    click GGML_BACKEND_CPP "https://github.com/ggml-org/ggml/blob/master/src/ggml-backend.cpp"
    click GGML_REG "https://github.com/ggml-org/ggml/blob/master/src/ggml-backend-reg.cpp"
    click GGML_OPT "https://github.com/ggml-org/ggml/blob/master/src/ggml-opt.cpp"
    click GGML_QUANTS "https://github.com/ggml-org/ggml/blob/master/src/ggml-quants.c"
    click GGUF "https://github.com/ggml-org/ggml/blob/master/src/gguf.cpp"
    click HDR_GGML "https://github.com/ggml-org/ggml/blob/master/include/ggml.h"
    click HDR_ALLOC "https://github.com/ggml-org/ggml/blob/master/include/ggml-alloc.h"
    click CPU "https://github.com/ggml-org/ggml/tree/master/src/ggml-cpu/"
    click BLAS "https://github.com/ggml-org/ggml/tree/master/src/ggml-blas/"
    click CUDA "https://github.com/ggml-org/ggml/tree/master/src/ggml-cuda/"
    click METAL "https://github.com/ggml-org/ggml/tree/master/src/ggml-metal/"
    click VULKAN "https://github.com/ggml-org/ggml/tree/master/src/ggml-vulkan/"
    click OPENCL "https://github.com/ggml-org/ggml/tree/master/src/ggml-opencl/"
    click SYCL "https://github.com/ggml-org/ggml/tree/master/src/ggml-sycl/"
    click CANN "https://github.com/ggml-org/ggml/tree/master/src/ggml-cann/"
    click KOMPUTE "https://github.com/ggml-org/ggml/tree/master/src/ggml-kompute/"
    click PublicAPI "https://github.com/ggml-org/ggml/tree/master/include/"
    click PythonBindings "https://github.com/ggml-org/ggml/tree/master/examples/python/ggml/"
    click Examples "https://github.com/ggml-org/ggml/tree/master/examples/"
    click Scripts "https://github.com/ggml-org/ggml/tree/master/scripts/"
    click Tests "https://github.com/ggml-org/ggml/tree/master/tests/"
    click RPC "https://github.com/ggml-org/ggml/tree/master/src/ggml-rpc/"

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
