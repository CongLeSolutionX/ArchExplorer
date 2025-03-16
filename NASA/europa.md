---
created: 2025-03-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# europas
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
title: "Eurora"
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
    'flowchart': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#2ff9',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TD
    subgraph Core_Engine_Components["Core Engine Components"]
        PD["Plan Database"]:::core
        PS["Problem Solver"]:::core
        CE["Constraint Engine"]:::core
        TM["Temporal Network"]:::core
        RM["Resource Manager"]:::core
        ND["NDDL Interpreter"]:::core
    end

    subgraph Presentation_Layer["Presentation Layer"]
        UI["Tool Box / UI"]:::ui
    end

    %% Interactions between UI and Plan Database
    UI -->|"sends queries"| PD
    PD -->|"responds data"| UI

    %% Interactions between Problem Solver and Plan Database
    PS -->|"updates plan"| PD
    PD -->|"provides plan"| PS

    %% Interactions from Specialized Modules to Problem Solver
    CE -->|"constraint info"| PS
    TM -->|"temporal data"| PS
    RM -->|"resource info"| PS

    %% Domain Modeling feeding into core components
    ND -->|"domain models"| PS
    ND -->|"domain models"| PD

    %% Styles
    classDef core fill:#DDF4,stroke:#000,stroke-width:2px
    classDef ui fill:#90EE,stroke:#000,stroke-width:2px

    %% Click Events
    click PD "https://github.com/nasa/europa/tree/master/src/PLASMA/PlanDatabase"
    click PS "https://github.com/nasa/europa/tree/master/src/PLASMA/Solvers"
    click CE "https://github.com/nasa/europa/tree/master/src/PLASMA/ConstraintEngine"
    click TM "https://github.com/nasa/europa/tree/master/src/PLASMA/TemporalNetwork"
    click RM "https://github.com/nasa/europa/tree/master/src/PLASMA/Resource"
    click ND "https://github.com/nasa/europa/tree/master/src/PLASMA/NDDL"
    click UI "https://github.com/nasa/europa/tree/master/src/Java/JavaUI"

```





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---