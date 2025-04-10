---
created: 2025-04-09 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://ai.meta.com/blog/llama-4-multimodal-intelligence/"
---



# The Llama 4 herd - The beginning of a new era of natively multimodal AI innovation - A Diagrammatic Guide 
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


---

## Llama 4 Model Family Overview

This diagram provides a high-level view of the new Llama 4 models and their relationship, highlighting the "teacher-student" dynamic with Behemoth.

```mermaid
---
title: "Llama 4 Model Family Overview"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
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
    subgraph Llama_4_Family["Llama 4 Model Family"]
        direction LR
        B(Llama 4 Behemoth):::teacher --> S(Llama 4 Scout):::student
        B --> M(Llama 4 Maverick):::student

        subgraph Released_Models ["Released Models<br/>(Open Weight)"]
            S[("Llama 4 Scout<br/>17B Active Params<br/>16 Experts<br/>10M Context<br/>Multimodal")]:::released
            M[("Llama 4 Maverick<br/>17B Active Params<br/>128 Experts<br/>~400B Total Params<br/>Multimodal")]:::released
        end

        subgraph Teacher_Model ["Teacher Model<br/>(Training)"]
            B[("Llama 4 Behemoth<br/>288B Active Params<br/>16 Experts<br/>~2T Total Params<br/>Multimodal")]:::teacher
        end
    end

    classDef student fill:#D5E8D4,stroke:#82B366,stroke-width:2px
    classDef teacher fill:#F8CECC,stroke:#B85450,stroke-width:2px
    classDef released fill:#DAE8FC,stroke:#6C8EBF,stroke-width:2px

    click S "https://llama.com/llama-downloads/" "Download Scout"
    click M "https://llama.com/llama-downloads/" "Download Maverick"

    %% note for B "Used for Co-distillation<br/>(Not yet released)"
    %% note for S "Best-in-class Size/Performance<br/>Industry-leading Context Length"
    %% note for M "Best Multimodal in Class<br/>Comparable to DeepSeek v3<br/>Beats GPT-4o/Gemini 2.0 Flash"
    
```


**Explanation:** This graph shows the three main models in the Llama 4 suite. Behemoth is presented as the large "teacher" model, which influenced the training of the smaller, released "student" models, Scout and Maverick. Key specifications and positioning for each model are included.

----

## Mixture-of-Experts (MoE) Architecture (Llama 4 Maverick Example)

This diagram illustrates the core concept of the MoE architecture as implemented in Llama 4 Maverick.

```mermaid
---
title: "Mixture-of-Experts (MoE) Architecture (Llama 4 Maverick Example)"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
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
    subgraph MoE_Architecture["Mixture-of-Experts (MoE) - Llama 4 Maverick"]
        Input[Input Token] --> Router{Routing Gate}

        Router --> SharedExpert("Shared Expert<br/>(Always Active)")
        Router -- Selects 1 --> RoutedExperts["Routed Experts<br/>(Pool of 128)"]

        subgraph Experts
            direction LR
            RoutedExperts --> RE1(Expert 1)
            RoutedExperts --> RE2(Expert 2)
            RoutedExperts --> RE_dots(...)
            RoutedExperts --> RE128(Expert 128)
        end

        SharedExpert --> Combine{Combine Outputs}
        RoutedExperts --> Combine

        Combine --> Output[Final Layer Output]

        %% note for Router "Activates only a subset of parameters per token"
        %% note for RoutedExperts "128 routed + 1 shared = 129 potential experts per MoE layer<br/>Only 1 routed + 1 shared active per token"
        %% note for Combine "Weighted combination of expert outputs"
    end

    subgraph Model_Stats["Llama 4 Maverick Stats"]
        P_Active("Active Parameters: 17B")
        P_Total("Total Parameters: ~400B")
        E_Count("Experts per MoE Layer: 128 Routed + 1 Shared")
        Efficiency("Compute Efficient Training & Inference")
        Deployment("Fits on single NVIDIA H100 Host")
    end

    classDef modelStats fill:#FFF2CC,stroke:#D6B656
    class P_Active,P_Total,E_Count,Efficiency,Deployment modelStats

    classDef process fill:#DAE8FC,stroke:#6C8EBF
    class Input,Router,Combine,Output process
    classDef expert fill:#D5E8D4,stroke:#82B366
    class SharedExpert,RE1,RE2,RE_dots,RE128 expert
    
```


**Explanation:** This flowchart depicts how a token is processed in an MoE layer. The router sends the token to a mandatory shared expert and selects one additional specialized expert from a large pool. Only these selected experts' parameters are active, leading to computational efficiency despite the large total parameter count. Maverick's specific stats related to MoE are noted.

----

## Llama 4 Pre-training Innovations

This diagram highlights the key techniques and data used during the pre-training phase.

```mermaid
---
title: "Llama 4 Pre-training Innovations"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
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
flowchart TD
    subgraph PreTraining ["Llama 4 Pre-training Pipeline"]
        A[Start Pre-training] --> B{MoE Architecture}
        B --> C["Native Multimodality<br/>(Early Fusion)"]
        C --> D["Improved Vision Encoder"]
        D -- Based on --> MetaCLIP
        D -- Adapted with --> FrozenLlama[Frozen Llama Model]
        C --> E[MetaP Hyperparameter Tuning]
        E --> F["Multilingual Data<br/>(200+ langs, >1B tokens for 100+)"]
        F --> G["Efficient Training<br/>(FP8 Precision)"]
        G -- Achieved --> TFLOPS["390 TFLOPs/GPU on Behemoth"]
        F --> H["Large & Diverse Dataset<br/>(>30 Trillion Tokens)"]
        H -- Includes --> TextData[Text]
        H -- Includes --> ImageData[Images]
        H -- Includes --> VideoData[Video Frames]
        G & H --> I{Core Pre-training Complete}
        I --> J[Mid-Training Phase]
        J -- Includes --> LC[Long Context Extension]
        LC -- Using --> SpecializedData[Specialized Datasets]
        J --> K[Enhanced Core Capabilities]
        K & LC -- Enables --> ContextLength["10M Context<br/>(Scout)"]
        K --> L[End Pre-training]
    end

    classDef innovation fill:#E1D5E7,stroke:#9673A6
    class B,C,D,E,F,G,LC,ContextLength innovation
    classDef data fill:#FFF2CC,stroke:#D6B656
    class H,TextData,ImageData,VideoData,SpecializedData data
    
```


**Explanation:** This flowchart outlines the crucial steps and innovations in the Llama 4 pre-training process. It covers the adoption of MoE, native multimodality via early fusion, vision encoder improvements, MetaP tuning, extensive multilingual data, efficient FP8 training, the vast dataset size, and the mid-training phase for enhancing capabilities like long context.

---

## Llama 4 Maverick Post-training Pipeline

This diagram details the specific supervised fine-tuning (SFT), reinforcement learning (RL), and direct preference optimization (DPO) stages used for Llama 4 Maverick.

```mermaid
---
title: "Llama 4 Maverick Post-training Pipeline"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
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
flowchart TD
    subgraph PostTrainingMaverick["Llama 4 Maverick Post-training"]
        Start[Pre-trained Llama 4 Maverick] --> SFT{Lightweight SFT}
        SFT -- Data Prep --> FilterEasy["Filter >50% Easy Data<br/>(Llama Judge)"]
        FilterEasy --> SFT_Run[Run SFT on Harder Data]

        SFT_Run --> RL{"Online Reinforcement Learning<br/>(RL)"}
        RL -- Strategy --> ContinuousRL[Continuous Online RL Strategy]
        ContinuousRL -- Focus --> SelectHard[Carefully Select Harder Prompts]
        ContinuousRL -- Loop --> TrainRL[Train RL Model] --> FilterMediumHard[Filter/Retain Medium-Hard Prompts] --> TrainRL
        RL --> RL_Output["Step Change in Performance<br/>(Reasoning, Coding, Math)"]

        RL_Output --> DPO{Lightweight DPO}
        DPO -- Goal --> HandleCorners["Handle Corner Cases<br/>(Response Quality)"]
        DPO --> FinalModel[Final Llama 4 Maverick]

        FinalModel -- Achieves --> Balance[Balance:<br/>Intelligence vs Conversation]
        FinalModel -- Achieves --> Capabilities[SOTA Intelligence & Image Understanding]

        %% note for SFT "Avoids over-constraining model for RL exploration"
        %% note for ContinuousRL "Alternates training & data filtering for compute/accuracy"
        %% note for DPO "Refines model for quality without sacrificing intelligence"
    end

    classDef stage fill:#DAE8FC,stroke:#6C8EBF
    class Start,SFT,RL,DPO,FinalModel stage
    classDef process fill:#D5E8D4,stroke:#82B366
    class FilterEasy,SFT_Run,ContinuousRL,SelectHard,TrainRL,FilterMediumHard,RL_Output,HandleCorners process
    classDef result fill:#F8CECC,stroke:#B85450
    class Balance,Capabilities result
    
```


**Explanation:** This flowchart illustrates the refined post-training pipeline for Llama 4 Maverick: lightweight SFT on harder data, followed by a continuous online RL phase focusing on difficult prompts, and concluding with lightweight DPO for quality refinement. This approach aims to balance intelligence and conversational ability effectively.

----

## Llama 4 Scout Long Context Architecture (iRoPE)

This diagram conceptualizes the iRoPE architecture enabling Llama 4 Scout's 10M context window.

```mermaid
---
title: "Llama 4 Scout Long Context Architecture (iRoPE)"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
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
    subgraph iRoPE_Architecture["Llama 4 Scout - iRoPE for Long Context<br/>(10M Tokens)"]
        InputSeq["Input Sequence<br/>(Up to 10M Tokens)"] --> Arch{iRoPE Architecture}

        subgraph Core_Components["Core Components"]
            Arch --> Interleaved["Interleaved Attention Layers"]
            Interleaved -- Lacks --> NoPE["No Positional Embeddings<br/>(in some layers)"]
            Arch --> RoPE["Rotary Position Embeddings (RoPE)<br/>(in most layers)"]
            Arch --> Scaling["Inference Time Temperature Scaling<br/>of Attention"]
        end

        Scaling & Interleaved & RoPE --> Output["Output with Length Generalization"]

        %% note for Arch "'i' = Interleaved / Infinite Context Goal<br>'RoPE' = Rotary Position Embeddings";
        %% note for Interleaved "Key innovation for handling very long sequences";
        %% note for Scaling "Enhances length generalization during inference";
        %% note for Output "Enables tasks like multi-doc summarization,<br>reasoning over vast codebases";

        InitialTraining["Pre/Post-trained up to 256K Context"] --> Arch
        %% note for InitialTraining "Base model trained with significant context length"

    end

    classDef component fill:#D5E8D4,stroke:#82B366
    class Interleaved,NoPE,RoPE,Scaling component
    classDef concept fill:#E1D5E7,stroke:#9673A6
    class Arch,Output,InitialTraining concept
    
```


**Explanation:** This diagram breaks down the iRoPE architecture used in Llama 4 Scout. It highlights the key components: interleaved attention layers (some without positional embeddings), the use of RoPE in most layers, and inference-time temperature scaling. These elements, combined with initial training on a large context, enable the model's advanced length generalization up to 10 million tokens.

----


## Co-distillation Process (Behemoth to Maverick)

This diagram illustrates how Llama 4 Behemoth was used as a teacher model to improve Llama 4 Maverick through co-distillation.

```mermaid
---
title: "Co-distillation Process (Behemoth to Maverick)"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
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
flowchart LR
    subgraph CoDistillation ["Co-distillation: Behemoth -> Maverick"]
        Teacher[("Llama 4 Behemoth<br/>(Teacher Model - 2T Params)")]:::teacher --> ForwardPass1{Forward Pass on<br/>Existing Training Data}
        ForwardPass1 --> Targets1[Compute Soft/Hard Targets]

        Student[("Llama 4 Maverick<br/>(Student Model - 17B Active)")]:::student --> TrainingLoop{Pre-training Loop}

        Targets1 --> Loss{Novel Distillation Loss Function}
        Loss -- Dynamically Weights --> SoftHard["Soft & Hard Targets"]
        Loss --> TrainingLoop

        NewData["Additional New Data"] --> ForwardPass2{"Forward Pass on New Data<br/>(Resource Intensive)"}
        ForwardPass2 --> Targets2[Create Distillation Targets]
        Targets2 --> TrainingLoop

        TrainingLoop --> ImprovedStudent["Substantially Improved<br/>Llama 4 Maverick"]

        %% note for Loss "Balances learning from teacher outputs (soft) <br/>and ground truth (hard)"
        %% note for ForwardPass1 "Amortizes cost by using existing data passes"
        %% note for ForwardPass2 "Needed specifically for new data incorporated later"
    end

    classDef teacher fill:#F8CECC,stroke:#B85450,stroke-width:2px
    classDef student fill:#D5E8D4,stroke:#82B366,stroke-width:2px
    classDef process fill:#DAE8FC,stroke:#6C8EBF
    class ForwardPass1,Targets1,Loss,SoftHard,TrainingLoop,ForwardPass2,Targets2,ImprovedStudent process
    
```


**Explanation:** This flowchart shows the co-distillation process where the larger Behemoth model acts as a teacher for Maverick. Targets (outputs) from Behemoth on training data are used alongside ground truth labels, guided by a dynamic loss function, to improve Maverick's performance during its pre-training. This leverages the power of the larger model efficiently.

----

## Llama 4 Safety and Mitigation Strategy

This diagram outlines the multi-layered approach to safety integrated into Llama 4 development.

```mermaid
---
title: "Llama 4 Safety and Mitigation Strategy"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
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
    subgraph SafetyStrategy ["Llama 4 Safety & Mitigation Strategy"]
        direction TB
        A["Goal:<br/>Helpful, Useful, Safe Models"] --> B{Layered Approach}

        subgraph DevelopmentMitigations["Development Mitigations"]
            direction TB
            B --> C[Pre-training]
            C --> C1[Data Filtering]
            C --> C2[Other Data Mitigations]

            B --> D["Post-training"]
            D --> D1["Policy Conformance Techniques"]
            D --> D2["Safety Data Integration<br/>(at each stage)"]
        end

        subgraph SystemLevelTools["System-Level Tools<br/>(Open Source)"]
            direction TB
            B --> E[Tunable System Safeguards]
            E --> F[Llama Guard]
            F -- Detects --> FG["Harmful Input/Output<br/>(Policy-Based)"]
            E --> G[Prompt Guard]
            G -- Detects --> GG["Malicious Prompts<br/>(Jailbreaks, Injections)"]
            E --> H[CyberSecEval]
            H -- Assesses --> HG["Generative AI Cybersecurity Risks"]
            note_for_E["Allows developer customization for specific needs"]
        end

        subgraph EvaluationRedTeaming["Evaluation & Red Teaming"]
            direction TB
            B --> I["Systematic Testing"]
            I --> I1["Wide Range of Scenarios/Use Cases"]
            I --> I2["Data Fed Back into Post-training"]

            B --> J["Adversarial Dynamic Probing"]
            J --> J1["Automated & Manual Testing"]

            B --> K["GOAT<br/>(Generative Offensive Agent Testing)"]
            K --> K1["Simulates Multi-Turn Adversarial Actors"]
            K --> K2["Increases Testing Coverage"]
            K --> K3["Frees Human Red Teams for Novel Areas"]
        end

        B --> L["Bias Reduction Efforts"]
        L --> SeeBiasDiagram["See Separate Bias Diagram"]

        A --> M["Overall Result:<br/>Empowering Developers for Safe Applications"]
    end

    classDef layer fill:#DAE8FC,stroke:#6C8EBF
    class C,D,E,I,J,K,L layer
    classDef tool fill:#D5E8D4,stroke:#82B366
    class F,G,H,K tool
    classDef goal fill:#F8CECC,stroke:#B85450
    class A,M goal
    
```


**Explanation:** This diagram illustrates the comprehensive safety strategy for Llama 4. It encompasses mitigations built-in during pre-training and post-training, open-source system-level tools (Llama Guard, Prompt Guard, CyberSecEval) for developers, and rigorous evaluation methods including automated testing with GOAT and traditional red teaming.

---

## Bias Reduction Efforts and Progress

This diagram summarizes the efforts made to reduce bias in Llama 4 compared to Llama 3.

```mermaid
---
title: "Bias Reduction Efforts and Progress"
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
    subgraph BiasReduction ["Llama 4 Bias Reduction Efforts"]
        A["Known Issue:<br/>LLMs Tend to Lean Left<br/>(Training Data Bias)"] --> B["Goal:<br/>Remove Bias, Understand/Articulate Multiple Sides"]

        B --> C[Actions Taken]
        C --> C1[Improve Responsiveness]
        C --> C2[Reduce Judgmental Responses]
        C --> C3[Avoid Favoring Specific Viewpoints]

        C --> D["Results & Progress<br/>(Llama 4 vs Llama 3.3)"]
        D -- Refusals --> D1["Refuses Less on Debated Topics<br/>(7% -> <2%)"]
        D -- Balance --> D2["More Balanced Refusals<br/>(Unequal Refusal <1%)"]
        D -- Lean --> D3["Reduced Strong Political Lean<br/>(Rate ~Grok, Half of Llama 3.3)"]

        D --> E[Status:<b/r>Significant Progress Made]
        E --> F[Future:<b/r>Continued Work to Eliminate Bias]

        %% note for D3 "Measured on a contentious set of political/social topics"
    end

    classDef goal fill:#F8CECC,stroke:#B85450
    class B,E,F goal
    classDef action fill:#DAE8FC,stroke:#6C8EBF
    class C,C1,C2,C3 action
    classDef result fill:#D5E8D4,stroke:#82B366
    class D,D1,D2,D3 result
    
```


**Explanation:** This flowchart outlines the acknowledged problem of bias in LLMs, the goal of reducing it in Llama 4, the actions taken, and the measured improvements compared to Llama 3.3, particularly in reducing refusals and political lean on contentious topics. It also acknowledges that this is ongoing work.

---

## Llama 4 Ecosystem and Availability

This diagram shows how developers and users can access and utilize the new Llama 4 models.

```mermaid
---
title: "Llama 4 Ecosystem and Availability"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: dark
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
mindmap
  root((Llama 4 Ecosystem & Availability))
    Models
      Llama 4 Scout (Released)
      Llama 4 Maverick (Released)
      Llama 4 Behemoth (In Training)
    Access Points
      Downloads
        llama.com
        Hugging Face
      Cloud & Data Platforms (Coming Soon)
        AWS
        Google Cloud
        Microsoft Azure
        Databricks
        Snowflake
        Oracle Cloud
        Nebius
        Scaleway
        Cloudflare
        IBM Watsonx
      Edge Silicon (Coming Soon)
        AMD
        Arm
        Intel
        Mediatek
        Qualcomm
      Service Integrators (Coming Soon)
        Accenture
        Deloitte
        Infosys
        PwC
        Wipro
      Tools & Libraries
        ollama
        vLLM
        Fireworks AI
        Groq
        Together AI
        Deepinfra
        TensorWave
        CentML
        SambaNova
        Cerebras
        Scale AI
        Sarvam AI
    Product Integrations
      Meta AI
        WhatsApp
        Messenger
        Instagram Direct
        Meta.AI Website
    Community & Events
      Open Source Community
      Developer Resources
      LlamaCon (April 29)
      Kaggle
      DeepLearning.AI
    Partnerships
      Acknowledged companies supporting the ecosystem
      
```


**Explanation:** This mind map provides a broad overview of where and how the Llama 4 models can be accessed and integrated. It covers direct downloads, upcoming availability on major cloud platforms and hardware, integration into Meta products, and community resources.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---