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
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExYjduN21jdHk3cjZ0eXQ2cml0OTloNWRvMDg0dDA2bmxlcWV0bzQzaSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3oEduHCqVio59FqcNi/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Material Components Android
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
    'graph': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'lineColor': '#F8B229'
    }
  }
}%%
graph TD
    Library["Core Library (MDC-Android)"]:::core
    Catalog["Catalog Demo App"]:::demo
    Tests["Test Suites"]:::test
    Build["Build & Configuration"]:::build
    Docs["Documentation"]:::docs

    subgraph "Internal Modules of Core Library"
        Utility["Utility Layer"]:::core
        Visual["Visual/Behavior Layer"]:::core
        subgraph "UI Components"
            APB["AppBar"]:::core
            BTN["Button"]:::core
            CHIP["Chip"]:::core
            SNK["Snackbar"]:::core
            DLG["Dialog"]:::core
            TXT["TextField"]:::core
            DTP["DatePicker"]:::core
            TTP["TimePicker"]:::core
            FAB["FloatingActionButton"]:::core
            SLD["Slider"]:::core
        end
    end

    %% Internal Library relationships
    Library -->|"supports"| Utility
    Library -->|"supports"| Visual
    Library -->|"contains"| BTN
    Utility -->|"enables"| Visual
    Utility -->|"assists"| BTN
    Visual -->|"enhances"| BTN

    %% Global dependencies and interactions
    Catalog -->|"depends_on"| Library
    Tests -->|"tests"| Library
    Build -->|"builds"| Library
    Build -->|"builds"| Catalog
    Build -->|"builds"| Tests
    Docs -->|"guides"| Library

    %% Click Events for Component Mapping
    click Library "https://github.com/material-components/material-components-android/tree/master/lib/"
    click Library "https://github.com/material-components/material-components-android/tree/master/lib/java/com/google/android/material/"
    click Catalog "https://github.com/material-components/material-components-android/tree/master/catalog/"
    click Tests "https://github.com/material-components/material-components-android/tree/master/lib/javatests/"
    click Tests "https://github.com/material-components/material-components-android/tree/master/catalog/test/"
    click Tests "https://github.com/material-components/material-components-android/tree/master/tests/"
    click Tests "https://github.com/material-components/material-components-android/tree/master/testing/"
    click Build "https://github.com/material-components/material-components-android/blob/master/build.gradle"
    click Build "https://github.com/material-components/material-components-android/blob/master/settings.gradle"
    click Build "https://github.com/material-components/material-components-android/tree/master/gradlew"
    click Build "https://github.com/material-components/material-components-android/blob/master/gradlew.bat"
    click Build "https://github.com/material-components/material-components-android/tree/master/gradle/"
    click Build "https://github.com/material-components/material-components-android/blob/master/.gitignore"
    click Build "https://github.com/material-components/material-components-android/blob/master/.editorconfig"
    click Docs "https://github.com/material-components/material-components-android/tree/master/docs/"
    click Docs "https://github.com/material-components/material-components-android/blob/master/README.md"

    %% Styles
    classDef core fill:#bbf,stroke:#333,stroke-width:2px;
    classDef demo fill:#cfc,stroke:#333,stroke-width:2px;
    classDef test fill:#fbb,stroke:#333,stroke-width:2px;
    classDef build fill:#fdd,stroke:#333,stroke-width:2px;
    classDef docs fill:#ddd,stroke:#333,stroke-width:2px;
    
```






---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
