---
created: 2025-03-17 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Light Show
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
title: "TESLA - Light Show"
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
      'textColor': '#F8B229',
      'lineColor': '#F8B229'
    }
  }
}%%
flowchart TD
    %% Repository Resources Subgraph
    subgraph "Repository Resources"
        direction TB
        UserDoc["User Documentation (README & Images)"]:::documentation
        GitHub["GitHub Workflows"]:::code
        Validator["Light Show Validator"]:::tool
        CrossVehicle["Cross-Vehicle Shows"]:::documentation
    end

    %% Process Flow Subgraph
    subgraph "Light Show Process"
        direction TB
        xLights["xLights Project Folder"]:::resource
        App["xLights Application (Sequence Editor)"]:::resource
        Examples["Example Sequences"]:::resource
        USB["(USB Flash Drive Packaging)"]:::storage
        Tesla["Tesla Vehicle"]:::device
    end

    %% Connections between Repository Resources and Process Flow
    UserDoc -->|"instructs"| xLights
    xLights -->|"loaded into"| App
    Examples -->|"informs"| App
    App -->|"validated by"| Validator
    Validator -->|"outputs to"| USB
    USB -->|"runs on"| Tesla

    %% Click Events for Component Mapping
    click UserDoc "https://github.com/teslamotors/light-show/blob/master/README.md"
    click UserDoc "https://github.com/teslamotors/light-show/tree/master/images/"
    click xLights "https://github.com/teslamotors/light-show/tree/master/xlights/"
    click Examples "https://github.com/teslamotors/light-show/tree/master/examples/"
    click Validator "https://github.com/teslamotors/light-show/blob/master/validator.py"
    click Validator "https://github.com/teslamotors/light-show/blob/master/validator-macos.zip"
    click Validator "https://github.com/teslamotors/light-show/blob/master/validator-windows.exe"
    click CrossVehicle "https://github.com/teslamotors/light-show/tree/master/cross-vehicle-shows/"
    click GitHub "https://github.com/teslamotors/light-show/blob/master/.github/workflows/build.yml"

    %% Styles
    classDef documentation fill:#AED6F1,stroke:#2E86C1,stroke-width:2px;
    classDef code fill:#A3E4D7,stroke:#1ABC9C,stroke-width:2px;
    classDef tool fill:#F9E79F,stroke:#F1C40F,stroke-width:2px;
    classDef resource fill:#FAD7A0,stroke:#F39C12,stroke-width:2px;
    classDef storage fill:#D2B4DE,stroke:#8E44AD,stroke-width:2px;
    classDef device fill:#F5B7B1,stroke:#EC7063,stroke-width:2px;
    
```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
