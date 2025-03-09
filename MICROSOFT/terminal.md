---
created: 2025-03-09 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Terminal
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
title: "MICROSOFT - Terminal"
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
    %% User Interface Layer
    subgraph User_Interface_Layer["User Interface Layer"]
        A1["TerminalApp<br>(UI)"]:::ui
        A2["CascadiaPackage<br>(UI)"]:::ui
        A3["WPF Terminal Control<br>(UI)"]:::ui
        A4["WPF Terminal TestNetCore<br>(UI)"]:::ui
    end

    %% Terminal Core & Parsing Layer
    subgraph Terminal_Core_and_Parsing_Layer["Terminal Core & Parsing Layer"]
        B1["TerminalCore"]:::core
        B2["Adapter Module"]:::core
        B3["Parser Module"]:::core
        B4["Input Processing"]:::core
    end

    %% Rendering Engines Layer
    subgraph Rendering_Engines_Layer["Rendering Engines Layer"]
        C1["Atlas Renderer"]:::render
        C2["Base Renderer"]:::render
        C3["GDI Renderer"]:::render
        C4["UIA Renderer"]:::render
        C5["WDDM Renderer"]:::render
    end

    %% Console Host & OS Integration Layer
    subgraph Console_Host_and_OS_Integration_Layer["Console Host & OS Integration Layer"]
        D1["Console Host"]:::host
        D2["Host EXE"]:::host
        D3["Host UT"]:::host
        D4["Host Lib"]:::host
    end

    %% Shared Components & Libraries
    subgraph Shared_Components_and_Libraries["Shared Components & Libraries"]
        E1["Inc"]:::shared
        E2["Types"]:::shared
        E3["Propsheet"]:::shared
        E4["Propslib"]:::shared
    end

    %% Tools & Testing
    subgraph Tools_and_Testing["Tools & Testing"]
        F1["Tools"]:::testing
        F2["LocalTests_TerminalApp"]:::testing
        F3["UnitTests_TerminalCore"]:::testing
        F4["UnitTests_SettingsModel"]:::testing
        F5["UT_til"]:::testing
    end

    %% Connections between layers

    %% UI triggers core operations
    A1 -->|"triggers"| B1
    A2 -->|"triggers"| B1
    A3 -->|"triggers"| B1
    A4 -->|"triggers"| B1

    %% Core internal module calls
    B1 -->|"calls"| B2
    B1 -->|"calls"| B3
    B1 -->|"calls"| B4

    %% Core outputs for rendering
    B1 -->|"renders"| C1
    B1 -->|"renders"| C2
    B1 -->|"renders"| C3
    B1 -->|"renders"| C4
    B1 -->|"renders"| C5

    %% Core integrates with host
    B1 -->|"integrates"| D1

    %% Host internal subdivisions
    D1 --> D2
    D1 --> D3
    D1 --> D4

    %% Shared Components usage
    A1 -->|"uses"| E1
    B1 -->|"uses"| E2
    B1 -->|"uses"| E3
    B1 -->|"uses"| E4

    %% Tools & Testing interactions
    F1 -->|"tests UI"| A1
    F1 -->|"tests core"| B1
    F1 -->|"tests host"| D1
    F2 -->|"validates"| A1
    F3 -->|"validates"| B1
    F4 -->|"validates"| B1
    F5 -->|"validates"| B1

    %% Classes for color-coding
    classDef ui fill:#a255,stroke:#000,stroke-width:1px;
    classDef core fill:#9e95,stroke:#000,stroke-width:1px;
    classDef render fill:#fa73,stroke:#000,stroke-width:1px;
    classDef host fill:#dad3,stroke:#000,stroke-width:1px;
    classDef shared fill:#f685,stroke:#000,stroke-width:1px;
    classDef testing fill:#fb63,stroke:#000,stroke-width:1px;

    %% Click Events
    click A1 "https://github.com/microsoft/terminal/tree/main/src/cascadia/TerminalApp"
    click A2 "https://github.com/microsoft/terminal/tree/main/src/cascadia/CascadiaPackage"
    click A3 "https://github.com/microsoft/terminal/tree/main/src/cascadia/WpfTerminalControl"
    click A4 "https://github.com/microsoft/terminal/tree/main/src/cascadia/WpfTerminalTestNetCore"
    click B1 "https://github.com/microsoft/terminal/tree/main/src/cascadia/TerminalCore"
    click B2 "https://github.com/microsoft/terminal/tree/main/src/terminal/adapter"
    click B3 "https://github.com/microsoft/terminal/tree/main/src/terminal/parser"
    click B4 "https://github.com/microsoft/terminal/tree/main/src/terminal/input"
    click C1 "https://github.com/microsoft/terminal/tree/main/src/renderer/atlas"
    click C2 "https://github.com/microsoft/terminal/tree/main/src/renderer/base"
    click C3 "https://github.com/microsoft/terminal/tree/main/src/renderer/gdi"
    click C4 "https://github.com/microsoft/terminal/tree/main/src/renderer/uia"
    click C5 "https://github.com/microsoft/terminal/tree/main/src/renderer/wddmcon"
    click D1 "https://github.com/microsoft/terminal/tree/main/src/host"
    click D2 "https://github.com/microsoft/terminal/tree/main/src/host/exe"
    click D3 "https://github.com/microsoft/terminal/tree/main/src/host/ut_host"
    click D4 "https://github.com/microsoft/terminal/tree/main/src/host/lib"
    click E1 "https://github.com/microsoft/terminal/tree/main/src/inc"
    click E2 "https://github.com/microsoft/terminal/tree/main/src/types"
    click E3 "https://github.com/microsoft/terminal/tree/main/src/propsheet"
    click E4 "https://github.com/microsoft/terminal/tree/main/src/propslib"
    click F1 "https://github.com/microsoft/terminal/tree/main/src/tools"
    click F2 "https://github.com/microsoft/terminal/tree/main/src/cascadia/LocalTests_TerminalApp"
    click F3 "https://github.com/microsoft/terminal/tree/main/src/cascadia/UnitTests_TerminalCore"
    click F4 "https://github.com/microsoft/terminal/tree/main/src/cascadia/UnitTests_SettingsModel"
    click F5 "https://github.com/microsoft/terminal/tree/main/src/til/ut_til"
    
```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---