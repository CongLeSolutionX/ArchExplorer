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
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExdmd3NXV2eDBxeHY1cmV4MXB1NWs3dmE0dDV3YzU2cnRnMHc0cXBmaCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/l41lW5bdMIQfRzt96/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----



# Material Web
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
    %% Aggregate UI Components node
    CompLib("Components Library"):::ui

    %% UI Components Subgraph
    subgraph "UI Components"
        Button("Button"):::ui
        Checkbox("Checkbox"):::ui
        Chips("Chips"):::ui
        Dialog("Dialog"):::ui
        Divider("Divider"):::ui
        Elevation("Elevation"):::ui
        Fab("Fab"):::ui
        Field("Field"):::ui
        Focus("Focus"):::ui
        Icon("Icon"):::ui
        IconButton("IconButton"):::ui
        List("List"):::ui
        Menu("Menu"):::ui
        Progress("Progress"):::ui
        Radio("Radio"):::ui
        Ripple("Ripple"):::ui
        Select("Select"):::ui
        Slider("Slider"):::ui
        Switch("Switch"):::ui
        Tabs("Tabs"):::ui
        TextField("TextField"):::ui
    end

    %% Composition: Components Library includes individual UI components
    CompLib -->|"includes"| Button
    CompLib -->|"includes"| Checkbox
    CompLib -->|"includes"| Chips
    CompLib -->|"includes"| Dialog
    CompLib -->|"includes"| Divider
    CompLib -->|"includes"| Elevation
    CompLib -->|"includes"| Fab
    CompLib -->|"includes"| Field
    CompLib -->|"includes"| Focus
    CompLib -->|"includes"| Icon
    CompLib -->|"includes"| IconButton
    CompLib -->|"includes"| List
    CompLib -->|"includes"| Menu
    CompLib -->|"includes"| Progress
    CompLib -->|"includes"| Radio
    CompLib -->|"includes"| Ripple
    CompLib -->|"includes"| Select
    CompLib -->|"includes"| Slider
    CompLib -->|"includes"| Switch
    CompLib -->|"includes"| Tabs
    CompLib -->|"includes"| TextField

    %% Internal Utilities & Shared Modules Subgraph
    subgraph "Internal Utilities & Shared Modules"
        InternalLogic("Internal Shared Logic"):::internal
        Tokens("Design Tokens & Theming"):::internal
        Typography("Typography/Base Styles"):::internal
        AllExports("Common Shared Exports (all.ts)"):::internal
        CommonExports("Common Shared Exports (common.ts)"):::internal
    end

    %% Catalog/Demo Site Subgraph
    subgraph "Catalog/Demo Site"
        Catalog("Catalog & Demo Site"):::demo
    end

    %% Documentation & Build Infrastructure Subgraph
    subgraph "Documentation & Build Infrastructure"
        Docs("Documentation"):::infra
        CI("Build & CI/CD Pipeline"):::infra
    end

    %% Auxiliary Elements Subgraph
    subgraph "Auxiliary Elements"
        Labs("Labs/Experimental Components"):::aux
        Testing("Testing Utilities"):::aux
        Migrations("Migration Scripts"):::aux
    end

    %% Dependencies and Relationships
    Catalog -->|"consumes"| CompLib
    CI -->|"builds"| CompLib
    Docs -->|"documents"| CompLib

    CompLib -->|"depends_on"| InternalLogic
    CompLib -->|"depends_on"| Tokens
    CompLib -->|"depends_on"| Typography
    CompLib -->|"depends_on"| AllExports
    CompLib -->|"depends_on"| CommonExports

    Labs -->|"experimental"| CompLib

    %% Click Events for UI Components
    click Button "https://github.com/material-components/material-web/tree/main/button/"
    click Checkbox "https://github.com/material-components/material-web/tree/main/checkbox/"
    click Chips "https://github.com/material-components/material-web/tree/main/chips/"
    click Dialog "https://github.com/material-components/material-web/tree/main/dialog/"
    click Divider "https://github.com/material-components/material-web/tree/main/divider/"
    click Elevation "https://github.com/material-components/material-web/tree/main/elevation/"
    click Fab "https://github.com/material-components/material-web/tree/main/fab/"
    click Field "https://github.com/material-components/material-web/tree/main/field/"
    click Focus "https://github.com/material-components/material-web/tree/main/focus/"
    click Icon "https://github.com/material-components/material-web/tree/main/icon/"
    click IconButton "https://github.com/material-components/material-web/tree/main/iconbutton/"
    click List "https://github.com/material-components/material-web/tree/main/list/"
    click Menu "https://github.com/material-components/material-web/tree/main/menu/"
    click Progress "https://github.com/material-components/material-web/tree/main/progress/"
    click Radio "https://github.com/material-components/material-web/tree/main/radio/"
    click Ripple "https://github.com/material-components/material-web/tree/main/ripple/"
    click Select "https://github.com/material-components/material-web/tree/main/select/"
    click Slider "https://github.com/material-components/material-web/tree/main/slider/"
    click Switch "https://github.com/material-components/material-web/tree/main/switch/"
    click Tabs "https://github.com/material-components/material-web/tree/main/tabs/"
    click TextField "https://github.com/material-components/material-web/tree/main/textfield/"

    %% Click Events for Internal Utilities & Shared Modules
    click InternalLogic "https://github.com/material-components/material-web/tree/main/internal/"
    click Tokens "https://github.com/material-components/material-web/tree/main/tokens/"
    click Typography "https://github.com/material-components/material-web/tree/main/typography/"
    click AllExports "https://github.com/material-components/material-web/blob/main/all.ts"
    click CommonExports "https://github.com/material-components/material-web/blob/main/common.ts"

    %% Click Event for Catalog/Demo Site
    click Catalog "https://github.com/material-components/material-web/tree/main/catalog/"

    %% Click Events for Documentation & Build Infrastructure
    click Docs "https://github.com/material-components/material-web/tree/main/docs/"
    click CI "https://github.com/material-components/material-web/tree/main/.github/"

    %% Click Events for Auxiliary Elements
    click Labs "https://github.com/material-components/material-web/tree/main/labs/"
    click Testing "https://github.com/material-components/material-web/tree/main/testing/"
    click Migrations "https://github.com/material-components/material-web/tree/main/migrations/"

    %% Styles
    classDef ui fill:#AED6F1,stroke:#2E86C1,stroke-width:2px
    classDef internal fill:#A9DFBF,stroke:#239B56,stroke-width:2px
    classDef demo fill:#F9E79F,stroke:#F1C40F,stroke-width:2px
    classDef infra fill:#F5B7B1,stroke:#E74C3C,stroke-width:2px
    classDef aux fill:#D2B4DE,stroke:#8E44AD,stroke-width:2px
    
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
