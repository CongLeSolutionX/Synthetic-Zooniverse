---
created: 2025-06-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/bigcode-project/starcoder
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




# bigcode-project - starcoder repo project
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
title: "bigcode-project - starcoder repo project"
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
    %% Configuration Layer
    subgraph "Configuration Layer"
        ConfigPY["config.py"]:::config
        ConfigYAML["config.yaml"]:::config
        DSConfig["deepspeed_z3_config_bf16.json"]:::config
    end

    %% CLI Scripts
    subgraph "CLI Scripts"
        TrainChat["chat/train.py"]:::script
        GenChat["chat/generate.py"]:::script
        Finetune["finetune/finetune.py"]:::script
        MergeAdapter["merge_peft_adapters.py"]:::script
    end

    %% Core Libraries
    subgraph "Core Libraries"
        ModelLoader["AutoModelForCausalLM & AutoTokenizer"]:::core
        PEFT["PEFT Adapters & BitsAndBytes"]:::core
        DatasetStream["Hugging Face Datasets"]:::core
        DeepSpeed["DeepSpeed (Z3, bf16)"]:::core
        Utils["utils.py"]:::core
    end

    %% External Services
    subgraph "External Services"
        HFHub["Hugging Face Hub"]:::external
        Wandb["wandb"]:::external
    end

    %% Data Stores
    subgraph "Data Stores"
        DataStore["Instruction Datasets"]:::datastore
        Checkpoints["./checkpoints"]:::datastore
    end

    %% Documentation
    subgraph "Documentation"
        ProjectReadme["README.md"]:::doc
        ChatReadme["chat/README.md"]:::doc
        ReqRoot["requirements.txt"]:::doc
        ReqChat["chat/requirements.txt"]:::doc
        License["LICENSE"]:::doc
        GitIgnore[".gitignore"]:::doc
    end

    %% Relationships
    ConfigPY -->|uses| TrainChat
    ConfigYAML -->|loads| TrainChat
    DSConfig -->|applies| TrainChat
    ConfigPY -->|uses| GenChat
    ConfigYAML -->|loads| GenChat
    ConfigPY -->|uses| Finetune
    ConfigPY -->|uses| MergeAdapter

    TrainChat -->|imports| Utils
    GenChat -->|imports| Utils
    Finetune -->|imports| Utils
    MergeAdapter -->|imports| Utils

    TrainChat -->|loads model| ModelLoader
    Finetune -->|loads model| ModelLoader
    GenChat -->|loads model| ModelLoader
    MergeAdapter -->|loads model| ModelLoader

    TrainChat -->|streams data| DatasetStream
    Finetune -->|streams data| DatasetStream

    TrainChat -->|configures| PEFT
    Finetune -->|configures| PEFT
    TrainChat -->|accelerates| DeepSpeed
    Finetune -->|accelerates| DeepSpeed

    DatasetStream -->|provides| DataStore
    TrainChat -->|writes checkpoints| Checkpoints
    Finetune -->|writes checkpoints| Checkpoints

    Checkpoints -->|adapter weights| MergeAdapter
    MergeAdapter -->|merged model| HFHub
    Finetune -->|push adapters| HFHub
    TrainChat -->|push adapters| HFHub

    GenChat -->|fetches model| HFHub
    GenChat -->|generates| userOutput["Generated Text"]

    TrainChat -->|logs metrics| Wandb
    Finetune -->|logs metrics| Wandb

    %% Documentation access
    ProjectReadme --> TrainChat
    ChatReadme --> TrainChat

    %% Click Events
    click ConfigPY "https://github.com/bigcode-project/starcoder/blob/main/chat/config.py"
    click ConfigYAML "https://github.com/bigcode-project/starcoder/blob/main/chat/config.yaml"
    click DSConfig "https://github.com/bigcode-project/starcoder/blob/main/chat/deepspeed_z3_config_bf16.json"
    click TrainChat "https://github.com/bigcode-project/starcoder/blob/main/chat/train.py"
    click GenChat "https://github.com/bigcode-project/starcoder/blob/main/chat/generate.py"
    click Finetune "https://github.com/bigcode-project/starcoder/blob/main/finetune/finetune.py"
    click MergeAdapter "https://github.com/bigcode-project/starcoder/blob/main/finetune/merge_peft_adapters.py"
    click Utils "https://github.com/bigcode-project/starcoder/blob/main/chat/utils.py"
    click ProjectReadme "https://github.com/bigcode-project/starcoder/blob/main/README.md"
    click ChatReadme "https://github.com/bigcode-project/starcoder/blob/main/chat/README.md"
    click ReqRoot "https://github.com/bigcode-project/starcoder/blob/main/requirements.txt"
    click ReqChat "https://github.com/bigcode-project/starcoder/blob/main/chat/requirements.txt"
    click License "https://github.com/bigcode-project/starcoder/tree/main/LICENSE"
    click GitIgnore "https://github.com/bigcode-project/starcoder/blob/main/.gitignore"

    %% Styles
    classDef script fill:#cce5ff,stroke:#004085,stroke-width:1px;
    classDef config fill:#d4edda,stroke:#155724,stroke-width:1px;
    classDef core fill:#e2e3e5,stroke:#383d41,stroke-width:1px;
    classDef external fill:#fff3cd,stroke:#856404,stroke-width:1px;
    classDef datastore fill:#d1ecf1,stroke:#0c5460,stroke-width:1px;
    classDef doc fill:#f8d7da,stroke:#721c24,stroke-width:1px;
    class TrainChat,GenChat,Finetune,MergeAdapter script
    class ConfigPY,ConfigYAML,DSConfig config
    class ModelLoader,PEFT,DatasetStream,DeepSpeed,Utils core
    class HFHub,Wandb external
    class DataStore,Checkpoints datastore
    class ProjectReadme,ChatReadme,ReqRoot,ReqChat,License,GitIgnore doc
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
