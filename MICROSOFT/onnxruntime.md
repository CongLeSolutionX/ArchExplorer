---
created: 2025-03-09 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExc2VvbnJ6dmphMzFnZWdhZnU5NGR5Yzh6eW9mcXJxc3g0dWliaTdpZSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3o85xAsvWZnf6zKvdu/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# onnxruntime
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
title: "MICROSOFT - Onnxruntime"
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
    "flowchart": {"htmlLabels": true, 'curve': 'natural'},
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#f231',
      'primaryTextColor': '#239',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph TD
    A["ONNX Model File"]:::input
    B["Session/Graph Loader"]
    C["Core and Session Management"]:::core
    D["Graph Optimizations and Transformations"]:::optimization
    E["Execution Provider Selector"]
    F["Execution Providers"]:::provider
    G["Memory Management and Utilities"]:::memory
    H["Gradient Graph Generation"]:::training
    I["Optimizer/Scheduler"]:::training
    J["Training Modules (Training vs Inference Pipeline)"]:::training
    K["APIs and Language Bindings"]:::api
    L["Additional Components (Logging,Tools,Samples)"]:::additional
    M["Client Application"]:::input

    A --> B
    B --> C
    C --> D

    %% Inference Pipeline
    D --> E
    E --> F
    F --> G
    G --> K

    %% Training Pipeline Branch
    D --> H
    H --> I
    I --> J
    J --> K

    %% Final API and Client Integration
    K --> M

    %% Additional components integrated with API layer
    L --- K

    %% Click Events
    click C "https://github.com/microsoft/onnxruntime/tree/main/onnxruntime/core/session"
    click D "https://github.com/microsoft/onnxruntime/tree/main/onnxruntime/core/optimizer"
    click F "https://github.com/microsoft/onnxruntime/tree/main/onnxruntime/core/providers"
    click G "https://github.com/microsoft/onnxruntime/tree/main/onnxruntime/core/common and onnxruntime/core/platform"
    click K "https://github.com/microsoft/onnxruntime/tree/main/csharp; java; js; rust; onnxruntime/python"
    click J "https://github.com/microsoft/onnxruntime/tree/main/orttraining/orttraining"
    click L "https://github.com/microsoft/onnxruntime/tree/main/docs; tools; samples; winml"

    %% Styles
    classDef input fill:#D5F5,stroke:#333,stroke-width:2px
    classDef core fill:#FEA5,stroke:#333,stroke-width:2px
    classDef optimization fill:#AEF5,stroke:#333,stroke-width:2px
    classDef provider fill:#C6C5,stroke:#333,stroke-width:2px
    classDef memory fill:#F8C4,stroke:#333,stroke-width:2px
    classDef training fill:#DE23,stroke:#333,stroke-width:2px
    classDef api fill:#FB73,stroke:#333,stroke-width:2px
    classDef additional fill:#EDF2,stroke:#333,stroke-width:2px
    
```



---

<!-- 
```mermaid
%% Current Mermaid version
info
```  -->


```mermaid
---
title: "CongLeSolutionX"
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
      'secondaryColor': '#81c784',
      'secondaryTextColor': '#6C3483',
      'lineColor': '#F8B229',
      'fontSize': '20px'
    }
  }
}%%
flowchart LR
  My_Meme@{ img: "https://raw.githubusercontent.com/CongLeSolutionX/CongLeSolutionX/refs/heads/main/assets/images/My-meme-light-bulb-question-marks.png", label: "Ăn uống gì chưa ngừi đẹp?", pos: "b", w: 200, h: 150, constraint: "off" }

  Closing_quote@{ shape: braces, label: "...searching insights in the process of formulating better questions..." }

  Closing_quote ~~~ My_Meme
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }

```

---
> **Licenses:**
>
> - **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
> - **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).
> 
---
