---
created: 2025-04-01 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExNzdiNzlocGJyNDJkdXgzbzd2NWFjd2U3a3lwNGF5eHljb21tcnhjNSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/l0MYrrom5dJyVjYn6/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Material Components iOS
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
title: "CHANGE_ME_DADDY"
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
    'flowchart': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'lineColor': '#F8B229'
    }
  }
}%%
flowchart TD
    A["Material Components for iOS"]:::integration

    subgraph "UI Components"
        AS["ActionSheet"]:::uiComponents
        AB["AppBar"]:::uiComponents
        BT["Buttons"]:::uiComponents
        CH["Chips"]:::uiComponents
        TC["TextControls"]:::uiComponents
        INK["Ink"]:::uiComponents
        TS["Tabs"]:::uiComponents
    end

    subgraph "Shared Infrastructure"
        TSCH["Theming & Schemes"]:::sharedInfra
        PU["Private Utilities"]:::sharedInfra
    end

    subgraph "Testing/Quality Assurance"
        TQA["Tests & Snapshot Goldens"]:::testing
    end

    subgraph "Build & Deployment"
        CI["CI & Scripts"]:::build
    end

    subgraph "Documentation & Contribution"
        DOC["Docs & Contributing"]:::docs
    end

    subgraph "Client Integration"
        CIApp["Client iOS App"]:::integration
    end

    %% High-level container connecting to groups
    A -->|"contains"| AS
    A -->|"contains"| TSCH
    A -->|"contains"| TQA
    A -->|"contains"| CI
    A -->|"contains"| DOC
    A -->|"integrates_with"| CIApp

    %% UI Components dependencies on Shared Infrastructure
    AS -->|"uses"| TSCH
    AB -->|"uses"| TSCH
    BT -->|"uses"| PU
    CH -->|"uses"| TSCH
    INK -->|"uses"| PU
    TC -->|"uses"| TSCH
    TS -->|"uses"| PU

    %% UI Components connection to Testing/Quality Assurance
    AS -->|"tested_by"| TQA
    BT -->|"tested_by"| TQA

    %% UI Components connection to Build & Deployment
    AB -->|"built_with"| CI

    %% UI Components connection to Documentation & Contribution
    BT -->|"documented_in"| DOC

    %% Client Integration consuming UI Components
    CIApp -->|"integrates"| TC

    %% Styles
    classDef uiComponents fill:#BBDEFB,stroke:#0D47A1,stroke-width:2px;
    classDef sharedInfra fill:#C8E6C9,stroke:#1B5E20,stroke-width:2px;
    classDef testing fill:#FFE082,stroke:#FF6F00,stroke-width:2px;
    classDef build fill:#FFCDD2,stroke:#B71C1C,stroke-width:2px;
    classDef docs fill:#D1C4E9,stroke:#4A148C,stroke-width:2px;
    classDef integration fill:#B0BEC5,stroke:#263238,stroke-width:2px;

    %% Click Events
    click AS "https://github.com/material-components/material-components-ios/tree/develop/components/ActionSheet"
    click AB "https://github.com/material-components/material-components-ios/tree/develop/components/AppBar"
    click BT "https://github.com/material-components/material-components-ios/tree/develop/components/Buttons"
    click CH "https://github.com/material-components/material-components-ios/tree/develop/components/Chips"
    click TSCH "https://github.com/material-components/material-components-ios/tree/develop/components/schemes"
    click PU "https://github.com/material-components/material-components-ios/tree/develop/components/private"
    click TQA "https://github.com/material-components/material-components-ios/tree/develop/snapshot_test_goldens"
    click CI "https://github.com/material-components/material-components-ios/tree/develop/scripts"
    click DOC "https://github.com/material-components/material-components-ios/tree/develop/docs"
    
```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
