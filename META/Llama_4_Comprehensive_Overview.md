---
created: 2025-04-09 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.

---



# Llama 4 Comprehensive Overview - A Diagrammatic Guide 
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

## Llama 4 Introduction on Hugging Face

Meta has released two new powerful, natively multimodal Mixture-of-Experts (MoE) large language models, Llama 4 Maverick and Llama 4 Scout, integrated into the Hugging Face ecosystem.

```mermaid
---
title: "Llama 4 Introduction on Hugging Face"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
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
  root((Llama 4 Release on Hugging Face))
    Models
      Llama 4 Maverick
        (~400B Total Params)
        (17B Active Params)
        (128 Experts)
        (MoE + Dense Interleaved)
        (Multimodal)
        (BF16/FP8)
        (Co-distilled from Llama Behemoth)
      Llama 4 Scout
        (~109B Total Params)
        (17B Active Params)
        (16 Experts)
        (Full MoE)
        (Multimodal)
        (BF16 / int4/int8 Quantizable)
    Key Features
      Mixture-of-Experts["Mixture-of-Experts (MoE) Architecture"]
      Native Multimodality (Text & Image Input)
      Auto-regressive
      Trained on up to 40T Tokens
      Supports ~200 Languages (12 fine-tuned)
      Large Context Lengths (up to 10M for Scout Instruct)
      Released under Llama 4 Community License
    Hugging Face Integration
      Model Hub (`meta-llama` org)
      `transformers` v4.51.0+ Support
      Text Generation Inference (TGI)
      Quantization Support (int4/FP8)
      Xet Storage Backend
      
```

---


## What is Llama 4?

Llama 4 introduces a new generation of MoE models focusing on performance and efficiency.

```mermaid
---
title: "What is Llama 4?"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
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
graph TD
    subgraph Meta_Llama_4_Architecture["Meta Llama 4 Architecture"]
        A[Llama 4 Generation] --> B(Auto-regressive MoE)
        B --> C{Two Models}
        C --> D[Llama 4 Maverick]
        C --> E[Llama 4 Scout]

        D --> D1("~400B Total Parameters")
        D --> D2("17B Active Parameters")
        D --> D3("128 Experts<br/>(Interleaved with Dense Layers)")
        D --> D4("BF16 / FP8 Formats")
        D --> D5("Co-distilled from Llama Behemoth")

        E --> E1("~109B Total Parameters")
        E --> E2("17B Active Parameters")
        E --> E3("16 Experts<br/>(Full MoE)")
        E --> E4("BF16 / On-the-fly int4/int8 Quantization")

        B --> F(Native Multimodality - Early Fusion)
        F -- Processes --> G[Text Inputs]
        F -- Processes --> H[Image Inputs]

        B --> I(Trained on up to 40 Trillion Tokens)
        I --> J("Data covers ~200 Languages")
        J --> K("Fine-tuned support for 12 Languages<br/>(Arabic, Spanish, etc.)")

        B --> L(Released under Llama 4 Community License)
    end
    
```

---


## Hugging Face Ecosystem Integration

Seamless integration allows immediate use within the Hugging Face ecosystem.

```mermaid
---
title: "Hugging Face Ecosystem Integration"
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
    subgraph Llama_4_Models["Llama 4 Models"]
        M[Llama 4 Maverick]
        S[Llama 4 Scout]
    end

    subgraph Hugging_Face_Ecosystem["Hugging Face Ecosystem"]
        HUB["Model Hub<br>(meta-llama org)"]
        TR["transformers Library<br>(v4.51.0+)"]
        TGI["Text Generation Inference (TGI)"]
        QUANT["Quantization<br>(int4 for Scout, FP8 for Maverick)"]
        XET["Xet Storage Backend"]
    end

    M --> HUB
    S --> HUB

    M --> TR
    S --> TR
    TR --> TR1[Easy Loading, Inference, Fine-tuning]
    TR --> TR2[Native Multimodal Support]
    TR --> TR3[Automatic Tensor Parallel / Device Mapping]
    TR --> TR4["Supports Downstream Libraries<br/>(TRL)"]

    M --> TGI
    S --> TGI
    TGI --> TGI1[Optimized & Scalable Deployment]
    TGI --> TGI2[High-Throughput Generation]

    M -- FP8 Weights --> QUANT
    S -- On-the-fly int4 --> QUANT
    QUANT --> QUANT1[Reduced Memory Footprint]

    M --> XET
    S --> XET
    XET --> XET1["Faster Uploads/Downloads"]
    XET --> XET2["~25% Deduplication(Base)"]
    XET --> XET3["~40%+ Deduplication<br/>(Derivatives)"]
    XET3 --> XET4["Saves Community Time & Bandwidth"]

    style M fill:#f9f3,stroke:#333,stroke-width:2px
    style S fill:#f9f3,stroke:#333,stroke-width:2px
    
```

----


## Context Length and Architectural Choices

Llama 4 models support exceptionally large context lengths through innovative architectural designs, especially in the Instruct versions.

**Context Length Summary:**

| Model           | Instruct | Context Length | Architecture Highlights |
| :-------------- | :------: | :------------: | :---------------------- |
| Scout (16E)     |    ✅    |      10M       | iRoPE, QK Norm          |
| Maverick (128E) |    ✅    |       1M       | iRoPE, MoE Interleaving |
| Scout (16E)     |          |      256K      | (Base Pre-training)     |
| Maverick (128E) |          |      256K      | (Base Pre-training)     |

**Key Architectural Innovations (iRoPE):**

```mermaid
---
title: "Key Architectural Innovations (iRoPE)"
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
    subgraph iRoPE Architecture for Long Context
        direction LR
        A["Large Context Challenge"] --> B("Attention Score Fading with Length")
        B --> C{"Solution:<br/>iRoPE"}

        C --> D["Interleaved Layers"]
        D --> E["NoPE Layers<br/>(1 in 4)"]
        D --> F["RoPE Layers<br/>(3 in 4)"]

        E --> G["No Positional Encoding"]
        E --> H["Full Causal Mask<br/>(Full Context Access)"]
        E --> I["Scaled Softmax<br/>(Temperature Tuning)"]
        I --> J("Counteracts Score Fading")

        F --> K[Traditional RoPE Positional Encoding]
        F --> L[Chunked Attention]
        L --> M["Processes context in smaller blocks<br/>(e.g., 8K)"]
        L --> N("Memory/Compute Efficient")
        F --> O("QK Normalization in Scout")

        C --> P["Improves Generalization for Arbitrary Lengths"]
        P --> Q("Key factor for 1M / 10M context")
    end
    
```

---


**Chunked Attention Concept (RoPE Layers):**

Chunked attention allows RoPE layers to operate more efficiently by focusing on local context blocks (e.g., 8192 tokens), while NoPE layers handle the full context.

```mermaid
---
title: "Chunked Attention Concept (RoPE Layers)"
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
    subgraph Chunked_Attention["Chunked Attention<br/>(Example: Chunk Size 3)"]
        Input["'What is chunked attention?'"] --> T0["'What' <br/>(Token 0)"]
        Input --> T1["' is' <br/>(Token 1)"]
        Input --> T2["' ch' <br/>(Token 2)"]
        Input --> T3["'unked' <br/>(Token 3)"]
        Input --> T4["' attention' <br/>(Token 4)"]
        Input --> T5["'?' <br/>(Token 5)"]

        T0 -- Attends to --> C0((Chunk 0))
        T1 -- Attends to --> C0
        T2 -- Attends to --> C0

        T3 -- Attends to --> C1((Chunk 1))
        T4 -- Attends to --> C1
        T5 -- Attends to --> C1

        C0 -- Contains --> T0 & T1 & T2
        C1 -- Contains --> T3 & T4 & T5

        Note --> N1["RoPE layers process within chunks<br/>(e.g., size 8192 for Llama 4)"]
        Note --> N2["NoPE layers see the entire sequence"]
    end

    subgraph Legend
      direction TB
        Node((Chunk))
        Node2["Token"]
        %% style Node fill:#lightblue
    end

    %% subgraph Note
    %%   direction TB
    %% end

```


*(Note: The diagram above simplifies the attention mask concept shown in the ASCII art for clarity within Mermaid's capabilities. Each token attends to tokens within its assigned chunk.)*

----

**MoE Interleaving (Maverick):**

```mermaid
---
title: "MoE Interleaving (Maverick)"
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
    M["Llama 4 Maverick<br/>(128E)"] --> L1["Layer 1: Dense"]
    L1 --> L2["Layer 2: MoE<br/>(128 Experts)"]
    L2 --> L3["Layer 3: Dense"]
    L3 --> L4["Layer 4: MoE<br/>(128 Experts)"]
    L4 --> Ldots[...]
    Ldots --> LN[Last Layer]

    S["Llama 4 Scout<br/>(16E)"] --> SL1["Layer 1: MoE<br/>(16 Experts)"]
    SL1 --> SL2["Layer 2: MoE<br/>(16 Experts)"]
    SL2 --> SLdots[...]
    SLdots --> SLN["Last Layer: MoE<br/>(16 Experts)"]

    style M fill:#f9f,stroke:#333,stroke-width:2px
    style S fill:#ccf,stroke:#333,stroke-width:2px
    
```


**Other Architectural Notes:**

*   **QK Normalization:** Applied in Scout's RoPE layers (after RoPE embeddings) for improved stability.
*   **Co-distillation:** Maverick learned from a larger model (Llama Behemoth) using a dynamic loss function.
*   **MetaP:** Likely inspired by MuP, used for optimal hyperparameter tuning across dimensions like model size and training budget.

----

## How to Use with Transformers

Using Llama 4 involves installing the latest `transformers` library, handling authentication for model access, and using the `AutoProcessor` and `Llama4ForConditionalGeneration` classes.

```mermaid
---
title: "How to Use with Transformers"
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
sequenceDiagram
    autonumber

    actor User

    participant Transformers as `transformers` Library<br/>(v4.51.0+)
    participant HuggingFaceHub as Hugging Face Hub
    participant Llama4Model as Llama 4 Model<br/>(on GPU)

    User ->> Transformers: Install/Update<br/>(`pip install -U transformers huggingface_hub[hf_xet]`)
    User ->> HuggingFaceHub: Login / Accept License Terms
    User ->> Transformers: `AutoProcessor.from_pretrained(model_id)`
    Transformers -->> User: processor
    User ->> Transformers: `Llama4ForConditionalGeneration.from_pretrained(...)`
    Note over Transformers, Llama4Model: Handles download, device_map='auto', attn_implementation, dtype
    Transformers -->> User: model<br/>(loaded on GPUs)

    User ->> Transformers: Define `messages`<br/>(incl. text & image URLs)
    User ->> Transformers: `processor.apply_chat_template(messages, ...)`
    Transformers -->> User: inputs<br/>(tokenized, formatted tensors)
    User ->> Llama4Model: `model.generate(**inputs, max_new_tokens=...)`
    Note over Llama4Model: Generation happens<br/>(potentially using tensor parallel if multi-GPU)
    Llama4Model -->> User: outputs<br/>(generated token IDs)

    User ->> Transformers: `processor.batch_decode(outputs)`
    Transformers -->> User: response<br/>(decoded text)
    
```


---


## Evaluation Scores

Llama 4 Maverick and Scout demonstrate state-of-the-art performance, surpassing previous models like Llama 3.1 405B on various reasoning, knowledge, coding, and multimodal benchmarks. (Refer to the detailed tables in the original document for specific scores).

## Xet Storage Benefits

Using the Xet backend provides significant advantages for downloading and managing these large models.

```mermaid
---
title: "Xet Storage Benefits"
config:
  layout: elk
  look: handDrawn
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#BB28',
      'primaryTextColor': '#299',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart LR
    A[Llama 4 Models on Hub] --> B{Xet Storage Backend};
    B --> C[Faster Uploads];
    B --> D[Faster Downloads];
    B --> E[Content-Defined Chunking];
    E --> F[Deduplication];
    F --> G["~25% on Base Models"];
    F --> H["~40%+ on Derivatives (Finetunes, Quants)"];
    C & D & H --> I[Benefits for Community];
    I --> J[Reduced Bandwidth Usage];
    I --> K[Faster Iteration];
    I --> L[Storage Savings];

    style B fill:#add,stroke:#333,stroke-width:2px
```


----


---

## Summary of Key Takeaways & Growth

```mermaid
mindmap
  root((Llama & Meta AI: 2024 Highlights & Growth))
    Llama_Model
      Adoption :: 650M+ Downloads (Doubled in 3 months)
      Derivatives :: 85,000+ on Hugging Face (5x increase YoY)
      Licensing :: Approvals doubled in 6 months (Strong global growth: LATAM, APAC, Europe)
      Innovation :: Rapid release cycle (3.0 -> 3.1 -> 3.2 -> 3.3)
      Daily Average :: ~1M downloads/day since Feb 2023
      Token Volume :: >50% MoM growth (Sept, key cloud partners)
    Meta_AI_Assistant
      User Base :: ~600M MAU (Monthly Active Users)
      Goal :: World's most used AI assistant by end of 2024
      Reach :: Expanding to 43 countries, 12 languages (by end of 2024)
      Platform :: WhatsApp, Instagram, Facebook, Messenger, Web, Ray-Ban Meta
      Engagement :: Strong retention/engagement (esp. India, Mexico on WhatsApp)
    Ecosystem_&_Partnerships
      Importance :: Crucial for availability and optimization
      Key Partners :: AWS, AMD, Azure, Databricks, Dell, Google Cloud, Groq, NVIDIA, IBM watsonx, Oracle, ScaleAI, Snowflake
      Tools :: Llama Stack, AI Studio
    Adoption_Areas
      Enterprises :: Block, Accenture, Spotify, LinkedIn, Arcee AI, ObjectsHQ
      Governments :: US, India, Argentina
      Community :: Driving innovation & product decisions
```

---

## Llama Model Evolution Timeline (2024)

```mermaid
---
title: "Llama Model Evolution Timeline (2024)"
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
gantt
    title Llama Model Releases & Innovations 2024
    dateFormat  YYYY-MM
    axisFormat  %Y-%m
    section Model Releases
    Llama 3 Introduced       :a1, 2024-01, 1M  // Approximate Start of Year
    Llama 3.1 (405B) Release :a2, 2024-07, 1M  // July Release
    Llama 3.2 (Multimodal/Edge) Ann. :a3, 2024-09, 1M // Announced at Connect (Sep/Oct)
    Llama 3.3 (70B) Release  :a4, 2024-11, 2M  // Approximate End of Year Release

    section Key Features & Milestones
    Frontier-Level Open Model (405B) : milestone, after a2, 1d
    First Multimodal & Edge Models   : milestone, after a3, 1d
    Performance/Cost Optimization (70B vs 405B) : milestone, after a4, 1d
    Llama Stack Introduced           : milestone, 2024-05, 7M // Approx timing within year
    AI Studio Launch                 : milestone, 2024-07, 5M // AI Character Creation Tool
    
```

---


## Llama Ecosystem Overview

```mermaid
---
title: "Llama Ecosystem Overview"
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
graph TD
    subgraph Llama_Core["Llama Foundational Models"]
        direction LR
        L3["Llama 3<br/>(Base)"]
        L31["Llama 3.1<br/>(405B)"]
        L32["Llama 3.2<br/>(Multi/Edge)"]
        L33["Llama 3.3<br/>(70B)"]
        L4["Llama 4<br/>(Future)"]
    end

    subgraph Tools_Features["Tools & Features"]
        direction TB
        LS["Llama Stack<br/>(Toolchain)"]
        AS["AI Studio<br/>(Creators)"]
        OS["Open Source Access"]
    end

    subgraph Partnership_Cloud["Partnerships & Deployment"]
        direction TB
        Cloud["Cloud Partners<br/>(AWS, Azure, GCP, Oracle, IBM)"]
        Hardware["Hardware<br/>(AMD, NVIDIA, Groq, Dell)"]
        DataPlatforms["Data Platforms<br/>(Databricks, Snowflake, ScaleAI)"]
        OnDevice["On-Device / Edge"]
        OnPrem["On-Premises"]
    end

    subgraph Adoption_UseCases["Adoption & Use Cases"]
        direction TB
        Ent["Enterprises<br/>(Block, Spotify, LinkedIn, Accenture, Arcee, ObjectsHQ)"]
        Gov["Governments<br/>(US, India, Argentina)"]
        Com["Community<br/>(Derivatives, Fine-tuning)"]
        MetaP["Meta Products<br/>(Meta AI, Ads, Ray-Ban)"]
    end

    Llama_Core --> Tools_Features
    Llama_Core --> Partnership_Cloud
    Partnership_Cloud --> Adoption_UseCases
    Tools_Features --> Adoption_UseCases
    Com ---> Llama_Core

    subgraph Community_Feedback_Loop["Community Feedback Loop"]
    end
    
```

---


## Meta AI Assistant: Reach and Integration

```mermaid
---
title: "Meta AI Assistant: Reach and Integration"
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
      'fontFamily': 'Fantasy'
    }
  }
}%%
mindmap
  root((Meta AI Assistant))
    Core :: Built with Llama
    Goal :: Most Used AI Assistant Globally (by end 2024)
    MAU :: ~600 Million
    Availability
      Countries :: 43 (by end 2024)
      Languages :: 12 (by end 2024)
    Platforms
      Messaging :: WhatsApp, Messenger
      Social :: Instagram, Facebook
      Web :: meta.ai
      Devices :: Ray-Ban Meta Smart Glasses
    Key Functions & Features
      Text Generation
      Image Understanding (Input)
      Information Retrieval
      Coaching / Goal Assistance
      Voice Interaction (Expanding)
      AI Characters (via AI Studio)
    Integration Examples
      WhatsApp :: High engagement (India, Mexico)
      Ray-Ban :: Hands-free info (Expanding EU)
      AI Studio :: Custom AI Characters
      Meta Ads :: Advantage+ Creative (Text, Video, Image Gen)
      
```

---


## Llama Adoption Examples

```mermaid
---
title: "Llama Adoption Examples"
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
    subgraph Enterprises
        B[Block / Cash App] -- Llama --> CS(Customer Support - Privacy Preserving)
        A[Accenture] -- Llama 3.1 --> Chatbot(Intergovernmental Org Chatbot on AWS)
        S[Spotify] -- Llama --> Reco(Contextual Recommendations & Personalized Narratives - DJ)
        L[LinkedIn] -- Llama --> Train(Efficient Fine-Tuning for Social Network Tasks - Liger-Kernel)
        Ar[Arcee AI] -- Llama --> FineTune(Cost Reduction vs Closed LLMs - 47% TCO down)
        Ohq[ObjectsHQ] -- Llama --> Ads(Advantage+ Creative Text Gen - 60% ROAS increase)
    end

    subgraph Governments
        US[US Government] -- Llama --> Efficiency(Public Service Delivery Improvement)
        IN[India - Min. Skill Dev.] -- Llama --> Learning(Enhanced Learning Outcomes & Support)
        AR[Argentina] -- Llama --> CitizenBot(WhatsApp Chatbot for Public Services)
    end

    subgraph Community
        HF[Hugging Face] -- Llama --> Derivatives(85k+ Models - Fueling Innovation)
        Devs[Developers Globally] -- Llama --> Custom(Building Diverse Applications)
    end

    Llama((Llama Open Models)) --> Enterprises
    Llama --> Governments
    Llama --> Community
    
```

---


## Future Roadmap (2025 Outlook)

```mermaid
---
title: "Future Roadmap (2025 Outlook)"
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
flowchart TD
    Start["2025:<br/>Increase Pace of Innovation"] --> L4Rel[Llama 4 Releases]
    L4Rel -- Advancements Across --> Speech[Speech Models - Natural, Conversational]
    L4Rel -- Advancements Across --> Reasoning[Advanced Reasoning]

    Speech --> VoiceAI[Enhanced Voice for Meta AI]
    VoiceAI --> CUI[Move Towards Voice-Based Experiences]

    Reasoning --> Agentic[Agentic AI Systems]
    Agentic --> BizAgents["Business Agents<br/>(Support, Commerce)"]
    Agentic --> PersonalAgents["Personal Assistants<br/>(Task-Oriented)"]

    MovieGen["Meta Movie Gen<br/>(Research)"] --> VidExp[AI Video Generation/Editing in Apps]

    CUI --> EndGoal[Support Future of Human Connection]
    PersonalAgents --> EndGoal
    VidExp --> EndGoal
    
```

----



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