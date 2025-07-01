---
created: 2025-07-01 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/saberzero1/quartz-syncer
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




# quartz-syncer repo project by saberzero1
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for 👨‍🎓 <ins>educational purposes</ins> 👨‍🎓 (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), 📖 <ins> personal study </ins> 📖, and 🔖 <ins> technical reference </ins> 🔖.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>



---

```mermaid
---
title: "quartz-syncer repo project by saberzero1"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright © 2025 Cong Le. All Rights Reserved."
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
    %% External Host
    subgraph Obsidian_Host["Obsidian Host"]
    direction TB

        subgraph Presentation_Layer["Presentation Layer<br/>(UI)"]
        direction TB
            SettingsView["SettingsView<br/>(Svelte)"]:::frontend
            PublicationCenter["PublicationCenter (Svelte)"]:::frontend
            Icon["Icon.svelte"]:::frontend
            LineDiff["LineDiff.svelte"]:::frontend
            TreeViewComp["TreeView.svelte"]:::frontend
            TreeNodeComp["TreeNode.svelte"]:::frontend
        end

        subgraph Application_Layer["Application Layer<br/>(Core Logic)"]
        direction TB

            subgraph Build_and_Config["Build & Config"]
                manifest["manifest.json"]:::business
                mainTS["main.ts"]:::business
                pkg["package.json"]:::business
                tsconfig["tsconfig.json"]:::business
                esbuild["esbuild.config.mjs"]:::business
                justfile["justfile"]:::business
            end

            subgraph Core_Modules["Core Modules"]
            direction TB
                compilerDir["src/compiler"]:::business
                publishFileDir["src/publishFile"]:::business
                publisherDir["src/publisher"]:::business
                repoConnDir["src/repositoryConnection"]:::business
                modelsDir["src/models"]:::business
                utilsDir["src/utils"]:::business
            end
        end
    end

    subgraph Data_Layer["Data Layer"]
    direction TB
        Vault["Local Vault<br/>(Folder)"]:::storage
        RemoteRepo["Remote Quartz Repo"]:::storage
    end

    %% External Service
    GitHubAPI["GitHub REST API"]:::external

    %% Connections
    SettingsView -->|"user action"| mainTS
    PublicationCenter -->|"publish command"| mainTS
    mainTS -->|loads plugins| compilerDir
    compilerDir -->|"transform notes"| publishFileDir
    publishFileDir -->|"prepare payloads"| repoConnDir
    repoConnDir -->|"sync & diff"| GitHubAPI
    GitHubAPI -->|"response"| repoConnDir
    repoConnDir -->|"status update"| publisherDir
    publisherDir -->|"commit changes"| GitHubAPI
    Vault -->|"read notes"| compilerDir
    GitHubAPI -->|"read remote"| repoConnDir
    publisherDir -->|"report status"| PublicationCenter

  %% Define classes
    classDef frontend fill:#D0E8FF,stroke:#0366d6,stroke-width:1px
    classDef business fill:#D0FFD6,stroke:#22863A,stroke-width:1px
    classDef storage fill:#FFE8A1,stroke:#D29922,stroke-width:1px
    classDef external fill:#EDEDED,stroke:#6a737d,stroke-width:1px


    %% Click events for config
    click manifest "https://github.com/saberzero1/quartz-syncer/blob/main/manifest.json"
    click mainTS "https://github.com/saberzero1/quartz-syncer/blob/main/main.ts"
    click pkg "https://github.com/saberzero1/quartz-syncer/blob/main/package.json"
    click tsconfig "https://github.com/saberzero1/quartz-syncer/blob/main/tsconfig.json"
    click esbuild "https://github.com/saberzero1/quartz-syncer/blob/main/esbuild.config.mjs"
    click justfile "https://github.com/saberzero1/quartz-syncer/tree/main/justfile"



    %% Click events for compiler
    click compilerDir "https://github.com/saberzero1/quartz-syncer/tree/main/src/compiler"
    click Frontmatter["FrontmatterCompiler.ts"] "src/compiler/FrontmatterCompiler.ts"
    click PluginCompiler["PluginCompiler.ts"] "src/compiler/PluginCompiler.ts"
    click SyncerPage["SyncerPageCompiler.ts"] "src/compiler/SyncerPageCompiler.ts"
    click Datacore["DatacoreCompiler.ts"] "src/compiler/plugins/DatacoreCompiler.ts"
    click Dataview["DataviewCompiler.ts"] "src/compiler/plugins/DataviewCompiler.ts"
    click Fantasy["FantasyStatblocksCompiler.ts"] "src/compiler/plugins/FantasyStatblocksCompiler.ts"

    %% Click events for publishFile
    click publishFileDir "https://github.com/saberzero1/quartz-syncer/tree/main/src/publishFile"
    click DataStore["DataStore.ts"] "src/publishFile/DataStore.ts"
    click FileMeta["FileMetaDataManager.ts"] "src/publishFile/FileMetaDataManager.ts"
    click FrontMatterEngine["ObsidianFrontMatterEngine.ts"] "src/publishFile/ObsidianFrontMatterEngine.ts"
    click PublishFile["PublishFile.ts"] "src/publishFile/PublishFile.ts"
    click Validator["Validator.ts"] "src/publishFile/Validator.ts"

    %% Click events for publisher
    click publisherDir "https://github.com/saberzero1/quartz-syncer/tree/main/src/publisher"
    click PublishStatus["PublishStatusManager.ts"] "src/publisher/PublishStatusManager.ts"
    click Publisher["Publisher.ts"] "src/publisher/Publisher.ts"

    %% Click events for repositoryConnection
    click repoConnDir "https://github.com/saberzero1/quartz-syncer/tree/main/src/repositoryConnection"
    click SiteManager["QuartzSyncerSiteManager.ts"] "src/repositoryConnection/QuartzSyncerSiteManager.ts"
    click RepoConn["RepositoryConnection.ts"] "src/repositoryConnection/RepositoryConnection.ts"

    %% Click events for models
    click modelsDir "https://github.com/saberzero1/quartz-syncer/tree/main/src/models"
    click TreeNodeModel["TreeNode.ts"] "src/models/TreeNode.ts"
    click SyncerTabModel["SyncerTab.ts"] "src/models/SyncerTab.ts"
    click ProgressBarModel["ProgressBar.ts"] "src/models/ProgressBar.ts"
    click SettingsModel["settings.ts"] "src/models/settings.ts"

    %% Click events for UI components
    click Icon "https://github.com/saberzero1/quartz-syncer/blob/main/src/ui/Icon.svelte"
    click LineDiff "https://github.com/saberzero1/quartz-syncer/blob/main/src/ui/LineDiff.svelte"
    click TreeViewComp "https://github.com/saberzero1/quartz-syncer/blob/main/src/ui/TreeView/TreeView.svelte"
    click TreeNodeComp "https://github.com/saberzero1/quartz-syncer/blob/main/src/ui/TreeView/TreeNode.svelte"
    click SettingsView "https://github.com/saberzero1/quartz-syncer/blob/main/src/views/SettingsView/SettingView.ts"
    click PublicationCenter "https://github.com/saberzero1/quartz-syncer/blob/main/src/views/PublicationCenter/PublicationCenter.svelte"
    click DiffView "https://github.com/saberzero1/quartz-syncer/blob/main/src/views/PublicationCenter/DiffView.svelte"
    click PubCenterCtrl "https://github.com/saberzero1/quartz-syncer/blob/main/src/views/PublicationCenter/PublicationCenter.ts"

    %% Click events for Settings Views
    click FrontmatterSettings "https://github.com/saberzero1/quartz-syncer/blob/main/src/views/SettingsView/Views/FrontmatterSettings.ts"
    click GithubSettings "https://github.com/saberzero1/quartz-syncer/blob/main/src/views/SettingsView/Views/GithubSettings.ts"
    click IntegrationSettings "https://github.com/saberzero1/quartz-syncer/blob/main/src/views/SettingsView/Views/IntegrationSettings.ts"
    click PerformanceSettings "https://github.com/saberzero1/quartz-syncer/blob/main/src/views/SettingsView/Views/PerformanceSettings.ts"
    click QuartzSettings "https://github.com/saberzero1/quartz-syncer/blob/main/src/views/SettingsView/Views/QuartzSettings.ts"
    click ThemesSettings "https://github.com/saberzero1/quartz-syncer/blob/main/src/views/SettingsView/Views/ThemesSettings.ts"

    %% Click events for utils
    click utilsDir "https://github.com/saberzero1/quartz-syncer/tree/main/src/utils"
    click Utils "https://github.com/saberzero1/quartz-syncer/blob/main/src/utils/utils.ts"
    click UtilsTest "https://github.com/saberzero1/quartz-syncer/blob/main/src/utils/utils.test.ts"
    click Regexes "https://github.com/saberzero1/quartz-syncer/blob/main/src/utils/regexes.ts"
    click Styles "https://github.com/saberzero1/quartz-syncer/blob/main/src/utils/styles.ts"

    %% Click events for testing
    click jestConfig "https://github.com/saberzero1/quartz-syncer/blob/main/jest.config.js"
    click TestDir["src/test"] "src/test"
    click SnapshotGen["src/test/snapshot/generateSyncerSnapshot.ts"] "src/test/snapshot/generateSyncerSnapshot.ts"
    click SnapshotMd["src/test/snapshot/snapshot.md"] "src/test/snapshot/snapshot.md"

    %% Click events for content and docs
    click Content "https://github.com/saberzero1/quartz-syncer/tree/main/content/"
    click Docs "https://github.com/saberzero1/quartz-syncer/tree/main/docs/"

    %% Class assignments
    class SettingsView,PublicationCenter,Icon,LineDiff,TreeViewComp,TreeNodeComp frontend
    class manifest,mainTS,pkg,tsconfig,esbuild,justfile business
    class compilerDir,publishFileDir,publisherDir,repoConnDir,modelsDir,utilsDir business
    class Vault,RemoteRepo storage
    class GitHubAPI external

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
    
  Closing_quote ~~~ My_Meme
    
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