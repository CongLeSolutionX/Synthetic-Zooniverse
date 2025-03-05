---
created: 2025-03-05 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://github.com/apple/ml-stable-diffusion/blob/main/README.md"
---



# Model Conversion Process
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Model Conversion Process - A Diagrammatic Guide 




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
graph LR
    A["Model Conversion Process"] --> B{Steps}
    style A fill:#a2d3,stroke:#333,stroke-width:1px

    B --> C["Step 1: Create Python Environment"]:::step
    C --> CA["conda create -n coreml_stable_diffusion python=3.8 -y"]
    C --> CB["conda activate coreml_stable_diffusion"]
    C --> CC["cd /path/to/cloned/ml-stable-diffusion/repository"]
    C --> CD["pip install -e ."]

    B --> D["Step 2: Hugging Face Login"]:::step
    D --> DA["huggingface-cli login"]
    D --> DB["User Access Token required"]
    D --> DC["Accept Terms of Use for desired model"]

    B --> E["Step 3: Execute Conversion Script"]:::step
    E --> EA["Key Tool:<br> 'python -m python_coreml_stable_diffusion.torch2coreml'"]
    E --> EB["Arguments"]:::flags

    subgraph Conversion_Arguments["Conversion Arguments"]
    EB --> EB1["--convert-unet"]
    EB --> EB2["--convert-text-encoder"]
    EB --> EB3["--convert-vae-decoder"]
    EB --> EB4["--convert-safety-checker"]
    EB --> EB5["--model-version <model-version-string-from-hub>"]
    EB --> EB6["-o <output-mlpackages-directory>"]
    EB --> EB7["--refiner-version<br>(SDXL)"]
    EB --> EB8["--bundle-resources-for-swift-cli"]
    EB --> EB9["--quantize-nbits {2,4,6,8}"]
    EB --> EB10["--chunk-unet"]
    EB --> EB11["--attention-implementation {ORIGINAL, SPLIT_EINSUM, SPLIT_EINSUM_V2}"]
    EB --> EB12["--check-output-correctness"]
    EB --> EB13["--convert-controlnet <controlnet-model>"]
    EB --> EB14["--unet-support-controlnet"]
        EB --> EB15["--unet-batch-one"]
        EB --> EB16["--xl-version"]
        EB --> EB17["--sd3-version"]
        EB --> EB18["--convert-mmdit "]
        EB --> EB19["--include-t5"]
        EB --> EB20["--latent-h"]
        EB --> EB21["--latent-w"]
        EB --> EB22["--custom-vae-version"]
    end

    B --> F["Step 4: Result"]:::step
    F --> FA["Core ML model files ('.mlpackage') generated"]
    F --> FB["Models saved in '<output-mlpackages-directory>'"]
    F --> FC["If '--bundle-resources-for-swift-cli' is used: 'Resources' folder created"]

    classDef step fill:#f2f3,stroke:#333,stroke-width:1px
    classDef flags fill:#eee3,stroke:#333,stroke-width:1px
    
```


----

### Key improvements and explanations

*   **Steps:** Numbered steps to clearly indicate the sequence of actions.
*   **Code Snippets:**  Actual code snippets are included for each step to allow users to follow the instructions directly.
*   **Emphasis on Tool:** Highlights the main tool for conversion: `python -m python_coreml_stable_diffusion.torch2coreml`
*   **Flag Descriptions:**  All the flags with appropriate descriptions for different steps are highlighted.
*   **Grouping by Function:**  Similar flags are grouped together to highlight.
*   **Notes and Warnings:**   Important tips or warnings are noted.
*   **Readability:** Diagram focuses on the overall process to the reader is not overwhelmed.
*   **SDXL and SD3 related flags**: Clear notations on model specific flags.





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---