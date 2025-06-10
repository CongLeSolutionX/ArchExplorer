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
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExamo5MHcxaW1jYnlraml2MXp0ZWhubGFpbDVuaGlocjluZDRtOTlyeSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/A1uwghbB69eQ3cOdXz/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----



# Cutlass
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
title: "NVIDIA - cutlass"
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
    %% Build System
    BS["Build System<br>(CMake)"]:::build

    %% External Dependencies
    CUDA["CUDA Toolkit"]:::external
    GPU["GPU Hardware"]:::external
    Compiler["C++17 Compiler"]:::external
    BLAS["cuBLAS/cuDNN"]:::external

    %% Top Layer: User Integration
    subgraph User_Integration["User Integration"]
        SDKExamples["SDK Examples"]:::user
        PythonBindings["Python Bindings"]:::user
        PythonDocs["Documentation"]:::user
    end

    %% Middle Layer: Core Libraries
    subgraph Core_Libraries["Core Libraries"]
        CuTeLibrary["CuTe Library"]:::core
        CUTLASSCoreLibrary["CUTLASS Core Library"]:::core
        Submodules["Submodules:<br>arch, conv, gemm, epilogue, layout, reduction, transform, thread,..."]:::coreText
    end

    %% Lower Layer: Supporting Tools and Tests
    subgraph Support_Tools["Support Tools"]
        ToolsLibrary["Tools:<br>Library Instantiation"]:::tool
        ToolsProfiler["Tools:<br>Profiler"]:::tool
        Tests["Tests<br>(Google Test)"]:::tool
    end

    %% Build system configuration
    BS --> CUTLASSCoreLibrary
    BS --> CuTeLibrary
    BS --> SDKExamples
    BS --> PythonBindings
    BS --> PythonDocs
    BS --> ToolsLibrary
    BS --> ToolsProfiler
    BS --> Tests

    %% External dependencies for core
    CUTLASSCoreLibrary --> CUDA
    CUTLASSCoreLibrary --> GPU
    CUTLASSCoreLibrary --> Compiler
    CUTLASSCoreLibrary --> BLAS

    %% CuTe integration into CUTLASS
    CuTeLibrary --> CUTLASSCoreLibrary

    %% Core Library usage by User Integration
    CUTLASSCoreLibrary --> SDKExamples
    CUTLASSCoreLibrary --> PythonBindings
    CUTLASSCoreLibrary --> PythonDocs

    %% Core Library usage by Tools and Tests
    CUTLASSCoreLibrary --> ToolsLibrary
    CUTLASSCoreLibrary --> ToolsProfiler
    CUTLASSCoreLibrary --> Tests

    %% Annotation for core submodules
    CUTLASSCoreLibrary --- Submodules

    %% Class Definitions for colour and style
    classDef build fill:#f9d3,stroke:#d14,stroke-width:2px
    classDef external fill:#ffd3,stroke:#da2,stroke-width:2px
    classDef core fill:#ccf3,stroke:#55a,stroke-width:2px
    classDef tool fill:#cfc3,stroke:#5a5,stroke-width:2px
    classDef user fill:#fcc3,stroke:#a55,stroke-width:2px
    classDef coreText fill:#ef33,stroke:#333,stroke-width:2px,stroke-dasharray: 5 5

    %% Click Events
    click CUTLASSCoreLibrary "https://github.com/nvidia/cutlass/tree/main/include/cutlass"
    click CuTeLibrary "https://github.com/nvidia/cutlass/tree/main/include/cute"
    click SDKExamples "https://github.com/nvidia/cutlass/tree/main/examples"
    click ToolsLibrary "https://github.com/nvidia/cutlass/tree/main/tools/library"
    click ToolsProfiler "https://github.com/nvidia/cutlass/tree/main/tools/profiler"
    click Tests "https://github.com/nvidia/cutlass/tree/main/test"
    click PythonBindings "https://github.com/nvidia/cutlass/tree/main/python"
    click PythonDocs "https://github.com/nvidia/cutlass/tree/main/python/docs"
    
```





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
