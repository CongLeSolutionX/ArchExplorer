---
created: 2025-03-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Fuser
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
title: "NVIDIA - Fuser"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: default
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "graph": { "htmlLabels": false, 'curve': 'linear' },
    'themeVariables': {
        'fontFamily': 'Comic Sans MS',
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
    %% Frontend Layer
    subgraph Frontend_Layer["Frontend Layer"]
        F1["nvFuser Package"]:::frontend
        F2["Python Bindings"]:::frontend
    end

    %% Compiler Core Layer
    subgraph Compiler_Core["Compiler Core"]
    style Compiler_Core fill:#ADD8E6,stroke:#000,stroke-width:2px
        %% IR Construction
        IR1["IR Construction"]:::core
        
        %% Optimization & Scheduling
        subgraph Optimization_and_Scheduling["Optimization & Scheduling"]
        style Optimization_and_Scheduling fill:#D8E6,stroke:#000,stroke-width:2px
            S1["Scheduler"]:::core
            S2["Preseg Passes"]:::core
            S3["Device Lower"]:::core
        end
        
        %% Code Generation
        subgraph Code_Generation["Code Generation"]
        style Code_Generation fill:#DD6,stroke:#000,stroke-width:2px
            CG1["codegen.cpp"]:::core
            CG2["codegen.h"]:::core
        end
    end

    %% Runtime Environment
    R1["CUDA Runtime & Kernel Executor"]:::runtime

    %% Testing & Benchmarking
    subgraph Support_and_Testing["Support & Testing"]
        T1["Benchmark Suites"]:::testing
        T2["Test Suites"]:::testing
    end

    %% Connections
    F1 -->|"API call"| IR1
    F2 -->|"API call"| IR1
    IR1 -->|"build IR"| S1
    S1 -->|"optimize"| S2
    S2 -->|"schedule"| S3
    S3 -->|"generate code"| CG1
    CG1 -->|"header dependency"| CG2
    CG2 -->|"final kernel"| R1
    R1 -->|"performance data"| T1
    R1 -->|"test results"| T2
    T1 -->|"feedback"| IR1
    T2 -->|"feedback"| IR1

    %% Click Events
    click F1 "https://github.com/nvidia/fuser/blob/main/nvfuser/__init__.py"
    click F2 "https://github.com/nvidia/fuser/tree/main/csrc/python_frontend"
    click IR1 "https://github.com/nvidia/fuser/tree/main/csrc/ir"
    click S1 "https://github.com/nvidia/fuser/tree/main/csrc/scheduler"
    click S2 "https://github.com/nvidia/fuser/tree/main/csrc/preseg_passes"
    click S3 "https://github.com/nvidia/fuser/tree/main/csrc/device_lower"
    click CG1 "https://github.com/nvidia/fuser/blob/main/csrc/codegen.cpp"
    click CG2 "https://github.com/nvidia/fuser/blob/main/csrc/codegen.h"
    click R1 "https://github.com/nvidia/fuser/tree/main/runtime"
    click T1 "https://github.com/nvidia/fuser/tree/main/benchmarks"
    click T2 "https://github.com/nvidia/fuser/tree/main/tests"

    %% Styles
    classDef frontend fill:#ADD8E6,stroke:#000,stroke-width:2px
    classDef core fill:#90EE90,stroke:#000,stroke-width:2px
    classDef runtime fill:#FFA07A,stroke:#000,stroke-width:2px
    classDef testing fill:#D3D3D3,stroke:#000,stroke-width:2px

```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---