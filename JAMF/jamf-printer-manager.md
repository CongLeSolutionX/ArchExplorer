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
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExZDJxZWZzZjF4aXkzNnkxMzlyZ21tdnZ0eDJhcjluNm1lZ2VweHU3ciZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/VX7yEoXAFf8as/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# JamF Printer Manager
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
title: "JamF Printer Manager"
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
    subgraph "User Interface"
        UI_Main["Main Storyboard"]
        UI_About["AboutVC"]
        UI_Add["AddPrinterVC"]
        UI_Help["HelpVC"]
        UI_Login["LoginVC"]
        UI_PrinterInfo["PrinterInfoVC"]
        UI_PrinterTab["PrinterInfoTabVC"]
        UI_ToU["ToUVC"]
    end

    %% Application Core
    subgraph "Application Core"
        Core_AppDelegate["AppDelegate"]
        Core_Globals["Globals"]
        Core_AppConfig["App Configuration"]
    end

    %% Parsing Modules
    subgraph "Parsing Modules"
        Parse_CUPS["CupsParser"]
        Parse_XML["XmlParser"]
        Parse_XMLDelegate["XmlDelegate"]
    end

    %% Utility Modules
    subgraph "Utility Modules"
        Util_Logging["Logging"]
        Util_WriteToLog["WriteToLog"]
        Util_Alert["Alert"]
    end

    %% Credential and Token Management
    subgraph "Credential & Token Management"
        Auth_Credentials["Credentials"]
        Auth_Token["TokenDelegate"]
    end

    %% External Communication
    External_Jamf["Jamf Pro Service"]

    %% Assets and Resources
    subgraph "Assets & Resources"
        Resources_Assets["Assets"]
        Resources_Help["Help Document"]
        Resources_PDF["User Guide PDF"]
    end

    %% Connections from UI Layer to Application Core
    UI_Main -->|"initiates"| Core_AppDelegate
    UI_About -->|"user action"| Core_AppDelegate
    UI_Add -->|"user action"| Core_AppDelegate
    UI_Help -->|"user action"| Core_AppDelegate
    UI_Login -->|"user action"| Core_AppDelegate
    UI_PrinterInfo -->|"user action"| Core_AppDelegate
    UI_PrinterTab -->|"user action"| Core_AppDelegate
    UI_ToU -->|"user action"| Core_AppDelegate

    %% Application Core to Parsing Modules and Auth Modules
    Core_AppDelegate -->|"parseConfig"| Parse_CUPS
    Core_AppDelegate -->|"parseConfig"| Parse_XML
    Core_AppDelegate -->|"initDelegate"| Parse_XMLDelegate

    Core_AppDelegate -->|"authRequest"| Auth_Credentials
    Core_AppDelegate -->|"tokenRequest"| Auth_Token

    %% Parsing output to External Service
    Parse_CUPS -->|"uploadData"| External_Jamf
    Parse_XML -->|"uploadData"| External_Jamf
    Auth_Token -->|"validate"| External_Jamf

    %% Logging and Alerting connections
    Core_AppDelegate -->|"logActivity"| Util_Logging
    Core_AppDelegate -->|"writeLog"| Util_WriteToLog
    Core_AppDelegate -->|"generateAlert"| Util_Alert

    Util_Logging -->|"notify"| UI_Main
    Util_WriteToLog -->|"notify"| UI_Main
    Util_Alert -->|"display"| UI_Main

    %% Resources connected to UI
    Resources_Assets -->|"resource"| UI_Main
    UI_Help -->|"viewHelp"| Resources_Help
    UI_Help -->|"viewGuide"| Resources_PDF

    %% Click Events for User Interface Components
    click UI_Main "https://github.com/jamf/jamf-printer-manager/blob/main/Jamf Printer Manager/Base.lproj/Main.storyboard"
    click UI_About "https://github.com/jamf/jamf-printer-manager/blob/main/Jamf Printer Manager/AboutVC.swift"
    click UI_Add "https://github.com/jamf/jamf-printer-manager/blob/main/Jamf Printer Manager/AddPrinterVC.swift"
    click UI_Help "https://github.com/jamf/jamf-printer-manager/blob/main/Jamf Printer Manager/HelpVC.swift"
    click UI_Login "https://github.com/jamf/jamf-printer-manager/blob/main/Jamf Printer Manager/LoginVC.swift"
    click UI_PrinterInfo "https://github.com/jamf/jamf-printer-manager/blob/main/Jamf Printer Manager/PrinterInfoVC.swift"
    click UI_PrinterTab "https://github.com/jamf/jamf-printer-manager/blob/main/Jamf Printer Manager/PrinterInfoTabVC.swift"
    click UI_ToU "https://github.com/jamf/jamf-printer-manager/blob/main/Jamf Printer Manager/ToUVC.swift"

    %% Click Events for Application Core
    click Core_AppDelegate "https://github.com/jamf/jamf-printer-manager/blob/main/Jamf Printer Manager/AppDelegate.swift"
    click Core_Globals "https://github.com/jamf/jamf-printer-manager/blob/main/Jamf Printer Manager/Globals.swift"
    click Core_AppConfig "https://github.com/jamf/jamf-printer-manager/blob/main/Jamf-Printer-Manager-Info.plist,Jamf_Printer_Manager.entitlements"

    %% Click Events for Parsing Modules
    click Parse_CUPS "https://github.com/jamf/jamf-printer-manager/blob/main/Jamf Printer Manager/CupsParser.swift"
    click Parse_XML "https://github.com/jamf/jamf-printer-manager/blob/main/Jamf Printer Manager/XmlParser.swift"
    click Parse_XMLDelegate "https://github.com/jamf/jamf-printer-manager/blob/main/Jamf Printer Manager/XmlDelegate.swift"

    %% Click Events for Utility Modules
    click Util_Logging "https://github.com/jamf/jamf-printer-manager/blob/main/Jamf Printer Manager/Logging.swift"
    click Util_WriteToLog "https://github.com/jamf/jamf-printer-manager/blob/main/Jamf Printer Manager/WriteToLog.swift"
    click Util_Alert "https://github.com/jamf/jamf-printer-manager/blob/main/Jamf Printer Manager/Alert.swift"

    %% Click Events for Credential and Token Management
    click Auth_Credentials "https://github.com/jamf/jamf-printer-manager/blob/main/Jamf Printer Manager/Credentials.swift"
    click Auth_Token "https://github.com/jamf/jamf-printer-manager/blob/main/Jamf Printer Manager/TokenDelegate.swift"

    %% Click Events for Assets & Resources
    click Resources_Assets "https://github.com/jamf/jamf-printer-manager/blob/main/Jamf Printer Manager/Assets.xcassets"
    click Resources_Help "https://github.com/jamf/jamf-printer-manager/blob/main/Jamf Printer Manager/jpm_help.html"
    click Resources_PDF "https://github.com/jamf/jamf-printer-manager/blob/main/Jamf Printer Manager.pdf"

    %% Style Classes
    class UI_Main,UI_About,UI_Add,UI_Help,UI_Login,UI_PrinterInfo,UI_PrinterTab,UI_ToU fill:#CEF6F5,stroke:#333,stroke-width:2px;
    class Core_AppDelegate,Core_Globals,Core_AppConfig fill:#C1F0C1,stroke:#333,stroke-width:2px;
    class Parse_CUPS,Parse_XML,Parse_XMLDelegate fill:#F9E79F,stroke:#333,stroke-width:2px;
    class Util_Logging,Util_WriteToLog,Util_Alert fill:#FAD7A0,stroke:#333,stroke-width:2px;
    class Auth_Credentials,Auth_Token fill:#D7BDE2,stroke:#333,stroke-width:2px;
    class External_Jamf fill:#F5B7B1,stroke:#333,stroke-width:2px;
    class Resources_Assets,Resources_Help,Resources_PDF fill:#D6EAF8,stroke:#333,stroke-width:2px


```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
