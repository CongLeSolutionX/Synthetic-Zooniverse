---
created: 2025-04-09 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://github.com/huggingface/blog/blob/main/llama4-release.md"
---



# llama4-release.md on HuggingFace - A Diagrammatic Guide 
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---



The set of diagrams below aims to visually capture the core information presented in the blog post, breaking down the models, their features, integrations, architecture, usage, and benefits.




## Llama 4 Introduction on Hugging Face

Meta has released two new powerful, natively multimodal Mixture-of-Experts (MoE) large language models, Llama 4 Maverick and Llama 4 Scout, integrated into the Hugging Face ecosystem.

```mermaid
---
title: "Llama 4 Release on Hugging Face"
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
title: "How to Use Llama 4 with Transformers"
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

    style B fill:#add3,stroke:#333,stroke-width:2px
```






---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---