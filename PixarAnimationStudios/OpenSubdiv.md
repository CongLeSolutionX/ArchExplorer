---
created: 2025-03-23 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# OpenSubdiv
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---



```mermaid
---
title: "Pixar Animation Studios - OpenSubdiv"
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
    'flowchart': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'lineColor': '#F8B229'
    }
  }
}%%
flowchart TD
    %% Build and Configuration Layer
    subgraph "Build and Configuration"
        CMS["CMakeLists.txt"]:::build
        CMD["cmake Directory"]:::build
        CONFIG["opensubdiv-config.cmake.in"]:::build
    end

    %% Core Library Modules Layer
    subgraph "Core Library Modules"
        HBR["HBR Module"]:::core
        FAR["FAR Module"]:::core
        SDC["SDC Module"]:::core
        BFR["BFR Module"]:::core
        VTR["VTR Module"]:::core
        OSD["OSD Module"]:::core
    end

    %% Backend Implementations Layer
    subgraph "Backend Implementations"
        BE["Backend Evaluators"]:::backend
    end

    %% Client Applications Layer
    subgraph "Client Applications"
        EX["Examples"]:::client
        TUT["Tutorials"]:::client
        REG["Regression Tests"]:::client
    end

    %% External Dependencies
    subgraph "External Dependencies"
        EXT1["GLFW & Ptex"]:::external
        EXT2["CUDA, OpenCL, DX11, Metal, TBB, OpenMP"]:::external
        EXT3["Documentation Tools"]:::external
    end

    %% Documentation
    DOC["Documentation"]:::core

    %% Connections: Build and Configuration to Core Modules
    CMS -->|"configures"| HBR
    CMD -->|"configures"| HBR
    CONFIG -->|"configures"| HBR

    %% Connections within Core Library Modules
    HBR -->|"provides_topology"| FAR
    FAR -->|"supplies_refinement"| OSD
    FAR -->|"uses_scheme"| SDC
    FAR -->|"uses_representation"| BFR
    FAR -->|"uses_representation"| VTR

    %% Connection from Core to Backend Implementations
    OSD -->|"delegates_evaluation"| BE

    %% Client Applications invoking Core modules
    EX -->|"calls_API"| OSD
    TUT -->|"calls_API"| OSD
    REG -->|"calls_API"| OSD

    %% External Dependencies linked to relevant components
    EXT1 --- HBR
    EXT1 --- OSD
    EXT2 --- BE
    DOC --- EXT3

    %% Documentation linked with Client Applications for guidance
    DOC --- EX
    DOC --- TUT
    DOC --- REG

    %% Click Events
    click HBR "https://github.com/pixaranimationstudios/opensubdiv/tree/release/opensubdiv/hbr"
    click FAR "https://github.com/pixaranimationstudios/opensubdiv/tree/release/opensubdiv/far"
    click OSD "https://github.com/pixaranimationstudios/opensubdiv/tree/release/opensubdiv/osd"
    click SDC "https://github.com/pixaranimationstudios/opensubdiv/tree/release/opensubdiv/sdc"
    click BFR "https://github.com/pixaranimationstudios/opensubdiv/tree/release/opensubdiv/bfr"
    click VTR "https://github.com/pixaranimationstudios/opensubdiv/tree/release/opensubdiv/vtr"
    click BE "https://github.com/pixaranimationstudios/opensubdiv/tree/release/opensubdiv/osd"
    click CMS "https://github.com/pixaranimationstudios/opensubdiv/blob/release/CMakeLists.txt"
    click CMD "https://github.com/pixaranimationstudios/opensubdiv/tree/release/cmake"
    click CONFIG "https://github.com/pixaranimationstudios/opensubdiv/blob/release/opensubdiv-config.cmake.in"
    click EX "https://github.com/pixaranimationstudios/opensubdiv/tree/release/examples"
    click TUT "https://github.com/pixaranimationstudios/opensubdiv/tree/release/tutorials"
    click REG "https://github.com/pixaranimationstudios/opensubdiv/tree/release/regression"
    click DOC "https://github.com/pixaranimationstudios/opensubdiv/tree/release/documentation"

    %% Styles
    classDef build fill:#f4a261, stroke:#333, color:#fff;
    classDef core fill:#2a9d8f, stroke:#333, color:#fff;
    classDef backend fill:#e76f51, stroke:#333, color:#fff;
    classDef client fill:#264653, stroke:#333, color:#fff;
    classDef external fill:#6a994e, stroke:#333, color:#fff;


```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---