---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/swiftlang/swiftly
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExeG9pMTVuMHA4NHh5cWlzanFoMzVqd3JlN3NndGE2NndjeDViMmszYSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/KeFAk6UBy7NUA4Vz3x/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# swiftly repo project
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
title: "swiftly repo project"
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
    %% User interaction
    User["User"]:::external -->|"swiftly &lt;command&gt; "| CLI["CLI Frontend\n(Sources/Swiftly)"]:::frontend

    subgraph "CLI Frontend" 
        direction TB
        CLIExec["swiftly\n(Sources/Swiftly/Swiftly.swift)"]:::frontend
        Install["InstallCommand\n(Sources/Swiftly/Install.swift)"]:::frontend
        Use["UseCommand\n(Sources/Swiftly/Use.swift)"]:::frontend
        Update["UpdateCommand\n(Sources/Swiftly/Update.swift)"]:::frontend
        Uninstall["UninstallCommand\n(Sources/Swiftly/Uninstall.swift)"]:::frontend
        List["ListCommand\n(Sources/Swiftly/List.swift)"]:::frontend
        ListAvail["ListAvailableCommand\n(Sources/Swiftly/ListAvailable.swift)"]:::frontend
        Run["RunCommand\n(Sources/Swiftly/Run.swift)"]:::frontend
        SelfUpdate["SelfUpdateCommand\n(Sources/Swiftly/SelfUpdate.swift)"]:::frontend
        Link["LinkCommand\n(Sources/Swiftly/Link.swift)"]:::frontend
        Unlink["UnlinkCommand\n(Sources/Swiftly/Unlink.swift)"]:::frontend
        InitCmd["InitCommand\n(Sources/Swiftly/Init.swift)"]:::frontend
        Proxy["ProxyCommand\n(Sources/Swiftly/Proxy.swift)"]:::frontend
        Config["Config definitions\n(Sources/Swiftly/Config.swift)"]:::frontend
    end

    CLIExec -->|invokes| Install
    CLIExec -->|invokes| Use
    CLIExec -->|invokes| Update
    CLIExec -->|invokes| Uninstall
    CLIExec -->|invokes| List
    CLIExec -->|invokes| ListAvail
    CLIExec -->|invokes| Run
    CLIExec -->|invokes| SelfUpdate
    CLIExec -->|invokes| Link
    CLIExec -->|invokes| Unlink
    CLIExec -->|invokes| InitCmd
    CLIExec -->|invokes| Proxy

    subgraph "Core Library" 
        direction TB
        CoreFacade["SwiftlyCore\n(Sources/SwiftlyCore)"]:::core
        CmdParse["ModeledCommandLine & Commands\n(ModeledCommandLine.swift, Commands.swift)"]:::core
        HTTPAbstr["HTTPClient\n(HTTPClient.swift)"]:::infra
        FileUtil["FileManager+FilePath\n(FileManager+FilePath.swift)"]:::infra
        VersionModel["SwiftlyVersion & ToolchainVersion\n(SwiftlyVersion.swift, ToolchainVersion.swift)"]:::core
        ErrorType["Error handling\n(Error.swift)"]:::core
        Messages["Messages & Localization\n(Messages.swift)"]:::core
        PlatformIface["Platform interface\n(Platform.swift)"]:::core
        StringExt["String utilities\n(StringExtensions.swift)"]:::core
    end

    Install -->|calls| CoreFacade
    Use -->|calls| CoreFacade
    Update -->|calls| CoreFacade
    SelfUpdate -->|calls| CoreFacade

    CoreFacade --> CmdParse
    CoreFacade --> HTTPAbstr
    CoreFacade --> FileUtil
    CoreFacade --> VersionModel
    CoreFacade --> ErrorType
    CoreFacade --> Messages
    CoreFacade --> PlatformIface
    CoreFacade --> StringExt

    subgraph "API Clients"
        direction TB
        DownloadAPI["SwiftlyDownloadAPI\n(Sources/SwiftlyDownloadAPI)"]:::infra
        WebsiteAPI["SwiftlyWebsiteAPI\n(Sources/SwiftlyWebsiteAPI)"]:::infra
    end

    HTTPAbstr -->|GET metadata| DownloadAPI
    HTTPAbstr -->|GET metadata| WebsiteAPI

    subgraph "Archive Extraction\n(CLibArchive)"
        direction TB
        CLib["CLibArchive\n(Sources/CLibArchive)"]:::infra
    end

    DownloadAPI -->|provides URL & checksum| HTTPAbstr
    HTTPAbstr -->|download archive| CLib
    CLib -->|extract| FileUtil

    subgraph "Platform Adapters"
        direction TB
        LinuxPlat["LinuxPlatform\n(Sources/LinuxPlatform)"]:::core
        MacPlat["MacOSPlatform\n(Sources/MacOSPlatform)"]:::core
    end

    PlatformIface --> LinuxPlat
    PlatformIface --> MacPlat

    subgraph "File System & Env Manager"
        direction TB
        FileUtil --> EnvScript["Shell Env Scripts\n(generated)"]:::infra
        EnvScript -->|"update PATH"| Shell["Shell Integration"]:::external
    end

    CLib --> FileUtil

    subgraph "External Services"
        direction TB
        SwiftOrgDL["Swift.org Download Server"]:::external
        SwiftOrgWeb["Swift.org Website API"]:::external
    end

    DownloadAPI -->|fetch metadata| SwiftOrgWeb
    DownloadAPI -->|download archive| SwiftOrgDL

    classDef frontend fill:#D6EAF8,stroke:#1B4F72,color:#1B4F72
    classDef core fill:#E8DAEF,stroke:#512E5F,color:#512E5F
    classDef infra fill:#D5F5E3,stroke:#1D8348,color:#1D8348
    classDef external fill:#FADBD8,stroke:#922B21,color:#922B21

    %% Click events
    click CLIExec "https://github.com/swiftlang/swiftly/blob/main/Sources/Swiftly/Swiftly.swift"
    click Install "https://github.com/swiftlang/swiftly/blob/main/Sources/Swiftly/Install.swift"
    click Use "https://github.com/swiftlang/swiftly/blob/main/Sources/Swiftly/Use.swift"
    click Update "https://github.com/swiftlang/swiftly/blob/main/Sources/Swiftly/Update.swift"
    click Uninstall "https://github.com/swiftlang/swiftly/blob/main/Sources/Swiftly/Uninstall.swift"
    click List "https://github.com/swiftlang/swiftly/blob/main/Sources/Swiftly/List.swift"
    click ListAvail "https://github.com/swiftlang/swiftly/blob/main/Sources/Swiftly/ListAvailable.swift"
    click Run "https://github.com/swiftlang/swiftly/blob/main/Sources/Swiftly/Run.swift"
    click SelfUpdate "https://github.com/swiftlang/swiftly/blob/main/Sources/Swiftly/SelfUpdate.swift"
    click Link "https://github.com/swiftlang/swiftly/blob/main/Sources/Swiftly/Link.swift"
    click Unlink "https://github.com/swiftlang/swiftly/blob/main/Sources/Swiftly/Unlink.swift"
    click InitCmd "https://github.com/swiftlang/swiftly/blob/main/Sources/Swiftly/Init.swift"
    click Proxy "https://github.com/swiftlang/swiftly/blob/main/Sources/Swiftly/Proxy.swift"
    click Config "https://github.com/swiftlang/swiftly/blob/main/Sources/Swiftly/Config.swift"
    click CoreFacade "https://github.com/swiftlang/swiftly/tree/main/Sources/SwiftlyCore"
    click HTTPAbstr "https://github.com/swiftlang/swiftly/blob/main/Sources/SwiftlyCore/HTTPClient.swift"
    click FileUtil "https://github.com/swiftlang/swiftly/blob/main/Sources/SwiftlyCore/FileManager+FilePath.swift"
    click DownloadAPI "https://github.com/swiftlang/swiftly/tree/main/Sources/SwiftlyDownloadAPI"
    click WebsiteAPI "https://github.com/swiftlang/swiftly/tree/main/Sources/SwiftlyWebsiteAPI"
    click CLib "https://github.com/swiftlang/swiftly/tree/main/Sources/CLibArchive"
    click LinuxPlat "https://github.com/swiftlang/swiftly/tree/main/Sources/LinuxPlatform"
    click MacPlat "https://github.com/swiftlang/swiftly/tree/main/Sources/MacOSPlatform"
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
