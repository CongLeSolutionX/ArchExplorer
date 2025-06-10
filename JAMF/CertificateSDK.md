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
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExdDl3cXMwNWE1aXBzbXhsNndkcW9saTBjazFxeHVzeWk3cTBkd240MyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/0U7bWQK9s75PjRKcHz/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----



# CertificateSDK
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
title: "JamF - CertificateSDK"
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
    'flowchart': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TB
    %% UI Components - iOS App
    subgraph "Certificate SDK Sample iOS App"
        direction TB
        A["ActionLogViewController.swift"]:::ui
        B["SetupTestViewController.swift"]:::ui
        C["AppDelegate.swift"]:::ui
        D["Base.lproj Storyboards"]:::ui
    end

    %% UI Components - visionOS App
    subgraph "Certificate SDK Sample visionOS App"
        direction TB
        V1["CertificateSDKSampleVisionOSApp.swift"]:::ui
        V2["ContentView.swift"]:::ui
        V3["RequestTypeView.swift"]:::ui
        V4["Assets"]:::ui
    end

    %% Shared Business Logic Module
    subgraph "Certificate SDK Sample Shared Module"
        direction TB
        S1["CertificateRequestManager.swift"]:::shared
        S2["KeychainHandler.swift"]:::shared
        S3["CertRequestConfiguration.swift"]:::shared
        S4["LocalNotificationService.swift"]:::shared
    end

    %% External Framework and Service
    X["CertificateSDK XCFramework"]:::external
    E["Jamf Pro Server"]:::external

    %% Connections between components
    C -->|"calls"| S1
    V1 -->|"calls"| S1
    S1 -->|"invokes"| X
    X -->|"communicatesTo"| E

    %% Click Events using component mapping paths
    click X "https://github.com/jamf/certificatesdk/blob/main/CertificateSDK.xcframework"
    click C "https://github.com/jamf/certificatesdk/tree/main/Certificate SDK Sample iOS"
    click V1 "https://github.com/jamf/certificatesdk/tree/main/Certificate SDK Sample visionOS"
    click S1 "https://github.com/jamf/certificatesdk/tree/main/Certificate SDK Sample Shared"

    %% Styles for color coding
    classDef ui fill:#FFD700,stroke:#B8860B,stroke-width:2px;
    classDef shared fill:#87CEFA,stroke:#4682B4,stroke-width:2px;
    classDef external fill:#90EE90,stroke:#32CD32,stroke-width:2px

```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
