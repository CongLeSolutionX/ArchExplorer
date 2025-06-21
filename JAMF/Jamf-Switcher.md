---
created: 2025-03-22 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExdXp3dTJrNjExdTd5c3JwdzlsZmo0ZmJqbjJhanN1d2JnMnBmNWN3ayZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/52qtwCtj9OLTi/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----

# Jamf Switcher
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
title: "Jamf Switcher"
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
      'textColor': '#F8B229',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TD

    %% UI Layer
    subgraph "UI Layer"
        UI1["Main.storyboard"]
        UI2["AppDelegate.swift"]
        UI3["ViewController.swift"]
    end

    %% Business Logic Layer
    subgraph "Business Logic"
        BL1["PolicyLogic.swift"]
    end

    %% Self Service Processing
    subgraph "Self Service Processing"
        SSP["JamfSelfServiceParser.swift"]
    end

    %% API/Service Layer
    subgraph "API/Service Layer"
        APIC1["CallAPI.swift"]
        APIC2["JamfAPI.swift"]
        APIL["JamfLogic.swift"]
        APIM["Structures.swift"]
        APIS["JamfService.swift"]
    end

    %% System Integration
    subgraph "System Integration"
        SI1["KeychainService.swift"]
        SI2["Configuration File Update"]
    end

    %% Connections
    UI1 -->|"user interaction"| BL1
    UI2 -->|"user interaction"| BL1
    UI3 -->|"user interaction"| BL1
    SSP -->|"parses bookmarks"| BL1

    BL1 -->|"invokes service"| APIS
    APIS -->|"calls API"| APIC1
    APIS -->|"calls API"| APIC2
    APIS -->|"processes logic"| APIL
    APIS -->|"manages data"| APIM

    BL1 -->|"triggers"| SI1
    BL1 -->|"updates"| SI2

    %% Click Events - UI Layer
    click UI1 "https://github.com/jamf/jamf-switcher/blob/master/Jamf Switcher/Base.lproj/Main.storyboard"
    click UI2 "https://github.com/jamf/jamf-switcher/blob/master/Jamf Switcher/AppDelegate.swift"
    click UI3 "https://github.com/jamf/jamf-switcher/blob/master/Jamf Switcher/ViewController.swift"

    %% Click Events - API Layer
    click APIC1 "https://github.com/jamf/jamf-switcher/blob/master/Jamf Switcher/JamfAPI/API/CallAPI.swift"
    click APIC2 "https://github.com/jamf/jamf-switcher/blob/master/Jamf Switcher/JamfAPI/API/JamfAPI.swift"
    click APIL "https://github.com/jamf/jamf-switcher/blob/master/Jamf Switcher/JamfAPI/Logic/JamfLogic.swift"
    click APIM "https://github.com/jamf/jamf-switcher/blob/master/Jamf Switcher/JamfAPI/Models/Structures.swift"
    click APIS "https://github.com/jamf/jamf-switcher/blob/master/Jamf Switcher/JamfAPI/Service/JamfService.swift"

    %% Click Event - Self Service Processing
    click SSP "https://github.com/jamf/jamf-switcher/blob/master/Jamf Switcher/JamfSelfServiceParser.swift"

    %% Click Events - System Integration and Business Logic
    click SI1 "https://github.com/jamf/jamf-switcher/blob/master/Jamf Switcher/KeychainService.swift"
    click BL1 "https://github.com/jamf/jamf-switcher/blob/master/Jamf Switcher/Logic/PolicyLogic.swift"

    %% Styles
    class UI1,UI2,UI3,SSP blue
    class BL1,APIL,APIS,APIC1,APIC2,APIM,SI1,SI2 yellow

    %% Additional styling for subgraphs (using linkStyle as placeholder for better clarity)
    linkStyle default fill:#f2f3,stroke-width:2px
    style UI1 fill:#2EF2,stroke:#1B4F72,stroke-width:2px
    style UI2 fill:#2EF2,stroke:#1B4F72,stroke-width:2px
    style UI3 fill:#2EF2,stroke:#1B4F72,stroke-width:2px
    style BL1 fill:#FE79F,stroke:#B9770E,stroke-width:2px
    style SSP fill:#D55,stroke:#1B4F72,stroke-width:2px
    style APIC1 fill:#A4D7,stroke:#117864,stroke-width:2px
    style APIC2 fill:#A4D7,stroke:#117864,stroke-width:2px
    style APIL fill:#A4D7,stroke:#117864,stroke-width:2px
    style APIM fill:#A4D7,stroke:#117864,stroke-width:2px
    style APIS fill:#A4D,stroke:#117864,stroke-width:2px
    style SI1 fill:#BC55,stroke:#922B21,stroke-width:2px
    style SI2 fill:#BC55,stroke:#922B21,stroke-width:2px
    
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
