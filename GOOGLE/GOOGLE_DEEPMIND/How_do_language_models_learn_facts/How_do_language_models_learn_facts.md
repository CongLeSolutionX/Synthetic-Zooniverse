---
created: 2025-03-29 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2503.21676"
---



# How do language models learn facts? Dynamics, curricula and hallucinations
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## A Diagrammatic Guide 

The diagrams below capture the core findings, mechanisms, and experimental approaches described in the paper summary, using Mermaid syntax to visualize the relationships and processes.


### Diagram 1: Overall Paper Structure & Focus

This diagram provides a high-level overview of the paper's flow and main investigation areas.

```mermaid
---
title: "Overall Paper Structure & Focus"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: default
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TD
    A["Motivation:<br>Understanding LLM Knowledge"] --> B("Methodology:<br>Synthetic Factual Recall Task")
    B --> C("Finding 1:<br>Learning Dynamics - Three Phases")
    C --> D("Mechanism:<br>Attention Circuit Formation during Plateau")
    B --> E("Finding 2:<br>Data Distribution Effects")
    E --> F("Strategy:<br>Data Scheduling / Curricula")
    B --> G("Finding 3:<br>Post-Training Challenges")
    G --> H("Issue 1:<br>Hallucinations")
    G --> I("Issue 2:<br>Fine-tuning Ineffectiveness for New Knowledge")
    I --> J("Mechanism:<br>Feed-forward Memory Corruption")
    F & J --> K("Discussion & Implications")

    style B fill:#ADD8E6,stroke:#333,stroke-width:2px
    style C fill:#90EE90,stroke:#333,stroke-width:2px
    style E fill:#90EE90,stroke:#333,stroke-width:2px
    style G fill:#90EE90,stroke:#333,stroke-width:2px
    
```


---


### Diagram 2: Methodology - Synthetic Biography Task

This diagram outlines the process for generating the synthetic data and measuring knowledge.

```mermaid
---
title: "Methodology - Synthetic Biography Task"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: default
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart LR
    subgraph Data_Generation_Inspired_by_Fig_1["Data Generation<br>(Inspired by Fig 1)"]
        direction TB
        A("Step 1: Define Population") --> B("N Individuals")
        B -- Each has --> C("Unique Name + 6 Attributes")
        D("Step 2: Generate Templates") --> E("25 Templates / Attribute")
        E -- Split --> F(("Train Templates"))
        E -- Split --> G(("Eval Templates"))
        H{"Sample Individual"} --> I{"Sample 1 Train Template / Attribute"}
        I --> J["Fill Templates w/ Info"]
        J --> K["Concatenate Sentences"]
        K --> L["Randomly Permute Order"]
        L --> M(("Training Biography"))
    end

    subgraph Knowledge_Measurement["Knowledge Measurement"]
        direction TB
        M -- Model Predicts --> N["Attribute Tokens<br>(Blue)"]
        N --> O("Calculate Attribute Loss / Accuracy")
        P("Compare to 'No Knowledge Baseline'")
        O --> P
        Q(("Evaluation Biography")) -- Generated using --> G
        Q -- Model Predicts --> N
        P -- Indicates --> R{"Knowledge Acquired?"}
    end

    style F fill:#DCDCDC,stroke:#333
    style G fill:#DCDCDC,stroke:#333
    style M fill:#FFFFED,stroke:#333
    style Q fill:#FFFFED,stroke:#333
    
```

---



### Diagram 3: Knowledge vs. Memorization Distinction

This diagram contrasts the key concepts of knowledge and memorization as defined in the paper.

```mermaid
---
title: "Knowledge vs. Memorization Distinction"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: default
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'graph': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph TD
    subgraph Core_Concepts["Core Concepts"]
        K[Knowledge]
            K --> K1("Abstracted, Internalized Info")
            K --> K2("Flexible Use Across Contexts")
            K --> K3("Enables Generalization")
            K --> K4("Desirable LLM Property")

        M[Memorization]
            M --> M1("Tied to Specific Training Examples")
            M --> M2("Surface-Level Recall")
            M --> M3("Risk of Data Leakage")
            M --> M4("Less Desirable")
    end
    K -.-> LatentSpace[("Knowledge ≈ Memorization<br>in Latent Semantic Space")]
    M -.-> SurfaceLevel[("Memorization ≈ Surface-Level<br>Pattern Matching")]

    style K fill:#CCFFCC,stroke:#060
    style M fill:#FFCCCC,stroke:#600
```


----

### Diagram 4: The Three Phases of Knowledge Acquisition

This diagram illustrates the sequential learning phases observed in the experiments.

```mermaid
---
title: "The Three Phases of Knowledge Acquisition"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: default
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TD
    Start["Start Training"] --> Phase1["Phase 1:<br>Initial Understanding"]
    Phase1 --> Desc1("Learns Generic Attribute Statistics<br>Loss approaches Baseline")
    Desc1 --> Plateau["Phase 2:<br>Performance Plateau"]
    Plateau --> Desc2("Loss ≈ Baseline (No Individual Knowledge)<br>Accuracy ≈ 0")
    Desc2 --> Mechanism["*Attention Circuits Form*"]
    Mechanism --> Phase3["Phase 3:<br>Knowledge Emergence"]
    Phase3 --> Desc3("Learns Individual-Specific Associations <br>Loss < Baseline<br>Accuracy Increases")
    Desc3 --> End["End Training"]

    Baseline["No Knowledge Baseline<br>(Entropy of Attribute Values)"] -.-> Phase1
    Baseline -.-> Plateau
    Baseline -.-> Phase3

    style Baseline fill:#ee3,stroke:#333,stroke-width:2px,color:#333
    style Mechanism fill:#ADD8E6,stroke:#333
    
```



----

### Diagram 5: Attention Circuit Formation During Plateau

This diagram focuses on the mechanistic explanation for the plateau phase.

```mermaid
---
title: "Attention Circuit Formation During Plateau"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: default
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'graph': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph TD
    P["Phase 2: Performance Plateau"] --> AC{"Attention Circuits Develop"}

    subgraph Recall_Mechanism["Recall Mechanism<br>(Simplified)"]
        direction LR
        Name[Name Tokens] --> Grouping["Early Attn: Grouping Circuit"]
        Grouping --> NameRep["Name Representation"]
        NameRep -- Query --> MLPs["MLPs:<br>Associative Memory<br>(Key-Value)"]
        AttrType["Attribute Type Info"] -- Condition --> Extraction["Final Attn:<br>Extraction Circuit"]
        MLPs -- Value --> Extraction
        Extraction --> Prediction
    end

    AC -- Enables --> EfficientBP["Efficient Error Backpropagation<br>(Attribute Value -> Name Tokens)"]
    AC -- Supported By --> PatchingExp["Attention Patching Experiment\n(Post-plateau patterns bypass plateau)"]
    AC -- Supported By --> PatternAnalysis["Attention Pattern Analysis<br>(Extraction circuit attention increases during plateau)"]

    style P fill:#FFFACD,stroke:#FFA500
    style AC fill:#ADD8E6,stroke:#00008B
```

----

### Diagram 6: Data Distribution Effects and Trade-off

This diagram shows how data imbalance impacts learning dynamics and the resulting trade-off.

```mermaid
---
title: "Data Distribution Effects and Trade-off"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: default
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'graph': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph TD
    DataDist["Data Distribution Properties"] --> Imbalance["Imbalance<br>(e.g., Inverse Power Law α > 0)"]
    DataDist --> Uniform["Uniform<br>(α = 0)"]

    Imbalance -- Affects Plateau --> PlateauI["Shorter Plateau Phase"]
    Imbalance -- Affects Knowledge Acq. --> KnowI["Slower Knowledge Acquisition"]

    Uniform -- Affects Plateau --> PlateauU["Longer Plateau Phase"]
    Uniform -- Affects Knowledge Acq. --> KnowU["Faster Knowledge Acquisition"]

    subgraph TradeOff
        direction LR
        PlateauI & KnowI --> T1["Trade-off"]
        PlateauU & KnowU --> T1
        T1 --> Optimal["Optimal *Static* Distribution Depends On:<br>- Training Time Budget<br>- Population Size"]
    end

    T1 -- Leads to --> Scheduler["Solution:<br>Data Scheduler <br>(e.g., Warm-up)"]
    Scheduler --> Benefit["Adapts distribution:<br>1. Imbalanced early (short plateau)<br>2. Uniform later (fast acquisition)"]

    style Imbalance fill:#FFEBCC
    style Uniform fill:#E6F3FF
    style Scheduler fill:#CCFFCC
```

----

### Diagram 7: Post-Training: Hallucinations & Fine-tuning Issues

This diagram illustrates the challenges encountered when trying to update knowledge post-training.

```mermaid
---
title: "Post-Training: Hallucinations & Fine-tuning Issues"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: default
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'graph': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph TD
    subgraph Post_Training_Challenges_Hallucinations_Issue
        KA[Phase 3: Knowledge Acquisition] --> Hallucinations["Hallucinations Emerge"];
        Hallucinations --> HDesc["Overconfident Predictions\non *Unseen* Individuals"];
        Hallucinations --> HDetect["Lower Confidence vs. Known Data (Detectable Gap)"];
    end

    subgraph Post_Training_Challenges_FineTuningChallenges
        FTNew["Fine-tuning on *New* Individuals"] --> InitialDrop["Rapid Performance Drop (on Pre-training Data)"];
        InitialDrop --> CatastrophicForgetting["Catastrophic Forgetting"];
        FTNew --> SlowLearning["Slow Acquisition of New Knowledge"];
        CatastrophicForgetting -- Likely Cause --> MemCorruption["Feed-forward Memory Corruption\n(MLP Key-Value Interference)"];
        CatastrophicForgetting -- Partially Mitigated By --> Replay["Adding Replay of Pre-training Data"];
    end

    subgraph Contrast
        FTOld["Fine-tuning on *Existing* Individuals"] --> Effective["Effective - No Major Drop"];
    end

    Hallucinations -- Hinders --> FTNew;

    %% style InitialDrop fill:#FFCCCC, stroke:#A00
    %% style SlowLearning fill:#FFDDCC, stroke:#A50
    %% style Effective fill:#CCFFCC, stroke:#060
    
```


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---