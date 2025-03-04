---
created: 2025-03-04 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2502.12524"
---



# YOLOv12: Attention-Centric Real-Time Object Detectors
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## YOLOv12 Paper Overview - A Diagrammatic Guide 



```mermaid
---
title: "YOLOv12: Attention-Centric Real-Time Object Detectors"
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
    A["YOLOv12:<br>Attention-Centric Real-Time Object Detectors"] --> B(Authors)
    B --> C{Yunjie Tian}
    B --> D{Qixiang Ye}
    B --> E{David Doermann}
    A --> F[Technical Report]
    F --> G{github.com/sunsmarterjie/yolov12}

    A --> H[Problem]
    H --> I(CNN-based YOLO limitations in attention mechanisms)
    I --> J{Inefficient attention mechanism speed}
    J --> K(Quadratic complexity)
    %% K --> KA(O(L^2d)  [Self Attention]  VS  O(kLd) [CNN]);
    J --> L(Inefficient memory access)
    L --> LA(Attention map storage overhead from GPU SRAM to HBM)
    M --> MA(Reduced adoption of attention in real time YOLO systems)
    A --> M[Contribution]

    M --> N(YOLOv12 Framework)
    N --> O{Key Improvements}
    O --> OA["Area Attention (A2)"]
    O --> OB["Residual Efficient Layer Aggregation Networks<br>(R-ELAN)"]
    O --> OC["Architectural Improvements (MLP ratio, FlashAttention)"]
    N --> P(Model Scales)
    P --> PA(YOLOv12-N)
    P --> PB(YOLOv12-S)
    P --> PC(YOLOv12-M)
    P --> PD(YOLOv12-L)
    P --> PE(YOLOv12-X)

    A --> Q{Performance}
    Q --> QA("Surpasses state-of-the-art real-time object detectors [Accuracy, Speed]")
    %% Q --> QB(Superior to YOLOv10/11 and RT-DETR/v2) : QA--Performance Compared to SOTA--> Table1;
    A --> R[Structure]
    %% R --> RS(Introduction-->Related Work-->Approach (Efficiency, Area Attention, R-ELAN, Architectural Improvements)-->Experiment (Experimental Setup, SOTA Comparison, Ablation, Speed Analysis, Diagnostics,  Visualization) --> Conclusion --> Limitations --> More Details)

    style A fill:#f9f3,stroke:#333,stroke-width:2px
    style B fill:#ccf3,stroke:#333,stroke-width:1px
    style C fill:#ccf3,stroke:#333,stroke-width:1px
    style D fill:#ccf3,stroke:#333,stroke-width:1px
    style E fill:#ccf3,stroke:#333,stroke-width:1px
    style F fill:#ccf3,stroke:#333,stroke-width:1px
    style G fill:#ccf3,stroke:#333,stroke-width:1px
    style H fill:#ccf3,stroke:#333,stroke-width:1px
    style I fill:#ccf3,stroke:#333,stroke-width:1px
    style J fill:#ccf3,stroke:#333,stroke-width:1px

    style K fill:#cff3,stroke:#333,stroke-width:1px
    style L fill:#cff3,stroke:#333,stroke-width:1px
    style M fill:#ccf3,stroke:#333,stroke-width:1px
    style N fill:#cff3,stroke:#333,stroke-width:1px
    style O fill:#cff3,stroke:#333,stroke-width:1px
    style P fill:#ccf3,stroke:#333,stroke-width:1px
    style QA fill:#cff3,stroke:#333,stroke-width:1px

```

---


```mermaid
---
title: "YOLOv12: Attention-Centric Real-Time Object Detectors"
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
    A[Attention Mechanism Speed Efficiency Factors] --> B(Complexity)
    B --> C[Quadratic Computational Complexity]
    C --> CA("O(L^2d) - Self-Attention")
    C --> CB(L = sequence length,<br>d = feature dimension)
    B --> D[Architectural Complexity]
    D --> DA("Overhead from architectures<br>(e.g. Swin Transformer, positional encoding)")
    A --> E[Memory Access]
    E --> F(Inefficient Memory Access Patterns)
    F --> FA("Intermediate maps storage<br>(attention map, Softmax)")
    F --> FB("From high-speed SRAM --> High Bandwidth Memory (HBM)")
    F --> FC(Read/Write Speed Diff:<br>  >10x slowdown)
    
```


---


```mermaid
---
title: "YOLOv12: Attention-Centric Real-Time Object Detectors"
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
    A["Area Attention (A2) Module"] --> B("Goal:<br>Reduce attention computational cost without greatly sacrificing receptive field")
    B --> C{Proposed Improvement}
    C --> CA("Partition feature map (H,W) into l segments of  (H/l,W) or (H, W/l)")
    C --> CB("Simplifies to only reshape -> Fast")
    CA --> CD("Eliminates window partitioning overhead")
    CB --> CE("Local attention mechanism, Figure 2")
    C --> CF("Reduce 2n^2hd * (vanilla attention) to 1/2n^2hd")
    F{"Empirical Setting"} --> FF("l = 4")
    B --> H("Reduce Receptive Field - yet remains LARGE")

    style A fill:#ccf3,stroke:#333,stroke-width:2px

```


---


```mermaid
---
title: "YOLOv12: Attention-Centric Real-Time Object Detectors"
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
    A["Residual Efficient Layer Aggregation Networks<br>(R-ELAN)"] --> B("Goal:<br>Improve feature aggregation, address optimization challenges particularly large-scale models")
    A --> C("Based on ELAN [56]")
    A --> D(Issues of ELAN)
    D --> DA(Gradient blocking, lack of shortcut connection)
    D --> DB(Instability of Large Scale model, even Adam Optimzer)
    A -->  E{Key Improvements: Residual &Aggregation}
    E --> EA("Residual connections introduces + Input with Scaling")
    EA --> EAA(* layer scaling, no slowDown * )

    E --> EB("Modified Feature Aggregation")
    EAB(Transition-->single feature map output) --> EBA(Subsequent Blocks)

```




---


```mermaid
---
title: "YOLOv12: Attention-Centric Real-Time Object Detectors"
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
    A["Architectural Improvements; Modifications from Vanilla Attention"] --> B(Improve efficiencies and make it aligned YOLO systerm)
    B --> S{Hierarchical Design:}
   S --> SA("Inherit hierarchical design from previous YOLO systems")
     S --> SB("Remove the 'stacking of three blocks' on final backbone for fewer blocks -->Better Optimization")
    A--> C{Refine from Vanilla Design}
    C --> CA(Adjust MLP from 4 ->  1.2 or 2 for different scale -> Allocating more computations to Area Attention)
     C --> CB("nn.Conv2d  +   BN  vs  nn.Linear  +  LN with benefit from convolution's efficiency")
    C --> CC(Remove Position Encoding to Keep Model Clean)
    C --> CD("Using position perceiver Convolution 7 x 7; Increase position  impacted")---> CD1(helps integrate position info for attention)

```

---


```mermaid
---
title: "YOLOv12: Attention-Centric Real-Time Object Detectors"
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
    A["Ablation Study on R-ELAN:<br> Table 2"] --> B("Impact of Reaggregation method and residual design on performance with Model Scale<br>(YOLOv12-N, /L/X )")
    
    subgraph YOLOv12_N["YOLOv12-N"]
    style A fill:#f9f3,stroke:#333,stroke-width:2px
    style B fill:#f9f3,stroke:#333,stroke-width:2px
        B --> C("no shortcut +ELAN (vanilla design) has comparable perf")
    
    end
    
    subgraph YOLOv12_L["YOLOv12-L"]
        B --> D("introduce residual Connection (With scale) --> essential for stable convergence")
        D --> DA(improve performance)
    
    end

    subgraph YOLOv_12_X["YOLOv-12 X"]
        B --> E("scaling factor  = Minimum for ensuring convergence")

    end

```


---


```mermaid
---
title: "YOLOv12: Attention-Centric Real-Time Object Detectors"
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
    A["Ablation Area Attention Study: TABLE 3"] --> B("validate proposed Area Attention effects with YOLO scale")
    B --> BA("Results:<br>YOLOv12-N, -S  and -X will run fast on GPU/ CPU")
    A --> C("Test:<br>CUDA (RTX 3080, A5000 ) / CUPS (IntelCore i-7 10700k@3.80 GHz) with performance results")

classDef Elements fill:#a319,stroke:#555,stroke-width:2px
class A,B Elements

```



---


```mermaid
---
title: "YOLOv12: Attention-Centric Real-Time Object Detectors"
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
    A("YOLOv12 Performance Comparison:<br>Table 1") --> B[Model Scale]
    B --> B_N(YOLOv12-N)
    B --> B_S(YOLOv12-S)
    B --> B_M(YOLOv12-M)
    B --> B_L(YOLOv12-L)
    B --> B_X(YOLOv12-X)

    A --> C[Metrics]
    C --> C_FLOPs("FLOPs (G)")
    C --> C_Params("#Param. (M)")
    C --> C_APval("APval (50:95%)")
    C --> C_APval50("APval 50%")
    C --> C_APval75("APval 75%")
    C --> C_Latency("Latency (mg)")


    A --> D["Comparison Table, Detailed"]
    %% D --> D_SOTA("Against State of the Art models") :  TABLE1 ----Detailed Performance Comparison--> ModelScale  & metrics

     style A fill:#ccf3,stroke:#333,stroke-width:2px

```

---


```mermaid
---
title: "YOLOv12: Attention-Centric Real-Time Object Detectors"
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
    A[Speed comparison on Different HW:<br>Table 4 ] --> B("YOLO Speed v9//v10//11 //12")
    A --> C(Hardware:<br>with varying precision)
    C --> CPU(intel)
    C --> GPU(RTX 3080)
    C --> GPUA5000(RTX A5000)
    C --> GPUA6000(RTXA6000)
    B --> M1(speed measured for each for various HW and precision)

```


----


```mermaid
---
title: "YOLOv12: Attention-Centric Real-Time Object Detectors"
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
    A["Diagnostic/ Visual Analysis"] --> B("Visual- heat map comparison for  Yolov 10 //11 and presented Yolvo12 in different models")
    B --> Y1("YOLO-10 is Object Contures / clear")
    B --> R1("YOLO-11 Is Precise Foreground")

    style Y1 fill:#ccf3,stroke:#333,stroke-width:2px
    
```


----


```mermaid
---
title: "YOLOv12: Attention-Centric Real-Time Object Detectors"
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
  pie
    title Diagnostic and Visualization of the Study
    "Area Atention " : 20.8
    "Hierarchical design " : 23.1
    "Training epoch" : 5.2
   "Position Perceiver" : 10.5
       " Position Embeddings": 19.6
        "MLP ratio " : 20.8

```

---


```mermaid
gantt
    title Timeline of the YOLOv12 Research
    dateFormat  YYYY-MM-DD
    axisFormat  %Y-%m-%d
    section Conceptualization and Planning
    Define Problem         :done,    a1, 2024-04-15, 3d
    Literature Review       :active,   a2, 2024-04-18, 5d
    Formulate Hypotheses  :      a3, 2024-04-23, 2d
    section Design & Implementation
    Develop Area Attention  :         b1, after a3, 7d
 Test and Refine     :   b2, after b1, 6d
    Implement R-ELAN  :        b3,   after  b2, 8d
    Integrate Architectural Improvements  :    after b3, 7d
    section Experimentation & Evaluation
    Train and Evaluate Models         :   c1, after b3, 15d
   Ablation studies  :        c2,after c1, 8d
  Performance Analysis and Benchmarking    :  c3,after c2, 10d
  section Analysis & Writing
    Analyze Results & Visualization        : d1,after c3,7d
  Write Draft   :  d2,  after d1, 10d
  refine Paper: d3, after d1 and d2
```

---

```mermaid
---
title: "YOLOv12: Attention-Centric Real-Time Object Detectors"
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
flowchart TD
    A["Start"] --> B("Setup Dataset & Metrics COCO 2017")
    B --> C{"Model training Loop:<br>600 epoch - SGD"}
    C --> D{"YOLO-N/S/M/L/X- scale"}
    D --> E("Evaluate Parameters & performance:<br>FLOPs, Params, APval, Latency")
    E --> F["Generate Table Result:<br> TABLE 6 / 7"]
    
```


----


```mermaid
---
config:
  layout: elk
  look: handDrawn
  theme: default
---
erDiagram
    %%  YOLOv12 ||--o| MSCOCO
     YOLOv12 {
        VARCHAR ModelName PK
        FLOAT AP_Val_50_95 "Mean Average Precision @ [0.5:0.95]"
        FLOAt AP_Val_50 "Mean  Average Precision, @ 0.5"
        %% FLOAT `AP_val_ 75   ` Average Precision, @ 0.75 threshold //
        %% FLOAT Param_G "Network Parameters, Million'
        %% FLOAT FLOP_G  "Flpo, Giga  (Billons operations per, seconds')"
        %% FLOAT latencyms "Average inference speed, ms/image"
    }

    %% MSCOCO" includes Benchmark dataset  and training detail such as data augmentation, epochs size. optimizer, learn rate "
    %% METHOD||-. YOLOvX , YOLOV12 models used in benchmark datasets for evaluations

```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---