---
created: 2025-03-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExeWdhMDA2OTFuNXJnZ3VsNXJtbWR5YTRydGphdGVscXVyMWp1bzdoNyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/26DNaIqCtz7u4KN7W/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# openmct
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
title: "openmct"
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
      'primaryColor': '#ffff',
      'primaryTextColor': '#2ff9',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph TD
    %% Presentation Layer
    subgraph Presentation_Layer["Presentation Layer"]
        UI["UI / Presentation Layer"]:::ui
    end

    %% Core Services
    subgraph Core_Services["Core Services"]
        API["Core API Services"]:::backend
        PL["Plugin System"]:::plugin
    end

    %% Persistence & External Services
    subgraph Persistence_and_External_Services["Persistence & External Services"]
        Persist["Persistence & External<br>(CouchDB)"]:::external
    end

    %% Testing & Build Infrastructure
    subgraph Testing_and_Build_Infrastructure["Testing & Build Infrastructure"]
        CircleCI["CircleCI"]:::testing
        GitHub["GitHub Workflows"]:::testing
        E2E["E2E Tests"]:::testing
    end

    %% Connections between layers
    UI -->|"triggers"| API
    UI -->|"registers custom views"| PL
    API <-->|"plugin interactions"| PL
    API -->|"persists data"| Persist
    PL -->|"data store calls"| Persist

    %% Testing related connections
    CircleCI ---|"build/deploy"| API
    GitHub ---|"build/deploy"| API
    E2E ---|"E2Etests"| UI

    %% Click Events
    click API "https://github.com/nasa/openmct/tree/master/src/api"
    click PL "https://github.com/nasa/openmct/tree/master/src/plugins"
    click UI "https://github.com/nasa/openmct/tree/master/src/ui"
    click Persist "https://github.com/nasa/openmct/tree/master/src/plugins/persistence/couch"
    click CircleCI "https://github.com/nasa/openmct/blob/master/.circleci"
    click GitHub "https://github.com/nasa/openmct/tree/master/.github/workflows"
    click E2E "https://github.com/nasa/openmct/tree/master/e2e"

    %% Styles
    classDef ui fill:#cce5ff,stroke:#004085,stroke-width:2px
    classDef backend fill:#d4edda,stroke:#155724,stroke-width:2px
    classDef plugin fill:#fff3cd,stroke:#856404,stroke-width:2px
    classDef external fill:#f8d7da,stroke:#721c24,stroke-width:2px
    classDef testing fill:#d1ecf1,stroke:#0c5460,stroke-width:2px
    
```






---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
