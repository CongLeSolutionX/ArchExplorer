---
created: 2025-03-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# cccl
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
title: "NVIDIA - cccl"
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
    "flowchart": { "htmlLabels": false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
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
    %% Interface Layer
    subgraph "Interface Layer"
        DA["Developer Applications"]:::interface
        PB["Python Bindings"]:::interface
    end

    %% Unified CUDA Core Compute Library
    subgraph "Unified CUDA Core Compute Library"
        TH["Thrust: High-Level Parallel Algorithms"]:::core
        CB["CUB: Low-Level Parallel Primitives"]:::core
        LC["libcudacxx: CUDA Standard Library"]:::core
    end

    %% Build & Integration Infrastructure
    subgraph "Build & Integration Infrastructure"
        BS1["CMakeLists.txt"]:::build
        BS2["cmake"]:::build
        CI1[".github"]:::ci
        CI2["ci"]:::ci
        DC[".devcontainer"]:::dev
    end

    %% Testing, Benchmarks, and Examples
    subgraph "Testing, Benchmarks, and Examples"
        TST["Testing"]:::test
        BM["Benchmarks"]:::test
        EX["Examples"]:::test
    end

    %% Relationships
    DA -->|"includes"| TH
    PB -->|"calls"| LC

    CI1 -->|"triggers"| BS1
    CI2 -->|"triggers"| BS1
    DC -->|"provides-env"| BS1

    BS1 -->|"compiles"| TH
    BS1 -->|"compiles"| CB
    BS1 -->|"compiles"| LC

    BS1 -->|"runs"| TST
    BS1 -->|"runs"| BM
    BS1 -->|"runs"| EX

    CI1 -->|"triggers"| TST
    CI2 -->|"triggers"| TST

    %% Click Events for Core Libraries
    click TH "https://github.com/nvidia/cccl/tree/main/thrust"
    click CB "https://github.com/nvidia/cccl/tree/main/cub"
    click LC "https://github.com/nvidia/cccl/tree/main/libcudacxx"

    %% Click Events for Build System
    click BS1 "https://github.com/nvidia/cccl/blob/main/CMakeLists.txt"
    click BS2 "https://github.com/nvidia/cccl/tree/main/cmake/"

    %% Click Events for CI Pipeline and Dev Containers
    click CI1 "https://github.com/nvidia/cccl/tree/main/.github/"
    click CI2 "https://github.com/nvidia/cccl/tree/main/ci/"
    click DC "https://github.com/nvidia/cccl/tree/main/.devcontainer/"

    %% Click Events for Testing, Benchmarks, and Examples
    click TST "https://github.com/nvidia/cccl/tree/main/test/"
    click BM "https://github.com/nvidia/cccl/tree/main/benchmarks/"
    click EX "https://github.com/nvidia/cccl/tree/main/examples/"

    %% Click Event for Python Bindings
    click PB "https://github.com/nvidia/cccl/tree/main/python/"

    %% Styles
    classDef core fill:#AED6F1,stroke:#1B4F72,stroke-width:2px;
    classDef build fill:#F9E79F,stroke:#F39C12,stroke-width:2px;
    classDef ci fill:#F5B7B1,stroke:#C0392B,stroke-width:2px;
    classDef dev fill:#D7BDE2,stroke:#6C3483,stroke-width:2px;
    classDef test fill:#ABEBC6,stroke:#196F3D,stroke-width:2px;
    classDef interface fill:#FAD7A0,stroke:#D68910,stroke-width:2px;
    
```





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---