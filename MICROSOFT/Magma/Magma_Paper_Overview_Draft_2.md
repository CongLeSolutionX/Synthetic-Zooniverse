---
created: 2025-03-04 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://www.arxiv.org/pdf/2502.13130"
---



# Magma: A Foundation Model for Multimodal AI Agents
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Magma - A Diagrammatic Guide 


### 1. Magma Overview: A Foundation Model for Multimodal AI Agents

```mermaid
---
title: "Magma: A Foundation Model for Multimodal AI Agents by Microsoft"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "graph": { "htmlLabels": false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#f529',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A[Magma] --> B{"Core Capabilities"}
    B --> C["Multimodal Understanding"]
    C --> C1["Verbal Intelligence<br>(VL Understanding)"]
    C --> C2["Spatial-Temporal Intelligence<br>(Plan & Act)"]
    B --> D[Agentic Tasks]
    D --> D1["Digital World<br>(UI Navigation)"]
    D --> D2["Physical World<br>(Robot Manipulation)"]
    A --> E["Pretraining Data"]
    E --> E1["Images, Videos, Robotics Data"]
    E --> E2["SoM for Action Grounding<br>(Images)"]
    E --> E3["ToM for Action Planning<br>(Videos)"]

    classDef detail fill:#f9f5,stroke:#333,stroke-width:2px
    
```

#### Description
This diagram provides a high-level overview of Magma, highlighting its key capabilities in multimodal understanding and agentic tasks across digital and physical environments. It emphasizes the use of SoM and ToM during pretraining to achieve these capabilities.

----

### 2. Bridging the Gap: Set-of-Mark (SoM) for Action Grounding

```mermaid
---
title: "Magma: A Foundation Model for Multimodal AI Agents by Microsoft"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "graph": { "htmlLabels": false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#f529',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A["Set-of-Mark<br>(SoM)"] --> B{Purpose}
    B --> C[Action Grounding in Images]
    C --> C1[Locate Actionable Points/Regions]
    B --> D{Process}
    D --> D1["Input:<br>Image Observation (I), Task, Context (ctx)"]
    D --> D2["Extract Candidate Regions/Points (P)"]
    D --> D3["Overlay Marks (M) on Image -> Marked Image (IM)"]
    D --> D4["Model predicts Marks (omark) and Action (action)"]
    D --> D5["Output:<br>omark = action : mark = π(IM, task, ctx)"]
    A --> E{Examples}
    E --> E1["UI Screenshots<br>(Clickable Buttons)"]
    E --> E2["Robotics Images<br>(Robot Arms)"]
    E --> E3["Human Videos<br>(Hands)"]

    classDef detail fill:#f9f5,stroke:#333,stroke-width:2px

```

#### Description
This diagram explains the Set-of-Mark (SoM) technique used in Magma for action grounding. It details the process from input to output, emphasizing its role in locating actionable elements in images across different domains.

---

### 3. Trace-of-Mark (ToM) for Action Planning

```mermaid
---
title: "Magma: A Foundation Model for Multimodal AI Agents by Microsoft"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "graph": { "htmlLabels": false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#f529',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A["Trace-of-Mark<br>(ToM)"] --> B{Purpose}
    B --> C[Action Planning in Videos]
    C --> C1["Learn Temporal Dynamics & 'Look Ahead'"]
    B --> D{Process}
    D --> D1["Input:<br>Video Observations (I = {I1, ..., It}), Task, Context (ctx)"]
    D --> D2["Extract Marks (M) at time t"]
    D --> D3["Track Mark Positions in Future l Frames -> Traces<br>(T = {Mt+1, ..., Mt+l})"]
    D --> D4["Model predicts Marks (omark), Action (action), and Future Traces (tracet+1:t+l)"]
    D --> D5["Output:<br>omark = action : mark : tracet+1:t+l = π({I1, ..., It−1, IMt }, task, ctx)"]
    A --> E{Benefits}
    E --> E1[Understand Temporal Dynamics]
    E --> E2["Efficient Long-Horizon Prediction<br>(Fewer Tokens)"]
    E --> E3[Leverage Unlabeled Video Data]

    classDef detail fill:#f9f5,stroke:#333,stroke-width:2px
    
```

#### Description
This diagram illustrates the Trace-of-Mark (ToM) technique for action planning. It outlines the process of predicting future trajectories of marked objects in videos, highlighting the benefits for temporal understanding and efficient learning from video data.

----

### 4. Magma Model Architecture

```mermaid
---
title: "Magma: A Foundation Model for Multimodal AI Agents by Microsoft"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "graph": { "htmlLabels": false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#f529',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A[Magma Model] --> B{Input}
    B --> C["Visual Observations<br>(I)"]
    C --> C1["Vision Encoder (V) - ConvNeXt"]
    B --> D["Task Description<br>(Text)"]
    B --> E["Context<br>(ctx)"]
    A --> F{"Processing"}
    F --> G["Vision Encoder (V) encodes Frames to Tokens"]
    F --> H["LLM (Decoder-only) - LLaMA-3-8B"]
    F --> I["Concatenate Visual & Language Tokens"]
    F --> J["Autoregressive Decoding Procedure"]
    J --> J1["ol,∗ t+1 ∼ p(ol t+1|{ol 1, ..., ol t}; V(I), task, ctx)"]
    A --> K{"Output"}
    K --> K1["Tokens (O = {ol 1, · · ·, ol T })"]
    K --> K2["Verbal or Spatial Tokens<br>(l ∈ {verbal, spatial})"]

    classDef detail fill:#f9f5,stroke:#333,stroke-width:2px
    
```

#### Description
This diagram describes the architecture of the Magma model. It details the input modalities, the roles of the Vision Encoder and LLM, and the autoregressive decoding process to generate multimodal outputs.

-----

### 5. Pretraining Data Sources for Magma

```mermaid
---
title: "Magma: A Foundation Model for Multimodal AI Agents by Microsoft"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "graph": { "htmlLabels": false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#f529',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A[Magma Pretraining Data] --> B{Categories}
    B --> C[Robotics Manipulation Data]
    C --> C1["Open-X-Embodiment<br>(OXE)"]
    B --> D[UI Navigation Data]
    D --> D1[SeeClick]
    D --> D2[Vision2UI]
    B --> E[Instructional Videos]
    E --> E1[Epic-Kitchen]
    E --> E2[Ego4d]
    E --> E3[Somethingv2]
    B --> F[Multimodal Understanding Data]
    F --> F1[ShareGPT4V]
    F --> F2["LLaVA-1.5<br>(SFT)"]
    F --> F3[OCR-related Datasets]
    A --> G[Total Samples ~ 39 Million]

    classDef detail fill:#f9f,stroke:#333,stroke-width:2px
    
```

#### Description
This diagram outlines the diverse pretraining datasets used for Magma. It categorizes them into robotics, UI navigation, instructional videos, and multimodal understanding, emphasizing the heterogeneity of the data.

----

### 6. SoM and ToM Generation Process for Videos and Robotics Data

```mermaid
---
title: "Magma: A Foundation Model for Multimodal AI Agents by Microsoft"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "graph": { "htmlLabels": false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#f529',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A["SoM & ToM Generation<br>(Videos/Robotics)"] --> B{Input}
    B --> C["Image Sequence (I = {It, ...Il})"]
    B --> D["Grid Size (s), Motion Thresholds (η, ϵ)"]
    A --> E{Process}
    E --> F["CoTracker (I, s) -> Marks (M = {Mt, ..., Ml})"];
    E --> G["Global Motion Removal (Homography)"]
    E --> H["Trace Classification (Foreground/Background) using ϵ"]
    E --> I["K-Means Clustering (Foreground & Background Traces)"]
    E --> J["SoM (It, {Mf t , Mb t }) on First Frame"]
    A --> K{Output}
    K --> K1["Marked Image Sequence (I)"]
    K --> K2["Foreground Traces (M∗ f )"]

    classDef detail fill:#f9f4,stroke:#333,stroke-width:2px
    
```

#### Description
This diagram details the process of generating SoM and ToM annotations specifically for videos and robotics data. It includes steps for trace extraction using CoTracker, motion removal, trace classification, and clustering.

-----

### 7. Zero-Shot Evaluation Tasks

```mermaid
---
title: "Magma: A Foundation Model for Multimodal AI Agents by Microsoft"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "graph": { "htmlLabels": false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#f529',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A["Zero-Shot Evaluation"] --> B{"Task Categories"}
    B --> C["UI Navigation"]
    C --> C1["ScreenSpot"]
    C --> C2["VisualWebBench"]
    B --> D["Robotic Manipulation"]
    D --> D1["SimplerEnv<br>(Bridge, Google Robot)"]
    B --> E["Multimodal Understanding"]
    E --> E1["VQA<br>(GQA, TextVQA)"]
    E --> E2["Hallucination Benchmark<br>(POPE)"]
    A --> F{"Key Findings"}
    F --> F1["Magma Outperforms General LMMs & Domain-Specific Models"]
    F --> F2["Superior Performance on UI Navigation & Robotics"]
    F --> F3["Resilient to Domain Gap<br>(Real-to-Sim)"]

    classDef detail fill:#f9f4,stroke:#333,stroke-width:2px
    
```

#### Description
This diagram summarizes the zero-shot evaluation tasks used to assess Magma's capabilities. It lists the benchmarks for UI navigation, robotic manipulation, and multimodal understanding, and highlights the key findings of Magma's superior performance.

----

### 8. Ablation Study: Impact of SoM and ToM

```mermaid
---
title: "Magma: A Foundation Model for Multimodal AI Agents by Microsoft"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "graph": { "htmlLabels": false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#f529',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A[Ablation Study] --> B{Focus}
    B --> C[Effect of SoM+ToM Pretraining Techniques]
    B --> D[Effect of Data Mixtures]
    A --> E{Key Observation}
    E --> E1["Combining UI & Robotics Data Alone -> No Gains<br>(Performance Hurt)"]
    E --> E2[SoM+ToM Enables Effective Learning from Heterogeneous Data]
    E --> E3[Highlights Importance of Verbal & Spatial Intelligence]
    A --> F{"Metrics<br>(Examples)"}
    F --> F1["SS-Overall, VWB-Ele-G, VWB-Act-G, SE-Bridge, SE-Google"]

    classDef detail fill:#f9f3,stroke:#333,stroke-width:2px
    
```

#### Description
This diagram explains the ablation study conducted to analyze the impact of SoM and ToM and different data combinations. It emphasizes that SoM and ToM are crucial for Magma to effectively learn from diverse datasets and bridge the gap between verbal and spatial intelligence.

----

### 9. Spatial Reasoning Evaluation

```mermaid
---
title: "Magma: A Foundation Model for Multimodal AI Agents by Microsoft"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "graph": { "htmlLabels": false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#f529',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A[Spatial Reasoning Evaluation] --> B{Benchmarks}
    B --> C["Visual Spatial Reasoning<br>(VSR)"]
    B --> D[BLINK]
    B --> E[SpatialEval]
    A --> F{Key Results}
    F --> F1[Magma Outperforms Existing Approaches on VSR, BLINK, SpatialEval]
    F --> F2[Highlights Improved Spatial Intelligence Learned by Magma]
    F --> F3[SoM/ToM Pretraining Enhances Spatial Reasoning Capabilities]
    A --> G{Examples}
    G --> G1[Spatial Map Maze Navigation]
    G --> G2[Spatial Grid]

    classDef detail fill:#f9f4,stroke:#333,stroke-width:2px
    
```

#### Description
This diagram focuses on the evaluation of Magma's spatial reasoning abilities. It lists the benchmarks used (VSR, BLINK, SpatialEval) and emphasizes the finding that Magma demonstrates improved spatial intelligence due to SoM and ToM pretraining.

-----

### 10. Video Question Answering (QA) Performance

```mermaid
---
title: "Magma: A Foundation Model for Multimodal AI Agents by Microsoft"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "graph": { "htmlLabels": false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#f529',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A[Video QA Performance] --> B{Benchmarks}
    B --> C[IntentQA]
    B --> D[NextQA]
    B --> E[VideoMME]
    B --> F[MVBench]
    A --> G{Key Findings}
    G --> G1[Magma Outperforms SOTA Models with Comparable Parameters]
    G --> G2[Effectiveness of ToM Pretraining for Temporal Dynamics Reasoning]
    G --> G3[Strong Performance Despite Fewer Video Instruction Tuning Data]
    A --> H{Metrics}
    H --> H1["Overall Accuracy, Action Prediction Accuracy, etc."]

    classDef detail fill:#f9f,stroke:#333,stroke-width:2px
    
```

#### Description
This diagram summarizes Magma's performance on video question answering benchmarks. It highlights Magma's competitive results, the impact of ToM on temporal reasoning, and its efficiency even with less video data.

---

### Method / Algorithm Analysis (Magma Pretraining)

```mermaid
---
title: "Magma: A Foundation Model for Multimodal AI Agents by Microsoft"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "graph": { "htmlLabels": false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#f529',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
	A(Magma) --> B{Pretraining Data}
	B --> C(Robotics Data)
	B --> D(UI Navigation Data)
	B --> E(Instructional Videos)
    B --> F(Multimodal Understanding Data)
    A --> G{SoM & ToM Generation}
    G --> H(SoM for Images)
    H --> I(Action Grounding)
    G --> J(ToM for Videos)
    J --> K(Action Planning)
    A --> L{Model Pretraining}
    L --> M(Vision Encoder & LLM)
    L --> N(Joint Training with SoM & ToM)
    A --> O{Evaluation}
    O --> P(Zero-Shot Evaluation)
    P --> Q(UI Navigation)
    P --> R(Robotic Manipulation)
    P --> S(Multimodal Understanding)
    O --> T(Finetuning Evaluation)
    T --> U(UI Navigation)
    T --> V(Robotic Manipulation)
    T --> W(Multimodal Understanding)


    style A fill:#aaf2,stroke:#333,stroke-width:2px
    style B fill:#aaf5,stroke:#333,stroke-width:2px
    style C fill:#aaf5,stroke:#333,stroke-width:2px
    style D fill:#aaf5,stroke:#333,stroke-width:2px
    style E fill:#aaf5,stroke:#333,stroke-width:2px
    style F fill:#aaf5,stroke:#333,stroke-width:2px
    style G fill:#aae2,stroke:#333,stroke-width:2px
    style H fill:#aae2,stroke:#333,stroke-width:2px
    style I fill:#aae2,stroke:#333,stroke-width:2px
    style J fill:#aae2,stroke:#333,stroke-width:2px
    style K fill:#aae2,stroke:#333,stroke-width:2px
    style L fill:#aae5,stroke:#333,stroke-width:2px
    style M fill:#aae5,stroke:#333,stroke-width:2px
    style N fill:#aae5,stroke:#333,stroke-width:2px
    style O fill:#aaf2,stroke:#333,stroke-width:2px
    style P fill:#aaf2,stroke:#333,stroke-width:2px
    style Q fill:#aaf2,stroke:#333,stroke-width:2px
    style R fill:#aaf2,stroke:#333,stroke-width:2px
    style S fill:#aaf2,stroke:#333,stroke-width:2px
    style T fill:#aaf2,stroke:#333,stroke-width:2px
    style U fill:#aaf2,stroke:#333,stroke-width:2px
    style V fill:#aaf2,stroke:#333,stroke-width:2px
    style W fill:#aaf2,stroke:#333,stroke-width:2px

```

#### Description
This diagram provides a flowchart-like summary of the Magma model's pretraining and evaluation methodology. It visually connects the key components: pretraining data, SoM/ToM generation, model pretraining, and different evaluation phases (zero-shot and finetuning) across various tasks. It acts as a consolidated overview of the entire process.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---