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
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExNWJlMjJneDNjaTk2eGR3cnBheTJwZjAwMWlzeHRsYng4Ym10dnoyMCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3o85xsw5ygzVXxzsxW/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# Visual Encoder Architecture
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


## Visual Encoder Architecture - A Diagrammatic Guide 



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
    A[Gemini Visual Encoder] --> B{Inspiration}
    style A fill:#a3a3,stroke:#333,stroke-width:1px
    B --> BA[Flamingo]:::detail
    style BA fill:#a2fa,stroke:#333,stroke-width:1px
    BA --> BAA[Foundation model approach]:::takeaway
    B --> BB[CoCa]:::detail
    style BB fill:#a2fa,stroke:#333,stroke-width:1px
    BB --> BBA[Joint image-text training]:::takeaway
    B --> BC[PaLI]:::detail
    style BC fill:#a2fa,stroke:#333,stroke-width:1px
    BC --> BCA[Jointly-scaled multilingual language-image model]:::takeaway

    A --> C{Key Features}
    style C fill:#a3ae,stroke:#333,stroke-width:1px
    C --> CA[Natively Multimodal]:::detail
    style CA fill:#f2fa,stroke:#333,stroke-width:1px
        CA --> CAA[Trained jointly with image, audio, video, and text]:::takeaway
        CA --> CAB[Avoids intermediate language bottlenecks]:::takeaway
    C --> CB[Discrete Image Tokens]:::detail
        style CB fill:#f2fa,stroke:#333,stroke-width:1px
        CB --> CBA["Uses discrete image tokens for image output (dVAE)"]:::takeaway
        CB --> CBB["References Ramesh et al. (2021); Yu et al. (2022b)"]:::takeaway
    C --> CC[Video Understanding]:::detail
        style CC fill:#f2fa,stroke:#333,stroke-width:1px
        CC --> CCA[Encodes video as a sequence of frames]:::takeaway
        CC --> CCB[Leverages large context window]:::takeaway
    C --> CD[Variable Input Resolution]:::detail
        style CD fill:#f2fa,stroke:#333,stroke-width:1px
        CD --> CDA[Spends more compute on fine-grained understanding]:::takeaway
    C --> CE[Audio Input]:::detail
        style CE fill:#f2fa,stroke:#333,stroke-width:1px
        CE --> CEA[Directly ingests 16kHz audio signals from USM]:::takeaway
        CE --> CEB[Captures nuances lost in text mapping]:::takeaway
    
 classDef takeaway fill:#f2b3,stroke:#333,stroke-width:1px
 classDef detail fill:#f2f3,stroke:#333,stroke-width:1px
 class BA,BB,BC,CA,CB,CC,CD,CE detail
 class BAA,BBA,BCA,CAA,CAB,CBA,CBB,CCA,CCB,CDA,CEA,CEB takeaway
 
```



---

### Key points and explanations

*   **Root Node:** `"Gemini Visual Encoder"` is the central theme.
*   **Inspiration:**  Highlights that the architecture builds upon previous work ("Inspiration" subgraph):
    *   Flamingo: Foundation model approach.
    *   CoCa: Joint image-text training.
    *   PaLI: Jointly-scaled multilingual language-image model.
*   **Key Features:**  Focuses on what makes the encoder unique.  Key aspects of its functionality:
    *   Natively Multimodal: It's not just adapted for multimodal input, it's designed that way from the start.  This avoids a bottleneck.
    *   Discrete Image Tokens: A technical detail that enables image output. The models can output images using discrete image tokens (Ramesh et al., 2021; Yu et al., 2022b).
    *   Video Understanding: Treats video as a series of frames within the context window, allowing for temporal analysis.
    *   Variable Input Resolution: Allows the model to dynamically allocate resources to more detailed sections of the input.
    *   Audio Input: Can process audio signals directly, which is more effective than simply converting the audio to text.





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
