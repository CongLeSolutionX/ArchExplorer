---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExcnlnZm40ZG40NHJmeW14ejZxdmw3bm04OGVvdjlmaHV5djRxOGl0YyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/l3vRatDKSXFmjAWBi/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Faiss
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
title: "Meta Research - faiss"
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
flowchart TD
    %% Core Components
    subgraph Core_Components["Core Components"]
        A["Core Library (CPU):<br> Core Search Algorithms"]:::core
        B["GPU Support:<br> GPU-Accelerated Indexing"]:::gpu
        G["Contrib Modules & External Extensions"]:::contrib
    end

    %% Interface Bindings
    subgraph Interface_Bindings["Interface Bindings"]
        C["C API Bindings:<br> External Integration"]:::api
        D["Python Wrappers:<br> High-level APIs"]:::pb
    end

    %% Evaluation Tools
    subgraph Evaluation_Tools["Evaluation Tools"]
        E1["Benchs"]:::bench
        E2["Demos"]:::bench
        E3["Tutorial"]:::bench
        E4["Tests"]:::bench
    end

    %% Build & Deployment
    subgraph Build_and_Deployment["Build & Deployment"]
        F1["CMakeLists.txt"]:::build
        F2[".dockerignore"]:::build
        F3["Conda Recipes"]:::build
        F4["CMake Directory"]:::build
        F5["CI/CD Config"]:::build
    end

    %% Relationships - Interface Bindings invoke Core Components
    C -->|"calls"| A
    D -->|"calls"| A

    %% Core interacts with GPU (optional delegation)
    A <-->|"optionalDelegation"| B

    %% Contrib extends the Core
    G -->|"extends"| A

    %% Evaluation Tools test the Core (and optionally GPU)
    E1 -->|"tests"| A
    E2 -->|"tests"| A
    E3 -->|"tests"| A
    E4 -->|"tests"| A
    E1 -->|"benchmarks"| B

    %% Build & Deployment builds all components (using F1 as a representative)
    F1 -->|"builds"| A
    F1 -->|"builds"| B
    F1 -->|"builds"| C
    F1 -->|"builds"| D
    F1 -->|"builds"| E1
    F1 -->|"builds"| G

    %% Click Events
    click A "https://github.com/facebookresearch/faiss/tree/main/faiss/"
    click B "https://github.com/facebookresearch/faiss/tree/main/faiss/gpu/"
    click C "https://github.com/facebookresearch/faiss/tree/main/c_api/"
    click D "https://github.com/facebookresearch/faiss/tree/main/faiss/python/"
    click E1 "https://github.com/facebookresearch/faiss/tree/main/benchs/"
    click E2 "https://github.com/facebookresearch/faiss/tree/main/demos/"
    click E3 "https://github.com/facebookresearch/faiss/tree/main/tutorial/"
    click E4 "https://github.com/facebookresearch/faiss/tree/main/tests/"
    click F1 "https://github.com/facebookresearch/faiss/blob/main/CMakeLists.txt"
    click F2 "https://github.com/facebookresearch/faiss/blob/main/.dockerignore"
    click F3 "https://github.com/facebookresearch/faiss/tree/main/conda/"
    click F4 "https://github.com/facebookresearch/faiss/tree/main/cmake/"
    click F5 "https://github.com/facebookresearch/faiss/tree/main/.github/"
    click G "https://github.com/facebookresearch/faiss/tree/main/contrib/"

    %% Styles
    classDef core fill:#fcc3,stroke:#000,stroke-width:1px
    classDef gpu fill:#cfc5,stroke:#000,stroke-width:1px
    classDef api fill:#ccf3,stroke:#000,stroke-width:1px
    classDef pb fill:#ffc3,stroke:#000,stroke-width:1px
    classDef bench fill:#fcf4,stroke:#000,stroke-width:1px
    classDef build fill:#cff3,stroke:#000,stroke-width:1px
    classDef contrib fill:#f0e6,stroke:#000,stroke-width:1px
    
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

