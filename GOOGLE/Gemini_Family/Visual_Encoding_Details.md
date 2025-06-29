---
created: 2025-03-04 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://arxiv.org/pdf/2312.11805"
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExcTg3NnhjbXA2NGI0Zzd4NXBvMDJzY2RxcmdlNnFybGJudzRudXFmaSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zZg05JXw0PR6Pod1NC/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# Visual Encoding Details
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes (<ins>sometimes, entertainment purposes</ins>), personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>

---


## Visual Encoding Details - A Diagrammatic Guide 



```mermaid
---
title: "Gemini: A Family of Highly Capable Multimodal Models - Google DeepMind"
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
    A[Visual Encoding Details] --> B{Data Types};
    style A fill:#a3a3,stroke:#333,stroke-width:1px;
    B --> C[Text]:::detail;
    style C fill:#a2da,stroke:#333,stroke-width:1px
    C --> CA[Used for textual descriptions, instructions, and labels]:::takeaway;
    C --> CB["Represents structured data (tables, code)"]:::takeaway
    C --> CC[Encoded using token embeddings]:::takeaway;
    B --> D[Images]:::detail;
    style D fill:#a2da,stroke:#333,stroke-width:1px
    D --> DA[Represented as pixel values or features]:::takeaway;
    D --> DB[Used for visual context, diagrams, charts, and scene understanding]:::takeaway;
    D --> DC[Encoded using vision transformers or similar architectures]:::takeaway;
    B --> E[Video]:::detail;
    style E fill:#a2da,stroke:#333,stroke-width:1px
    E --> EA[Encoded as a sequence of frames]:::takeaway;
    E --> EB[Captures temporal information and actions]:::takeaway;
    E --> EC["Encoded using video-specific architectures (e.g., convolutional or recurrent networks)"]:::takeaway
    B --> F[Audio]:::detail;
    style F fill:#a2da,stroke:#333,stroke-width:1px
    F --> FA["Represented as audio signals or features (e.g., spectrograms)"]:::takeaway
    F --> FB[Captures speech and sound]:::takeaway;
    F --> FC["Encoded using audio-specific architectures (e.g., spectrograms)"]:::takeaway

    A --> G{Encoding Techniques};
        style G fill:#a3ae,stroke:#333,stroke-width:1px;
        G --> GA[Embeddings]:::detail;
        style GA fill:#a2fa,stroke:#333,stroke-width:1px;
        GA --> GAA[Text embeddings for words and sentences]:::takeaway;
        GA --> GAB[Learned representations that capture semantic meaning]:::takeaway;
    G --> GB[Vision Transformers]:::detail;
        style GB fill:#a2fa,stroke:#333,stroke-width:1px;
        GB --> GBA[Process images as a sequence of patches]:::takeaway;
        GB --> GBB[Capture spatial relationships and features]:::takeaway
    G --> GC["Universal Speech Model (USM)"]:::detail
      style GC fill:#a2fa,stroke:#333,stroke-width:1px;
        GC --> GCA[Features capture nuances lost in text mapping]:::takeaway;

    A --> H{Interleaving};
        style H fill:#a3ae,stroke:#333,stroke-width:1px;
        H --> HA[Sequence of tokens from different modalities]:::detail;
         style HA fill:#a2ff,stroke:#333,stroke-width:1px;
        HA --> HAA[Text, image, audio, and video tokens are interleaved]:::takeaway;
        HA --> HAB[Models are trained to handle these interleaved sequences natively]:::takeaway;

    classDef takeaway fill:#f2b3,stroke:#333,stroke-width:1px;
    classDef detail fill:#f2f3,stroke:#333,stroke-width:1px;
    class C,D,E,F,GA,GB,GC,HA detail;
    class CA,CB,CC,DA,DB,DC,EA,EB,EC,FA,FB,FC,GAA,GAB,GBA,GBB,GCA,HAA,HAB takeaway;

```

---


### Key improvements and explanations

*   **Focus on Visual Encoding:** The diagram now specifically addresses how the different modalities (text, image, video, audio) are encoded into a format that the Gemini model can process.
*   **Data Types and Encoding Techniques:** The diagram details both the data types used and the specific encoding techniques (embeddings, transformers, etc.).
*   **Takeaways:** Clearly identifies what makes each encoding technique significant.
*   **Interleaving**: The diagram shows how the models are designed to handle interleaved modalities
*   **Specific Technologies Mentioned:**  The diagram explicitly mentions the techniques used by the models, including Vision Transformers and Universal Speech Model (USM) features.
*   **Code Structure:**  The Mermaid code is well-structured and easy to read.
*   **Clear Visuals:** It uses color and shapes to distinguish between categories and highlight important information.




---


```mermaid
---
title: "❓...CongLeSolutionX....❓"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%{
  init: {
    'flowchart': { 'htmlLabels': false },
    'fontFamily': 'Bradley Hand',
    'themeVariables': {
      'primaryColor': '#fc82',
      'primaryTextColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#5229',
      'secondaryTextColor': '#6C3483',
      'lineColor': '#F8B229',
      'fontSize': '20px'
    }
  }
}%%
flowchart LR
    My_Meme@{ img: "https://raw.githubusercontent.com/CongLeSolutionX/CongLeSolutionX/refs/heads/main/assets/images/My-meme-and-question-marks-open-book-old-characters-background.png", label: "..🙉..👀..📖..", pos: "b", w: 200, h: 150, constraint: "off" }
   
    Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote@{ shape: braces, label: "..👀..<br/>'Unfortunately,<br/>no one can be told<br/> what the Matrix is.<br/>You have to see it<br/>for yourself'<br/>...📚..<br/>-<ins>Morpheus,<br/>a character from the movie The Matrix 1999</ins>"}

   Closing_quote ~~~ My_Meme

    My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }

```

---
><b>Licenses</b>:
>
>- <b>MIT License</b>:  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
>- <b>Creative Commons Attribution-ShareAlike 4.0 International</b>: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) [![CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/88x31.png)](https://creativecommons.org/licenses/by-sa/4.0/) - Legal details in [LICENSE-CC-BY-SA-4.0](THE_PAST/LICENSE-CC-BY-SA-4.0) and at [Creative Commons official site](https://creativecommons.org/licenses/by-sa/4.0/).
>
---
