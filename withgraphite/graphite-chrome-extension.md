---
created: 2025-06-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/withgraphite/graphite-chrome-extension
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




# graphite-chrome-extension repo project
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


----

```mermaid
---
title: "graphite-chrome-extension repo project"
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
    %% Browser Environment
    subgraph "Browser Environment"
        subgraph "Extension Host"
            ContentScript["Content Script"]:::internal
            BackgroundScript["Background Script"]:::internal
            Storage[(Browser Storage)]:::storage
            Manifest["Manifest & Static Assets"]:::internal
        end
        GitHubDOM["GitHub PR Page (DOM)"]:::external
    end

    %% External Service
    GraphiteAPI["Graphite Backend API"]:::external

    %% Build and Config
    subgraph "Config & Build Tools"
        PackageJson["package.json"]:::build
        Tsconfig["tsconfig.json"]:::build
        Eslint[".eslintrc"]:::build
        Yarn[".yarn/"]:::build
        Esbuild["Build Pipeline (esbuild)"]:::build
    end

    %% Relationships
    ContentScript -->|"chrome.runtime.sendMessage"| BackgroundScript
    BackgroundScript -->|"chrome.storage.local.set/get"| Storage
    ContentScript <-->|"DOM queries & events"| GitHubDOM
    BackgroundScript -->|"fetch POST/GET"| GraphiteAPI
    Esbuild -->|"bundles & packages"| ContentScript
    Esbuild -->|"bundles & packages"| BackgroundScript
    Esbuild -->|"includes manifest & assets"| Manifest
    PackageJson --> Esbuild
    Tsconfig --> Esbuild
    Eslint --> Esbuild
    Yarn --> Esbuild

    %% Click Events
    click ContentScript "https://github.com/withgraphite/graphite-chrome-extension/blob/main/src/pr-content-script.ts"
    click BackgroundScript "https://github.com/withgraphite/graphite-chrome-extension/blob/main/src/background.ts"
    click Manifest "https://github.com/withgraphite/graphite-chrome-extension/blob/main/public/manifest.json"
    click Esbuild "https://github.com/withgraphite/graphite-chrome-extension/blob/main/scripts/esbuild.js"
    click Tsconfig "https://github.com/withgraphite/graphite-chrome-extension/blob/main/tsconfig.json"
    click Eslint "https://github.com/withgraphite/graphite-chrome-extension/blob/main/.eslintrc"
    click Yarn "https://github.com/withgraphite/graphite-chrome-extension/tree/main/.yarn/"
    click PackageJson "https://github.com/withgraphite/graphite-chrome-extension/blob/main/package.json"

    %% Styles
    classDef internal fill:#D0E8FF,stroke:#000,stroke-width:1px
    classDef external fill:#D5E8D4,stroke:#000,stroke-width:1px
    classDef build fill:#FFF2CC,stroke:#000,stroke-width:1px
    classDef storage fill:#FFE599,stroke:#000,stroke-width:1px

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