---
created: 2025-07-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/zlovatt/obsidian-trim-whitespace
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


# trim-whitespace repo project by zlovatt
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



----

```mermaid
---
title: "OBSIDIAN PLUGINS - zlovatt - obsidian-trim-whitespace repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright © 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'linear'},
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#22BB',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EEF2',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '15px'
    }
  }
}%%
flowchart TD
    %% Obsidian Host Layer
    subgraph "Obsidian Host" 
        direction TB
        HostAPI["Obsidian Plugin API"]:::host
        UI["Command Palette & Ribbon"]:::host
        Editor["Editor / Document Model"]:::host
    end

    %% Plugin Core Layer
    subgraph "Trim-Whitespace Plugin" 
        direction TB
        main["Plugin Entry Point\nmain.ts"]:::core
        settings["Settings Manager\nsettings.ts"]:::core
        storage["PluginData Storage"]:::storage
    end

    %% Utilities Layer
    subgraph "Pure-Function Utils" 
        direction TB
        trimText["Core Trimming Algorithm\ntrimText.ts"]:::utils
        searchReplace["Search/Replace Logic\nsearchReplaceTokens.ts"]:::utils
        cursorFence["Cursor Fence Handling\ngetCursorFenceIndices.ts"]:::utils
    end

    %% Build & CI/CD Layer
    subgraph "Build, Test & Release" 
        direction TB
        tsconfig["tsconfig.json"]:::build
        jestConfig["jest.config.js"]:::build
        versionScript["Version Bump Script\nset-versions.mjs"]:::build
        ciWorkflow["GitHub Actions Workflow\nrelease.yml"]:::build
        manifest["Plugin Metadata\nmanifest.json"]:::build
        package["package.json"]:::build
        versions["versions.json"]:::build
        changelog["changelog.md"]:::build
        typings["Custom Types\nindex.d.ts"]:::build
        trimTextTest["Unit Tests\ntrimText.test.ts"]:::build
    end

    %% Interactions
    HostAPI -->|"activate()"| main
    main -->|"registerCommands()"| UI
    UI -->|"onCommandTrigger"| main
    UI -->|"onSaveEvent"| main
    main -->|"Editor.getValue()"| Editor
    Editor -->|text| trimText
    trimText -->|uses| searchReplace
    trimText -->|uses| cursorFence
    trimText -->|result| main
    main -->|"Editor.replace()"| Editor
    main -->|"openSettingsUI()"| settings
    settings -->|saveSettings| storage
    settings -->|loadSettings| storage

    %% Testing
    trimTextTest --> trimText
    trimTextTest --> searchReplace
    trimTextTest --> cursorFence

    %% Build/Release
    manifest & package -->|defines| main
    tsconfig & jestConfig -->|build/test config| main
    versionScript -->|updates versions.json| versions
    ciWorkflow -->|publishes release| versions & changelog

    %% Click Events
    click main "https://github.com/zlovatt/obsidian-trim-whitespace/blob/main/src/main.ts"
    click settings "https://github.com/zlovatt/obsidian-trim-whitespace/blob/main/src/settings.ts"
    click trimText "https://github.com/zlovatt/obsidian-trim-whitespace/blob/main/src/utils/trimText.ts"
    click searchReplace "https://github.com/zlovatt/obsidian-trim-whitespace/blob/main/src/utils/searchReplaceTokens.ts"
    click cursorFence "https://github.com/zlovatt/obsidian-trim-whitespace/blob/main/src/utils/getCursorFenceIndices.ts"
    click manifest "https://github.com/zlovatt/obsidian-trim-whitespace/blob/main/manifest.json"
    click package "https://github.com/zlovatt/obsidian-trim-whitespace/blob/main/package.json"
    click tsconfig "https://github.com/zlovatt/obsidian-trim-whitespace/blob/main/tsconfig.json"
    click jestConfig "https://github.com/zlovatt/obsidian-trim-whitespace/blob/main/jest.config.js"
    click trimTextTest "https://github.com/zlovatt/obsidian-trim-whitespace/blob/main/test/utils/trimText.test.ts"
    click versionScript "https://github.com/zlovatt/obsidian-trim-whitespace/blob/main/scripts/set-versions.mjs"
    click ciWorkflow "https://github.com/zlovatt/obsidian-trim-whitespace/blob/main/.github/workflows/release.yml"
    click versions "https://github.com/zlovatt/obsidian-trim-whitespace/blob/main/versions.json"
    click changelog "https://github.com/zlovatt/obsidian-trim-whitespace/blob/main/changelog.md"
    click typings "https://github.com/zlovatt/obsidian-trim-whitespace/blob/main/typings/index.d.ts"

    %% Styles
    classDef host fill:#D0E6FF,stroke:#333,stroke-width:1px
    classDef core fill:#D0FFD6,stroke:#333,stroke-width:1px
    classDef utils fill:#E8FFDE,stroke:#333,stroke-width:1px
    classDef storage fill:#FFF7D6,stroke:#333,stroke-width:1px,stroke-dasharray: 5 5
    classDef build fill:#E0E0E0,stroke:#333,stroke-width:1px,stroke-dasharray: 2 2
```

-----

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