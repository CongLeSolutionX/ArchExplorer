---
created: 2025-03-17 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# renode
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
title: "TESLA - Renode"
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
    'graph': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'lineColor': '#F8B229'
    }
  }
}%%
graph TB
    %% Styles and classes
    classDef core fill:#b3d1ff,stroke:#333
    classDef plugin fill:#90EE90,stroke:#333
    classDef external fill:#FFB366,stroke:#333
    classDef testing fill:#DDA0DD,stroke:#333
    classDef ui fill:#D3D3D3,stroke:#333

    %% Legend
    subgraph Legend
        L1[Core Components]:::core
        L2[Plugin Modules]:::plugin
        L3[External Interfaces]:::external
        L4[Testing Components]:::testing
        L5[User Interface]:::ui
    end

    %% Top Layer - User Interfaces
    subgraph UI
        CLI[CLI Interface]:::ui
        Monitor[Monitor UI]:::ui
        RFInterface[Robot Framework Interface]:::ui
        ExtAPI[External Control API]:::ui
    end

    %% Middle Layer - Core Components
    subgraph Core
        PlatformParser[Platform Description Parser]:::core
        EmulationEnv[Emulation Environment]:::core
        TimeController[Virtual Time Controller]:::core
        EventSystem[Event System]:::core
        Infrastructure[Infrastructure]:::core
    end

    %% Bottom Layer - Hardware Simulation
    subgraph HWSim
        CPUEmu[CPU Emulation]:::core
        PeripheralSim[Peripheral Simulation]:::core
        NetworkSim[Network Simulation]:::core
        MemoryMgmt[Memory Management]:::core
    end

    %% Plugin Components
    subgraph Plugins
        CoSim[CoSimulation Plugin]:::plugin
        SystemC[SystemC Plugin]:::plugin
        Wireshark[Wireshark Plugin]:::plugin
    end

    %% Testing Components
    subgraph Testing
        RobotFramework[Robot Framework Tests]:::testing
        UnitTests[Unit Tests]:::testing
    end

    %% Relationships
    CLI --> PlatformParser
    Monitor --> EmulationEnv
    RFInterface --> RobotFramework
    ExtAPI --> NetworkSim

    PlatformParser --> EmulationEnv
    EmulationEnv --> TimeController
    TimeController --> EventSystem
    EventSystem --> Infrastructure

    Infrastructure --> CPUEmu
    Infrastructure --> PeripheralSim
    Infrastructure --> NetworkSim
    Infrastructure --> MemoryMgmt

    CoSim --> EmulationEnv
    SystemC --> EmulationEnv
    Wireshark --> NetworkSim

    %% Click events for component mapping
    click Infrastructure "https://github.com/renode/renode/tree/master/src/Infrastructure/"
    click PlatformParser "https://github.com/renode/renode/tree/master/src/Renode/PlatformDescription/"
    click EmulationEnv "https://github.com/renode/renode/blob/master/src/Renode/EmulationEnvironment/EmulationEnvironment.cs"
    click Monitor "https://github.com/renode/renode/tree/master/src/Renode/UI/"
    click CoSim "https://github.com/renode/renode/tree/master/src/Plugins/CoSimulationPlugin/"
    click SystemC "https://github.com/renode/renode/tree/master/src/Plugins/SystemCPlugin/"
    click Wireshark "https://github.com/renode/renode/tree/master/src/Plugins/WiresharkPlugin/"
    click RFInterface "https://github.com/renode/renode/tree/master/src/Renode/RobotFrameworkEngine/"
    click ExtAPI "https://github.com/renode/renode/tree/master/src/Renode/Network/ExternalControl/"
    click NetworkSim "https://github.com/renode/renode/tree/master/src/Renode/Network/NetworkServer/"
    click RobotFramework "https://github.com/renode/renode/tree/master/tests/"
    click UnitTests "https://github.com/renode/renode/tree/master/tests/unit-tests/"
    click CPUEmu "https://github.com/renode/renode/tree/master/platforms/cpus/"
    click PeripheralSim "https://github.com/renode/renode/tree/master/platforms/boards/"
    
```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---