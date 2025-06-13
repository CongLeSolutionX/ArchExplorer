---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/leoMehlig/TDLib-iOS
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExMXVjejV3dnVjc2o5MXd3eXBvcDR1cHlzbHQ1Z2R6YjY0ZHpmdjJ6OCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/hL9q5k9dk9l0wGd4e0/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# leoMehlig_TDLib-iOS repo project
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


```mermaid
---
title: "leoMehlig_TDLib-iOS repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
  look: handDrawn
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'American Typewriter, monospace',
    'logLevel': 'fatal',
    'themeVariables': {
      'primaryColor': '#22BB',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#E2F1',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '20px'
    }
  }
}%%
flowchart TB
    %% Client Application
    ClientApp["Client App"]:::orange

    %% Swift Library Internals
    subgraph "TDLib-iOS Swift API"
        direction TB
        Coordinator["Coordinator (Facade)"]:::blue
        streamGroup(("Streams")):::blue
        PromiseIntegration["PromiseKit Integration"]:::blue
        JSONUtils["JSON Utilities"]:::blue
        CoreHelpers(("Core Types & Helpers")):::blue
        subgraph "Generated API Types"
            direction TB
            GeneratedAPI["TDLib/Generated"]:::blue
        end
    end

    %% Native Bridge and tdlib
    subgraph "Native Bridge & tdlib"
        direction TB
        TDJsonClient["TDJsonClient (ObjC++ wrapper)"]:::gray
        TdlibCPP["tdlib C++ library"]:::gray
    end

    %% Code-Generation Pipeline
    subgraph "Code-Generation Pipeline"
        direction TB
        TLParser["TLParser/parser.rb"]:::green
        Templates(("Templates/*.stencil")):::green
    end

    %% Testing, Docs, Build
    subgraph "Support & CI"
        direction TB
        Tests["TDLibTests"]:::gray
        Docs["API Documentation (docs/)"]:::gray
        BuildConfig(("Build/Test/Deploy Config")):::gray
        Project["Swift Framework Project (TDLib.xcodeproj)"]:::gray
    end

    %% Relationships
    ClientApp -->|"send(Function)"| Coordinator
    Coordinator -->|"wraps JSON"| TDJsonClient
    TDJsonClient -->|"calls C++"| TdlibCPP
    TdlibCPP -->|"JSON callback"| TDJsonClient
    TDJsonClient -->|"callback JSON"| Coordinator
    Coordinator -->|"fulfill Promise / emit Stream"| streamGroup
    ClientApp -.->|"subscribe"| streamGroup

    %% Code-gen flow
    TLParser -->|"uses templates"| Templates
    Templates -->|"generate types"| GeneratedAPI
    GeneratedAPI -->|"used by"| Coordinator

    %% Support flows
    Tests -->|"validate code"| Coordinator
    Tests -->|"validate generated API"| GeneratedAPI
    Docs -->|"generated from"| GeneratedAPI
    BuildConfig -->|"builds"| Project

    %% Click Events
    click Coordinator "https://github.com/leomehlig/tdlib-ios/blob/master/TDLib/Coordinator.swift"
    click TDJsonClient "https://github.com/leomehlig/tdlib-ios/blob/master/TDLib/TDJsonClient.swift"
    click JSONUtils "https://github.com/leomehlig/tdlib-ios/blob/master/TDLib/JSON.swift"
    click GeneratedAPI "https://github.com/leomehlig/tdlib-ios/tree/master/TDLib/Generated/"
    click TLParser "https://github.com/leomehlig/tdlib-ios/blob/master/TLParser/parser.rb"
    click Templates "https://github.com/leomehlig/tdlib-ios/blob/master/Templates/EquatableEnum.stencil"
    click Tests "https://github.com/leomehlig/tdlib-ios/blob/master/TDLibTests/TDLibTests.swift"
    click Project "https://github.com/leomehlig/tdlib-ios/blob/master/TDLib.xcodeproj"
    click Docs "https://github.com/leomehlig/tdlib-ios/tree/master/docs/"

    %% Styles
    classDef orange fill:#F6B26B,stroke:#333,stroke-width:1px
    classDef blue fill:#6FA8DC,stroke:#333,stroke-width:1px
    classDef gray fill:#999999,stroke:#333,stroke-width:1px
    classDef green fill:#93C47D,stroke:#333,stroke-width:1px
```

-----


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
    
  My_Meme ~~~ Closing_quote
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }



```

---
>**Licenses:**
>
>- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
>- **Creative Commons Attribution-ShareAlike 4.0 International**: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) [![CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/88x31.png)](https://creativecommons.org/licenses/by-sa/4.0/) - Legal details in [LICENSE-CC-BY-SA-4.0](THE_PAST/LICENSE-CC-BY-SA-4.0) and at [Creative Commons official site](https://creativecommons.org/licenses/by-sa/4.0/).
>
---