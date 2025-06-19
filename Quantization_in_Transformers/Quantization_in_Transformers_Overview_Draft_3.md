---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://huggingface.co/docs/transformers/v4.49.0/quantization/overview"
---



# An Overview of Quantization in Transformers
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Key Concepts and Relationships


* **Quantization:** The core concept is representing numerical data with fewer bits, trading off accuracy for reduced memory footprint and faster inference.  This directly impacts model size and speed.

* **Quantization Methods:** The document introduces a variety of quantization methods, including:
    * **AQLM:** Additive Quantization of Language Models, a technique that quantizes groups of weights as a sum of codes.
    * **AWQ:** Activation-aware Weight Quantization, which focuses on preserving weights crucial for model accuracy.
    * **bitsandbytes:** A comprehensive library for 8-bit and 4-bit quantization.  Includes strategies like LLM.int8() and QLoRA support.
    * **Compressed Tensors:** A unified format supporting various quantization and sparsity schemes, including FP8 and INT4, optimized for different hardware.
    * **EETQ:**  Per-channel int8 quantization for NVIDIA GPUs, leveraging FasterTransformer and TensorRT.
    * **FBGEMM FP8:** FP8 quantization per channel, targeting smaller batch sizes on compute-capable GPUs.
    * **Fine-grained FP8:**  FP8 quantization per 2D block, leveraging DeepSeek implementations.
    * **GPTQ:** A post-training quantization technique that quantizes each row of the weight matrix independently.  Supports int4, int8, and various backends.
    * **Marlin:** 4-bit GPTQ kernel optimized for NVIDIA A100 GPUs.
    * **ExLlama/ExLlamaV2:** CUDA implementations for faster 4-bit GPTQ inference.
    * **HQQ:** Half-Quadratic Quantization, a robust on-the-fly quantization technique for diverse models.
    * **Optimum:** A general library for quantization that supports various backends.
    * **Optimum-quanto:**  Supports various quantization levels (e.g., int8), modality-agnostic, and device-agnostic.
    * **SpQR:**  16x16 tiled bi-level group 3-bit quantization structure for LLMs.
    * **BitNet:** Replaces linear layers with specialized BitLinear layers for ternary/binary weight and 8-bit activation quantization.
    * **TorchAO:** An architecture optimization library for PyTorch, including quantization techniques like int4_weight_only.


* **Libraries and Tools:**  Crucially, the document highlights specific libraries (e.g., bitsandbytes, compressed-tensors, optimum, etc.) and associated commands for implementing each quantization technique.  There's emphasis on installing the correct versions and using appropriate configuration options.


* **Hardware Considerations:** Each quantization method often has specific hardware requirements (e.g., compute capability, GPU type, etc.).  The document explicitly notes compatibility with CPUs, GPUs (CUDA, ROCm, Apple Silicon), and specific GPU architectures (e.g., NVIDIA A100).


* **Accuracy/Performance Tradeoffs:** The document emphasizes the trade-offs inherent in quantization (reduced memory usage vs. potential loss of accuracy).  It frequently provides benchmarks and comparisons to highlight the performance gains or limitations of each approach.


* **Use Cases and Support:**  The document identifies specific use cases where each method excels (e.g., on-the-fly quantization, calibration-based compression, specific hardware support). This is presented through various examples of loading, using, and potentially saving quantized models.

----


## Diagrammatic Representations (Conceptual Outline)


* **Quantization Techniques Overview:** A mind map or flowchart outlining the various quantization techniques, their pros and cons, and the associated libraries/tools.  Each quantization method could be a branch with sub-branches representing specific features, use cases, or hardware support.
* **Hardware Compatibility Matrix:** A table showing the compatibility of each quantization technique with different hardware.  This would clearly display the constraints of each technique based on the targeted hardware.
* **Quantization Pipeline:** A sequence diagram to illustrate the steps involved in quantizing a model (e.g., loading, configuring, quantization, inference).
* **Accuracy-Performance Tradeoff Charts:**  Scatter plots or bar graphs illustrating the trade-offs between accuracy and performance for different quantization levels.
* **Library Integration Graph:** A graph showing the relationships and dependencies between the quantization libraries and the Hugging Face Transformers library.  Nodes could be specific library packages, and the edges would indicate how they integrate or call each other.



```mermaid
---
title: Quantization Techniques
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%{
  init: {
    'fontFamily': 'verdana',
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
    subgraph Quantization_Techniques["Quantization Techniques"]
        A[Quantization] --> B(AQLM)
        B --> BA{Grouped Weights, Additive Codes}
        B --> BB[Reduced Memory, Potential Accuracy Loss]
        
        A --> C(AWQ)
        C --> CA{Preserves Important Weights}
        C --> CB[Reduced Quantization Loss, Potential Performance Gains]

        A --> D(bitsandbytes)
        D --> DA{8-bit, 4-bit Quantization}
        D --> DB["Reduced Memory (2x/4x), FP16 Conversion"]
        D --> DC["LLM.int8(), QLoRA Support"]
        
        A --> E(Compressed Tensors)
        E --> EA{Unified Format, FP8/INT4/INT8}
        E --> EB["Supports Various Optimizations (GPTQ, AWQ, etc)"]
        
        A --> F(EETQ)
        F --> FA{Per-Channel INT8 Quantization}
        F --> FB[NVIDIA GPUs, High Performance GEMM Kernels]

        A --> G(FBGEMM FP8)
        G --> GA{FP8 Quantization per Channel}
        G --> GB["NVIDIA GPUs (compute capability >= 9)"]
        
        A --> H(Fine-grained FP8)
        H --> HA{FP8 Quantization per 2D Block}
        H --> HB["NVIDIA GPUs (compute capability >= 9), DeepSeek Models"]
        
        A --> I(GPTQ)
        I --> IA{Post-training Quantization, Int4 Weights}
        I --> IB[Potential Memory Savings, Speed Improvements]
        I --> IC[Marlin, ExLlama Support]
        
        A --> J(HQQ)
        J --> JA{On-the-fly, Robust Optimization}
        J --> JB[No Calibration, Supports Various Bitwidths]
        
        A --> K(Optimum)
        K --> KA{General Quantization Library, Intel/Furiosa/ONNX Support}

        A --> L(Optimum-Quanto)
        L --> LA{Linear Quantization, Weights/Activations}
        L --> LB[Modality Agnostic, Device Agnostic]
        
        A --> M(SpQR)
        M --> MA{Tiled Group Quantization, 3-bit}
        M --> MB[Sparse Outliers, Reduced Memory]
        
        A --> N(BitNet)
        N --> NA{BitLinear Layers, Ternary/Binary Weights}
        N --> NB[8-bit Activations, Quantization-Aware Training]
        
        A --> O(TorchAO)
        O --> OA{Architecture Optimization, Int4/Int8/FP8}
        O --> OB[Composable with other PyTorch Optimizations]
    end
    
    subgraph Hardware_Considerations["Hardware Considerations"]
        A -- GPU (CUDA, ROCm, Apple Silicon) --> P[Compute Capability]
        A -- CPU (Intel) --> Q[x86 Architecture]
    end

    subgraph Accuracy_Performance_Tradeoffs["Accuracy Performance Tradeoffs"]
        A -- Accuracy --> R[Reduced Precision]
        A -- Performance --> S[Faster Inference]
    end
    
    subgraph Library_Integration["Library Integration"]
        A --> T(Hugging Face Transformers) --> U[Integration]
        T -- Quantization Libraries --> V[bitsandbytes, compressed-tensors, optimum, etc]
    end
    
```


----

```mermaid
---
title: Quantization Libraries
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%{
  init: {
    'fontFamily': 'verdana',
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
    subgraph Quantization_Libraries["Quantization Libraries"]
        A[bitsandbytes] --> AA{"Installation, Config"}
        AA --> AB["8-bit, 4-bit"]
        
        A --> AC["8-bit (LLM.int8()),<br> 4-bit (QLoRA)"]
        
        A --> AD["Offloading, Outlier Thresholds"]
        
        A --> AE["Skip Modules, Finetuning"]
        
        B["Compressed Tensors"] --> BA{"Installation, Loading"}
        BA --> BB["FP8, INT4, INT8"]
        BA --> BC["Quantization Strategies<br>(tensor, channel, etc.)"]
        
        C[EETQ] --> CA{"Installation, Config"}
        CA --> CB["INT8, Per-Channel Quantization"]
        CA --> CC["No Calibration"]
        
        D[FBGEMM FP8] --> DA{Installation, Config}
        DA --> DB[FP8, Per-Channel]
        DA --> DC[NVIDIA GPUs >= Compute Capability 9]

        E[Fine-grained FP8] --> EA{Installation, Config}
        EA --> EB[FP8, Per 2D Block]
        EA --> EC[NVIDIA GPUs >= Compute Capability 9]
        
        F[GPTQ] --> FA{Installation, Config}
        FA --> FB["Int4 Weights, Backends<br>(Marlin, ExLlama)"]
        
        G[HQQ] --> GA{Installation, Config}
        GA --> GB["On-the-fly, Dynamic Configs"]

        H[Optimum] --> HA{"Installation, General Library"}
        H --> HB["Intel/Furiosa/ONNX Support"]
    
        I[Optimum-Quanto] --> IA{"Installation, Config"}
        IA --> IB["Various Quantization Levels, Modality Agnostic"]
    
        J[SpQR] --> JA{Installation, Loading}
        JA --> JB[Tiled 3-bit Quantization]

        K[BitNet] --> KA{"Installation, Loading"}
        KA --> KB["BitLinear Layers, 8-bit Activations"]
        
        L[TorchAO] --> LA{"Installation, Config"}
        LA --> LB["Int4/Int8/FP8, Composable Optimizations"]

    end
    
```



----

```mermaid
---
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%{
  init: {
    'fontFamily': 'verdana',
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
    A[Quantization Library] --> B(Model)
    B -- Configurations --> C{Quantization Method, Bits, Strategies, Hardware}
    C -- Quantization Process --> D[Quantized Model]
    D -- Inference --> E[Faster Inference, Reduced Memory]
    
    subgraph Hardware_Compatibility["Hardware Compatibility"]
    P["GPU<br>(CUDA, ROCm, Apple)"] -- Support --> C
    Q["CPU<br>(Intel)"] -- Support --> C
    end

    subgraph Accuracy_Performance_Tradeoffs["Accuracy Performance Tradeoffs"]
    R[Accuracy] -- Trade-off --> S[Performance]
    end
    
```



These are highly simplified conceptual representations.  A more detailed diagram would require more complex Mermaid structure, potentially including nested subgraphs for specific configurations and libraries, tables for hardware compatibility, and graphs to illustrate performance trade-offs. Remember to incorporate the code examples and mathematical expressions as annotations within the diagrams for a more complete and informative representation.





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---