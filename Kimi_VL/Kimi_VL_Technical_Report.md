---
created: 2025-04-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://github.com/MoonshotAI/Kimi-VL"
---



# KIMI-VL TECHNICAL REPORT - A Diagrammatic Guide 
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---



Here are several Mermaid diagrams illustrating the key concepts extracted from the Kimi-VL Technical Report mindmap structure.



## Diagram 1: Kimi-VL Core Architecture & Capabilities

This diagram shows the main components of the Kimi-VL model and highlights its core capabilities mentioned in the abstract.

```mermaid
---
title: "Kimi-VL Core Architecture & Capabilities"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'graph': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Monospace',
    'themeVariables': {
      'primaryColor': '#BEF',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#EE2',
      'tertiaryColor': '#fff',
      'stroke':'#3323',
      'stroke-width': '0.5px'
    }
  }
}%%
graph LR
    subgraph Kimi_VL_Model["Kimi-VL Core Architecture"]
        direction TB
        Input_Image[Input Image] --> MoonViT["MoonViT (Vision Encoder - 400M)<br/>Native Resolution<br/>2D RoPE + SigLIP Init"]
        Input_Text["Input Text/Prompt"] --> MoE_LLM
        MoonViT --> Features["Image Features"]
        Features --> MLP_Projector["MLP Projector (2 Layers)<br/>Pixel Shuffle"]
        MLP_Projector --> LLM_Embeddings["LLM Embeddings"]
        LLM_Embeddings --> MoE_LLM["Moonlight MoE LLM (Decoder)<br/>2.8B Activated / 16B Total"]
        MoE_LLM --> Output["Multimodal Output"]
    end

    subgraph Capabilities["Key Capabilities"]
        direction LR
        Cap1["Advanced Multimodal Reasoning"]
        Cap2["Long-Context Understanding (128K)"]
        Cap3[Strong Agent Capabilities]
        Cap4[Efficient MoE Architecture]
        Cap5[High-Resolution Perception]
        Cap6[Competitive Performance vs SoTA]
    end

    Kimi_VL_Model -.-> Capabilities
    
```

**Explanation:** This diagram uses a flowchart (`graph LR` and `graph TB` within subgraphs) to show the flow of information through the model's main architectural components (MoonViT, MLP Projector, MoE LLM) and lists its primary capabilities separately.

---

## Diagram 2: Kimi-VL Training & Development Pipeline

This flowchart outlines the sequential stages involved in training the base Kimi-VL model and the specialized Kimi-VL-Thinking variant.

```mermaid
---
title: "Kimi-VL Training & Development Pipeline"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'graph': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Monospace',
    'themeVariables': {
      'primaryColor': '#BEF',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#EE2',
      'tertiaryColor': '#fff',
      'stroke':'#3323',
      'stroke-width': '0.5px'
    }
  }
}%%
graph TD
    A["Start: Moonlight LLM Pre-trained<br/>(5.2T Text)"] --> B("Stage 1:<br/>ViT Training")
    B -- Image-Text Pairs, CoCa Loss --> C{"MoonViT Trained & Aligned"}
    C --> D("Stage 2:<br/>Joint Pre-training - 1.4T")
    D -- Text + Multimodal Data --> E{"Base Multimodal Ability"}
    E --> F("Stage 3:<br/>Joint Cooldown - 0.6T")
    F -- High-Quality Text/Multimodal, Synth Data --> G{"Enhanced Abilities"}
    G --> H("Stage 4:<br/>Joint Long-Context Activation - 0.3T")
    H -- Long Text/Video/Docs, RoPE Adjust --> I{"128K Context Enabled"}

    I --> J("Stage 5:<br/>Joint SFT - 32K -> 128K")
    J -- Instruction Data, ChatML --> K["Kimi-VL<br/>(Base Interactive Model)"]

    I --> L("Stage 6:<br/>Long-CoT SFT")
    L -- Reasoning Warmup Data --> M{"Primed for Long Reasoning"}
    M --> N("Stage 7:<br/>Reinforcement Learning")
    N -- Online Policy Mirror Descent, Reward Model --> O["Kimi-VL-Thinking<br/>(Advanced Reasoning)"]

    style K fill:#ccf,stroke:#333,stroke-width:2px
    style O fill:#cfc,stroke:#333,stroke-width:2px
    
```

**Explanation:** This flowchart (`graph TD`) depicts the progression through the various pre-training and post-training stages, highlighting the key inputs and outputs for each stage and the branching leading to the final Kimi-VL and Kimi-VL-Thinking models.

---

## Diagram 3: Data Construction Categories

This mindmap categorizes the different types of data used during the various training phases of Kimi-VL.

```mermaid
---
title: "Data Construction Categories"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%{
  init: {
    'themeVariables': {
      'fontSize': '12px',
      'fontFamily': 'Monospace'
    }
  }
}%%
mindmap
  root((Data Construction))
    Data Processing Pipelines
      (Filtering)
      (Synthesis)
      (Deduplication)
    Pre-Training Data
      (Caption Data)
      (Image-text Interleaving Data)
      (OCR Data - Single/Multi-page)
      (Knowledge Data - Textbooks, Web, Geometry)
      (Agent Data - Grounding, Planning, Trajectories)
      (Video Data - Long/Short, Description, Grounding)
      (Text Data - From Moonlight Corpus)
    Instruction Data (SFT)
      (Conversational & Instruction Following)
      (Seed Dataset -> Human Ranking -> Refinement)
      (Rejection Sampling for Reasoning)
    Reasoning Data (Long-CoT SFT & RL)
      (High-Quality Long-CoT)
      (QA + Ground Truth + Reasoning Trajectories)
      (Synthesis & Rejection Sampling w/ Reward Model)
```

**Explanation:** A mindmap is used here to show the hierarchical breakdown of the data sources and types used for pre-training, instruction tuning (SFT), and reasoning enhancement (Long-CoT SFT/RL).

---

## Diagram 4: Evaluation Areas and Key Performance Aspects

This diagram summarizes the major areas where Kimi-VL was evaluated and highlights its standout performance characteristics.

```mermaid
---
title: "Evaluation Areas and Key Performance Aspects"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'graph': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Monospace',
    'themeVariables': {
      'primaryColor': '#BEF',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#EE2',
      'tertiaryColor': '#fff',
      'stroke':'#3323',
      'stroke-width': '0.5px'
    }
  }
}%%
graph TD
    A[Kimi-VL Evaluation] --> B(Comparison to SoTA Models);
    B --> C{Key Findings};
    C --> C1["Competitive/Superior vs Efficient VLMs (Qwen, Gemma, DeepSeek-VL2)"];
    C --> C2["Outperforms GPT-4o in specific domains"];
    C --> C3["Parameter Efficient (2.8B Activated)"];

    A --> D(Performance Domains);
    D --> D1[College-level Academic];
    D --> D2[General Visual Ability];
    D --> D3[Multi-image Reasoning];
    D --> D4[Mathematical Reasoning];
    D --> D5[Document Understanding & OCR];
    D --> D6[Agent Grounding & Interaction];
    D --> D7[Long Document & Video Understanding];
    D --> D8[Egocentric & Fine-grained Video];

    A --> E(Kimi-VL-Thinking Evaluation);
    E --> F["Significant Gains over Kimi-VL"];
    E --> G["Competitive vs Larger Thinking/Non-Thinking Models"];
    E --> H["Strong Test-Time Scaling"];

    style C1 fill:#dff,stroke:#333
    style C2 fill:#dff,stroke:#333
    style D5 fill:#fdf,stroke:#333
    style D6 fill:#fdf,stroke:#333
    style D7 fill:#fdf,stroke:#333
    style E fill:#cfc,stroke:#333
```

**Explanation:** This flowchart (`graph TD`) categorizes the evaluation approach, summarizing the comparative findings and highlighting the specific domains tested, along with the separate evaluation of the Kimi-VL-Thinking variant.

---

## Diagram 5: Infrastructure Overview

This mindmap provides a high-level view of the storage and parallelism strategies used for training Kimi-VL.

```mermaid
---
title: "Infrastructure Overview"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%{
  init: {
    'themeVariables': {
      'fontSize': '12px',
      'fontFamily': 'Monospace'
    }
  }
}%%
mindmap
  root((Infrastructure))
    Storage
      (S3-Compatible Object Storage)
      Data Loading System
        (On-the-fly Processing: Shuffle, Mix, Tokenize, Pack)
        (Random Augmentation)
        (Reproducibility Control)
        (High Performance Caching)
        (Centralized Data Platform)
    Parallelism
      4D Strategy
        (Data Parallelism - DP)
        (Expert Parallelism - EP)
        (Pipeline Parallelism - PP)
        (Context Parallelism - CP)
      Other Optimizations
        (ZeRO1)
        (Selective Checkpointing Activation)
```

**Explanation:** This mindmap structure effectively outlines the two main aspects of the infrastructure – Storage and Parallelism – detailing the key features and techniques employed within each.

----


## Diagram 6: Kimi-VL-Thinking Enhancement Pipeline

This diagram focuses specifically on the stages that differentiate Kimi-VL-Thinking from the base Kimi-VL model.

```mermaid
---
title: "Kimi-VL-Thinking Enhancement Pipeline"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'graph': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Monospace',
    'themeVariables': {
      'primaryColor': '#BEF',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#EE2',
      'tertiaryColor': '#fff',
      'stroke':'#3323',
      'stroke-width': '0.5px'
    }
  }
}%%
graph TD
    subgraph Base_Model
        direction LR
        KimiVL["Kimi-VL<br/>(Post Joint SFT)"]
    end

    subgraph Thinking_Enhancement
        direction TB
        A["Input:<br/>Reasoning QA Data"] --> B{"Generate Reasoning Trajectories"}
        B -- Kimi k1.5 + Prompts --> C("Candidate Trajectories")
        C --> D{Filter & Select}
        D -- Reward Model / Rules --> E["High-Quality Long-CoT Data"]
        E --> F("Stage 1:<br/>Long-CoT SFT")
        F -- Planning, Eval, Reflect, Explore Patterns --> G{"Model Primed for Reasoning"}
        G --> H("Stage 2:<br/>Reinforcement Learning")
        H -- Online Policy Mirror Descent --> I{"Policy Refinement"}
        I -- "Reward (Correctness) & Penalty (Length)" --> J{"Iterative Optimization"}
        J -- Curriculum/Prioritized Sampling --> K["Kimi-VL-Thinking"]
    end

    KimiVL --> A

    style K fill:#cfc,stroke:#333,stroke-width:2px
    
```

**Explanation:** This flowchart details the process of creating the reasoning data (using Kimi k1.5 and filtering) and the subsequent Long-CoT SFT and Reinforcement Learning stages used to produce the Kimi-VL-Thinking variant.

---

## Diagram 7: Evaluation Benchmark Categories

This diagram groups the various benchmarks mentioned in the report according to the capability they primarily assess.

```mermaid
---
title: "Evaluation Benchmark Categories"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'graph': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Monospace',
    'themeVariables': {
      'primaryColor': '#BEF',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#EE2',
      'tertiaryColor': '#fff',
      'stroke':'#3323',
      'stroke-width': '0.5px'
    }
  }
}%%
graph LR
    Eval[Evaluation Benchmarks] --> Cat1(College-level Academic)
    Cat1 --> B1_1[MMMU]
    Cat1 --> B1_2[VideoMMMU]
    Cat1 --> B1_3[MMVU]

    Eval --> Cat2(General Visual Ability)
    Cat2 --> B2_1[MMBench-EN-v1.1]
    Cat2 --> B2_2[MMStar]
    Cat2 --> B2_3[MMVet]
    Cat2 --> B2_4[RealWorldQA]
    Cat2 --> B2_5[AI2D]

    Eval --> Cat3(Multi-image Reasoning)
    Cat3 --> B3_1[BLINK]

    Eval --> Cat4(Mathematical Reasoning)
    Cat4 --> B4_1[MathVista]
    Cat4 --> B4_2[MathVision]

    Eval --> Cat5(Document Understanding & OCR)
    Cat5 --> B5_1[InfoVQA]
    Cat5 --> B5_2[OCRBench]
    Cat5 --> B5_3[MMLongBench-Doc]

    Eval --> Cat6(Agent Grounding & Interaction)
    Cat6 --> B6_1[ScreenSpot-V2]
    Cat6 --> B6_2[ScreenSpot-Pro]
    Cat6 --> B6_3[OSWorld]
    Cat6 --> B6_4[WindowsAgentArena]

    Eval --> Cat7(Video Understanding)
    Cat7 --> B7_1[Video-MME]
    Cat7 --> B7_2[MLVU]
    Cat7 --> B7_3[LongVideoBench]
    Cat7 --> B7_4[EgoSchema]
    Cat7 --> B7_5[VSI-Bench]
    Cat7 --> B7_6[TOMATO]

    style Cat1 fill:#lightblue
    style Cat2 fill:#lightgreen
    style Cat3 fill:#lightcoral
    style Cat4 fill:#lightgoldenrodyellow
    style Cat5 fill:#lightpink
    style Cat6 fill:#lightsalmon
    style Cat7 fill:#lightseagreen
    
```


**Explanation:** This uses a tree structure (`graph TD`) to categorize the benchmarks under the main capability areas evaluated in the paper, providing a clearer overview of the testing scope.

---

### Summary of Key Innovations in Kimi-VL:

Beyond the diagrams, here's a concise summary of the core innovations presented:

1.  **Efficient MoE Architecture:** Leverages a Mixture-of-Experts language model (Moonlight) for vision-language tasks, achieving strong performance with significantly fewer *activated* parameters (2.8B) compared to dense models of similar capability.
2.  **Native-Resolution Vision Encoder (MoonViT):** Processes images at their original resolutions without complex patching/stitching, using techniques like NaViT's packing and 2D RoPE for better handling of varying aspect ratios and high resolutions efficiently.
3.  **Integrated Long-Context (128K):** Extends context handling to 128K tokens across both text and multimodal inputs (long documents, long videos) during pre-training stages.
4.  **Long-Thinking Enhancement (Kimi-VL-Thinking):** Introduces a method combining Long-CoT SFT and Reinforcement Learning to explicitly improve multi-step reasoning capabilities on top of the base VLM, allowing the model to "think longer" for complex problems.
5.  **Enhanced Muon Optimizer:** Develops and utilizes a modified Muon optimizer with distributed implementation for efficient training across all model components.
6.  **Comprehensive Data Strategy:** Employs a multi-stage training process with carefully curated and synthesized data across diverse categories (caption, interleaving, OCR, knowledge, agent, video, reasoning) to build robust and varied capabilities.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---