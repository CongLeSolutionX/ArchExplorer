---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/electron/fiddle
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




# fiddle repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes (<ins>sometimes, entertainment purposes</ins>), personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


---

```mermaid
---
title: "fiddle repo project"
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
flowchart LR
    %% Electron App Container
    subgraph "Electron App"
        direction TB

        %% Main Process
        subgraph "Main Process (src/main)" 
            direction TB
            MP_Main["main.ts"]:::main
            MP_Menu["menu.ts"]:::main
            MP_Dialogs["dialogs.ts"]:::main
            MP_About["about-panel.ts"]:::main
            MP_CLI["command-line.ts"]:::main
            MP_FirstRun["first-run.ts"]:::main
            MP_Files["files.ts"]:::main
            MP_Templates["templates.ts"]:::main
            MP_Versions["versions.ts"]:::main
            MP_Update["update.ts"]:::main
            MP_Squirrel["squirrel.ts"]:::main
            MP_NPM["npm.ts"]:::main
            MP_SentryMain["sentry.ts"]:::main
            MP_IPC["ipc.ts"]:::main

            subgraph "Utils"
                direction TB
                MP_CheckFirstRun["check-first-run.ts"]:::main
                MP_Exec["exec.ts"]:::main
                MP_GetFiles["get-files.ts"]:::main
                MP_ReadFiddle["read-fiddle.ts"]:::main
            end
        end

        %% Preload Bridge
        subgraph "Preload Bridge (src/preload)"
            direction TB
            PB_Preload["preload.ts"]:::preload
            PB_IPCEvents["ipc-events.ts"]:::preload
        end

        %% Renderer Process
        subgraph "Renderer (src/renderer + src/less)"
            direction TB
            R_App["app.tsx"]:::renderer
            R_Main["main.tsx"]:::renderer
            R_State["state.ts"]:::renderer
            R_TaskRunner["task-runner.ts"]:::renderer
            R_Runner["runner.ts"]:::renderer
            R_RemoteLoader["remote-loader.ts"]:::renderer

            subgraph "Components"
                direction TB
                RC_FileTree["sidebar-file-tree.tsx"]:::renderer
                RC_PkgManager["sidebar-package-manager.tsx"]:::renderer
                RC_VersionChooser["commands-version-chooser.tsx"]:::renderer
                RC_VersionSelect["version-select.tsx"]:::renderer
                RC_Editor["editor.tsx"]:::renderer
                RC_EditorsToolbar["editors-toolbar-button.tsx"]:::renderer
                RC_Output["output.tsx"]:::renderer
                RC_Settings["settings-general.tsx"]:::renderer
                RC_Tour["tour.tsx"]:::renderer
                RC_TourWelcome["tour-welcome.tsx"]:::renderer
            end

            R_Styling["less styles"]:::renderer
        end
    end

    %% External Runner Process
    ER["Electron Runner"]:::external

    %% External Services
    subgraph "External Services"
        direction TB
        ES_NPM["NPM Registry"]:::service
        ES_GitHub["GitHub Gist/API"]:::service
        ES_Releases["Electron Releases"]:::service
        ES_SentryRenderer["Sentry (Renderer)"]:::service
        ES_SentryMain2["Sentry (Main)"]:::service
        ES_AutoUpdate["Auto-Updater"]:::service
    end

    %% Build / Tooling
    subgraph "Build & Tooling"
        direction TB
        BT_WebpackMain["webpack.main.config.ts"]:::build
        BT_WebpackRenderer["webpack.renderer.config.ts"]:::build
        BT_Forge["forge.config.ts"]:::build
        BT_CI_Circle[".circleci/config.yml"]:::build
        BT_CI_GH[".github/workflows"]:::build
    end

    %% Relationships
    R_App -->|"calls UI init"| R_Main
    R_Main -->|"IPC read/write/run"| PB_Preload
    PB_Preload -->|"forwards IPC"| MP_IPC

    MP_IPC --> MP_ReadFiddle
    MP_IPC --> MP_CheckFirstRun
    MP_IPC --> MP_Exec

    MP_Main --> ES_NPM
    MP_Main --> ES_GitHub
    MP_Main --> ES_SentryMain2
    MP_Main --> ES_AutoUpdate

    R_Runner --> ER
    ER -->|"stdout/stderr"| RC_Output

    %% Build flows
    BT_WebpackMain -.->|"bundles main"| MP_Main
    BT_WebpackRenderer -.->|"bundles renderer"| R_App
    BT_Forge -.->|"packages app"| ElectronApp

    %% Classes
    classDef main fill:#FFCC00,stroke:#333,stroke-width:1px
    classDef preload fill:#00CCFF,stroke:#333,stroke-width:1px
    classDef renderer fill:#99FF99,stroke:#333,stroke-width:1px
    classDef external fill:#FF9999,stroke:#333,stroke-width:1px
    classDef service fill:#CCFFCC,stroke:#333,stroke-width:1px
    classDef build fill:#CCCCFF,stroke:#333,stroke-width:1px

    %% Click Events - Main Process
    click MP_Main "https://github.com/electron/fiddle/blob/main/src/main/main.ts"
    click MP_Menu "https://github.com/electron/fiddle/blob/main/src/main/menu.ts"
    click MP_Dialogs "https://github.com/electron/fiddle/blob/main/src/main/dialogs.ts"
    click MP_About "https://github.com/electron/fiddle/blob/main/src/main/about-panel.ts"
    click MP_CLI "https://github.com/electron/fiddle/blob/main/src/main/command-line.ts"
    click MP_FirstRun "https://github.com/electron/fiddle/blob/main/src/main/first-run.ts"
    click MP_Files "https://github.com/electron/fiddle/blob/main/src/main/files.ts"
    click MP_Templates "https://github.com/electron/fiddle/blob/main/src/main/templates.ts"
    click MP_Versions "https://github.com/electron/fiddle/blob/main/src/main/versions.ts"
    click MP_Update "https://github.com/electron/fiddle/blob/main/src/main/update.ts"
    click MP_Squirrel "https://github.com/electron/fiddle/blob/main/src/main/squirrel.ts"
    click MP_NPM "https://github.com/electron/fiddle/blob/main/src/main/npm.ts"
    click MP_SentryMain "https://github.com/electron/fiddle/blob/main/src/main/sentry.ts"
    click MP_IPC "https://github.com/electron/fiddle/blob/main/src/main/ipc.ts"
    click MP_CheckFirstRun "https://github.com/electron/fiddle/blob/main/src/main/utils/check-first-run.ts"
    click MP_Exec "https://github.com/electron/fiddle/blob/main/src/main/utils/exec.ts"
    click MP_GetFiles "https://github.com/electron/fiddle/blob/main/src/main/utils/get-files.ts"
    click MP_ReadFiddle "https://github.com/electron/fiddle/blob/main/src/main/utils/read-fiddle.ts"

    %% Click Events - Preload
    click PB_Preload "https://github.com/electron/fiddle/blob/main/src/preload/preload.ts"
    click PB_IPCEvents "https://github.com/electron/fiddle/blob/main/src/ipc-events.ts"

    %% Click Events - Renderer
    click R_App "https://github.com/electron/fiddle/blob/main/src/renderer/app.tsx"
    click R_Main "https://github.com/electron/fiddle/blob/main/src/renderer/main.tsx"
    click R_State "https://github.com/electron/fiddle/blob/main/src/renderer/state.ts"
    click R_TaskRunner "https://github.com/electron/fiddle/blob/main/src/renderer/task-runner.ts"
    click R_Runner "https://github.com/electron/fiddle/blob/main/src/renderer/runner.ts"
    click R_RemoteLoader "https://github.com/electron/fiddle/blob/main/src/renderer/remote-loader.ts"
    click RC_FileTree "https://github.com/electron/fiddle/blob/main/src/renderer/components/sidebar-file-tree.tsx"
    click RC_PkgManager "https://github.com/electron/fiddle/blob/main/src/renderer/components/sidebar-package-manager.tsx"
    click RC_VersionChooser "https://github.com/electron/fiddle/blob/main/src/renderer/components/commands-version-chooser.tsx"
    click RC_VersionSelect "https://github.com/electron/fiddle/blob/main/src/renderer/components/version-select.tsx"
    click RC_Editor "https://github.com/electron/fiddle/blob/main/src/renderer/components/editor.tsx"
    click RC_EditorsToolbar "https://github.com/electron/fiddle/blob/main/src/renderer/components/editors-toolbar-button.tsx"
    click RC_Output "https://github.com/electron/fiddle/blob/main/src/renderer/components/output.tsx"
    click RC_Settings "https://github.com/electron/fiddle/blob/main/src/renderer/components/settings-general.tsx"
    click RC_Tour "https://github.com/electron/fiddle/blob/main/src/renderer/components/tour.tsx"
    click RC_TourWelcome "https://github.com/electron/fiddle/blob/main/src/renderer/components/tour-welcome.tsx"
    click R_Styling "https://github.com/electron/fiddle/tree/main/src/less"

    %% Click Events - Runner
    click ER "https://github.com/electron/fiddle/blob/main/src/main/utils/exec.ts"

    %% Click Events - Services
    click ES_NPM "https://github.com/electron/fiddle/blob/main/src/main/npm.ts"
    click ES_GitHub "https://github.com/electron/fiddle/blob/main/src/utils/gist.ts"
    click ES_Releases "https://github.com/electron/fiddle/blob/main/tools/fetch-releases.ts"
    click ES_SentryRenderer "https://github.com/electron/fiddle/blob/main/src/renderer/sentry.ts"
    click ES_SentryMain2 "https://github.com/electron/fiddle/blob/main/src/main/sentry.ts"
    click ES_AutoUpdate "https://github.com/electron/fiddle/blob/main/src/main/update.ts"

    %% Click Events - Build
    click BT_WebpackMain "https://github.com/electron/fiddle/blob/main/tools/webpack/webpack.main.config.ts"
    click BT_WebpackRenderer "https://github.com/electron/fiddle/blob/main/tools/webpack/webpack.renderer.config.ts"
    click BT_Forge "https://github.com/electron/fiddle/blob/main/forge.config.ts"
    click BT_CI_Circle "https://github.com/electron/fiddle/blob/main/.circleci/config.yml"
    click BT_CI_GH "https://github.com/electron/fiddle/tree/main/.github/workflows"


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