---
created: 2025-03-28 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Actions - JavaScript Action
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
title: "JavaScript Action"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'graph': { 'htmlLabels': false, 'curve': 'linear' },
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
graph TD
    %% GitHub Environment
    subgraph GitHub_Environment["GitHub Environment"]
        A["GitHub Actions Infrastructure / CI-CD"]
    end

    %% Action Configuration
    subgraph Action_Configuration["Action Configuration"]
        B["Action Metadata<br>(action.yml)"]
    end

    %% Dependency & License Management
    subgraph Dependency_and_License_Management["Dependency & License Management"]
        DPM1["package.json"]
        DPM2["package-lock.json"]
        DPM3[".licenses"]
        DPM4["licensed.yml"]
    end

    %% Core Logic
    subgraph Core_Logic["Core Logic"]
        S["Source Code<br>(src/)"]
    end

    %% Build Process
    subgraph Build_Process["Build Process"]
        E["Rollup Config<br>(rollup.config.js)"]
        F["Bundled Distribution<br>(dist/)"]
    end

    %% Testing Infrastructure
    subgraph Testing_Infrastructure["Testing Infrastructure"]
        T["Tests<br>(__tests__)"]
        X["Fixtures<br>(__fixtures__)"]
    end

    %% Relationships
    A -->|"triggers"| B
    B -->|"invokes"| S
    DPM1 -->|"dependency"| S
    DPM2 -->|"dependency"| S
    DPM3 -->|"license check"| S
    DPM4 -->|"license check"| S
    S -->|"compiled by"| E
    E -->|"bundles into"| F
    S -->|"validated by"| T
    F -->|"validated by"| T
    T -->|"uses"| X
    A -->|"runs CI"| T

    %% Click Events
    click A "https://github.com/actions/javascript-action/tree/main/.github/workflows"
    click B "https://github.com/actions/javascript-action/blob/main/action.yml"
    click S "https://github.com/actions/javascript-action/tree/main/src/"
    click E "https://github.com/actions/javascript-action/blob/main/rollup.config.js"
    click F "https://github.com/actions/javascript-action/tree/main/dist/"
    click T "https://github.com/actions/javascript-action/tree/main/__tests__"
    click X "https://github.com/actions/javascript-action/tree/main/__fixtures__"
    click DPM1 "https://github.com/actions/javascript-action/blob/main/package.json"
    click DPM2 "https://github.com/actions/javascript-action/blob/main/package-lock.json"
    click DPM3 "https://github.com/actions/javascript-action/blob/main/.licenses"
    click DPM4 "https://github.com/actions/javascript-action/blob/main/licensed.yml"

    %% Styles
    classDef github fill:#f9e79f,stroke:#333,stroke-width:2px
    classDef actionConfig fill:#aed6f1,stroke:#333,stroke-width:2px
    classDef dep fill:#f5cba7,stroke:#333,stroke-width:2px
    classDef core fill:#abebc6,stroke:#333,stroke-width:2px
    classDef build fill:#d6eaf8,stroke:#333,stroke-width:2px
    classDef testing fill:#fcf3cf,stroke:#333,stroke-width:2px

    class A github
    class B actionConfig
    class DPM1,DPM2,DPM3,DPM4 dep
    class S core
    class E,F build
    class T,X testing
    
```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---