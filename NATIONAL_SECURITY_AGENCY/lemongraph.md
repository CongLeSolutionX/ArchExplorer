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
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnI4bzh6NjE4OTV0NWkwOXQ0MTlxOWk3dHdmMndtM2N3aHBvN3E1cSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/mLP9tIkMbXiog/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Lemongraph
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
title: "NATIONAL SECURITY AGENCY - Lemongraph"
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
    %% Core Layer
    subgraph Core_Layer["Core Layer"]
    style Core_Layer fill:#c2c3,stroke:#333,stroke-width:2px
        C_Core["C Core Library"]:::c_core
        LMDB(("LMDB Key/Value Store")):::lmdb
    end

    %% Application Layer
    subgraph Application_Layer["Application Layer"]
    style Application_Layer fill:#fc22,stroke:#333,stroke-width:2px
        Python_Binding["Python Binding/Wrapper"]:::python_binding
        Query_Engine["Query Language Engine"]:::query_engine
    end

    %% Interface Layer
    subgraph Interface_Layer["Interface Layer"]
    style Interface_Layer fill:#e223,stroke:#333,stroke-width:2px
        REST_Service["REST Service"]:::rest_service
        CLI_Utilities["CLI Utilities & Scripts"]:::cli
        Build_Setup["Build/Setup Components"]:::build
    end

    %% Relationships
    REST_Service -->|"REST request/response"| Python_Binding
    CLI_Utilities -->|"CLI operation"| Python_Binding
    Build_Setup -->|"setup"| Python_Binding
    Python_Binding -->|"transaction call"| C_Core
    Query_Engine -->|"query execution"| C_Core
    C_Core -->|"data storage"| LMDB

    %% Click Events
    click C_Core "https://github.com/nationalsecurityagency/lemongraph/blob/master/lib/lemongraph.c"
    click Python_Binding "https://github.com/nationalsecurityagency/lemongraph/blob/master/LemonGraph/__init__.py"
    click Query_Engine "https://github.com/nationalsecurityagency/lemongraph/blob/master/LemonGraph/query.py"
    click REST_Service "https://github.com/nationalsecurityagency/lemongraph/blob/master/LemonGraph/server/__init__.py"
    click LMDB "https://github.com/nationalsecurityagency/lemongraph/tree/master/deps/lmdb"
    click CLI_Utilities "https://github.com/nationalsecurityagency/lemongraph/blob/master/LemonGraph/dbtool.py"
    click Build_Setup "https://github.com/nationalsecurityagency/lemongraph/blob/master/setup.py"

    %% Styles
    classDef c_core fill:#DE62,stroke:#000,stroke-width:2px
    classDef python_binding fill:#9EF2,stroke:#000,stroke-width:2px
    classDef query_engine fill:#FD4512,stroke:#000,stroke-width:2px
    classDef rest_service fill:#FC75,stroke:#000,stroke-width:2px
    classDef lmdb fill:#8CE5,stroke:#000,stroke-width:2px
    classDef cli fill:#DAD2,stroke:#000,stroke-width:2px
    classDef build fill:#D3D3,stroke:#000,stroke-width:2px
    
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
