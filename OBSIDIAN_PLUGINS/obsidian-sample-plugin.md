---
created: 2025-07-01 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/obsidianmd/obsidian-sample-plugin
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




# obsidian-sample-plugin repo project by obsidianmd
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
title: "obsidian-sample-plugin repo project by obsidianmd"
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
flowchart LR
    %% Host Application Layer
    subgraph "Host Application"
        O["Obsidian Core"]:::host
        PL["Plugin Loader"]:::host
    end

    %% External API Definitions
    API["obsidian.d.ts"]:::external

    %% Plugin Package
    subgraph "Sample Plugin Package"
        MP["manifest.json"]:::plugin
        MT["main.ts"]:::plugin
        SC["styles.css"]:::plugin
        subgraph "Plugin Runtime Features"
            RIB["Ribbon Icon Handler"]:::plugin
            CMD["Command: Open Sample Modal"]:::plugin
            MOD["Modal Window"]:::plugin
            SET["Settings UI"]:::plugin
            EV["Global Event Handler"]:::plugin
            INT["Interval Logger"]:::plugin
        end
    end

    %% Developer Toolchain
    subgraph "Developer Toolchain"
        NPM["Node.js / npm"]:::dev
        ESB["esbuild.config.mjs"]:::dev
        TS["tsconfig.json"]:::dev
        PKG["package.json"]:::dev
        VBS["version-bump.mjs"]:::dev
        VRS["versions.json"]:::dev
        RMD["README.md"]:::dev
        ESLRC[".eslintrc"]:::dev
        ESLIG[".eslintignore"]:::dev
        EDCFG[".editorconfig"]:::dev
    end

    %% Relationships
    O -->|"discovers/plugins"| PL
    PL -->|"load() lifecycle"| MT
    PL --> MP
    PL --> SC
    MT --> RIB
    MT --> CMD
    CMD --> MOD
    SET -->|"reads/writes"| MT
    EV -->|"listens to"| API
    INT -->|"calls"| API

    API -.->|API Definitions| MT

    %% Build Pipeline
    ESB -->|"bundle"| SC
    ESB -->|"bundle"| MT
    TS -->|"compile"| MT
    PKG -->|"scripts"| NPM
    NPM -->|"runs"| ESB
    NPM -->|"runs"| TS
    VBS -->|"updates"| VRS
    RMD -->|"docs for"| MT

    %% Styles
    classDef host fill:#d3d3d3,stroke:#333,stroke-width:1px;
    classDef plugin fill:#add8e6,stroke:#333,stroke-width:1px;
    classDef dev fill:#90ee90,stroke:#333,stroke-width:1px;
    classDef external fill:#f4a460,stroke:#333,stroke-width:1px;

    %% Click Events
    click MP "https://github.com/obsidianmd/obsidian-sample-plugin/blob/master/manifest.json"
    click MT "https://github.com/obsidianmd/obsidian-sample-plugin/blob/master/main.ts"
    click SC "https://github.com/obsidianmd/obsidian-sample-plugin/blob/master/styles.css"
    click ESB "https://github.com/obsidianmd/obsidian-sample-plugin/blob/master/esbuild.config.mjs"
    click TS "https://github.com/obsidianmd/obsidian-sample-plugin/blob/master/tsconfig.json"
    click PKG "https://github.com/obsidianmd/obsidian-sample-plugin/blob/master/package.json"
    click VBS "https://github.com/obsidianmd/obsidian-sample-plugin/blob/master/version-bump.mjs"
    click VRS "https://github.com/obsidianmd/obsidian-sample-plugin/blob/master/versions.json"
    click RMD "https://github.com/obsidianmd/obsidian-sample-plugin/blob/master/README.md"
    click ESLRC "https://github.com/obsidianmd/obsidian-sample-plugin/blob/master/.eslintrc"
    click ESLIG "https://github.com/obsidianmd/obsidian-sample-plugin/blob/master/.eslintignore"
    click EDCFG "https://github.com/obsidianmd/obsidian-sample-plugin/blob/master/.editorconfig"
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