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



# ReEnroller
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
title: "JamF - ReEnroller"
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
    %% UI Layer
    subgraph "UI Layer (Storyboards & View Controllers)"
        UI1["Main.storyboard"]:::ui
        UI2["HelpViewController.swift"]:::ui
        UI3["SourceMdmViewController.swift"]:::ui
        UI4["ViewController.swift"]:::ui
    end

    %% Business Logic / Controller Layer
    subgraph "Business Logic"
        BL1["Command.swift"]:::business
        BL2["Globals.swift"]:::business
        BL3["Alert.swift"]:::business
    end

    %% Networking/API Layer
    subgraph "Networking/API Module"
        NW1["ApiCall.swift"]:::networking
        NW2["JamfPro.swift"]:::networking
        ES1["Source Jamf Pro Server"]:::networking
        ES2["Destination Jamf Pro Server"]:::networking
    end

    %% Installation and Scripting Artifacts
    subgraph "Deployment Scripts"
        D1["1/preinstall"]:::deployment
        D2["1/postinstall"]:::deployment
        D3["2/preinstall"]:::deployment
        D4["2/postinstall"]:::deployment
        D5["ade.sh"]:::deployment
        D6["ReEnrollerNotification.mobileconfig"]:::deployment
    end

    %% Configuration and Assets
    subgraph "Configuration & Assets"
        CFG1["Info.plist"]:::config
        CFG2["settings.plist"]:::config
        CFG3["ReEnroller-component.plist"]:::config
        CFG4["ReEnroller.entitlements"]:::config
        CFG5["Assets.xcassets"]:::config
    end

    %% Logging and Diagnostics
    subgraph "Logging & Diagnostics"
        LOG1["WriteToLog.swift"]:::log
        LOG2["Notes.md"]:::log
        LOG3["help/apiMDM_remove.txt"]:::log
    end

    %% Data Flow Connections
    UI1 -->|"user input"| BL1
    UI2 --> BL1
    UI3 --> BL1
    UI4 --> BL1

    BL1 -->|"initiate enrollment"| NW1
    BL1 -->|"initiate enrollment"| NW2
    NW1 -->|"API Request"| ES1
    NW1 -->|"API Request"| ES2
    NW2 -->|"API Request"| ES1
    NW2 -->|"API Request"| ES2

    NW1 -->|"response"| BL1
    NW2 -->|"response"| BL1

    %% Conditional flow for error handling and fallback
    BL1 -- "Success" --> NW1
    NW1 -- "Failback" --> BL1

    %% Deployment Trigger after business logic decisions
    BL1 -->|"trigger scripts"| D1
    BL1 --> D2
    BL1 --> D3
    BL1 --> D4
    BL1 --> D5
    BL1 --> D6

    %% Configuration Lookup
    BL1 -->|"load config"| CFG1
    BL1 --> CFG2
    BL1 --> CFG3
    BL1 --> CFG4
    BL1 --> CFG5

    %% Logging occurs at critical steps (using dashed lines)
    UI1 --- LOG1
    BL1 --- LOG1
    NW1 --- LOG1
    D1 --- LOG1
    CFG1 --- LOG1

    %% Additional logging links
    UI2 --- LOG2
    BL2 --- LOG2
    NW2 --- LOG3

    %% Click Events for UI Layer
    click UI1 "https://github.com/jamf/reenroller/blob/master/ReEnroller/Base.lproj/Main.storyboard"
    click UI2 "https://github.com/jamf/reenroller/blob/master/ReEnroller/HelpViewController.swift"
    click UI3 "https://github.com/jamf/reenroller/blob/master/ReEnroller/SourceMdmViewController.swift"
    click UI4 "https://github.com/jamf/reenroller/blob/master/ReEnroller/ViewController.swift"

    %% Click Events for Business Logic
    click BL1 "https://github.com/jamf/reenroller/blob/master/ReEnroller/Command.swift"
    click BL2 "https://github.com/jamf/reenroller/blob/master/ReEnroller/Globals.swift"
    click BL3 "https://github.com/jamf/reenroller/blob/master/ReEnroller/Alert.swift"

    %% Click Events for Networking/API Layer
    click NW1 "https://github.com/jamf/reenroller/blob/master/ReEnroller/ApiCall.swift"
    click NW2 "https://github.com/jamf/reenroller/blob/master/ReEnroller/JamfPro.swift"

    %% Click Events for Deployment Scripts
    click D1 "https://github.com/jamf/reenroller/tree/master/ReEnroller/1/preinstall"
    click D2 "https://github.com/jamf/reenroller/tree/master/ReEnroller/1/postinstall"
    click D3 "https://github.com/jamf/reenroller/tree/master/ReEnroller/2/preinstall"
    click D4 "https://github.com/jamf/reenroller/tree/master/ReEnroller/2/postinstall"
    click D5 "https://github.com/jamf/reenroller/blob/master/ReEnroller/ade.sh"
    click D6 "https://github.com/jamf/reenroller/blob/master/ReEnrollerNotification.mobileconfig"

    %% Click Events for Configuration and Assets
    click CFG1 "https://github.com/jamf/reenroller/blob/master/ReEnroller/Info.plist"
    click CFG2 "https://github.com/jamf/reenroller/blob/master/ReEnroller/settings.plist"
    click CFG3 "https://github.com/jamf/reenroller/blob/master/ReEnroller/ReEnroller-component.plist"
    click CFG4 "https://github.com/jamf/reenroller/blob/master/ReEnroller/ReEnroller.entitlements"
    click CFG5 "https://github.com/jamf/reenroller/blob/master/ReEnroller/Assets.xcassets"

    %% Click Events for Logging and Diagnostics
    click LOG1 "https://github.com/jamf/reenroller/blob/master/ReEnroller/WriteToLog.swift"
    click LOG2 "https://github.com/jamf/reenroller/blob/master/Notes.md"
    click LOG3 "https://github.com/jamf/reenroller/blob/master/ReEnroller/help/apiMDM_remove.txt"

    %% Styles
    classDef ui fill:#D6E9F8,stroke:#1F78C1,stroke-width:2px;
    classDef business fill:#FCF6BD,stroke:#D4AC0D,stroke-width:2px;
    classDef networking fill:#D5F5E3,stroke:#28B463,stroke-width:2px;
    classDef deployment fill:#FADBD8,stroke:#E74C3C,stroke-width:2px;
    classDef config fill:#E8DAEF,stroke:#8E44AD,stroke-width:2px;
    classDef log fill:#F0F3F4,stroke:#BDC3C7,stroke-width:2px

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
