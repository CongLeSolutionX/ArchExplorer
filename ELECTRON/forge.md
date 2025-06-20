---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/electron/forge
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




# forge repo project
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
title: "electron - forge repo project"
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
    %% API Layer
    subgraph "API Layer"
        CLI["CLI Front-End\npackages/api/cli"]:::core
        Core["Core Orchestrator\npackages/api/core"]:::core
    end

    %% Extension Packages
    subgraph "Plugin System"
        BasePlugin["Base Plugin Interface\npackages/plugin/base"]:::extension
        AutoUnpack["Auto-Unpack Natives\npackages/plugin/auto-unpack-natives"]:::extension
        Electronegativity["Electronegativity Plugin\npackages/plugin/electronegativity"]:::extension
        Fuses["Fuses Plugin\npackages/plugin/fuses"]:::extension
        LocalElectron["Local Electron Plugin\npackages/plugin/local-electron"]:::extension
        VitePlugin["Vite Plugin\npackages/plugin/vite"]:::extension
        WebpackPlugin["Webpack Plugin\npackages/plugin/webpack"]:::extension
    end

    subgraph "Maker Modules"
        BaseMaker["Base Maker Interface\npackages/maker/base"]:::extension
        AppX["AppX Maker\npackages/maker/appx"]:::extension
        Deb["Debian Maker\npackages/maker/deb"]:::extension
        DMG["DMG Maker\npackages/maker/dmg"]:::extension
        Flatpak["Flatpak Maker\npackages/maker/flatpak"]:::extension
        PKG["Mac PKG Maker\npackages/maker/pkg"]:::extension
        RPM["RPM Maker\npackages/maker/rpm"]:::extension
        SnapMaker["Snap Maker\npackages/maker/snap"]:::extension
        Squirrel["Squirrel Maker\npackages/maker/squirrel"]:::extension
        Wix["Wix Maker\npackages/maker/wix"]:::extension
        ZipMaker["Zip Maker\npackages/maker/zip"]:::extension
    end

    subgraph "Publisher Modules"
        BasePub["Base Publisher Interface\npackages/publisher/base"]:::extension
        StaticPub["Static Publisher\npackages/publisher/base-static"]:::extension
        Bitbucket["Bitbucket Publisher\npackages/publisher/bitbucket"]:::extension
        ERSPub["Electron Release Server\npackages/publisher/electron-release-server"]:::extension
        GCSPub["Google Cloud Storage\npackages/publisher/gcs"]:::extension
        GitHubPub["GitHub Publisher\npackages/publisher/github"]:::extension
        Nucleus["Nucleus Publisher\npackages/publisher/nucleus"]:::extension
        S3Pub["S3 Publisher\npackages/publisher/s3"]:::extension
        Snapcraft["Snapcraft Publisher\npackages/publisher/snapcraft"]:::extension
    end

    subgraph "Template Engine"
        BaseTemplate["Base Template\npackages/template/base"]:::extension
        ViteTemplate["Vite Template\npackages/template/vite"]:::extension
        ViteTS["Vite TS Template\npackages/template/vite-typescript"]:::extension
        WebpackTS["Webpack TS Template\npackages/template/webpack-typescript"]:::extension
        WebpackTemplate["Webpack Template\npackages/template/webpack"]:::extension
    end

    subgraph "Utility Libraries"
        CoreUtils["Core Utilities\npackages/utils/core-utils"]:::util
        TestUtils["Test Utilities\npackages/utils/test-utils"]:::util
        Tracer["Tracer\npackages/utils/tracer"]:::util
        TypesDef["Types Definitions\npackages/utils/types"]:::util
        MultiLogger["Web Multi-Logger\npackages/utils/web-multi-logger"]:::util
    end

    subgraph "External Integration"
        CreateApp["Create Electron App Wrapper\npackages/external/create-electron-app"]:::external
    end

    subgraph "Tooling Scripts"
        Tools["Monorepo Tooling\ntools/"]:::external
    end

    subgraph "CI/CD Pipelines"
        CircleCI["CircleCI Config\n.circleci/config.yml"]:::ci
        GHActions["GitHub Actions\n.github/workflows/"]:::ci
    end

    %% Flow
    CLI -->|"invokes"| Core
    Core -->|"loads config & hooks"| BasePlugin
    Core --> AutoUnpack
    Core --> Electronegativity
    Core --> Fuses
    Core --> LocalElectron
    Core --> VitePlugin
    Core --> WebpackPlugin

    Core -->|"init"| BaseTemplate
    Core --> ViteTemplate
    Core --> ViteTS
    Core --> WebpackTS
    Core --> WebpackTemplate

    Core -->|"make"| BaseMaker
    Core --> AppX
    Core --> Deb
    Core --> DMG
    Core --> Flatpak
    Core --> PKG
    Core --> RPM
    Core --> SnapMaker
    Core --> Squirrel
    Core --> Wix
    Core --> ZipMaker

    Core -->|"publish"| BasePub
    Core --> StaticPub
    Core --> Bitbucket
    Core --> ERSPub
    Core --> GCSPub
    Core --> GitHubPub
    Core --> Nucleus
    Core --> S3Pub
    Core --> Snapcraft

    Core -->|"uses"| CoreUtils
    Core --> TestUtils
    Core --> Tracer
    Core --> TypesDef
    Core --> MultiLogger

    CreateApp -->|"wraps"| CLI
    CreateApp --> Core

    Tools -->|"scripts run by"| CircleCI
    Tools --> GHActions
    CircleCI --> Tools
    GHActions --> Tools

    %% Click Events
    click CLI "https://github.com/electron/forge/tree/main/packages/api/cli"
    click Core "https://github.com/electron/forge/tree/main/packages/api/core"
    click BasePlugin "https://github.com/electron/forge/tree/main/packages/plugin/base"
    click AutoUnpack "https://github.com/electron/forge/tree/main/packages/plugin/auto-unpack-natives"
    click Electronegativity "https://github.com/electron/forge/tree/main/packages/plugin/electronegativity"
    click Fuses "https://github.com/electron/forge/tree/main/packages/plugin/fuses"
    click LocalElectron "https://github.com/electron/forge/tree/main/packages/plugin/local-electron"
    click VitePlugin "https://github.com/electron/forge/tree/main/packages/plugin/vite"
    click WebpackPlugin "https://github.com/electron/forge/tree/main/packages/plugin/webpack"
    click BaseMaker "https://github.com/electron/forge/tree/main/packages/maker/base"
    click AppX "https://github.com/electron/forge/tree/main/packages/maker/appx"
    click Deb "https://github.com/electron/forge/tree/main/packages/maker/deb"
    click DMG "https://github.com/electron/forge/tree/main/packages/maker/dmg"
    click Flatpak "https://github.com/electron/forge/tree/main/packages/maker/flatpak"
    click PKG "https://github.com/electron/forge/tree/main/packages/maker/pkg"
    click RPM "https://github.com/electron/forge/tree/main/packages/maker/rpm"
    click SnapMaker "https://github.com/electron/forge/tree/main/packages/maker/snap"
    click Squirrel "https://github.com/electron/forge/tree/main/packages/maker/squirrel"
    click Wix "https://github.com/electron/forge/tree/main/packages/maker/wix"
    click ZipMaker "https://github.com/electron/forge/tree/main/packages/maker/zip"
    click BasePub "https://github.com/electron/forge/tree/main/packages/publisher/base"
    click StaticPub "https://github.com/electron/forge/tree/main/packages/publisher/base-static"
    click Bitbucket "https://github.com/electron/forge/tree/main/packages/publisher/bitbucket"
    click ERSPub "https://github.com/electron/forge/tree/main/packages/publisher/electron-release-server"
    click GCSPub "https://github.com/electron/forge/tree/main/packages/publisher/gcs"
    click GitHubPub "https://github.com/electron/forge/tree/main/packages/publisher/github"
    click Nucleus "https://github.com/electron/forge/tree/main/packages/publisher/nucleus"
    click S3Pub "https://github.com/electron/forge/tree/main/packages/publisher/s3"
    click Snapcraft "https://github.com/electron/forge/tree/main/packages/publisher/snapcraft"
    click BaseTemplate "https://github.com/electron/forge/tree/main/packages/template/base"
    click ViteTemplate "https://github.com/electron/forge/tree/main/packages/template/vite"
    click ViteTS "https://github.com/electron/forge/tree/main/packages/template/vite-typescript"
    click WebpackTS "https://github.com/electron/forge/tree/main/packages/template/webpack-typescript"
    click WebpackTemplate "https://github.com/electron/forge/tree/main/packages/template/webpack"
    click CoreUtils "https://github.com/electron/forge/tree/main/packages/utils/core-utils"
    click TestUtils "https://github.com/electron/forge/tree/main/packages/utils/test-utils"
    click Tracer "https://github.com/electron/forge/tree/main/packages/utils/tracer"
    click TypesDef "https://github.com/electron/forge/tree/main/packages/utils/types"
    click MultiLogger "https://github.com/electron/forge/tree/main/packages/utils/web-multi-logger"
    click CreateApp "https://github.com/electron/forge/tree/main/packages/external/create-electron-app"
    click Tools "https://github.com/electron/forge/tree/main/tools/"
    click CircleCI "https://github.com/electron/forge/blob/main/.circleci/config.yml"
    click GHActions "https://github.com/electron/forge/tree/main/.github/workflows/"

    %% Styles
    classDef core fill:#FFD700,stroke:#333,stroke-width:2px
    classDef extension fill:#87CEEB,stroke:#333,stroke-width:1px
    classDef util fill:#90EE90,stroke:#333,stroke-width:1px
    classDef external fill:#FFB6C1,stroke:#333,stroke-width:1px
    classDef ci fill:#D3D3D3,stroke:#333,stroke-width:1px
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