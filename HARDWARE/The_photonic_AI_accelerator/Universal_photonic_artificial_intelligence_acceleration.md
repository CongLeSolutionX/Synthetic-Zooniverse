---
created: 2025-03-09 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://doi.org/10.1038/s41586-025-08854-x"
---



# Universal photonic artificial intelligence acceleration
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Paper Overview

The paper introduces a novel photonic AI processor designed to address the limitations of traditional electronic hardware posed by the end of Moore's Law and Dennard scaling. Built by Lightmatter, this processor integrates photonic and electronic components (four 90nm Photonic Tensor Cores (PTCs) and two 12nm Digital Control Interface (DCI) chips) in a single package. It aims to perform high-speed, energy-efficient tensor operations, specifically matrix-vector products (MVPs), crucial for AI workloads.

Key achievements highlighted are:
1.  **First Photonic Processor for Advanced AI:** Capable of running complex models like ResNet, BERT, and DeepMind's Atari reinforcement learning algorithms directly.
2.  **Near-Digital Precision:** Achieves accuracies comparable to 32-bit floating-point (FP32) systems on many tasks *without* specialized retraining (like quantization-aware training), using an Adaptive Block Floating-Point (ABFP) format.
3.  **High Integration & Performance:** Combines six chips with high-speed interconnects. It reports a capability of 65.5 TFLOPs (ABFP16) at 78W electrical + 1.6W optical power, though current operation is at a reduced clock speed (500 MHz) due to DCI clock tree issues, with potential for 2 GHz (262 TFLOPS).
4.  **Hybrid Architecture:** Leverages photonics for the core matrix multiplication (within PTCs) and advanced CMOS (12nm DCI) for control, data management (unified buffer, RISC cores, NCE), and high-speed data conversion (ADCs/DACs).

The architecture uses differential light encoding for vectors, hybrid photonic-electronic unit cells for weights, and electrical current summation for outputs. While achieving significant results, limitations include optical power constraints due to silicon nonlinear absorption (affecting gain and thus accuracy on larger models) and the current clock speed bottleneck. Future work focuses on scaling, developing memory-aware network architectures, overcoming material limitations, and potentially using Wavelength Division Multiplexing (WDM).

---
 
## Mermaid Diagrams and Explanations

Here are diagrams illustrating the core concepts:


---

## 1. High-Level System Architecture & Interaction

This diagram shows the main components and the flow of control and data from the host system to the photonic processor.

```mermaid
---
title: "High-Level System Architecture & Interaction"
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
    subgraph HostSystem["Host System<br/>(x86 CPU + Linux)"]
        direction LR
        HostApp["Host Program<br/>(Python Interface)"] --> Compiler["Compiler<br/>(PyTorch/TF -> Binaries/ISA)"]
        Compiler --> HostBin["Host x86 Binary"]
        Compiler --> RISCVBin["RISC-V Binary"]
        Compiler --> ISA["Device ISA Code"]
    end

    subgraph PhotonicProcessorCard["Photonic Processor<br/>(PCIe Card)"]
        direction LR
        PCIe["PCIe Gen4 x16 Interface"]
        subgraph DCI["Digital Control Interface<br/>(12nm CMOS)"]
            direction TB
            CTRL["CTRL Sequencer<br/>(NuttX RTOS)"]
            RISCV["RISC-V Cores<br/>(x64)"]
            Memory["Unified Buffer<br/>(SRAM)"]
            NCE["Neural Compute Engine<br/>(SIMD)"]
            Pipelines["Input/Output Pipelines"]
            ADCs["High-Speed ADCs"]
            WeightIF["Weight Interface"]
        end
        subgraph PTCs["Photonic Tensor Cores<br/>(x4, 90nm Photonics)"]
             direction TB
             PVU["Photonic Vector Units<br/>(10-bit)"]
             PWU["Photonic Weight Units<br/>(7-bit)"]
             Stabilization["Stabilization & Monitoring"]
        end
        Lasers["External Laser Source<br/>(8x DFB, 1310nm)"] --> PTCs
        PCIe --> DCI
        DCI -- "Control & Data" --> PTCs
        PTCs -- "Processed Data" --> DCI

    end

    HostSystem -- "Binaries, ISA, Data over PCIe" --> PCIe
    PCIe -- "Results back to Host" --> HostSystem

    Memory -- "Weights/Activations/Data" <--> NCE
    Memory -- "Weights/Data" <--> RISCV
    Memory -- "Weights" --> WeightIF
    WeightIF --> PTCs
    CTRL -- "Commands" --> RISCV
    CTRL -- "Commands" --> NCE
    CTRL -- "Commands" --> Pipelines
    RISCV -- "Calibration/Support" --> PTCs
    NCE -- "On-the-fly Weights/Data" --> Pipelines
    Pipelines -- "Activations" --> PTCs
    PTCs -- "Output Current" --> ADCs
    ADCs -- "Digital Output" --> Pipelines
    Pipelines -- "Accumulation/Results" --> Memory

```

**Explanation:** The host system compiles the AI model into binaries and instruction sets (ISA). These are sent via PCIe to the Digital Control Interface (DCI) chip. The DCI manages execution using RISC-V cores and a Neural Compute Engine (NCE), storing data in a unified buffer. It sends weights and activation vectors (after conversion) to the Photonic Tensor Cores (PTCs). External lasers provide light. PTCs perform the core matrix-vector product using photonics. The results (electrical currents) are converted back to digital by ADCs in the DCI, processed by pipelines, potentially accumulated, stored back in the buffer, and finally sent back to the host.


---

## 2. Physical Chip Packaging Architecture


This diagram illustrates the physical arrangement of the different chips within the packaged processor, highlighting the 3D integration.

```mermaid
---
title: "Physical Chip Packaging Architecture"
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
    subgraph ProcessorPackage["Packaged Photonic Processor"]
        direction TB
        TopHeatSpreader["Heat Spreader<br/>(Top)"]
        DCI_Die1["DCI Die 1<br/>(12nm CMOS)"]
        DCI_Die2["DCI Die 2<br/>(12nm CMOS)"]
        Interposer["Organic Interposer w/ Stacked Vias"]
        PTC_Die1["PTC Die 1<br/>(90nm Photonics)"]
        PTC_Die2["PTC Die 2<br/>(90nm Photonics)"]
        PTC_Die3["PTC Die 3<br/>(90nm Photonics)"]
        PTC_Die4["PTC Die 4<br/>(90nm Photonics)"]
        BottomSubstrate["Bottom Substrate<br/>(BGA)"]
        BottomHeatSpreader["Heat Spreader<br/>(Bottom/Silicon)"]
    end

    TopHeatSpreader --> DCI_Die1
    TopHeatSpreader --> DCI_Die2
    DCI_Die1 -- "Electrical Connection" --> Interposer
    DCI_Die2 -- "Electrical Connection" --> Interposer
    Interposer -- "Electrical Connection" --> PTC_Die1
    Interposer -- "Electrical Connection" --> PTC_Die2
    Interposer -- "Electrical Connection" --> PTC_Die3
    Interposer -- "Electrical Connection" --> PTC_Die4
    PTC_Die1 --> BottomSubstrate
    PTC_Die2 --> BottomSubstrate
    PTC_Die3 --> BottomSubstrate
    PTC_Die4 --> BottomSubstrate
    PTC_Die1 --- BottomHeatSpreader
    PTC_Die2 --- BottomHeatSpreader
    PTC_Die3 --- BottomHeatSpreader
    PTC_Die4 --- BottomHeatSpreader

    style DCI_Die1 fill:#lightblue,stroke:#333,stroke-width:2px
    style DCI_Die2 fill:#lightblue,stroke:#333,stroke-width:2px
    style PTC_Die1 fill:#lightgreen,stroke:#333,stroke-width:2px
    style PTC_Die2 fill:#lightgreen,stroke:#333,stroke-width:2px
    style PTC_Die3 fill:#lightgreen,stroke:#333,stroke-width:2px
    style PTC_Die4 fill:#lightgreen,stroke:#333,stroke-width:2px
    style Interposer fill:#lightgrey,stroke:#333,stroke-width:2px
    
```

**Explanation:** This shows the vertical stacking. The two large 12nm DCI chips sit on top of an organic interposer. Four smaller 90nm PTC chips are mounted underneath the interposer, allowing direct, high-density electrical connections between the DCI and PTCs. Heat spreaders manage thermal dissipation from both DCI and PTC layers. The entire assembly connects to the outside world via a Ball Grid Array (BGA) on the bottom substrate.

---


## 3. Photonic Tensor Core (PTC) - Conceptual Data Flow for MVP


This simplified diagram illustrates the data flow within a single PTC during a Matrix-Vector Product (MVP) operation.

```mermaid
---
title: "Photonic Tensor Core (PTC) - Conceptual Data Flow for MVP"
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
graph LR
    subgraph DCI_Interface["From/To DCI"]
        WeightsIn["Weights<br/>(7-bit ABFP)"]
        ActivationsIn["Activations<br/>(10-bit ABFP)"]
        OutputDataOut["Partial Sum Out<br/>(bfloat16)"]
    end

    subgraph PTC["Photonic Tensor Core<br/>(Conceptual 128x128)"]
        direction TB
        WeightUnitCells["Weight Unit Cells (128x128)<br/> Hybrid Photodetector + 7-bit DAC"]
        VectorEncoders["Vector Encoders (x128) <br/> 10-bit DAC + MZI Modulator"]

        subgraph PhotonicMesh["Photonic Distribution & Interaction"]
             LightSource["Input Light<br/>(From Laser via Tree)"] --> VectorEncoders
             VectorEncoders -- "Modulated Light<br/>(Represents Activation Vector x)" --> WeightUnitCells
        end

        subgraph ElectricalSummation["Electrical Domain"]
             WeightUnitCells -- "Scaled Photocurrent<br/>(Wij * xi)" --> SummationWires["Differential Current Summation Wires"]
             SummationWires -- "Summed Current<br/>(Σ Wij * xi)" --> TIA_Array["TIA Array<br/>(x128)"]
             TIA_Array -- "Amplified Voltage" --> ADC_Array["ADC Array (x128, 11-bit) <br/> [Located in DCI]"]
        end
    end

    WeightsIn --> WeightUnitCells
    ActivationsIn --> VectorEncoders
    ADC_Array --> OutputDataOut


    style WeightUnitCells fill:#lightcoral,stroke:#333
    style VectorEncoders fill:#lightskyblue,stroke:#333
    style PhotonicMesh fill:#lightyellow,stroke:#333,stroke-dasharray: 5 5
    style ElectricalSummation fill:#lightgrey,stroke:#333,stroke-dasharray: 5 5
    
```


**Explanation:** Within a PTC, activation vector elements (`x`) are encoded onto optical signals using Mach-Zehnder Interferometers (MZIs), driven by DACs (Vector Encoders). These optical signals are distributed to an array of Weight Unit Cells. Each weight unit cell contains a photodetector and a DAC that sets the weight value (`Wij`). The cell multiplies the incoming optical power (representing `xi`) by the programmed weight (`Wij`), producing a proportional photocurrent. The photocurrents from all weight cells corresponding to a single output element are summed electrically along shared wires. This summed current (representing the dot product) is amplified by a Transimpedance Amplifier (TIA) and then converted back to a digital value by a high-speed Analog-to-Digital Converter (ADC), technically located in the DCI but logically part of the PTC output chain.

---


## 4. Adaptive Block Floating-Point (ABFP) Conversion and Computation Flow


This diagram outlines the process of converting standard floating-point numbers to the ABFP format used by the PTC, the computation, and the conversion back.

```mermaid
---
title: "Adaptive Block Floating-Point (ABFP) Conversion and Computation Flow"
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
    Start["Input Tensors<br/>(Weights W, Activations X)<br/> Format: bfloat16 in DCI"]
    --> NormalizeW["Normalize Weight Vector<br/>(per 128 elements):<br/> w_norm = W_vec / max(|W_vec|) <br/> Store scale s_w = max(|W_vec|)"]
    --> QuantizeW["Quantize Normalized Weights:<br/> w_q = Quantize(w_norm, 7 bits)"]

    Start --> NormalizeX["Normalize Activation Vector<br/>(per 128 elements): <br/> x_norm = X_vec / max(|X_vec|) <br/> Store scale s_x = max(|X_vec|)"]
    --> QuantizeX["Quantize Normalized Activations:<br/> x_q = Quantize(x_norm, 10 bits)"]

    subgraph PTC_Compute["Photonic Tensor Core Computation"]
        QuantizeW -- "7-bit weights" --> PTC_MVP["Matrix-Vector Multiply <br/> Y_raw = w_q * x_q<br/>(Analog Domain)"]
        QuantizeX -- "10-bit activations" --> PTC_MVP
    end

    subgraph Output_Processing["Output Processing<br/>(in DCI)"]
        PTC_MVP -- "Analog Output Current" --> TIA["Apply Gain<br/>(TIA)"]
        TIA -- "Amplified Voltage" --> ADC["Digitize<br/>(ADC, 11 bits)<br/> Y_adc"]
        ADC -- "Digital Output" --> Rescale["Rescale to bfloat16:<br/> Y_out = Y_adc * s_w * s_x"]
        Rescale --> Accumulate["Accumulate Partial Sums<br/> (if needed, bfloat16/bfloat24)"]
    end

    Accumulate --> FinalResult["Final Output Tensor Y<br/> Format: bfloat16"]

    style Start fill:#lightblue
    style PTC_Compute fill:#lightgreen
    style Output_Processing fill:#lightgrey
    style FinalResult fill:#lightblue
    
```


**Explanation:** Standard bfloat16 weight and activation vectors (handled in the DCI) are converted to the ABFP format before being sent to the PTC. This involves normalizing each 128-element vector by its maximum absolute value (storing this scale factor) and then quantizing the normalized vector to the PTC's precision (7 bits for weights, 10 bits for activations). The PTC performs the multiplication in the analog domain using these quantized values. The resulting analog output is amplified (TIA) and digitized (ADC). Back in the DCI, this digital result is rescaled using the stored scale factors (`s_w` and `s_x`) to convert it back to a bfloat16 representation. Partial results for larger matrix multiplications are accumulated in bfloat16 or bfloat24 precision.

---

## 5. AI Workload Performance Summary & Influencing Factors

This diagram summarizes the processor's performance on different AI tasks and highlights the key factors affecting accuracy.

```mermaid
---
title: "AI Workload Performance Summary & Influencing Factors"
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
    subgraph Processor["Photonic AI Processor"]
        Input["AI Model & Input Data <br/> (e.g., ResNet/CIFAR, BERT/IMDb, DQN/Atari)"] --> Execution["Execute on Photonic Hardware<br/>(ABFP)"]
        Execution --> Output["Model Output<br/>(Predictions, Actions, Text)"]
    end

    subgraph EvaluationMetrics["Evaluation"]
        FP32["FP32 Baseline<br/>(Digital Reference)"]
        Accuracy["Task Accuracy / Score"]
        Comparison["Compare Photonic vs. FP32"]
    end

    Output --> Comparison
    FP32 --> Comparison
    Comparison --> Accuracy

    subgraph PerformanceFactors ["Factors Affecting Accuracy"]
        direction LR
        Noise["Analog Noise<br/>(Logistic-like error)"]
        Precision["Limited Precision<br/>(ABFP: 7/10 bits)"]
        GainLimit["Optical Power/Gain Limitation <br/> (Due to Si Nonlinear Absorption)"]
        ModelSize["Model Complexity/Size"]
        TaskType["Task Type<br/>(Classification vs. Regression)"]
    end

    subgraph MitigationTechniques["Potential Accuracy Improvements"]
        QAT["Quantization-Aware Training (QAT) / Fine-tuning"]
        HardwareOpts["Hardware Enhancements<br/>(e.g., higher gain, better materials)"]
    end

    Accuracy -- "Affected by" --> PerformanceFactors
    Accuracy -- "Can be Improved by" --> MitigationTechniques


    style Processor fill:#lightcyan
    style EvaluationMetrics fill:#honeydew
    style PerformanceFactors fill:#lavenderblush
    style MitigationTechniques fill:#cornsilk

    %% Example Results (Highlights)
    Comparison -- "Classification(ResNet, BERT-IMDb):<br/>Near FP32 Accuracy" --> Accuracy
    Comparison -- "Regression (BERT-SQuAD):<br/>Reduced Accuracy" --> Accuracy
    Comparison -- "Reinforcement Learning (Atari):<br/>Functional but < FP32 Score" --> Accuracy
    QAT -- "Shown Effective<br/>(ResNet18/ImageWoof)" --> Accuracy
    GainLimit -- "Major Limiting Factor Identified" --> Accuracy
    
```


**Explanation**: The processor runs various AI models. Its output is compared against a standard 32-bit floating-point (FP32) baseline to measure accuracy. Performance is generally close to FP32 for classification tasks but degrades for regression and complex reinforcement learning, primarily attributed to limited optical gain (due to silicon nonlinearities), inherent analog noise, and the limited precision of the ABFP format. Larger models are more affected due to the gain issue. Techniques like Quantization-Aware Training (QAT) can substantially recover lost accuracy by adapting the model to the hardware's characteristics during training.




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---