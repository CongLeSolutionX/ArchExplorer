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




# PPPC-Utility
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
title: "JamF - PPPC-Utility"
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
    %% Application Core
    subgraph "Application Core"
        A["AppDelegate"]:::appCore
        B["Main Storyboard"]:::appCore
    end

    %% User Interface
    subgraph User_Interface["User Interface"]
        C["UploadInfoView"]:::ui
        D["OpenViewController"]:::ui
        E["SaveViewController"]:::ui
        F["TCCProfileViewController"]:::ui
        G["Alert"]:::ui
        H["InfoButton"]:::ui
        I["FlippedClipView"]:::ui
    end

    %% Business Logic / Models
    subgraph Business_Logic_Models["Business Logic / Models"]
        J["AppleEventRule"]:::business
        K["Executable"]:::business
        L["LoadExecutableError"]:::business
        M["Model"]:::business
        N["PPPCServiceInfo"]:::business
        O["PPPCServicesManager"]:::business
        P["SemanticVersion"]:::business
        Q["SigningIdentity"]:::business
        R["TCCProfile"]:::business
    end

    %% Networking / External Services
    subgraph Networking_External_Services["Networking / External Services"]
        S["JamfProAPIClient"]:::network
        T["JamfProAPITypes"]:::network
        U["NetworkAuthManager"]:::network
        V["Token"]:::network
        W["UploadManager"]:::network
        X["Networking"]:::network
        Y["URLSessionAsyncCompatibility"]:::network
    end

    %% TCC Profile Handling
    subgraph TCC_Profile_Handling["TCC Profile Handling"]
        Z["TCCProfileImporter"]:::tcc
        AA["TCCProfileConfigurationPanel"]:::tcc
        AB["TCCProfileImportError"]:::tcc
        AC["TCCProfileExtensions"]:::tcc
    end

    %% External Dependencies
    subgraph "External Dependencies"
        AD["SwiftyCMSDecoder"]:::external
    end

    %% Relationships
    A -->|"initUI"| B
    B -->|"initUI"| D
    B -->|"initUI"| E
    B -->|"initUI"| F

    C -->|"buildProfile"| O
    D -->|"buildProfile"| O
    E -->|"buildProfile"| O
    F -->|"buildProfile"| O

    O -->|"uploadProfile"| S
    S -->|"authRequest"| U

    Z -->|"updates"| O
    O -->|"import"| Z
    Z -->|"extends"| AC

    X -->|"decode"| AD

    D -->|"showAlert"| G
    F -->|"infoAction"| H

    %% Styles
    classDef appCore fill:#cce5ff,stroke:#0066cc,stroke-width:2px;
    classDef ui fill:#d4edda,stroke:#229954,stroke-width:2px;
    classDef business fill:#fff3cd,stroke:#ffcc00,stroke-width:2px;
    classDef network fill:#ffe5b4,stroke:#ff9900,stroke-width:2px;
    classDef tcc fill:#e2d6f3,stroke:#8a2be2,stroke-width:2px;
    classDef external fill:#f8d7da,stroke:#d9534f,stroke-width:2px;

    %% Click Events
    click A "https://github.com/jamf/pppc-utility/blob/master/Source/AppDelegate.swift"
    click B "https://github.com/jamf/pppc-utility/blob/master/Resources/Base.lproj/Main.storyboard"
    click C "https://github.com/jamf/pppc-utility/blob/master/Source/SwiftUI/UploadInfoView.swift"
    click D "https://github.com/jamf/pppc-utility/blob/master/Source/View Controllers/OpenViewController.swift"
    click E "https://github.com/jamf/pppc-utility/blob/master/Source/View Controllers/SaveViewController.swift"
    click F "https://github.com/jamf/pppc-utility/blob/master/Source/View Controllers/TCCProfileViewController.swift"
    click G "https://github.com/jamf/pppc-utility/blob/master/Source/Views/Alert.swift"
    click H "https://github.com/jamf/pppc-utility/blob/master/Source/Views/InfoButton.swift"
    click I "https://github.com/jamf/pppc-utility/blob/master/Source/Views/FlippedClipView.swift"
    click J "https://github.com/jamf/pppc-utility/blob/master/Source/Model/AppleEventRule.swift"
    click K "https://github.com/jamf/pppc-utility/blob/master/Source/Model/Executable.swift"
    click L "https://github.com/jamf/pppc-utility/blob/master/Source/Model/LoadExecutableError.swift"
    click M "https://github.com/jamf/pppc-utility/blob/master/Source/Model/Model.swift"
    click N "https://github.com/jamf/pppc-utility/blob/master/Source/Model/PPPCServiceInfo.swift"
    click O "https://github.com/jamf/pppc-utility/blob/master/Source/Model/PPPCServicesManager.swift"
    click P "https://github.com/jamf/pppc-utility/blob/master/Source/Model/SemanticVersion.swift"
    click Q "https://github.com/jamf/pppc-utility/blob/master/Source/Model/SigningIdentity.swift"
    click R "https://github.com/jamf/pppc-utility/blob/master/Source/Model/TCCProfile.swift"
    click S "https://github.com/jamf/pppc-utility/blob/master/Source/Networking/JamfProAPIClient.swift"
    click T "https://github.com/jamf/pppc-utility/blob/master/Source/Networking/JamfProAPITypes.swift"
    click U "https://github.com/jamf/pppc-utility/blob/master/Source/Networking/NetworkAuthManager.swift"
    click V "https://github.com/jamf/pppc-utility/blob/master/Source/Networking/Token.swift"
    click W "https://github.com/jamf/pppc-utility/blob/master/Source/Networking/UploadManager.swift"
    click X "https://github.com/jamf/pppc-utility/blob/master/Source/Networking/Networking.swift"
    click Y "https://github.com/jamf/pppc-utility/blob/master/Source/Networking/URLSessionAsyncCompatibility.swift"
    click Z "https://github.com/jamf/pppc-utility/blob/master/Source/TCCProfileImporter/TCCProfileImporter.swift"
    click AA "https://github.com/jamf/pppc-utility/blob/master/Source/TCCProfileImporter/TCCProfileConfigurationPanel.swift"
    click AB "https://github.com/jamf/pppc-utility/blob/master/Source/TCCProfileImporter/TCCProfileImportError.swift"
    click AC "https://github.com/jamf/pppc-utility/blob/master/Source/Extensions/TCCProfileExtensions.swift"
    click AD "https://github.com/jamf/pppc-utility/blob/master/External/SwiftyCMSDecoder.swift"

```





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
