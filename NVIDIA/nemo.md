---
created: 2025-03-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExcDU1Nzh4NHFiYWdhMjlzZzVxdzI2Y2t4ZjNyNHRkMmJqczRnYzUycSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/ag9LVCPdksh56/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Nemo
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## A Diagrammatic Guide 


```mermaid
---
title: "NVIDIA - Nemo"
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
    "graph": { "htmlLabels": false, 'curve': 'linear' },
    'themeVariables': {
        'fontFamily': 'Fantasy',
        'fontSize': '20px',
        'primaryColor': '#ffff',
        'primaryTextColor': '#55ff',
        'primaryBorderColor': '#7c2',
        'lineColor': '#F8B229',
        'secondaryColor': '#006100',
        'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TD
    UI["User Interface & Experiment Management"]:::ui

    subgraph Core_Infrastructure["Core Infrastructure"]
        Core1["Core Module"]
        Core2["Lightning Module"]
    end

    subgraph Domain_Collections["Domain Collections"]
        D1["ASR Collection"]
        D2["NLP Collection"]
        D3["TTS Collection"]
        D4["Vision Collection"]
        D5["Multimodal Collection"]
        D6["LLM Collection"]
    end

    TE["Training & Inference Engine<br/>(FSDP, MoE, TP)"]:::training

    subgraph Deploy_and_Export_Tools["Deploy & Export Tools"]
        E1["Export Suite"]
        DPL["Deployment Suite"]
    end

    EI["External Integrations & Ecosystem"]:::external

    %% Connections from User Interface
    UI -->|"triggers"| Core1
    UI -->|"triggers"| Core2
    UI -->|"utilizes"| EI

    %% Core Infrastructure supports Domain Collections
    Core1 -->|"provides base"| D1
    Core1 -->|"provides base"| D2
    Core1 -->|"provides base"| D3
    Core1 -->|"provides base"| D4
    Core1 -->|"provides base"| D5
    Core1 -->|"provides base"| D6

    %% Domain Collections and Core feed into Training Engine
    Core2 -->|"integrates with"| TE
    D1 -->|"supplies models"| TE
    D2 -->|"supplies models"| TE
    D3 -->|"supplies models"| TE
    D4 -->|"supplies models"| TE
    D5 -->|"supplies models"| TE
    D6 -->|"supplies models"| TE

    %% Training Engine connects to Deploy & Export Tools
    TE -->|"exports optimized model"| E1
    TE -->|"prepares for serving"| DPL

    %% External Integrations communicates with Training and Deployment
    EI -->|"orchestrates"| TE
    DPL -->|"integrates with"| EI

    %% Click Events for Component Mapping
    click Core1 "https://github.com/nvidia/nemo/tree/main/nemo/core"
    click Core2 "https://github.com/nvidia/nemo/tree/main/nemo/lightning"
    click D1 "https://github.com/nvidia/nemo/tree/main/nemo/collections/asr"
    click D2 "https://github.com/nvidia/nemo/tree/main/nemo/collections/nlp"
    click D3 "https://github.com/nvidia/nemo/tree/main/nemo/collections/tts"
    click D4 "https://github.com/nvidia/nemo/tree/main/nemo/collections/vision"
    click D5 "https://github.com/nvidia/nemo/tree/main/nemo/collections/multimodal"
    click D6 "https://github.com/nvidia/nemo/tree/main/nemo/collections/llm"
    click TE "https://github.com/nvidia/nemo/tree/main/nemo/lightning/pytorch/strategies"
    click E1 "https://github.com/nvidia/nemo/tree/main/nemo/export"
    click DPL "https://github.com/nvidia/nemo/tree/main/nemo/deploy"

    %% Styles
    classDef ui fill:#CCD1D,stroke:#5D6D7E,stroke-width:2px
    classDef core fill:#AED6F,stroke:#1B4F72,stroke-width:2px
    classDef collection fill:#ABEBC,stroke:#1D8348,stroke-width:2px
    classDef training fill:#EE54,stroke:#B7950B,stroke-width:2px
    classDef deploy fill:#F5B7B,stroke:#922B21,stroke-width:2px
    classDef external fill:#D7BDE,stroke:#6C3483,stroke-width:2px

    class Core1,Core2 core
    class D1,D2,D3,D4,D5,D6 collection
    class TE training
    class E1,DPL deploy
    class EI external
    
```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
