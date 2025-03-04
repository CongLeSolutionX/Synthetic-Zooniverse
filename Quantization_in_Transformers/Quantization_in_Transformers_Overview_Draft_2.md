---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://huggingface.co/docs/transformers/v4.49.0/quantization/overview"
---



# An Overview of Quantization in Transformers - A Diagrammatic Guide
> This content is dual-licensed under your choice of the following licenses:
> 1.  **MIT License:** For the code implementations in Swift and Mermaid provided in this document.
> 2.  **Creative Commons Attribution 4.0 International License (CC BY 4.0):** For all other content, including the text, explanations, and the Mermaid diagrams and illustrations.

---

Below is my personal notes on the topics and I might gather information from various sources, which I wil cite accordingly.

---


```mermaid
%%{
  init: {
    'theme': 'dark',
    'look': 'handDrawn',
    'fontFamily': 'verdana',
    'themeVariables': {
      'primaryColor': '#BB2528',
      'primaryTextColor': '#fff',
      'primaryBorderColor': '#7C0000',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
%%%%%%%% Mermaid version v11.4.1-b.14
mindmap
  root(("Quantization Techniques in Transformers - Relationships"))
    Core_Concept["Core Concept:<br>Reducing Precision"]
      Core_Concept --> PTQ["Post-Training Quantization<br>(PTQ)"]
      Core_Concept --> QAT["Quantization Aware Training<br>(QAT)"]

    PTQ
      PTQ --> Calibration_Needed[Calibration Needed]
      PTQ --> Calibration_Free["Calibration Free / 0-Shot"]

    QAT
      QAT --> BitNet[BitNet]
        note[Pre-training/Fine-tuning required]

    Calibration_Needed["Calibration Needed"]
      Calibration_Needed --> GPTQ[GPTQ]
        note[Row-wise, Int4, Fast Inference]
        GPTQ --> Marlin_Kernel[Marlin Kernel]
          note[CUDA, A100 Optimized]
        GPTQ --> ExLlama_Kernel[ExLlama Kernel]
          note[CUDA, Faster Inference, Llama]
        GPTQ --> AutoGPTQ[AutoGPTQ]
          note[Original Library, Potentially Deprecated]
        GPTQ --> GPTQModel[GPTQModel]
          note[Maintained Fork, Broader Support]
      Calibration_Needed --> AWQ[AWQ]
        note[Activation-Aware, 4-bit, Near-Lossless]
        AWQ --> Fused_Modules[Fused Modules]
          note[Improved Perf, Llama/Mistral]
        AWQ --> ExLlama_v2_Support[ExLlama-v2 Support]
          note[Faster Prefill/Decode]
        AWQ --> Intel_CPU_GPU_Support[Intel CPU/GPU Support]
          note[IPEX Optimizations]
      Calibration_Needed --> VPTQ[VPTQ]
        note["Vector PTQ, Ultra-Low Bit (<2-bit), High Accuracy"]
        VPTQ --> Low_Bitwidth_Focus[Low Bitwidth Focus]
          note[1-2 bits, 70B & 405B Models]
        VPTQ --> VPTQ_Community_Models[VPTQ Community Models]
          note[Pre-quantized Models on Hub]
      Calibration_Needed --> SpQR[SpQR]
        note[Sparse-Quantized, 3-bit, Near-Lossless]
        SpQR --> Tiled_Quantization[Tiled Quantization]
          note[16x16 Bi-level Group]

    Calibration_Free["Calibration Free"]
      Calibration_Free --> HQQ[HQQ]
        note[On-the-Fly, Robust Optimization, Any Model]
        HQQ --> Optimized_Runtime[Optimized Runtime]
          note[PyTorch/CUDA Kernels, Fused Kernels]
      Calibration_Free --> EETQ[EETQ]
        note[Int8 Weight-Only, Per-Channel, NVIDIA GPUs]
        EETQ --> FasterTransformer_Kernels[FasterTransformer Kernels]
          note[High-Performance GEMM/GEMV]
      Calibration_Free --> HIGGS[HIGGS]
        note[0-Shot, Hadamard, MSE-Optimal, SOTA Performance]
        HIGGS --> FLUTE_Runtime[FLUTE Runtime]
          note[Optimized for Llama3, Gemma-2]
        HIGGS --> Torch_Compile_Compatible[Torch Compile Compatible]
          note[Speedups with torch.compile]
      Calibration_Free --> bitsandbytes[bitsandbytes]
        note[Easy 8-bit & 4-bit, Versatile, Multi-Backend]
        bitsandbytes --> LLM_int8["LLM.int8() (8-bit)"]
          note[Outlier Handling, Offloading]
        bitsandbytes --> QLoRA_4bit["QLoRA (4-bit)"]
          note[NF4, Nested Quantization, Compute Dtype]
      Calibration_Free --> Optimum_quanto[Optimum-quanto]
        note[Versatile Toolkit, Linear Quantization, Multi-Hardware]
        Optimum_quanto --> Weights_Quantization[Weights Quantization Focus]
          note[Int2-Int8, Float8]
        Optimum_quanto --> Device_Agnostic[Device Agnostic]
          note[CUDA, XPU, MPS, CPU]
      Calibration_Free --> FBGEMM_FP8[FBGEMM FP8]
        note["FP8 (W8A8), Per-Channel Weights, Per-Token Activations"]
        FBGEMM_FP8 --> FBGEMM_Library[FBGEMM Library]
          note[Efficient Low-Precision GEMM]
      Calibration_Free --> Fine_grained_FP8[Fine-grained FP8]
        note["FP8 (W8A8), Block-wise Weights, Group-wise Activations"]
        Fine_grained_FP8 --> DeepSeek_Inspired[DeepSeek Inspired]
          note[Block & Group Quantization Scheme]
      Calibration_Free --> TorchAO[TorchAO]
        note[Architecture Optimization, High-Performance, Tensor Subclasses]
        TorchAO --> Tensor_Subclasses[Tensor Subclasses]
          note[Non-Safetensor Serialization]
      Calibration_Free --> Compressed_Tensors[Compressed Tensors]
        note[Unified Format, Versatile, Multi-Scheme Support]
        Compressed_Tensors --> Multiple_Formats[Multiple Formats]
          note[Dense, Int-Quantized, Float-Quantized, Pack-Quantized]

    Hardware_Optimization["Hardware Optimization Focus"]
      Hardware_Optimization --> Optimum[Optimum Library]
        note[Intel, Furiosa, ONNX Runtime]
      Hardware_Optimization --> TorchAO["TorchAO"]
      Hardware_Optimization --> FBGEMM_FP8["FBGEMM FP8"]
      Hardware_Optimization --> Fine_grained_FP8["Fine-grained FP8"]
      Hardware_Optimization --> EETQ["EETQ"]
      Hardware_Optimization --> Marlin_Kernel["Marlin Kernel"]
      Hardware_Optimization --> ExLlama_Kernel["ExLlama Kernel"]
      Hardware_Optimization --> ExLlama_v2_Support["ExLlama v2 Support"]
      Hardware_Optimization --> Intel_CPU_GPU_Support["Intel CPU GPU Support"]
      Hardware_Optimization --> FLUTE_Runtime["FLUTE Runtime"]
      Hardware_Optimization --> VPTQ["VPTQ"]
    %%   Though VPTQ is also about accuracy, its speed is a key selling point

    Bitwidth_Spectrum["Bitwidth Spectrum"]
      Bitwidth_Spectrum --> Ultra_Low_Bitwidth["Ultra-Low Bitwidth<br>(less than 2-bit)"]
        Bitwidth_Spectrum --> VPTQ["VPTQ"]
      Bitwidth_Spectrum --> Three_Bit["3-bit"]
        Bitwidth_Spectrum --> SpQR["SpQR"]
      Bitwidth_Spectrum --> Four_Bit["4-bit"]
        Bitwidth_Spectrum --> GPTQ["GPTQ"]
        Bitwidth_Spectrum --> AWQ["AWQ"]
        Bitwidth_Spectrum --> bitsandbytes["bitsandbytes<br>(QLoRA)"]
        Bitwidth_Spectrum --> Optimum_quanto["Optimum_quanto"]
        Bitwidth_Spectrum --> HIGGS["HIGGS"]
        Bitwidth_Spectrum --> HQQ["HQQ"]
        Bitwidth_Spectrum --> TorchAO["TorchAO"]
      Bitwidth_Spectrum --> Eight_Bit["8-bit"]
        Bitwidth_Spectrum --> bitsandbytes["bitsandbytes<br>(LLM.int8)"]
        Bitwidth_Spectrum --> EETQ["EETQ"]
        Bitwidth_Spectrum --> FBGEMM_FP8["FBGEMM FP8"]
        Bitwidth_Spectrum --> Fine_grained_FP8["Fine-grained FP8"]
        Bitwidth_Spectrum --> Optimum_quanto["Optimum quanto"]
        Bitwidth_Spectrum --> TorchAO["TorchAO"]
      Bitwidth_Spectrum --> Arbitrary_Bitwidth["Arbitrary Bitwidth"]
        Bitwidth_Spectrum --> Compressed_Tensors["Compressed Tensors"]

    Serialization_Support["Serialization Support"]
      Serialization_Support --> bitsandbytes["bitsandbytes"]
      Serialization_Support --> GPTQ["GPTQ"]
      Serialization_Support --> EETQ["EETQ"]
      Serialization_Support --> FBGEMM_FP8["FBGEMM FP8"]
      Serialization_Support --> Fine_grained_FP8["Fine-grained FP8"]
      Serialization_Support --> Compressed_Tensors["Compressed Tensors"]
      Serialization_Support --> TorchAO["TorchAO"]
        note[Non-Safetensor Only]

    PEFT_Finetuning_Support["PEFT Finetuning Support"]
      PEFT_Finetuning_Support --> bitsandbytes["bitsandbytes"]
      PEFT_Finetuning_Support --> AQLM["AQLM"]
      PEFT_Finetuning_Support --> AWQ["AWQ"]
    %%   Implicitly supported through libraries like AutoAWQ and Optimum

    On_the_Fly_Quantization["On-the-Fly Quantization"]
      On_the_Fly_Quantization --> bitsandbytes["bitsandbytes"]
      On_the_Fly_Quantization --> HQQ["HQQ"]
      On_the_Fly_Quantization --> EETQ["EETQ"]
      On_the_Fly_Quantization --> FBGEMM_FP8["FBGEMM FP8"]
      On_the_Fly_Quantization --> Fine_grained_FP8["Fine-grained FP8"]
      On_the_Fly_Quantization --> TorchAO["TorchAO"]
      On_the_Fly_Quantization --> Optimum_quanto["Optimum quanto"]
      On_the_Fly_Quantization --> GPTQ["GPTQ"]
      On_the_Fly_Quantization --> AWQ["AWQ"]
      On_the_Fly_Quantization --> BitNet["BitNet"]
      On_the_Fly_Quantization --> SpQR["SpQR"]
      On_the_Fly_Quantization --> VPTQ["VPTQ"]
      On_the_Fly_Quantization --> HIGGS["HIGGS"]
      On_the_Fly_Quantization --> Compressed_Tensors["Compressed Tensors"]
    %%   Loading is fast, but quantization process is not on-the-fly

```
DOI: [10.13140/RG.2.2.35823.34729](http://dx.doi.org/10.13140/RG.2.2.35823.34729)


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---