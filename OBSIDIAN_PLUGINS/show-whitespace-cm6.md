---
created: 2025-07-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/ebullient/obsidian-show-whitespace-cm6
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




# show-whitespace-cm6 repo project by ebullient
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
title: "OBSIDIAN PLUGINS - ebullient - obsidian-show-whitespace-cm6 repo project"
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
    subgraph "Developer Machine"
        subgraph "Build Tools"
            ESBUILD["esbuild.config.mjs"]:::build
            BIOME["biome.json"]:::build
            TSCONFIG["tsconfig.json"]:::build
        end
        DEV_SRCS["TypeScript & SCSS Source"]:::build
        ESBUILD & BIOME & TSCONFIG & DEV_SRCS --> BUNDLE["bundle.js & style.css"]:::build
    end

    subgraph "CI/CD Workflows"
        BUILDYML[".github/workflows/build.yml"]:::build
        RELEASEYML[".github/workflows/release.yml"]:::build
    end

    subgraph "Obsidian Host"
        HOST["Obsidian Host (Electron)"]:::host
        META1["manifest.json"]:::host
        META2["manifest-beta.json"]:::host
        HOST --> META1
        HOST --> META2
        META1 & META2 & BUNDLE --> PLUGIN_LOADER["Plugin Loader"]:::host
    end

    subgraph "Show-Whitespace Plugin"
        ENTRY["main.ts (Plugin Entry)"]:::plugin
        PLUGIN_MOD["whitespace-Plugin.ts"]:::plugin
        SETTINGS["whitespace-SettingsTab.ts"]:::plugin
        STYLES["styles.scss (CSS Injector)"]:::plugin
        I18NIDX["i18n/index.ts"]:::plugin
        I18NEN["i18n/en.ts"]:::plugin
        TYPES["@types/settings.d.ts"]:::plugin
    end

    PLUGIN_LOADER --> ENTRY
    ENTRY --> PLUGIN_MOD
    ENTRY --> SETTINGS
    ENTRY --> STYLES
    ENTRY --> I18NIDX
    I18NIDX --> I18NEN
    SETTINGS -->|"reads/writes"| STORE["Persistent Settings Store"]:::store
    PLUGIN_MOD --> CODEMIRROR["CodeMirror 6 Engine"]:::engine
    STYLES --> EDITOR_DOM["Editor DOM"]:::host

    click ESBUILD "https://github.com/ebullient/obsidian-show-whitespace-cm6/blob/main/esbuild.config.mjs"
    click BIOME "https://github.com/ebullient/obsidian-show-whitespace-cm6/blob/main/biome.json"
    click TSCONFIG "https://github.com/ebullient/obsidian-show-whitespace-cm6/blob/main/tsconfig.json"
    click BUNDLE "https://github.com/ebullient/obsidian-show-whitespace-cm6/blob/main/src/styles.scss"
    click META1 "https://github.com/ebullient/obsidian-show-whitespace-cm6/blob/main/manifest.json"
    click META2 "https://github.com/ebullient/obsidian-show-whitespace-cm6/blob/main/manifest-beta.json"
    click ENTRY "https://github.com/ebullient/obsidian-show-whitespace-cm6/blob/main/src/main.ts"
    click PLUGIN_MOD "https://github.com/ebullient/obsidian-show-whitespace-cm6/blob/main/src/whitespace-Plugin.ts"
    click SETTINGS "https://github.com/ebullient/obsidian-show-whitespace-cm6/blob/main/src/whitespace-SettingsTab.ts"
    click STYLES "https://github.com/ebullient/obsidian-show-whitespace-cm6/blob/main/src/styles.scss"
    click I18NIDX "https://github.com/ebullient/obsidian-show-whitespace-cm6/blob/main/src/i18n/index.ts"
    click I18NEN "https://github.com/ebullient/obsidian-show-whitespace-cm6/blob/main/src/i18n/en.ts"
    click TYPES "https://github.com/ebullient/obsidian-show-whitespace-cm6/blob/main/src/@types/settings.d.ts"
    click BUILDYML "https://github.com/ebullient/obsidian-show-whitespace-cm6/blob/main/.github/workflows/build.yml"
    click RELEASEYML "https://github.com/ebullient/obsidian-show-whitespace-cm6/blob/main/.github/workflows/release.yml"

    classDef build fill:#aedff7,stroke:#000
    classDef plugin fill:#c2f7a4,stroke:#000
    classDef host fill:#f7d6a4,stroke:#000
    classDef engine fill:#fe68c,stroke:#000
    classDef store fill:#cccccc,stroke:#000


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