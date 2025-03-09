---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# pkl
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
title: "Apple - pkl"
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
    "graph": {"htmlLabels": true, 'curve': 'natural'},
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
    %% External Nodes
    U["User Input"]:::external
    Gs["Gradle Build<br>(buildSrc & Config)"]:::external

    %% Core Language Processing Layer
    subgraph Core_Language_Processing["Core Language Processing"]
        A["Core Engine<br>(Parser,AST,Evaluator,ModuleResolver)"]:::core
        B["Standard Library<br>(JSON,YAML,XML,etc.)"]:::core
    end

    %% Interfaces Layer
    subgraph Interfaces["Interfaces"]
        C["CLI<br>(Interactive/Scriptable)"]:::interface
        D["Executor<br>(Remote/Embedded)"]:::interface
        E["Server<br>(Execution Service)"]:::interface
        F["Build Integration<br>(Gradle Plugin)"]:::interface
    end

    %% Tooling Layer
    subgraph Tooling["Tooling"]
        G["Java Code Generation"]:::tooling
        H["Kotlin Code Generation"]:::tooling
        I["Commons CLI Support"]:::tooling
        J["Documentation Generator"]:::tooling
        K["Additional Tools & Plugins"]:::tooling
    end

    %% Data Flows & Relationships
    U -->|"triggers"| C
    U -->|"triggers"| F

    Gs -->|"configures"| A
    Gs -->|"configures"| C
    Gs -->|"configures"| F
    Gs -->|"configures"| G
    Gs -->|"configures"| H
    Gs -->|"configures"| I
    Gs -->|"configures"| J

    C -->|"invokes"| A
    F -->|"invokes"| A

    A -->|"imports"| B

    A -->|"executes"| D
    A -->|"executes"| E

    A -->|"generates"| G
    A -->|"generates"| H
    A -->|"supports"| I
    A -->|"provides info"| J

    A -->|"integrates with"| K

    %% Click Events
    click A "https://github.com/apple/pkl/tree/main/pkl-core"
    click B "https://github.com/apple/pkl/tree/main/stdlib"
    click C "https://github.com/apple/pkl/tree/main/pkl-cli"
    click D "https://github.com/apple/pkl/tree/main/pkl-executor"
    click E "https://github.com/apple/pkl/tree/main/pkl-server"
    click F "https://github.com/apple/pkl/tree/main/pkl-gradle"
    click G "https://github.com/apple/pkl/tree/main/pkl-codegen-java"
    click H "https://github.com/apple/pkl/tree/main/pkl-codegen-kotlin"
    click I "https://github.com/apple/pkl/tree/main/pkl-commons-cli"
    click J "https://github.com/apple/pkl/tree/main/pkl-doc"
    click K "https://github.com/apple/pkl/tree/main/pkl-tools"

    %% Styles
    classDef core fill:#f8d7d,stroke:#721c24,stroke-width:2px
    classDef interface fill:#d4edd,stroke:#155724,stroke-width:2px
    classDef tooling fill:#d1ecf,stroke:#0c5460,stroke-width:2px
    classDef external fill:#fff3c,stroke:#856404,stroke-width:2px
    
```






---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---