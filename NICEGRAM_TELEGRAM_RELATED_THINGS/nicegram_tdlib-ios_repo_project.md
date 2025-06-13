---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/nicegram/tdlib-ios
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



# nicegram_tdlib-ios repo project
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
title: "nicegram_tdlib-ios repo project"
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
flowchart TD
    %% Runtime Modules
    subgraph "Runtime Stack"
        direction TB
        App["iOS Application"]:::external
        Coordinator["Coordinator"]:::swift
        GeneratedAPI["Generated API Module"]:::swift
        StreamsGroup["Streams Module"]:::swift
        PromiseKit["PromiseKit"]:::external
        TDJsonClient["TDJsonClient"]:::swift
        BridgingHeader["TDLib.h"]:::swift
        TDJSON["TDJSON (C++ TDLib)"]:::external
    end

    %% Build-Time Pipeline
    subgraph "Build-Time Pipeline"
        direction TB
        TLParser["TLParser Tool"]:::build
        Templates["Stencil Templates"]:::build
        Codegen["Code Generation"]:::build
        GeneratedAPIBuild["Generate Swift Code"]:::build
        Jazzy["Jazzy Docs Generator"]:::build
        Docs["docs/ (HTML Reference)"]:::build
        Docsets["docs/docsets/"]:::build
    end

    %% CI/CD & Configuration
    subgraph "CI/CD & Config"
        direction TB
        Fastlane["Fastlane Scripts"]:::build
        Travis[".travis.yml"]:::build
        ConfigFiles["Config Files"]:::build
        Tests["Unit Tests"]:::swift
    end

    %% Runtime flow
    App -->|"calls"| Coordinator
    Coordinator -->|"uses API types"| GeneratedAPI
    Coordinator -->|"serializes JSON"| TDJsonClient
    TDJsonClient -->|"bridges"| TDJSON
    TDJSON -->|"responses JSON"| TDJsonClient
    TDJsonClient -->|"returns JSON"| Coordinator
    Coordinator -->|"async via"| PromiseKit
    Coordinator -->|"publishes events to"| StreamsGroup
    StreamsGroup -->|"subscriptions"| App

    %% Codegen flow
    TLParser --> Templates
    Templates --> Codegen
    Codegen --> GeneratedAPIBuild
    GeneratedAPIBuild --> GeneratedAPI

    %% Docs flow
    Jazzy --> Docs
    Jazzy --> Docsets

    %% CI/CD & Config
    Fastlane --> Travis
    Fastlane --> ConfigFiles
    Fastlane --> Tests

    %% Click Events
    click Coordinator "https://github.com/nicegram/tdlib-ios/blob/master/TDLib/Coordinator.swift"
    click TDJsonClient "https://github.com/nicegram/tdlib-ios/blob/master/TDLib/TDJsonClient.swift"
    click StreamsGroup "https://github.com/nicegram/tdlib-ios/blob/master/TDLib/Stream.swift"
    click StreamsGroup "https://github.com/nicegram/tdlib-ios/blob/master/TDLib/StreamPromise.swift"
    click StreamsGroup "https://github.com/nicegram/tdlib-ios/blob/master/TDLib/AutoLockStream.swift"
    click StreamsGroup "https://github.com/nicegram/tdlib-ios/blob/master/TDLib/FloodStream.swift"
    click GeneratedAPI "https://github.com/nicegram/tdlib-ios/tree/master/TDLib/Generated/"
    click GeneratedAPI "https://github.com/nicegram/tdlib-ios/blob/master/TDLib/Generated/TDLib.generated.swift"
    click GeneratedAPI "https://github.com/nicegram/tdlib-ios/blob/master/TDLib/Generated/TDEnum.generated.swift"
    click GeneratedAPI "https://github.com/nicegram/tdlib-ios/blob/master/TDLib/Generated/EquatableEnum.generated.swift"
    click TLParser "https://github.com/nicegram/tdlib-ios/blob/master/TLParser/parser.rb"
    click Templates "https://github.com/nicegram/tdlib-ios/blob/master/Templates/TDEnum.stencil"
    click Templates "https://github.com/nicegram/tdlib-ios/blob/master/Templates/EquatableEnum.stencil"
    click Docs "https://github.com/nicegram/tdlib-ios/tree/master/docs/"
    click Docsets "https://github.com/nicegram/tdlib-ios/tree/master/docs/docsets/"
    click Fastlane "https://github.com/nicegram/tdlib-ios/tree/master/fastlane/Fastfile"
    click Fastlane "https://github.com/nicegram/tdlib-ios/blob/master/fastlane/push.sh"
    click Travis "https://github.com/nicegram/tdlib-ios/blob/master/.travis.yml"
    click ConfigFiles "https://github.com/nicegram/tdlib-ios/blob/master/.swiftlint.yml"
    click ConfigFiles "https://github.com/nicegram/tdlib-ios/tree/master/Cartfile"
    click ConfigFiles "https://github.com/nicegram/tdlib-ios/blob/master/Cartfile.resolved"
    click ConfigFiles "https://github.com/nicegram/tdlib-ios/tree/master/Gemfile"
    click ConfigFiles "https://github.com/nicegram/tdlib-ios/blob/master/Gemfile.lock"
    click Tests "https://github.com/nicegram/tdlib-ios/blob/master/TDLibTests/TDLibTests.swift"
    click BridgingHeader "https://github.com/nicegram/tdlib-ios/blob/master/TDLib/TDLib.h"

    %% Styles
    classDef swift fill:#ADD8E6,stroke:#333,stroke-width:1px;
    classDef external fill:#90EE90,stroke:#333,stroke-width:1px;
    classDef build fill:#FFA500,stroke:#333,stroke-width:1px;
```

----

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