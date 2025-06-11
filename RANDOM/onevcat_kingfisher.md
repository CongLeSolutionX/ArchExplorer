---
created: 2025-03-30 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExbWVrNTRoMWN5MXBrNnkzNHd1d3RqN3R5dGd0bmFqYzg3bDlkemEyOSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/dCRE4wbV5efkXOAi0K/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# KingFisher by onevcat
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
title: "Kingfisher by onevcat"
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
    'fontFamily': 'Monospace',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TD

    subgraph "Library Core"
        KFAPI["Kingfisher API (General Utilities)"]:::core
        Cache["Cache System (Memory & Disk)"]:::core
        Net["Networking (Image Downloader)"]:::core
        ImgProc["Image Processing Pipeline"]:::core
    end

    subgraph "Extensions & Integration"
        UIKit["UI Extensions (UIKit/AppKit)"]:::integration
        SwiftUI["SwiftUI Integration"]:::integration
        AdditionalViews["Additional Views"]:::integration
    end

    subgraph "Project Configuration"
        SPM["Swift Package Manager"]:::package
        CocoaPods["CocoaPods Spec"]:::package
        RubyAuto["Ruby Automation"]:::package
    end

    Helpers["Utility Helpers"]:::helper
    Demo["Demo Applications"]:::external
    CICD_GH["GitHub Workflows (CI/CD)"]:::external
    Fastlane["Fastlane Automation"]:::external
    UnitTests["Unit Tests"]:::external

    %% Data flow from UI Extensions to Core API
    UIKit -->|"initiate_request"| KFAPI
    SwiftUI -->|"initiate_request"| KFAPI
    AdditionalViews -->|"initiate_request"| KFAPI

    %% Core API triggers networking and cache lookup
    KFAPI -->|"download_image"| Net
    KFAPI -->|"check_cache"| Cache

    %% Networking passes image to processing then to cache
    Net -->|"pass_to_processing"| ImgProc
    ImgProc -->|"store_result"| Cache

    %% Cache returns image back to UI layers
    Cache -->|"return_cached"| UIKit
    Cache -->|"return_cached"| SwiftUI
    Cache -->|"return_cached"| AdditionalViews

    %% Library core components use utility helpers
    KFAPI ---|"uses"| Helpers
    Cache ---|"uses"| Helpers
    Net ---|"uses"| Helpers
    ImgProc ---|"uses"| Helpers

    %% Project configuration components help configure the core
    SPM ---|"configures"| KFAPI
    CocoaPods ---|"configures"| KFAPI
    RubyAuto ---|"configures"| KFAPI

    %% Testing and automation flows
    UnitTests ---|"tests"| KFAPI
    Fastlane ---|"automates_build&deploy"| KFAPI
    CICD_GH ---|"runs_pipelines"| KFAPI

    %% Demo applications illustrate integration usage
    Demo -->|"demonstrates"| UIKit
    Demo -->|"demonstrates"| SwiftUI
    Demo -->|"demonstrates"| AdditionalViews

    %% Click Events
    click KFAPI "https://github.com/onevcat/kingfisher/tree/master/Sources/General"
    click Cache "https://github.com/onevcat/kingfisher/tree/master/Sources/Cache"
    click Net "https://github.com/onevcat/kingfisher/tree/master/Sources/Networking"
    click ImgProc "https://github.com/onevcat/kingfisher/tree/master/Sources/Image"
    click UIKit "https://github.com/onevcat/kingfisher/tree/master/Sources/Extensions"
    click SwiftUI "https://github.com/onevcat/kingfisher/tree/master/Sources/SwiftUI"
    click AdditionalViews "https://github.com/onevcat/kingfisher/tree/master/Sources/Views"
    click Helpers "https://github.com/onevcat/kingfisher/tree/master/Sources/Utility"
    click Demo "https://github.com/onevcat/kingfisher/tree/master/Demo"
    click CICD_GH "https://github.com/onevcat/kingfisher/tree/master/.github/workflows"
    click Fastlane "https://github.com/onevcat/kingfisher/tree/master/fastlane"
    click UnitTests "https://github.com/onevcat/kingfisher/tree/master/Tests"
    click SPM "https://github.com/onevcat/kingfisher/blob/master/Package.swift"
    click CocoaPods "https://github.com/onevcat/kingfisher/blob/master/Kingfisher.podspec"
    click RubyAuto "https://github.com/onevcat/kingfisher/tree/master/Gemfile"

    %% Class definitions for styling
    classDef core fill:#BBDEFB,stroke:#1E88E5,stroke-width:2px,color:#0D47A1;
    classDef integration fill:#C8E6C9,stroke:#43A047,stroke-width:2px,color:#1B5E20;
    classDef package fill:#FFECB3,stroke:#FFA000,stroke-width:2px,color:#FF6F00;
    classDef external fill:#F8BBD0,stroke:#C2185B,stroke-width:2px,color:#880E4F;
    classDef helper fill:#D1C4E9,stroke:#5E35B1,stroke-width:2px,color:#311B92

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
