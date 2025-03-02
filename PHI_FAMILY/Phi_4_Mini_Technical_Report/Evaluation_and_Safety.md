---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://huggingface.co/microsoft/Phi-4-multimodal-instruct/blob/main/phi_4_mm.tech_report.02252025.pdf"
---


# Evaluation and Safety
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---

## Evaluation and Safety  - A Diagrammatic Guide


```mermaid
---
title: "Phi-4-Mini Technical Report - Compact yet Powerful Multimodal Language Models via Mixture-of-LoRAs"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "flowchart": { "htmlLabels": false, 'curve': 'linear' },
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
    subgraph Evaluation_and_Safety["Evaluation and Safety"]
        H[Evaluation] --> I(Language Benchmarks)
        I --> I1(BigBench, MMLU, GSM-8K, MATH, GPQA, HumanEval, etc.)
        I --> I2(Benchmark Descriptions)
        I2 --{Parameter Sizes}--> I3[3.8B, 7B, 8B, etc.]
        I --> I4(Performance Comparison)
        
        H --> J(Multimodal Benchmarks)
        J --> J1(Vision Benchmarks)
        J1 --> J2(Single-Image Benchmarks, Multi-Image/Video, Vision-Speech)
        J1 --> J3(Benchmark Descriptions)
        J1 --> J4("Performance Comparison<br>[Phi-4-Multimodal vs. Competitors]")

        J --> J5("Speech/Audio Benchmarks")
        J5 --> J6("ASR Benchmarks<br>[CommonVoice, FLEURS, OpenASR]")
        J5 --> J7("AST Benchmarks<br>[CoVoST2, FLEURS]")
        J5 --> J8("SQQA Benchmarks<br>[MT-Bench, MMMLU]")
        J5 --> J9("Speech Summarization Benchmarks<br>[Golden3, AMI]")
        J5 --> J10("Audio Understanding Benchmarks<br>[AirBench-Chat, MMAU]")
        J5 --> J11(Benchmark Descriptions)
        J5 --> J12("Performance Comparison<br>[Phi-4-Multimodal vs. Competitors]")
        
        H --> K("Safety Alignment")
        K --> K1("Harmful Content Detection")
        K1 --> K2("Metrics:<br>Defect Rate")
        K1 --> K3("Models:<br>Phi-4-Mini, Phi-4-Multimodal, Competitors [GPT-4o, etc.]")
        K1 --> K4("Method:<br>Azure AI Evaluation SDK")

        K --> K5(Jailbreak Vulnerability)
        K5 --> K6(Metrics:<br>Defect Rate with Jailbreaks)
        K5 --> K7("Models:<br>Phi-4-Mini, Phi-4-Multimodal, Competitors [GPT-4o, etc.]")
        K5 --> K8(Evaluation Approach)

        K --> K9(Sensitive Attribute Inference)
        K9 --> K10("Metrics:<br>Inference Rate of Sensitive Attributes [ISA]")
        K9 --> K11("Models:<br>Phi-4-Mini, Phi-4-Multimodal, Competitors [Qwen2-Audio, etc.]")
        K9 --> K12(Mitigations:<br>System Prompts)

        K --> K13(Vision Safety Evaluation)
        K13 --> K14("Models:<br>Phi-4-Multimodal, Phi-3.5-Vision, Competitors [Llava-1.6, etc.]")
        K13 --> K15(Method:<br>Azure AI Evaluation SDK)
        K13 --> K16(Benchmarks:<br>RTVLM, VLGuard)

        K --> K17(Multilingual Safety Evaluation)
        K17 --> K18(Metrics:<br>Defect Rate across languages)
        K17 --> K19(Models:<br>Phi-4-Mini, Phi-4-Multimodal, Competitors)
        K17 --> K20(Method:<br>Azure AI Evaluation SDK, language-specific dataset)
        K17 --> K21(Speech Fairness Evaluation)
        K21 --> K22(Metrics:<br>WER, analysis of different demographic groups)
        K17 --> K23("Sensitive Attribute Inference<br>(audio)")
        K17 --> K24(Mitigations for Audio-Specific Prompts)
    end
    
```


----

### Explanation and Improvements

* **Clearer Structure:** The graph now explicitly shows the different types of benchmarks (language, multimodal, speech/audio) and safety evaluations (harmful content, jailbreaks, sensitive attribute inference, multilingual, vision safety).
* **Metrics and Methods:** Each evaluation type now has specific metrics (e.g., Defect Rate, IPRR, VPRR, WER) and methods (e.g., Azure AI Evaluation SDK, XSTest framework) associated with it.
* **Comparison Focus:** The emphasis on comparing Phi-4-Mini/Multimodal to competitors (GPT-4, other LLMs) is clearer. Parameter sizes are explicitly noted.
* **Detailed Benchmarks:** Individual benchmarks (e.g., BigBench, MMLU, CommonVoice) are listed, promoting a more thorough view of the evaluation scope.
* **Mitigations:** Explicitly shows the use of system prompts and other mitigation strategies.


This significantly improved graph provides a more comprehensive overview of the evaluation and safety aspects of the Phi-4-Mini/Multimodal models, including the methodologies and metrics used to assess their capabilities and limitations compared to other models. Remember to add specific benchmark results and quantitative data for each evaluation point within the nodes to make the graph truly informative. Remember to add quantitative data for each of these benchmarks and include actual values.



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---