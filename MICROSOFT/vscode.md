---
created: 2025-03-09 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# vscode
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
title: "MICROSOFT - VSCode"
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
    subgraph UI_and_Workbench["UI & Workbench"]
        UI["UI / Editor Frontend"]:::frontend
    end

    subgraph Services_and_Backend["Services & Backend"]
        CS["Services and Core Functionality"]:::service
        LS["Language Services & Tokenization"]:::service
    end

    subgraph Platform_Layer["Platform Layer"]
        CP["Core Platform<br>(Electron Shell / Host Process)"]:::platform
        EH["Extension Host / Worker Layer"]:::platform
        RP["Remote Services"]:::platform
    end

    subgraph Testing_and_Debugging["Testing & Debugging"]
        T["Testing / Debugging / Profiling Infrastructure"]:::testing
    end

    %% Connections between layers
    UI -->|"calls"| CS
    UI -->|"depends on"| LS
    UI -->|"IPC"| EH

    EH -->|"registers extensions"| CS
    CP -->|"IPC"| EH
    EH -->|"IPC"| CP
    CP -->|"remote sync"| RP
    RP -->|"remote sync"| CP
    CS -->|"injects"| LS

    T -->|"tests"| CP
    T -->|"tests"| CS
    T -->|"tests"| UI

    %% Styles
    classDef platform fill:#FC55,stroke:#333,stroke-width:2px;
    classDef frontend fill:#9FC5,stroke:#333,stroke-width:2px;
    classDef service fill:#C9F5,stroke:#333,stroke-width:2px;
    classDef testing fill:#F993,stroke:#333,stroke-width:2px;

    %% Click Events
    click CP "https://github.com/microsoft/vscode/blob/main/src/bootstrap-node.ts and src/vs/code/electron-main/ (e.g. app.ts, main.ts)"
    click EH "https://github.com/microsoft/vscode/tree/main/extensions/"
    click UI "https://github.com/microsoft/vscode/tree/main/src/vs and src/vs/workbench"
    click CS "https://github.com/microsoft/vscode/tree/main/src/vs/base and src/vs/workbench/services"
    click LS "https://github.com/microsoft/vscode/tree/main/src/vs/editor/common/tokenizationRegistry.ts and src/vs/workbench/services/textMate"
    click T "https://github.com/microsoft/vscode/tree/main/test/"
    
```






---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---