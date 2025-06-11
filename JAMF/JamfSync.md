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
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExdXp3dTJrNjExdTd5c3JwdzlsZmo0ZmJqbjJhanN1d2JnMnBmNWN3ayZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/52qtwCtj9OLTi/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# JamfSync
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
title: "JamF - JamfSync"
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
      'textColor': '#F8B229',
      'lineColor': '#F8B229'
    }
  }
}%%
graph TD
    %% User Initiation
    UserCLI["User (CLI)"]:::external

    %% UI Layer
    subgraph "UI Layer"
        UI1["JamfSyncApp"]:::ui
        UI2["ContentView"]:::ui
        UI3["AboutView/SettingsView/PackageListView"]:::ui
        UI1 -->|"loads"| UI2
        UI2 -->|"navigates"| UI3
    end

    %% Model Layer
    subgraph "Model Layer"
        M6["ViewModels"]:::model
        M1["DataModel"]:::model
        M2["DistributionPoint"]:::model
        M3["FileShareDp"]:::model
        M4["FolderDp"]:::model
        M5["Jcds2Dp"]:::model
        M6 -->|"updates"| M1
        M1 -->|"coordinates with"| M2
        M2 -->|"invokes subtype"| M3
        M2 -->|"invokes subtype"| M4
        M2 -->|"invokes subtype"| M5
    end

    %% Persistence
    subgraph "Persistence"
        P1["CoreData (StoredSettings & DataManager)"]:::persistence
    end

    %% Utility Layer
    subgraph "Utility"
        U1["ArgumentParser"]:::utility
        U2["FileHash"]:::utility
        U3["FileShare"]:::utility
        U4["KeychainHelper"]:::utility
        U5["CloudSessionDelegate"]:::utility
    end

    %% External Interfaces
    subgraph "External Interfaces"
        E1["JamfProPackageApi"]:::external
        E2["JamfProPackageClassicApi"]:::external
        E3["JamfProPackageUApi"]:::external
    end

    %% Testing Modules
    subgraph "Testing"
        T1["JamfSyncTests"]:::testing
        T2["JamfSyncUITests"]:::testing
    end

    %% Inter-layer Connections
    UI1 -->|"triggers"| M6
    M1 -->|"persists data"| P1
    M1 -->|"initiates sync"| M2
    M2 -->|"uses"| U2
    M2 -->|"uses"| U3
    M1 -->|"secure-access"| U4
    M2 -->|"calls API"| E1
    M2 -->|"calls API"| E2
    M2 -->|"calls API"| E3
    UserCLI -->|"parses args via"| U1
    U1 -->|"updates"| M1

    %% Styles
    classDef ui fill:#f9c74f,stroke:#000,stroke-width:1px;
    classDef model fill:#90be6d,stroke:#000,stroke-width:1px;
    classDef persistence fill:#f9844a,stroke:#000,stroke-width:1px;
    classDef utility fill:#577590,stroke:#000,stroke-width:1px;
    classDef external fill:#f94144,stroke:#000,stroke-width:1px;
    classDef testing fill:#277da1,stroke:#000,stroke-width:1px;

    %% Click Events - UI Layer
    click UI1 "https://github.com/jamf/jamfsync/blob/main/JamfSync/UI/JamfSyncApp.swift"
    click UI2 "https://github.com/jamf/jamfsync/blob/main/JamfSync/UI/ContentView.swift"

    %% Click Events - Model Layer
    click M1 "https://github.com/jamf/jamfsync/blob/main/JamfSync/Model/DataModel.swift"
    click M2 "https://github.com/jamf/jamfsync/blob/main/JamfSync/Model/DistributionPoint.swift"
    click M3 "https://github.com/jamf/jamfsync/blob/main/JamfSync/Model/FileShareDp.swift"
    click M4 "https://github.com/jamf/jamfsync/blob/main/JamfSync/Model/FolderDp.swift"
    click M5 "https://github.com/jamf/jamfsync/blob/main/JamfSync/Model/Jcds2Dp.swift"
    click M6 "https://github.com/jamf/jamfsync/tree/main/JamfSync/Model/ViewModels"

    %% Click Events - Persistence
    click P1 "https://github.com/jamf/jamfsync/tree/main/CoreData"

    %% Click Events - Utility Layer
    click U1 "https://github.com/jamf/jamfsync/blob/main/JamfSync/Utility/ArgumentParser.swift"
    click U2 "https://github.com/jamf/jamfsync/blob/main/JamfSync/Utility/FileHash.swift"
    click U3 "https://github.com/jamf/jamfsync/blob/main/JamfSync/Utility/FileShare.swift"
    click U4 "https://github.com/jamf/jamfsync/blob/main/JamfSync/Utility/KeychainHelper.swift"
    click U5 "https://github.com/jamf/jamfsync/blob/main/JamfSync/Utility/CloudSessionDelegate.swift"

    %% Click Events - External Interfaces
    click E1 "https://github.com/jamf/jamfsync/blob/main/JamfSync/Model/JamfProPackageApi.swift"
    click E2 "https://github.com/jamf/jamfsync/blob/main/JamfSync/Model/JamfProPackageClassicApi.swift"
    click E3 "https://github.com/jamf/jamfsync/blob/main/JamfSync/Model/JamfProPackageUApi.swift"

    %% Click Events - Testing
    click T1 "https://github.com/jamf/jamfsync/tree/main/JamfSyncTests"
    click T2 "https://github.com/jamf/jamfsync/tree/main/JamfSyncUITests"

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
