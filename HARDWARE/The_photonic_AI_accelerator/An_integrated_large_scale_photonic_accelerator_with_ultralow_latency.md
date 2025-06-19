---
created: 2025-03-09 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: "https://doi.org/10.1038/s41586-025-08786-6"
---



# An integrated large-scale photonic accelerator with ultralow latency - A Diagrammatic Guide 
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## Integrated Photonic Accelerator (PACE) Overview

This diagram provides a high-level overview of the problem context, the proposed solution (PACE system), its key features, and the main application demonstrated.

```mermaid
---
title: "Integrated Photonic Accelerator (PACE) Overview"
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
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'graph': { 'htmlLabels': false},
    'fontFamily': 'Monospace',
    'themeVariables': {
      'primaryColor': '#B28',
      'primaryTextColor': '#F82',
      'primaryBorderColor': '#7C33',
      'secondaryColor': '#615',
      'lineColor': '#F8B229'
    }
  }
}%%
mindmap
  root((Integrated Large-Scale Photonic Accelerator))
    ::icon(fa fa-brain)
    **Problem Context**
      Growing AI Compute Demands
      Limitations of Electronic Computing
        Power Consumption
        Latency Bottlenecks (esp. MAC)
      Photonic Computing Promise
        High Speed / Bandwidth
        Low Latency Potential
        Energy Efficiency
      Photonic Scaling Challenges
        ::icon(fa fa-exclamation-triangle)
        Device Consistency & Yield
        Complex Circuit Design/Verification
        Advanced Packaging Needs
        Optical-Electronic Co-integration
        Analogue Accuracy

    **Proposed Solution: PACE System**
      ::icon(fa fa-cogs)
      Photonic Arithmetic Computing Engine
      Target: Linear Matrix Multiply-Accumulate (MAC)
      **Key Features**
        Large Scale: >16,000 Photonic Components
        Matrix Size: 64x64 oMAC
        Hybrid Integration
          Photonic_Integrated_Circuit["Photonic Integrated Circuit (PIC) - Silicon Photonics (65nm)"]
          Electronic_Integrated_Circuit["Electronic Integrated Circuit (EIC) - CMOS (28nm)"]
        Advanced Packaging: 2.5D Flip-Chip SiP (System in Package)
        High Speed: Up to 1 GHz Operation
        Ultralow Latency: < 5 ns demonstrated (potential for 3 ns)
        Accuracy: ~7.61 ENOB for oMAC
        Co_integration["Co-integration: Logic, Memory (SRAM), Control in EIC"]

    **Core Technology**
      ::icon(fa fa-lightbulb)
      Optical_MAC["Optical MAC (oMAC) Operation"]
      Incoherent Light Architecture
      Components
        High-Perf Grating Couplers (~ -1 dB loss)
        Mach-Zehnder Modulators (Vector & Weight)
        Germanium Photodetectors (~ 1 A/W)
      Controllable_Noise_Injection["Controllable Noise Injection (Laser, TIA, Digital) for Algorithm"]

    **Demonstrated Application**
      ::icon(fa fa-puzzle-piece)
      Heuristic Recurrent Algorithm for Ising Problems
      Solves Combinatorial Optimization (NP-complete)
        Graph Max-Cut
        Image Memorization (Cat Example)
      Leverages Ultralow Latency
      Performance
        >92% Convergence Rate (@ 5 ns)
        >100x Faster Total Compute Time vs. NVIDIA A10 GPU

    **Significance**
     ::icon(fa fa-trophy)
     Milestone in Large-Scale Photonic Computing
     Demonstrates Viability of Scaled Integration & Packaging
     Highlights Potential for Latency-Sensitive Applications
     Path Towards Commercialization
     
```


---

## Photonic MAC (oMAC) vs. Electronic MAC (TPU) Latency

This diagram conceptually contrasts the latency scaling behavior of the proposed optical MAC approach with a traditional electronic systolic array (like in a TPU).

```mermaid
---
title: "Photonic MAC (oMAC) vs. Electronic MAC (TPU) Latency"
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
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'graph': { 'htmlLabels': false},
    'fontFamily': 'Monospace',
    'themeVariables': {
      'primaryColor': '#B28',
      'primaryTextColor': '#FFF',
      'primaryBorderColor': '#7C33',
      'secondaryColor': '#615',
      'lineColor': '#F8B229'
    }
  }
}%%
graph LR
    subgraph Electronic_MAC["Electronic MAC<br/>(e.g., TPU Systolic Array)"]
        direction TB
        style Electronic_MAC fill:#f9f,stroke:#333,stroke-width:2px
        EM1(Input Data) --> EM2{"Clock Cycle 1:<br/>Local MAC & Shift"}
        EM2 --> EM3{"Clock Cycle 2:<br/>Local MAC & Shift"}
        EM3 --> EM4{...}
        EM4 --> EMN{"Clock Cycle N:<br/>Final MAC"}
        EMN --> EM_Out("Output")
        EM_Note(("Latency ~ N * Clock Period<br/>Scales with Matrix Size (N)<br/>and Clock Cycles"))
    end

    subgraph Photonic_MAC["Photonic MAC<br/>(oMAC - PACE)"]
        direction TB
        style Photonic_MAC fill:#ccf,stroke:#333,stroke-width:2px
        PM1("Input Data Vector") --> PM2["Parallel Optical Multiplication<br/>(Vector * Weight Matrix)"]
        PM2 --> PM3["Optical Signal Propagation & Summation"]
        PM3 --> PM_Out("Output Vector")
        PM_Note(("Latency ~ Optical Path Length<br/>Scales linearly (weakly) with Matrix Size<br/>Independent of Clock Cycles for core MAC"))
    end

    Electronic_MAC --> Comparison{"Latency Comparison"}
    Photonic_MAC --> Comparison
    Comparison --> Result(("oMAC offers significantly lower<br/>latency, especially for large matrices"))
    
```



----

## PACE System Architecture

This diagram details the architecture of the PACE system, showing the interaction between the Electronic Integrated Circuit (EIC) and the Photonic Integrated Circuit (PIC) within the System-in-Package (SiP).

```mermaid
---
title: "PACE System Architecture"
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
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'graph': { 'htmlLabels': false},
    'fontFamily': 'Monospace',
    'themeVariables': {
      'primaryColor': '#B28',
      'primaryTextColor': '#000',
      'primaryBorderColor': '#7C33',
      'secondaryColor': '#615',
      'lineColor': '#F8B229'
    }
  }
}%%
graph TD
    subgraph Host_System
        H[Host Computer]
    end

    subgraph Interface_Module
        SOM["System on Module<br/>(SOM)"]
        ETH[Ethernet IO]
        SPI["Serial Peripheral Interface"]
    end

    subgraph PACE_SiP["System-in-Package (SiP) - 2.5D Advanced Packaging"]
        subgraph EIC["Electronic Integrated Circuit (EIC - 28nm CMOS)"]
            EIC_SPI["SPI Interface"]
            EIC_Logic["Digital Logic & Control"]
            EIC_SRAM["SRAM Memory"]
            EIC_DAC_W["Weight DACs + Drivers"] -->|Weight Data| EIC_PMA_W("EIC-PIC Matrix Connections")
            EIC_DAC_V[Vector DACs + Drivers] -->|Vector Data| EIC_PMA_V("EIC-PIC Vector Connections")
            EIC_Comp[Comparators] --> EIC_Logic
            %% EIC_TIA["Transimpedance Amplifiers<br/>(TIAs)"] <--|Electrical Summed Signal| EIC_PRA("EIC-PIC RX Connections")
        end

        subgraph PIC["Photonic Integrated Circuit (PIC - 65nm Silicon Photonics)"]
            PIC_LI["Laser Input<br/>(External)"] --> PIC_GC(Grating Couplers)
            PIC_GC --> PIC_VM("Vector Modulator Array - 1x64")
            PIC_VM --> PIC_WM("Weight Modulator Matrix - 64x64")
            PIC_WM --> PIC_PD("Photodetector Array - RX")
            PIC_PD --> |Optical Summation| EIC_PRA

            EIC_PMA_V --> PIC_VM
            EIC_PMA_W --> PIC_WM
        end

        EIC_SPI <--> SPI
    end

    Host_System -- Ethernet --> Interface_Module
    Interface_Module -- SPI --> PACE_SiP

    style PIC fill:#lightblue,stroke:#333,stroke-width:2px
    style EIC fill:#lightgrey,stroke:#333,stroke-width:2px
    style PACE_SiP fill:#eee,stroke:#000,stroke-width:3px
    
```

----

## Heuristic Recurrent Algorithm for Ising Problems (Implemented on PACE)

This flowchart illustrates the steps of the iterative heuristic algorithm used to solve Ising problems on the PACE hardware.

```mermaid
---
title: "Heuristic Recurrent Algorithm for Ising Problems (Implemented on PACE)"
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
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'graph': { 'htmlLabels': false},
    'fontFamily': 'Monospace',
    'themeVariables': {
      'primaryColor': '#B28',
      'primaryTextColor': '#000',
      'primaryBorderColor': '#7C33',
      'secondaryColor': '#615',
      'lineColor': '#F8B229'
    }
  }
}%%
graph TD
    A["Start: Define Ising Problem<br/>(Matrix K)"] --> B(Map K to Weight Matrix W)
    B --> C("Load W into Weight Modulators")
    C --> D{"Initialize Random Spin State S(t)"}
    D --> E("Load S(t) into Vector Modulators")
    E --> F["Perform oMAC: v(t) = W * S(t)"]
    F --> G("Add Controllable Noise Sources<br/>Laser, TIA, Digital")
    G --> H["Receive & Amplify Signal<br/>(TIA)"]
    H --> I{"Compare v(t) with Pre-computed Threshold T"}
    I --> J["Generate New Spin State S(t+1) <br/> (0 if v < T, 1 if v >= T)"]
    J --> K{"Store S(t+1) / Calculate Energy<br/>(Optional Parallel)"}
    K --> L{"Reached Max Iterations<br/>(e.g., 5000)?"}
    L -- No --> M{"Check Convergence<br/>(Energy Minima?)"}
    
    %% Loop back with S(t+1)
    M -- No --> E
    
    L -- Yes --> N["End: Output Best Found State"]
	
	%% Converged
    M -- Yes --> N

    subgraph PACE_Hardware_Core["PACE Hardware Loop"]
      direction LR
        E
        F
        G
        H
        I
        J
    end

    style PACE_Hardware_Core fill:#def,stroke:#333,stroke-width:1px,stroke-dasharray: 5 5
    
```

---

## PACE System - Addressing Key Photonic Scaling Challenges

This diagram shows how the design and implementation of the PACE system address the critical challenges faced in scaling integrated photonics.

```mermaid
---
title: "PACE System - Addressing Key Photonic Scaling Challenges"
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
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'graph': { 'htmlLabels': false},
    'fontFamily': 'Monospace',
    'themeVariables': {
      'primaryColor': '#B28',
      'primaryTextColor': '#FFF',
      'primaryBorderColor': '#7C33',
      'secondaryColor': '#615',
      'lineColor': '#F8B229'
    }
  }
}%%
graph LR
    subgraph Challenges["Scaling Challenges in Integrated Photonics"]
        C1["Large-Scale Integration & Yield"]
        C2["Device Performance Consistency"]
        C3["Complex Circuit Design/Verification"]
        C4["Advanced Packaging<br/>(Optical-Electronic)"]
        C5["Analogue Computation Accuracy"]
        C6["Algorithm/Hardware Compatibility"]
    end

    subgraph PACE_Solutions["PACE System Solutions & Approaches"]
        S1["Commercial SiPh Foundry (65nm)<br/>Tight Component Spec Control"]
        S2["System-Level Calibration<br/>High SNR Design (>12dB gain)"]
        S3["Modular Design<br/>(Data/Weight Modules)<br/>Co-Design Simulation"]
        S4["2.5D Flip-Chip Bonding<br/>EIC/PIC Co-Integration in SiP"]
        S5["~7.61 ENOB Achieved<br/>Potential for Active Feedback Control"]
        S6["Heuristic Recurrent Algorithm Optimized<br/>Co-designed EIC Logic/Memory"]
    end

    C1 --> S1
    C2 --> S1
    C2 --> S2
    C3 --> S3
    C4 --> S4
    C5 --> S2
    C5 --> S5
    C6 --> S6
    
```

---

## Performance Summary and Comparison

This diagram summarizes the key performance metrics achieved by the PACE system and compares its Ising problem solving speed to a conventional GPU.

```mermaid
---
title: "Performance Summary and Comparison"
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
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'graph': { 'htmlLabels': false},
    'fontFamily': 'Monospace',
    'themeVariables': {
      'primaryColor': '#B28',
      'primaryTextColor': '#FFF',
      'primaryBorderColor': '#7C33',
      'secondaryColor': '#615',
      'lineColor': '#F8B229'
    }
  }
}%%
graph TD
    A["PACE System Performance"] --> B("Core oMAC Operation")
    B --> B1["Matrix Size:<br/> 64x64"]
    B --> B2["Operating Frequency:<br/> ~1 GHz"]
    B --> B3["Throughput:<br/> ~8.19 TOPS"]
    B --> B4["Energy Efficiency:<br/> ~2.38 TOPS/W<br/>(incl. Laser)"]
    B --> B5["Accuracy:<br/> ~7.61 ENOB"]

    A --> C("Ising Problem Solving")
    C --> C1["Algorithm:<br/> Heuristic Recurrent"]
    C --> C2["Latency per Iteration:<br/> < 5 ns Demonstrated"]
    C --> C3["Convergence Rate:<br/> > 92%<br/>(@ 5 ns)"]

    A --> D("Comparison vs. NVIDIA A10 GPU")
    subgraph GPU_Comparison["GPU Comparison<br/>(Specific Ising Task)"]
        Comp1["Metric"] --> Comp2["PACE"] & Comp3["A10 GPU"]
        Comp1_Iter["Avg. Iterations to Converge"] --> Comp2_Iter["~537"] & Comp3_Iter["~347"]
        Comp1_Latency["Latency per Iteration"] --> Comp2_Latency["~5 ns"] & Comp3_Latency["> 2,300 ns"]
        Comp1_Time["Total Computation Time"] --> Comp2_Time["~2.7 µs"] & Comp3_Time["~798 µs"]
        Comp1_Speedup["Speedup Factor"] --> Comp4["PACE is > 100x faster in total time"]
        Comp4 --> Comp5(["Note:<br/>Algorithmic efficiency (iterations) similar,<br/> hardware latency drives massive speedup"])
    end
    D --> GPU_Comparison

```


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---