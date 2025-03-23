---
created: 2025-03-23 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Replicator
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
title: "JamF - Replicators"
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
      'lineColor': '#F8B229'
    }
  }
}%%
flowchart TD
    %% User Interface Layer
    subgraph "User Interface Layer"
        UI1["Main.storyboard"]
        UI2["Preferences.storyboard"]
        UI3["HelpViewController.swift"]
        UI4["SummaryViewController.swift"]
        UI5["PreferencesViewController.swift"]
        UI6["PrefsWindowController.swift"]
        UI7["ViewController.swift"]
    end

    %% Application Logic/Controller Layer
    subgraph "Application Logic Layer"
        L1["CreateEndpoints.swift"]
        L2["Cleanup.swift"]
        L3["ExistingObjects.swift"]
        L4["RemoveData.swift"]
        L5["RemoveObjects.swift"]
        L6["Headless.swift"]
    end

    %% API Integration & Communication Layer
    subgraph "API Integration & Communication Layer"
        A1["JamfPro.swift"]
        A2["Jpapi.swift"]
        A3["Credentials.swift"]
        A4["EndpointXml.swift"]
    end

    %% Data Handling & Persistence
    subgraph "Data Handling & Persistence"
        D1["ExportItem.swift"]
        D2["SaveDelegate.swift"]
        D3["XmlDelegate.swift"]
        D4["Json.swift"]
        D5["JsonObjects.swift"]
        D6["WriteToLog.swift"]
        D7["LoggerExtension.swift"]
    end

    %% Utility and Support Modules
    subgraph "Utility and Support Modules"
        U1["Globals.swift"]
        U2["Utilities.swift"]
        U3["SecurityScopedBookmarks.swift"]
        U4["Alert.swift"]
        U5["IconDelegate.swift"]
        U6["ObjectDelegate.swift"]
        U7["PackagesDelegate.swift"]
        U8["PatchDelegate.swift"]
        U9["TimeDelegate.swift"]
    end

    %% Additional Assets & Resources
    subgraph "Additional Assets & Resources"
        AR1["Assets.xcassets"]
        AR2["images"]
        AR3["index.html"]
        AR4["README.md"]
        AR5["settings.plist"]
    end

    %% Connections between layers
    UI7 -->|"triggers"| L1
    UI3 -->|"triggers"| L2
    UI4 -->|"displays"| L3
    L6 -->|"invokes"| L1

    %% Application Logic interacts with API Integration
    L1 -->|"calls"| A1
    L1 -->|"calls"| A2
    L2 -->|"calls"| A3
    L2 -->|"calls"| A4
    A1 -->|"returns"| L1
    A2 -->|"returns"| L1

    %% Application Logic interacts with Data Handling & Persistence
    L2 -->|"processes"| D1
    L3 -->|"processes"| D2
    L4 -->|"processes"| D3
    L5 -->|"processes"| D4

    %% Data Handling utilizes Logging
    D1 -->|"logs"| D6
    D2 -->|"logs"| D7
    D6 -->|"utilizes"| U4
    D7 -->|"utilizes"| U4

    %% Application Logic makes use of Utility/Support modules
    L1 -->|"uses"| U2
    U2 -->|"supports"| L2

    %% Parallel Command-Line Interface (CLI) aspect
    UI7 ---|"parallel_with"| L6

    %% Additional Assets providing resources and documentation
    AR1 ---|"resources"| UI7
    AR2 ---|"resources"| UI7
    AR3 ---|"documentation"| UI3
    AR4 ---|"documentation"| UI3
    AR5 ---|"configuration"| UI5

    %% Click Events for User Interface Layer
    click UI1 "https://github.com/jamf/replicator/blob/main/Replicator/Base.lproj/Main.storyboard"
    click UI2 "https://github.com/jamf/replicator/blob/main/Replicator/Base.lproj/Preferences.storyboard"
    click UI3 "https://github.com/jamf/replicator/blob/main/Replicator/HelpViewController.swift"
    click UI4 "https://github.com/jamf/replicator/blob/main/Replicator/SummaryViewController.swift"
    click UI5 "https://github.com/jamf/replicator/blob/main/Replicator/Preferences/PreferencesViewController.swift"
    click UI6 "https://github.com/jamf/replicator/blob/main/Replicator/PrefsWindowController.swift"
    click UI7 "https://github.com/jamf/replicator/blob/main/Replicator/ViewController.swift"

    %% Click Events for Application Logic/Controller Layer
    click L1 "https://github.com/jamf/replicator/blob/main/Replicator/CreateEndpoints.swift"
    click L2 "https://github.com/jamf/replicator/blob/main/Replicator/Cleanup.swift"
    click L3 "https://github.com/jamf/replicator/blob/main/Replicator/ExistingObjects.swift"
    click L4 "https://github.com/jamf/replicator/blob/main/Replicator/RemoveData.swift"
    click L5 "https://github.com/jamf/replicator/blob/main/Replicator/RemoveObjects.swift"
    click L6 "https://github.com/jamf/replicator/blob/main/Replicator/Headless.swift"

    %% Click Events for API Integration & Communication Layer
    click A1 "https://github.com/jamf/replicator/blob/main/Replicator/JamfPro.swift"
    click A2 "https://github.com/jamf/replicator/blob/main/Replicator/Jpapi.swift"
    click A3 "https://github.com/jamf/replicator/blob/main/Replicator/Credentials.swift"
    click A4 "https://github.com/jamf/replicator/blob/main/Replicator/EndpointXml.swift"

    %% Click Events for Data Handling & Persistence
    click D1 "https://github.com/jamf/replicator/blob/main/Replicator/ExportItem.swift"
    click D2 "https://github.com/jamf/replicator/blob/main/Replicator/SaveDelegate.swift"
    click D3 "https://github.com/jamf/replicator/blob/main/Replicator/XmlDelegate.swift"
    click D4 "https://github.com/jamf/replicator/blob/main/Replicator/Json.swift"
    click D5 "https://github.com/jamf/replicator/blob/main/Replicator/JsonObjects.swift"
    click D6 "https://github.com/jamf/replicator/blob/main/Replicator/WriteToLog.swift"
    click D7 "https://github.com/jamf/replicator/blob/main/Replicator/LoggerExtension.swift"

    %% Click Events for Utility and Support Modules
    click U1 "https://github.com/jamf/replicator/blob/main/Replicator/Globals.swift"
    click U2 "https://github.com/jamf/replicator/blob/main/Replicator/Utilities.swift"
    click U3 "https://github.com/jamf/replicator/blob/main/Replicator/SecurityScopedBookmarks.swift"
    click U4 "https://github.com/jamf/replicator/blob/main/Replicator/Alert.swift"
    click U5 "https://github.com/jamf/replicator/blob/main/Replicator/IconDelegate.swift"
    click U6 "https://github.com/jamf/replicator/blob/main/Replicator/ObjectDelegate.swift"
    click U7 "https://github.com/jamf/replicator/blob/main/Replicator/PackagesDelegate.swift"
    click U8 "https://github.com/jamf/replicator/blob/main/Replicator/PatchDelegate.swift"
    click U9 "https://github.com/jamf/replicator/blob/main/Replicator/TimeDelegate.swift"

    %% Click Events for Additional Assets & Resources
    click AR1 "https://github.com/jamf/replicator/blob/main/Replicator/Assets.xcassets"
    click AR2 "https://github.com/jamf/replicator/tree/main/Replicator/images"
    click AR3 "https://github.com/jamf/replicator/blob/main/Replicator/index.html"
    click AR4 "https://github.com/jamf/replicator/blob/main/README.md"
    click AR5 "https://github.com/jamf/replicator/blob/main/settings.plist"

    %% Styles: Color Definitions
    classDef ui fill:#ADD8E6,stroke:#000,stroke-width:1px;
    classDef logic fill:#90EE90,stroke:#000,stroke-width:1px;
    classDef api fill:#FFD700,stroke:#000,stroke-width:1px;
    classDef data fill:#FFA07A,stroke:#000,stroke-width:1px;
    classDef util fill:#FFB6C1,stroke:#000,stroke-width:1px;
    classDef asset fill:#D3D3D3,stroke:#000,stroke-width:1px;

    class UI1,UI2,UI3,UI4,UI5,UI6,UI7 ui;
    class L1,L2,L3,L4,L5,L6 logic;
    class A1,A2,A3,A4 api;
    class D1,D2,D3,D4,D5,D6,D7 data;
    class U1,U2,U3,U4,U5,U6,U7,U8,U9 util;
    class AR1,AR2,AR3,AR4,AR5 asset
    
```


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---