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
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExZTM4ejZwZTh2YmRyN2E1OHRvZzVvZHVqYzU5N3lkZW1vNGJwc3J0YiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/iIqmM5tTjmpOB9mpbn/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Code NASA Gov
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
title: "Code NASA Gov"
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
graph TD
  %% Frontend Application (Polymer)
  subgraph Frontend_Application["Frontend Application<br>(Polymer)"]
    AR_UI["AR:<br>UI Assets"]:::frontend
    SRC_UI["src:<br>Polymer Components"]:::frontend
    PolyConfig["Polymer Config<br>(polymer.json, bower.json)"]:::frontend
    SW["Service Worker<br>(service-worker.js, sw-precache-config.js)"]:::frontend
  end

  %% Data Layer (JSON Files)
  subgraph Data_Layer["Data Layer<br>(JSON Files)"]
    JSON_Data["JSON Data Files (data)"]:::data
    Deprecated_Data["Deprecated JSON (data/deprecated)"]:::data
  end

  %% Data Transformation Process
  subgraph Data_Transformation["Data Transformation"]
    Cron["Cron Scripts"]:::processing
  end

  %% Build & Deployment Process
  subgraph Build_and_Deployment["Build & Deployment"]
    Build_Process["Build Process<br>(Polymer CLI)"]:::build
    Deployment_Config["Deployment Config<br>(app.yaml, package.json, package-lock.json)"]:::deploy
    Deployment_Server["Deployment Server<br>(Static Hosting)"]:::deploy
  end

  %% Development & CI/CD
  subgraph Development_and_CI_CD["Development & CI/CD"]
    Git_CI["Source Control<br>(Git)"]:::ci
    CI_Config["CI Configuration<br>(Travis CI, GitHub workflows)"]:::ci
  end

  %% Static Assets and Miscellaneous
  subgraph "Static Assets"
    F_images["Images"]:::static
    F_fonts["Fonts"]:::static
    F_docs["Supporting Documents"]:::static
  end

  %% Relationships and Data Flow
  JSON_Data --> Cron
  Deprecated_Data --> Cron
  Cron --> SRC_UI
  PolyConfig --> Build_Process
  CI_Config --> Build_Process
  Build_Process --> Deployment_Config
  Deployment_Config --> Deployment_Server
  AR_UI --> SW
  SRC_UI --> SW
  F_images --> AR_UI
  F_fonts --> AR_UI
  F_docs --> AR_UI
  Git_CI --> CI_Config

  %% Click Events for Frontend Application – UI Assets
  click AR_UI "https://github.com/nasa/code-nasa-gov/tree/master/AR/"
  click SRC_UI "https://github.com/nasa/code-nasa-gov/tree/master/src/"

  %% Click Events for Frontend Application – Polymer Components & Configuration
  click PolyConfig "https://github.com/nasa/code-nasa-gov/blob/master/polymer.json"

  %% Click Events for Frontend Application – Service Worker
  click SW "https://github.com/nasa/code-nasa-gov/blob/master/service-worker.js"

  %% Click Events for Data Layers – JSON Data Files
  click JSON_Data "https://github.com/nasa/code-nasa-gov/tree/master/data/"
  click Deprecated_Data "https://github.com/nasa/code-nasa-gov/tree/master/data/deprecated"

  %% Click Event for Data Transformation Process – Cron Scripts
  click Cron "https://github.com/nasa/code-nasa-gov/tree/master/cron_scripts/"

  %% Click Event for Build & Deployment Process – Deployment Configuration
  click Deployment_Config "https://github.com/nasa/code-nasa-gov/blob/master/app.yaml"

  %% Click Events for Development & CI/CD
  click Git_CI "https://github.com/nasa/code-nasa-gov/blob/master/.gitignore"
  click CI_Config "https://github.com/nasa/code-nasa-gov/blob/master/.travis.yml"

  %% Click Events for Static Assets
  click F_images "https://github.com/nasa/code-nasa-gov/tree/master/images/"
  click F_fonts "https://github.com/nasa/code-nasa-gov/tree/master/fonts/"
  click F_docs "https://github.com/nasa/code-nasa-gov/blob/master/NASA-M-16-21-Framework.pdf"

  %% Styles
  classDef frontend fill:#cce5ff,stroke:#004085,stroke-width:2px
  classDef data fill:#d4edda,stroke:#155724,stroke-width:2px
  classDef processing fill:#fff3cd,stroke:#856404,stroke-width:2px
  classDef build fill:#d1ecf1,stroke:#0c5460,stroke-width:2px
  classDef deploy fill:#f8d7da,stroke:#721c24,stroke-width:2px
  classDef ci fill:#e2e3e5,stroke:#41464b,stroke-width:2px
  classDef static fill:#fefefe,stroke:#6c757d,stroke-width:2px


```


---

<!-- 
```mermaid
%% Current Mermaid version
info
```  -->


```mermaid
---
title: "CongLeSolutionX"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%{
  init: {
    'flowchart': { 'htmlLabels': false },
    'fontFamily': 'Bradley Hand',
    'themeVariables': {
      'primaryColor': '#fc82',
      'primaryTextColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#81c784',
      'secondaryTextColor': '#6C3483',
      'lineColor': '#F8B229',
      'fontSize': '20px'
    }
  }
}%%
flowchart LR
  My_Meme@{ img: "https://raw.githubusercontent.com/CongLeSolutionX/CongLeSolutionX/refs/heads/main/assets/images/My-meme-light-bulb-question-marks.png", label: "Ăn uống gì chưa ngừi đẹp?", pos: "b", w: 200, h: 150, constraint: "off" }

  Closing_quote@{ shape: braces, label: "...searching insights in the process of formulating better questions..." }

  Closing_quote ~~~ My_Meme
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }

```

---
> **Licenses:**
>
> - **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
> - **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).
> 
---

