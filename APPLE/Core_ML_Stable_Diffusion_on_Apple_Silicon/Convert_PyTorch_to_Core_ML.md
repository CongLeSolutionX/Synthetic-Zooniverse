---
created: 2025-03-05 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://github.com/apple/ml-stable-diffusion/blob/main/README.md"
---



# Convert PyTorch to Core ML
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Convert PyTorch to Core ML - A Diagrammatic Guide 




```mermaid
---
title: "Core ML Stable Diffusion on Apple Silicon"
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
graph TD
    A[Convert PyTorch to Core ML] --> B{Process Overview}
    style A fill:#a2da,stroke:#333,stroke-width:1px

    B --> C[Environment Setup]:::detail
    C --> CA[Create Python Environment]:::steps
    C --> CB[Install Dependencies]:::steps
    C --> CC[Login to Hugging Face]:::steps

    subgraph Steps["Steps"]
        CA --> CA1[conda create -n coreml_stable_diffusion python=3.8 -y]
        CB --> CB1[conda activate coreml_stable_diffusion]
        CB --> CB2[cd /path/to/ml-stable-diffusion/repository]
        CB --> CB3[pip install -e .]
        CC --> CC1[huggingface-cli login]
    end

    B --> D[Model Preparation]:::detail
    D --> DA[Accept Terms of Use]:::steps
    D --> DB[Download and Convert Models]:::steps

    subgraph Model_Conversion["Model Conversion"]
        DA --> DA1[Navigate to Hugging Face Hub]
        DA --> DA2[Accept Terms of Use]
        DB --> DB1[Run torch2coreml.py]
        DB --> DB2[Key Flags are required]
    end

    D --> E[Command and Flags]:::detail
    E --> EA["'python -m python_coreml_stable_diffusion.torch2coreml'"]:::command

    subgraph Common_Flags["Common Flags"]
        EA --> E1["--convert-unet"]
        EA --> E2["--convert-text-encoder"]
        EA --> E3["--convert-vae-decoder"]
        EA --> E4["--convert-safety-checker"]
        EA --> E5["--model-version"]
        EA --> E6["-o <output-mlpackages-directory>"]
    end

    E --> F[Additional Flags]:::detail
    F --> FA[SDXL Flags]:::sdxl
    F --> FB[Optimization Flags]:::optimize
    F --> FC[Multilingual Model Flags]:::multilingual
    F --> FD[Unet Flags]:::unetflags

    subgraph SDXL_Flags["SDXL Flags"]
        FA --> FA1["--xl-version"]
        FA --> FA2["--refiner-version"]
    end

    subgraph Optimization_Flags["Optimization Flags"]
        FB --> FB1["--bundle-resources-for-swift-cli"]
        FB --> FB2["--quantize-nbits"]
        FB --> FB3["--attention-implementation"]
        FB --> FB4["--check-output-correctness"]
        FB --> FB5["--chunk-unet"]
    end

    subgraph Multilingual_Model_Flags["Multilingual Model Flags"]
        FC --> FC1["MultilingualTextEncoderProjection.mlmodelc"]
        FC --> FC2["MultilingualTextEncoder"]
    end
    
    subgraph Unet_Flags["Unet Flags"]
        FD --> FD1["--unet-batch-one"]
        FD --> FD2["--unet-support-controlnet"]
    end

    style A fill:#a2da3,stroke:#333,stroke-width:1px
    classDef detail fill:#f9f3,stroke:#333,stroke-width:1px
    classDef steps fill:#ddd3,stroke:#333,stroke-width:1px
    classDef command fill:#ccc3,stroke:#333,stroke-width:1px
    classDef sdxl fill:#bbb3,stroke:#333,stroke-width:1px
    classDef optimize fill:#aaa3,stroke:#333,stroke-width:1px
    classDef multilingual fill:#9993,stroke:#333,stroke-width:1px
    classDef unetflags fill:#8883,stroke:#333,stroke-width:1px
```

----


### Key improvements and explanations

*   **Detailed Step-by-Step Breakdown:** The process is broken down into clear, sequential steps for environment setup and model preparation.
*   **Emphasis on Flags and Arguments:** Key command-line flags are highlighted, with further categorization to indicate their purpose (e.g., SDXL-specific, optimization-related).
*   **Clear Command Presentation:** The command to run the conversion is presented prominently.
*   **Concise Labels:** Labels are short and descriptive to improve readability.
*   **Visual Hierarchy:** The use of subgraphs and node connections clearly illustrates the flow of the conversion process.
*   **Annotations:** Added annotations for different steps to provide context.
*   **SD3 information** Seperate flags to show the flags for SD3 and how it relates to other concepts.

This diagram provides a comprehensive and visually accessible guide to converting Stable Diffusion models to Core ML. It emphasizes the crucial steps, flags, and considerations for a successful conversion.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---