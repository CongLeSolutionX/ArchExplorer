---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ipfs/ipfs-desktop
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExaHNwdmJteDFidGlyMnE4MHFiYnU3ZG05dnQ1eHY5NDQ4dnlzNmtzdCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/qc5fbrb4qpupRA9r4o/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# ipfs repo project
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
title: "ipfs repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'linear' },
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#222B2B',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#2221',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '20px'
    }
  }
}%%
flowchart TD
    %% Application Boundary
    subgraph "IPFS Desktop App"
        direction TB

        subgraph "Electron Processes"
            direction TB
            Main["Electron Main Process"]:::electron
            Renderer["Electron Renderer Processes (UI)"]:::electron
        end

        %% IPC between Main & Renderer
        Main <-->|"IPC"| Renderer

        %% Embedded Web UI in Renderer
        Renderer -->|"loads assets"| WebUI["IPFS Web UI"]:::ipfs
        WebUI -->|"HTTP API"| Daemon

        %% Main spawns Daemon
        Main -->|"spawn/control"| Daemon["IPFS Daemon (Kubo)"]:::ipfs

        %% OS Integration Modules
        subgraph "OS Integration" 
            direction TB
            Tray["Tray / Menu"]:::os
            AppMenu["App Menu"]:::os
            AutoLaunch["Auto-Launch"]:::os
            ProtocolHandlers["Protocol Handlers"]:::os
        end
        Main --> Tray
        Main --> AppMenu
        Main --> AutoLaunch
        Main --> ProtocolHandlers

        %% Main Modules
        subgraph "Main Modules"
            direction TB
            AutoUpdater["Auto-Updater"]:::os
            Analytics["Analytics / Telemetry"]:::external
            Store["Configuration Store"]:::storage
            Logger["Logging"]:::storage
            I18n["i18n Loader"]:::frontend
            FileImport["File Import Utility"]:::ipfs
            ScreenshotUtil["Screenshot Utility"]:::frontend
            Dialogs["Dialogs"]:::os
            AutoGC["Automatic GC Control"]:::ipfs
            RunGC["Run GC"]:::ipfs
            SecondInstance["Second Instance Handler"]:::os
            ArgvHandler["CLI Args Handler"]:::os
            CustomBinary["Custom IPFS Binary Selection"]:::ipfs
            Utils["Misc Utilities"]:::os
        end

        Main --> AutoUpdater
        Main --> Analytics
        Main --> Store
        Main --> Logger
        Main --> I18n
        Main --> FileImport
        Main --> ScreenshotUtil
        Main --> Dialogs
        Main --> AutoGC
        Main --> RunGC
        Main --> SecondInstance
        Main --> ArgvHandler
        Main --> CustomBinary
        Main --> Utils
    end

    %% Local Storage
    Store --> Repo["Kubo Repo (fs)"]:::storage
    Store --> ConfigFiles["Config & Logs"]:::storage

    %% External Services
    Daemon -->|"P2P"| IPFSNet["IPFS Network"]:::external
    AutoUpdater -->|"Update Check"| UpdateServer["GitHub / Snapcraft / Chocolatey"]:::external
    Analytics -->|"Telemetry Post"| Telemetry["Telemetry Endpoint"]:::external

    %% Click Events
    click Main "https://github.com/ipfs/ipfs-desktop/blob/main/src/index.js"
    click Renderer "https://github.com/ipfs/ipfs-desktop/tree/main/src/webui/"
    click Daemon "https://github.com/ipfs/ipfs-desktop/tree/main/src/daemon/"
    click WebUI "https://github.com/ipfs/ipfs-desktop/tree/main/src/webui/"
    click Ipc "https://github.com/ipfs/ipfs-desktop/blob/main/src/common/ipc-main-events.js"
    click Tray "https://github.com/ipfs/ipfs-desktop/blob/main/src/tray.js"
    click AppMenu "https://github.com/ipfs/ipfs-desktop/blob/main/src/app-menu.js"
    click AutoLaunch "https://github.com/ipfs/ipfs-desktop/blob/main/src/auto-launch.js"
    click ProtocolHandlers "https://github.com/ipfs/ipfs-desktop/blob/main/src/protocol-handlers.js"
    click AutoUpdater "https://github.com/ipfs/ipfs-desktop/blob/main/src/auto-updater/index.js"
    click ElectronBuilder "https://github.com/ipfs/ipfs-desktop/blob/main/electron-builder.yml"
    click Analytics "https://github.com/ipfs/ipfs-desktop/blob/main/src/analytics/index.js"
    click Store "https://github.com/ipfs/ipfs-desktop/blob/main/src/common/store.js"
    click Logger "https://github.com/ipfs/ipfs-desktop/blob/main/src/common/logger.js"
    click I18n "https://github.com/ipfs/ipfs-desktop/blob/main/src/i18n.js"
    click ScreenshotUtil "https://github.com/ipfs/ipfs-desktop/blob/main/src/take-screenshot.js"
    click FileImport "https://github.com/ipfs/ipfs-desktop/blob/main/src/add-to-ipfs.js"
    click Dialogs "https://github.com/ipfs/ipfs-desktop/tree/main/src/dialogs/"
    click AutoGC "https://github.com/ipfs/ipfs-desktop/blob/main/src/automatic-gc.js"
    click RunGC "https://github.com/ipfs/ipfs-desktop/blob/main/src/run-gc.js"
    click SecondInstance "https://github.com/ipfs/ipfs-desktop/blob/main/src/second-instance.js"
    click ArgvHandler "https://github.com/ipfs/ipfs-desktop/blob/main/src/argv-files-handler.js"
    click CustomBinary "https://github.com/ipfs/ipfs-desktop/blob/main/src/custom-ipfs-binary.js"
    click Utils "https://github.com/ipfs/ipfs-desktop/tree/main/src/utils/"

    %% Styles
    classDef electron fill:#cce5ff,stroke:#000,stroke-width:1px;
    classDef ipfs fill:#d4edda,stroke:#000,stroke-width:1px;
    classDef os fill:#fff3cd,stroke:#000,stroke-width:1px;
    classDef storage fill:#e2e3e5,stroke:#000,stroke-width:1px;
    classDef external fill:#ffe5b4,stroke:#000,stroke-width:1px;
    classDef frontend fill:#e0f7fa,stroke:#000,stroke-width:1px;
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
    
  My_Meme ~~~ Closing_quote
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

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