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
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExcW81YW4zenN4bGY0Y2txemY2bmIxZGx0bzJhcThzbTk3eG4zZzFzOSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/RGMDSeGPAPyrC/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Transformer Engine
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
title: "NVIDIA - Transformer Engine"
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
    %% External Dependencies
    EXDEP["External Dependencies"]:::external

    %% API Layer Subgraph
    subgraph API_Layer["API Layer"]
        PT["Transformer Engine: PyTorch API"]:::pyapi
        JAX["Transformer Engine: JAX API"]:::jaxapi
    end

    %% Core Engine Subgraph
    subgraph Core_Engine["Core Engine"]
        CORE["Core C++/CUDA Engine"]:::core
    end

    %% Integration & Support Subgraph
    subgraph Integration_and_Support["Integration & Support"]
        BUILDT["Build Tools & CI Framework"]:::build
        DOC["Documentation"]:::docs
        CIW["CI & Workflows"]:::ci
        subgraph Examples_and_Tests["Examples & Tests"]
            EX["Examples"]:::ex
            TS["Tests"]:::ex
        end
    end

    %% Connections
    EXDEP -->|"supports"| CORE
    PT -->|"calls"| CORE
    JAX -->|"calls"| CORE

    BUILDT -->|"builds"| PT
    BUILDT -->|"builds"| JAX
    BUILDT -->|"builds"| CORE

    DOC -->|"docs for"| PT
    DOC -->|"docs for"| CORE

    CIW -->|"triggers"| BUILDT

    EX -->|"demonstrates"| PT
    EX -->|"demonstrates"| CORE

    TS -->|"validates"| CORE
    TS -->|"validates"| PT
    TS -->|"validates"| JAX

    %% Click Events - Component Mapping
    click CORE "https://github.com/nvidia/transformerengine/tree/main/transformer_engine/common"
    click PT "https://github.com/nvidia/transformerengine/tree/main/transformer_engine/pytorch"
    click JAX "https://github.com/nvidia/transformerengine/tree/main/transformer_engine/jax"
    click BUILDT "https://github.com/nvidia/transformerengine/tree/main/build_tools"
    click DOC "https://github.com/nvidia/transformerengine/tree/main/docs"
    click CIW "https://github.com/nvidia/transformerengine/blob/main/.github"
    click EX "https://github.com/nvidia/transformerengine/tree/main/examples"
    click TS "https://github.com/nvidia/transformerengine/tree/main/tests"

    %% Styles
    classDef external fill:#B16A,stroke:#000,stroke-width:2px
    classDef pyapi fill:#D087,stroke:#000,stroke-width:2px
    classDef jaxapi fill:#BEA3,stroke:#000,stroke-width:2px
    classDef core fill:#EBC3,stroke:#000,stroke-width:2px
    classDef build fill:#CCF3,stroke:#000,stroke-width:2px
    classDef docs fill:#81A,stroke:#000,stroke-width:2px
    classDef ci fill:#5E81,stroke:#000,stroke-width:2px
    classDef ex fill:#A3BE,stroke:#000,stroke-width:2px

```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
