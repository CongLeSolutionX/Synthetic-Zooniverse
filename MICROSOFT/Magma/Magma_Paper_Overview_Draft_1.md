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

Below are a collection of diagrams and illustrations using Mermaid syntax to visually represent the core concepts and complexities of the paper.

```mermaid
---
title: "Magma: A Foundation Model for Multimodal AI Agents by Microsoft"
config:
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
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
mindmap
  root((Magma: Multimodal AI Agent))
    Concept((Core Concept: Foundation Model for Multimodal AI Agents))
      Central_Idea(Magma bridges verbal and spatial intelligence for agentic tasks in digital and physical worlds.)
      Capabilities(Capabilities)
        Multimodal_Understanding(Multimodal Understanding: Semantic, spatial, and temporal understanding of diverse inputs.)
        Action_Prediction(Multimodal Action Prediction: Breaking down tasks into executable action sequences.)
        Agentic_Tasks(Agentic Tasks: UI navigation, robotic manipulation, and multimodal understanding.)
      Novelty(Novelty)
        First_Foundation_Model(First foundation model for multimodal AI agents with spatial-temporal reasoning.)
        SoM_ToM["SoM_ToM(Set-of-Mark (SoM) and Trace-of-Mark (ToM) for enhanced spatial-temporal intelligence.)"]
        Heterogeneous_Data(Pretrained on large heterogeneous datasets: VL, UI, robotics, instructional videos.)
        SOTA_Performance(Achieves new SOTA on UI navigation and robotic manipulation.)
    Challenges((Challenges & Solutions))
      Problem_1(Problem 1: Bridging the gap between verbal understanding and spatial action.)
        Solution_1(Solution: Surrogate tasks - Action Grounding and Action Planning using SoM & ToM.)
      Problem_2(Problem 2: Limited Vision-Language-Action Data.)
        Solution_2(Solution: Leverage unlabeled video data and instructional videos using ToM.)
    Methodology((Methodology: SoM and ToM))
      Set_of_Mark["Set_of_Mark(Set-of-Mark (SoM))"]
        Action_Grounding(Action Grounding: Locating actionable points/regions in images.)
        Marked_Image(Marked Image Input: Overlaying marks on candidate regions.)
        Tasks(Tasks: UI buttons, robot arms, actionable objects.)
      Trace_of_Mark["Trace_of_Mark(Trace-of-Mark (ToM))"]
        Action_Planning(Action Planning: Predicting future trajectories of marks in videos.)
        Temporal_Dynamics(Temporal Dynamics: Understanding video dynamics and "looking ahead".)
        Efficient_Temporal_Horizon(Efficient Temporal Horizon: Capturing long horizons with fewer tokens than frame prediction.)
    Architecture((Model Architecture))
      Vision_Encoder(Vision Encoder: ConvNeXt for encoding images and videos of various resolutions.)
      LLM_Decoder["LLM_Decoder(LLM Decoder: Decoder-only LLM (LLaMA-3-8B) for language and action token generation.)"]
      Unified_Interface(Unified Interface: SoM and ToM bridge verbal and action supervisions.)
    Pretraining((Pretraining Strategy))
      Datasets(Datasets)
        Robotics_Data["Robotics_Data(Robotics Manipulation Data: Open-X-Embodiment (OXE). Trajectories for physical interaction.)"]
        UI_Navigation_Data(UI Navigation Data: SeeClick, Vision2UI. Screenshots for digital environment interaction.)
        Instructional_Videos(Instructional Videos: Epic-Kitchen, Ego4d, Somethingv2. Human action and object interaction videos.)
        Multimodal_Understanding_Data(Multimodal Understanding Data: ShareGPT4V, LLaVA-1.5. Image-text pairs for VL understanding.)
      SoM_ToM_Application(SoM & ToM Application)
        SoM_All_Data["SoM_All_Data(SoM for all data types (UI, Robotics, Videos): Unified action grounding.)"]
        ToM_Video_Robotics(ToM for Videos & Robotics: Action planning from dynamic data.)
      Pretraining_Tasks(Pretraining Tasks)
        Action_Grounding_Prediction["Action_Grounding_Prediction(Action Grounding Prediction (SoM): Predict marks for actionable regions in images.)"]
        Trace_Prediction["Trace_Prediction(Trace Prediction (ToM): Predict future trajectories of marks in videos.)"]
        Text_Generation(Text Generation: Standard language modeling and instruction tuning.)
    Evaluation((Evaluation))
      Tasks_Evaluated(Tasks Evaluated)
        UI_Navigation_Tasks(UI Navigation: Mind2Web, AITW. Reasoning and acting in digital interfaces.)
        Robotic_Manipulation_Tasks(Robotic Manipulation: Bridge, LIBERO, WidowX. 3D spatial intelligence for physical tasks.)
        VL_Understanding_Tasks(VL Understanding: GQA, VideoMME, VSR, BLINK. Language grounding in visual content.)
      Key_Results(Key Results)
        SOTA_UI_Robotics(New SOTA on UI Navigation and Robotic Manipulation tasks.)
        Competitive_VL_Performance(Competitive performance on VL tasks, comparable to SOTA LMMs.)
        SoM_ToM_Effectiveness(SoM & ToM effectiveness proven through ablation studies.)
        Spatial_Temporal_Reasoning(Demonstrated strong spatial-temporal reasoning abilities.)
    Contributions((Key Contributions))
      Magma_Model_Proposal(Magma Model Proposal: First foundation model for multimodal agentic tasks with spatial-temporal reasoning.)
      SoM_ToM_Techniques(SoM & ToM Techniques: Enhanced spatial-temporal intelligence for action grounding and planning.)
      Large_Scale_Dataset(Large-Scale Pretraining Dataset: Curated dataset with diverse samples and auto-labeled SoM/ToM.)
      Superior_Performance(Superior Performance: SOTA results on robotic manipulation and UI navigation.)
      Improved_Verbal_Spatial_Intelligence(Improved Verbal & Spatial-Temporal Intelligence: Demonstrated SOTA on BLINK and video QA.)
      
```

### Explanation of the Mindmap Diagram:

*   **Central Node:** `Magma: Multimodal AI Agent` serves as the root, representing the core topic.
*   **Branches:** Main branches extend from the root, covering key aspects like `Concept`, `Challenges & Solutions`, `Methodology`, `Architecture`, `Pretraining`, `Evaluation`, and `Contributions`.
*   **Sub-branches:** Each main branch further breaks down into more specific sub-topics, providing a hierarchical view of Magma's key features and details.
*   **Keywords and Phrases:** Nodes are labeled with concise keywords and phrases extracted directly from the paper, making it easy to grasp the essential information at a glance.
*   **Color Coding (Optional):** You can customize the mindmap with colors for different branches to further enhance visual organization if needed.

This mindmap is designed to provide a high-level overview of the Magma model and its key components, making it easy to understand the paper's structure and core message.

---

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
    subgraph Input["Input"]
    A["Visual Observations (I) Images/Video Frames"]
    B[Task Description
    Textual Goal]
    end

    C["Magma Model<br>(π)"]
    style C fill:#ccf5,stroke:#333,stroke-width:2px

    subgraph Output["Output"]
        D["Action Tokens (O) Verbal & Spatial"]
    end

    A --> C
    B --> C
    C --> D

    subgraph Tasks["Tasks"]
        E[UI Navigation]
        F[Robotic Manipulation]
        G[Multimodal Understanding]
    end
    
    D --> E & F & G

    E --> H(2D Screenshots)
    F --> I(3D Physical World)
    G --> J(Images/Videos)

    H --> K["Actions:<br> 'click', 'type', (x, y)"]
    I --> L["Actions:<br> 6-DoF displacements, gripper"]
    J --> M["Output:<br>Text description, object location"]

    style Input fill:#eee5,stroke:#333,stroke-width:1px
    style Output fill:#eee5,stroke:#333,stroke-width:1px
    style Tasks fill:#eee5,stroke:#333,stroke-width:1px

    linkStyle 0,1,2,3,4,5,6,7,8,9,10,11 stroke-width:1.5px,stroke:#555,fill:none
    
```

### Explanation of the System Diagram:

*   **Input Subgraph:**  Clearly defines the inputs to the Magma model: `Visual Observations` (Images/Video Frames) and `Task Description` (Textual Goal).
*   **Magma Model Node:** The central `Magma Model (π)` node, styled distinctively to emphasize its role as the core processing unit.
*   **Output Subgraph:**  Specifies the output as `Action Tokens (O)` which can be both `Verbal & Spatial`, highlighting Magma's multimodal action generation.
*   **Tasks Subgraph:** Lists the three main task categories Magma is designed for: `UI Navigation`, `Robotic Manipulation`, and `Multimodal Understanding`.
*   **Task-Specific Details:**  For each task, the diagram further specifies the environment (2D Screenshots, 3D Physical World, Images/Videos) and the nature of actions or outputs (e.g., "click, type, (x, y)" for UI Navigation, "Text description, object location" for Multimodal Understanding).
*   **Arrows:**  Arrows indicate the flow of information, from inputs to the Magma model, and then to outputs and specific tasks.
*   **Styling:** Subgraphs and the main model node are styled for visual grouping and emphasis.

This diagram provides a clear, system-level view of how Magma works, from input to output across different task domains.

---

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
    A[Start] --> B{Unified Pretraining Interface?}
    style B fill:#aaf5,stroke:#333,stroke-width:1px
    B -- Yes --> C{Predict 2D/3D Coordinates & Text?}
    style C fill:#aaf5,stroke:#333,stroke-width:1px
    C -- "No<br>(Domain Gaps)" --> D[Propose Surrogate Tasks]
    style D fill:#aa55,stroke:#333,stroke-width:1px
    D --> E{"Action Grounding (SoM)?"}
    style E fill:#aa53,stroke:#333,stroke-width:1px
    E -- Yes --> F["Set-of-Mark (SoM) Locate Actionable Points/Regions"]
    style F fill:#af22,stroke:#333,stroke-width:1.5px
    D --> G{"Action Planning (ToM)?"}
    style G fill:#aa21,stroke:#333,stroke-width:1px
    G -- Yes --> H["Trace-of-Mark (ToM) Predict Future Trajectories"]
    style H fill:#afa5,stroke:#333,stroke-width:1.5px
    B -- "No<br>(Straightforward Prediction)" --> I["Directly Predict 2D/3D Coordinates & Text"]
    style I fill:#afa5,stroke:#333,stroke-width:1.5px

    J[Data Scaling-up Challenge?] --> K{Limited VLA Data?}
    style J fill:#aaf5,stroke:#333,stroke-width:1px
    style K fill:#aaf5,stroke:#333,stroke-width:1px
    K -- Yes --> L[Leverage Unlabeled Video Data]
    style L fill:#aaf3,stroke:#333,stroke-width:1px
    L --> H
    K -- "No<br>(Sufficient Data)" --> M[Use Existing VLA Data]
    style M fill:#afa5,stroke:#333,stroke-width:1.5px
    M --> I

    F --> N{Unified Pretraining Achieved}
    style N fill:#afa5,stroke:#333,stroke-width:1.5px
    H --> N
    I --> N
    L --> H
    M --> I
    N --> Z[End]

    %% style Challenges_Solutions fill:#e5ee5,stroke:#333,stroke-width:1px
    Z[End]

    classDef challengeNode fill:#aaf5,stroke:#333,stroke-width:1px
    class B,C,D,E,G,J,K challengeNode
    classDef solutionNode fill:#afa5,stroke:#333,stroke-width:1.5px
    class F,H,I,M,N solutionNode
    classDef endNode fill:#eee5,stroke:#333,stroke-width:1px
    class Z endNode
    
```


### Explanation of the Challenges and Solutions Flowchart:

*   **Start Node:** Begins with "Start" to indicate the initiation of the thought process.
*   **Challenge Nodes (Blue):** Represent key challenges in developing a multimodal AI agent:
    *   `Unified Pretraining Interface?`: Questions the straightforward approach of predicting diverse outputs directly.
    *   `Predict 2D/3D Coordinates & Text?`:  Highlights the initial idea but identifies domain gaps as a problem.
    *   `Action Grounding (SoM)?` and `Action Planning (ToM)?`: Proposes surrogate tasks as solutions.
    *   `Data Scaling-up Challenge?` and `Limited VLA Data?`:  Points out the data scarcity issue for VLA models.
*   **Solution Nodes (Green):**  Showcase Magma's proposed solutions:
    *   `Set-of-Mark (SoM)` and `Trace-of-Mark (ToM)`:  Introduce the core techniques for action grounding and planning.
    *   `Directly Predict 2D/3D Coordinates & Text`: Represents the less effective, direct prediction approach.
    *   `Leverage Unlabeled Video Data`:  Suggests using video data to overcome data limitations.
    *   `Use Existing VLA Data`:  Indicates the use of available vision-language-action datasets.
    *   `Unified Pretraining Achieved`: Marks the successful outcome of applying SoM and ToM.
*   **Decision Nodes (Diamond):**  Represent decision points where the path diverges based on whether a challenge is addressed or a certain approach is taken.
*   **Arrows:**  Arrows guide the flow from challenges to solutions and decisions, illustrating the logical progression of problem-solving.
*   **End Node:** Concludes with "End" to signify the completion of the process.
*   **Styling:** Different node colors and border styles are used to visually distinguish between challenges and solutions.

This flowchart effectively illustrates the thought process behind Magma's design, highlighting the challenges faced and the innovative solutions (SoM and ToM) proposed to overcome them.

---

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
    subgraph Input_Image["Input Image $$I_t$$"]
    A["Image Observation $$I_t$$"]
    B["Task Description"]
    C["Context<br>(ctx)"]
    end

    D["Candidate Region/Point Extraction<br>(P)"] --> E["Overlay Marks<br>(M)"]
    E --> F[Marked Image $$I^M_t$$]
    style F fill:#efe5,stroke:#333,stroke-width:1px

    F --> G["Magma Model<br>(π)"]
    style G fill:#ccf5,stroke:#333,stroke-width:2px

    G --> H["Output:<br>Action $action_t$ & Mark $mark_t$"]
    H --> I["Action Grounding"]

    style Input_Image fill:#ee45,stroke:#333,stroke-width:1px

```

### Explanation of the Set-of-Mark (SoM) Diagram:

*   **Input Subgraph:**  Defines the inputs for SoM: `Input Image` ($I_t$), `Task Description`, and `Context (ctx)`.
*   **Process Flow:**
    *   `Candidate Region/Point Extraction (P)`: Indicates the first step of identifying potential actionable regions or points in the input image.
    *   `Overlay Marks (M)`: Shows the process of overlaying numerical marks onto the identified regions/points.
    *   `Marked Image` ($I^M_t$): Represents the resulting image with overlaid marks, which is fed into the Magma model.
*   **Magma Model Node:** The `Magma Model (π)` node receives the marked image, task description, and context.
*   **Output Node:**  `Output: Action` ($action_t$) `& Mark` ($mark_t$) represents the model's prediction—selecting a mark corresponding to an action and its location.
*   **Action Grounding Node:** `Action Grounding` indicates the purpose of SoM, which is to achieve precise grounding of actions to visual elements.
*   **Styling:** The `Marked Image` node is styled to highlight its modified state, and the `Magma Model` node is emphasized as the central component.

This diagram clearly visualizes the process of Set-of-Mark, from input image to action grounding, emphasizing how marks facilitate the model's ability to locate and interact with actionable elements in an image.

---

```mermaid
---
config:
  layout: elk
  theme: dark
---
graph LR
    subgraph Input_Image["Input Image  $$I_t$$"]
    A[Image Observation $I_t$]
    B[Task Description]
    C["Context (ctx)"]
    end

    D["Candidate Region/Point Extraction<br>(P)"] --> E["Overlay Marks<br>(M)"]
    E --> F[Marked Image $$I^M_t$$]
    style F fill:#efe5,stroke:#333,stroke-width:1px

    F --> G["Magma Model<br>(π)"]
    style G fill:#ccf5,stroke:#333,stroke-width:2px

    G --> H["Output:<br>Action $action_t$ & Mark $mark_t$"]
    H --> I[Action Grounding]

    style Input_Image fill:#ee45,stroke:#333,stroke-width:1px

```

### Explanation of the Trace-of-Mark (ToM) Diagram:

*   **Input Subgraph:**  Defines the inputs for ToM: `Input Video Sequence` ($I = \{I_1, ..., I_t\}$), `Task Description`, and `Context (ctx)`.
*   **Process Flow:**
    *   `Point Tracking (CoTracker)`:  Indicates the use of a point tracking model (CoTracker) to track keypoints across video frames.
    *   `Marks at Frame` $I_t$ `(M)`: Represents the initial marks placed on the current frame $I_t$.
    *   `Extract Traces (T)`: Shows the extraction of future traces ($T = \{M_{t+1}, ..., M_{t+l}\}$) representing the movement of the marks over subsequent frames.
*   **Magma Model Node:** The `Magma Model (π)` receives the video frame sequence, task description, and context.
*   **Output Node:** `Output: Action` ($action_t$), `Mark` ($mark_t$), `Trace` ($trace_{t+1:t+l}$) represents the model's prediction—action, mark, and the predicted future trajectory of the mark.
*   **Action Planning Node:** `Action Planning` indicates the purpose of ToM, which is to enable the model to plan actions by predicting future movements and dynamics in the video.
*   **Styling:** The `Input Video Sequence` subgraph is styled to group video-related inputs, and the `Magma Model` is highlighted.

This diagram effectively visualizes the process of Trace-of-Mark, from input video sequence to action planning, emphasizing how predicting future traces allows the model to understand temporal dynamics and plan ahead.

---

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
    subgraph Inputs
        A["Video Data, Robotics Data, UI Navigation Data, Multimodal Understanding Data"]
    end

    subgraph Processing_SoM_ToM["SoM & ToM Generation"]
        B["SoM Generation<br>(All Data Types)"]
        C["ToM Generation<br>(Video & Robotics Data)"]
    end

    subgraph Model_Architecture["Magma Model Architecture"]
        D["Vision Encoder ConvNeXt"]
        E["LLM Decoder LLaMA-3-8B"]
        F["Fusion & Decoding"]
    end

    subgraph Outputs
        G[Verbal Tokens]
        H[Spatial Tokens]
        I[Action Tokens]
    end

    A --> B
    A --> C
    B --> D
    C --> D
    D --> F
    E --> F
    F --> G
    F --> H
    F --> I
    D -- Visual Encoding --> F
    E -- Text Encoding --> F

    style Inputs fill:#eee5,stroke:#333,stroke-width:1px
    style Processing_SoM_ToM fill:#eee5,stroke:#333,stroke-width:1px
    style Model_Architecture fill:#eee5,stroke:#333,stroke-width:1px
    style Outputs fill:#eee5,stroke:#333,stroke-width:1px

```

### Explanation of the Magma Architecture Diagram:

*   **Inputs Subgraph:** Lists the diverse data sources used for pretraining: `Video Data`, `Robotics Data`, `UI Navigation Data`, and `Multimodal Understanding Data`.
*   **Processing_SoM_ToM Subgraph:** Highlights the key preprocessing steps:
    *   `SoM Generation (All Data Types)`:  Indicates that Set-of-Mark is applied across all data types for unified action grounding.
    *   `ToM Generation (Video & Robotics Data)`: Shows that Trace-of-Mark is used for video and robotics data to enable action planning.
*   **Model_Architecture Subgraph:**  Details the core components of the Magma model:
    *   `Vision Encoder (ConvNeXt)`: Specifies ConvNeXt as the vision backbone for encoding visual inputs.
    *   `LLM Decoder (LLaMA-3-8B)`: Indicates LLaMA-3-8B as the decoder-only Language Model for generating tokens.
    *   `Fusion & Decoding`: Represents the process where visual and textual encodings are fused and decoded to produce outputs.
*   **Outputs Subgraph:**  Lists the types of tokens generated by Magma: `Verbal Tokens`, `Spatial Tokens`, and `Action Tokens`, reflecting its multimodal output capabilities.
*   **Data and Process Flow:** Arrows show the flow of data from inputs through SoM/ToM processing, into the model architecture, and finally to the outputs.
*   **Encoding Paths:** Dashed arrows indicate the encoding paths—`Visual Encoding` from the Vision Encoder to Fusion & Decoding and `Text Encoding` from the LLM Decoder (acting as encoder in this context) to Fusion & Decoding.
*   **Styling:** Subgraphs are styled for visual grouping, and key components are clearly labeled.

This diagram offers a comprehensive view of Magma's architecture, from data ingestion and preprocessing to model components and output generation, emphasizing the role of SoM and ToM in bridging different data modalities.

---

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
    subgraph Data_Sources["Pretraining Datasets"]
        A[Robotics Data Open-X-Embodiment]
        B[UI Navigation Data SeeClick, Vision2UI]
        C[Instructional Videos Epic-Kitchen, Ego4d, Somethingv2]
        D[Multimodal Understanding Data ShareGPT4V, LLaVA-1.5]
    end

    subgraph SoM_ToM_Application["SoM & ToM Application"]
        E["SoM Applied to All Data Types"]
        F["ToM Applied to Videos & Robotics"]
    end

    subgraph Pretraining_Tasks["Pretraining Tasks"]
        G["Action Grounding Prediction<br>(SoM)"]
        H["Trace Prediction<br>(ToM)"]
        I["Text Generation<br>(Standard LM Tasks)"]
    end

    subgraph Magma_Model["Magma Model"]
        J[Pretrained Magma Model]
    end

    Data_Sources --> SoM_ToM_Application
    SoM_ToM_Application --> Pretraining_Tasks
    Pretraining_Tasks --> Magma_Model

    style Data_Sources fill:#eee4,stroke:#333,stroke-width:1px
    style SoM_ToM_Application fill:#eee4,stroke:#333,stroke-width:1px
    style Pretraining_Tasks fill:#eee4,stroke:#333,stroke-width:1px
    style Magma_Model fill:#ee44,stroke:#333,stroke-width:1px

```

### Explanation of the Pretraining Strategy Diagram:

*   **Data_Sources Subgraph:**  Details the specific datasets used for pretraining, categorized by domain:
    *   `Robotics Data (Open-X-Embodiment)`
    *   `UI Navigation Data (SeeClick, Vision2UI)`
    *   `Instructional Videos (Epic-Kitchen, Ego4d, Somethingv2)`
    *   `Multimodal Understanding Data (ShareGPT4V, LLaVA-1.5)`
*   **SoM_ToM_Application Subgraph:**  Clarifies how SoM and ToM are applied to these datasets:
    *   `SoM Applied to All Data Types`: Reinforces the broad application of SoM for unified grounding.
    *   `ToM Applied to Videos & Robotics`:  Specifies ToM's use for dynamic data to enable planning.
*   **Pretraining_Tasks Subgraph:**  Lists the primary pretraining tasks:
    *   `Action Grounding Prediction (SoM)`
    *   `Trace Prediction (ToM)`
    *   `Text Generation (Standard LM Tasks)`: Includes standard language modeling tasks for general language understanding.
*   **Magma_Model Subgraph:**  Represents the `Pretrained Magma Model` as the outcome of the pretraining process.
*   **Data Flow:** Arrows illustrate the sequential flow from data sources to SoM/ToM application, then to pretraining tasks, and finally resulting in the pretrained Magma model.
*   **Styling:** Subgraphs are styled for visual organization and clear labeling of each stage.

This diagram summarizes the pretraining strategy of Magma, from the diverse datasets used to the key pretraining tasks enabled by SoM and ToM, culminating in the pretrained model ready for downstream tasks.

---

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
    subgraph Evaluation_Tasks[Evaluation Tasks]
        A[UI Navigation Mind2Web, AITW]
        B[Robotic Manipulation Bridge, LIBERO, WidowX]
        C[VL Understanding GQA, VideoMME, VSR, BLINK]
    end

    subgraph Key_Metrics[Key Evaluation Metrics]
        D["Success Rate<br>(Robotics, UI Navigation)"]
        E["Accuracy, F1 Score<br>(UI Navigation)"]
        F["VQA Accuracy, MME Score<br>(VL Understanding)"]
        G["Spatial Reasoning Metrics<br>(VSR, BLINK, SpatialEval)"]
    end

    subgraph SOTA_Comparison[Comparison with SOTA]
        H["Outperforms Domain-Specific Models (UI, Robotics)"]
        I["Competitive with SOTA LMMs<br>(VL Tasks)"]
        J["Ablation Studies SoM & ToM Effectiveness"]
        K["Spatial Reasoning Benchmarks VSR, BLINK, SpatialEval"]
    end

    Evaluation_Tasks --> Key_Metrics
    Key_Metrics --> SOTA_Comparison

    style Evaluation_Tasks fill:#e44,stroke:#333,stroke-width:1px
    style Key_Metrics fill:#ee44,stroke:#333,stroke-width:1px
    style SOTA_Comparison fill:#ee44,stroke:#333,stroke-width:1px
    
```

### Explanation of the Evaluation Diagram:

*   **Evaluation_Tasks Subgraph:**  Lists the tasks used to evaluate Magma, categorized by domain:
    *   `UI Navigation (Mind2Web, AITW)`
    *   `Robotic Manipulation (Bridge, LIBERO, WidowX)`
    *   `VL Understanding (GQA, VideoMME, VSR, BLINK)`
*   **Key_Metrics Subgraph:**  Specifies the evaluation metrics used for each task domain:
    *   `Success Rate (Robotics, UI Navigation)`
    *   `Accuracy, F1 Score (UI Navigation)`
    *   `VQA Accuracy, MME Score (VL Understanding)`
    *   `Spatial Reasoning Metrics (VSR, BLINK, SpatialEval)`
*   **SOTA_Comparison Subgraph:**  Summarizes Magma's performance relative to state-of-the-art models:
    *   `Outperforms Domain-Specific Models (UI, Robotics)`:  Highlights Magma's superiority over specialized models.
    *   `Competitive with SOTA LMMs (VL Tasks)`:  Shows Magma's strong performance in VL tasks, comparable to top LMMs.
    *   `Ablation Studies (SoM & ToM Effectiveness)`:  Notes the use of ablation studies to validate the contribution of SoM and ToM.
    *   `Spatial Reasoning Benchmarks (VSR, BLINK, SpatialEval)`: Emphasizes evaluations on spatial reasoning tasks to confirm improved spatial intelligence.
*   **Evaluation Flow:** Arrows indicate that evaluation tasks are assessed using key metrics, and the results are then compared against the state-of-the-art.
*   **Styling:** Subgraphs are styled to group related information, making it easy to see the evaluation scope and outcomes.

This diagram offers a concise overview of Magma's evaluation, highlighting the tasks, metrics, and key findings regarding its performance compared to existing models.


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---