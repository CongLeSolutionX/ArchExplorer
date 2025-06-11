---
created: 2025-03-23 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExeGNsOXdrYjc0ZWFteWI4eGx5anAzaW5iZjRmd3F4NGpueTVudHFjNSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/ZO9b1ntYVJmjZlsWlm/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----



# Munki Catalog Browser
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---



```mermaid
---
title: "JamF - Munki Catalog Browser"
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
    'graph': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'lineColor': '#F8B229'
    }
  }
}%%
graph TD
    %% UI Layer
    subgraph "User Interface Layer"
        UI_ST("Main.storyboard"):::ui
        VC("ViewController.swift"):::ui
        AD("AppDelegate.swift"):::ui
    end

    %% Application Logic Layer
    subgraph "Application Logic"
        CDP("Catalog Data Processor"):::logic
        CSV("CSV Export Module"):::logic
        AL1("MyStructures.swift"):::logic
        AL2("AppCell.swift"):::logic
    end

    %% External System
    subgraph "External System"
        LFS("Local File System"):::external
    end

    %% CI/CD Pipeline
    subgraph "CI/CD Pipeline"
        CICD("Pipeline"):::cicd
    end

    %% Interactions
    UI_ST -->|"displays"| CDP
    VC -->|"triggers"| CDP
    AD -->|"initializes"| CDP

    CDP -->|"reads"| LFS
    CDP -->|"exportCommand"| CSV
    CSV -->|"writesCSV"| LFS

    CICD -->|"build&test"| AD

    %% Click events for UI Layer
    click UI_ST "https://github.com/jamf/munki-catalog-browser/blob/master/Munki Catalog Browser/Base.lproj/Main.storyboard"
    click VC "https://github.com/jamf/munki-catalog-browser/blob/master/Munki Catalog Browser/ViewController.swift"
    click AD "https://github.com/jamf/munki-catalog-browser/blob/master/Munki Catalog Browser/AppDelegate.swift"

    %% Click events for Application Logic
    click AL1 "https://github.com/jamf/munki-catalog-browser/blob/master/Munki Catalog Browser/MyStructures.swift"
    click AL2 "https://github.com/jamf/munki-catalog-browser/blob/master/Munki Catalog Browser/AppCell.swift"

    %% Click event for CI/CD Integration
    click CICD "https://github.com/jamf/munki-catalog-browser/tree/master/.ci/Jenkinsfile"

    %% Styles
    classDef ui fill:#ffdddd,stroke:#990000,stroke-width:2px;
    classDef logic fill:#ddffdd,stroke:#009900,stroke-width:2px;
    classDef external fill:#ddddff,stroke:#000099,stroke-width:2px,stroke-dasharray: 5 5;
    classDef cicd fill:#ffffcc,stroke:#999900,stroke-width:2px;
    
    %% Additional styling for clarity if needed
    linkStyle 0,1,2 stroke:#444444,stroke-width:2px;
    linkStyle 3,4,5 stroke:#444444,stroke-width:2px;
    linkStyle 6 stroke:#444444,stroke-width:2px

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
