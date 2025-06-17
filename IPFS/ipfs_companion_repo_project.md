---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ipfs/ipfs-companion
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




# ipfs-companion repo project
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
title: "ipfs-companion repo project"
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
    %% Browser Extension Layer
    subgraph "Browser Extension" 
        direction TB
        BG["Background Script"]:::extComp
        CS["Content Script\n(linkifyDOM.js)"]:::extComp
        PU["Popup UI\n(browser-action)"]:::extComp
        QI["Quick-import Popup"]:::extComp
        OP["Options Page UI"]:::extComp
        LP["Landing Pages"]:::extComp
        LIB["Lib Modules"]:::extComp
        MAN["Manifest Files"]:::extComp
        ASSETS["_locales & Assets"]:::extComp
    end

    %% Local IPFS Services
    subgraph "Local IPFS Services"
        direction TB
        API["Local IPFS Daemon API\n(port 5001)"]:::local
        GW["Local IPFS Gateway\n(port 8080)"]:::local
    end

    %% External Network
    subgraph "External Network"
        direction TB
        DNS["DNSLink Resolver"]:::external
        PGW["Public Gateways"]:::external
        TEL["Telemetry Endpoint"]:::external
    end

    %% Dev & CI Tools
    subgraph "Dev & CI Tooling"
        direction TB
        BUILD["Webpack/Babel\nBundle"]:::dev
        TEST["Mocha/E2E & Functional Tests"]:::dev
        CI["CI Workflows"]:::dev
        SCRIPTS["Scripts"]:::dev
        DOCKER["Docker & Make"]:::dev
    end

    %% Relationships
    PU <-->|"message"| BG
    OP <-->|"message"| BG
    LP <-->|"navigation"| BG
    CS -->|"message"| BG
    BG -->|"HTTP API"| API
    BG -->|"Gateway Redirect"| GW
    DNS -->|"resolve IPNS"| BG
    BG -->|"DNSLink redirect"| GW
    LIB -->|"telemetry events"| TEL

    %% Build/Test pipelines
    BUILD -->|"produces"| BG
    TEST -->|"validates"| BG
    CI -->|"runs"| TEST
    CI -->|"runs"| BUILD
    SCRIPTS -->|"assist"| BUILD
    DOCKER -->|"env for"| TEST

    %% Click Events for component mapping
    click BG "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/background/background.js"
    click CS "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/contentScripts/linkifyDOM.js"
    click PU "https://github.com/ipfs/ipfs-companion/tree/main/add-on/src/popup/browser-action/"
    click QI "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/popup/quick-import.html"
    click QI "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/popup/quick-import.js"
    click QI "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/popup/quick-import.css"
    click ASSETS "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/popup/logo.js"
    click ASSETS "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/popup/heartbeat.css"
    click OP "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/options/options.html"
    click OP "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/options/options.js"
    click OP "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/options/options.css"
    click OP "https://github.com/ipfs/ipfs-companion/tree/main/add-on/src/options/forms/"
    click LP "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/landing-pages/permissions/request.html"
    click LP "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/landing-pages/permissions/request.js"
    click LP "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/landing-pages/permissions/request.css"
    click LP "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/landing-pages/welcome/index.html"
    click LP "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/landing-pages/welcome/index.js"
    click LP "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/landing-pages/welcome/page.js"
    click LP "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/landing-pages/welcome/store.js"
    click LIB "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/lib/ipfs-client/index.js"
    click LIB "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/lib/ipfs-client/brave.js"
    click LIB "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/lib/ipfs-client/external.js"
    click LIB "https://github.com/ipfs/ipfs-companion/tree/main/add-on/src/lib/redirect-handler/"
    click LIB "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/lib/state.js"
    click LIB "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/lib/telemetry.ts"
    click LIB "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/lib/context-menus/ContextMenus.ts"
    click LIB "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/lib/http-proxy.js"
    click LIB "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/lib/dnslink.js"
    click LIB "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/lib/ipfs-request.js"
    click LIB "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/lib/ipfs-path.js"
    click LIB "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/lib/notifier.js"
    click LIB "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/lib/on-installed.js"
    click LIB "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/lib/on-uninstalled.js"
    click LIB "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/lib/options.js"
    click LIB "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/lib/precache.js"
    click LIB "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/lib/copier.js"
    click LIB "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/lib/inspector.js"
    click LIB "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/lib/runtime-checks.js"
    click LIB "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/lib/ipfs-companion.js"
    click LIB "https://github.com/ipfs/ipfs-companion/blob/main/add-on/src/lib/ipfs-import.js"
    click MAN "https://github.com/ipfs/ipfs-companion/blob/main/add-on/manifest.common.json"
    click MAN "https://github.com/ipfs/ipfs-companion/blob/main/add-on/manifest.chromium.json"
    click MAN "https://github.com/ipfs/ipfs-companion/blob/main/add-on/manifest.firefox.json"
    click MAN "https://github.com/ipfs/ipfs-companion/blob/main/add-on/manifest.brave.json"
    click MAN "https://github.com/ipfs/ipfs-companion/blob/main/add-on/manifest.firefox-beta.json"
    click MAN "https://github.com/ipfs/ipfs-companion/blob/main/add-on/manifest.brave-beta.json"
    click ASSETS "https://github.com/ipfs/ipfs-companion/tree/main/add-on/_locales/"
    click ASSETS "https://github.com/ipfs/ipfs-companion/tree/main/add-on/icons/png/"
    click ASSETS "https://github.com/ipfs/ipfs-companion/tree/main/add-on/images/"
    click TEST "https://github.com/ipfs/ipfs-companion/blob/main/test/e2e/ipfs-companion.test.js"
    click TEST "https://github.com/ipfs/ipfs-companion/tree/main/test/functional/"
    click BUILD "https://github.com/ipfs/ipfs-companion/blob/main/.babelrc"
    click BUILD "https://github.com/ipfs/ipfs-companion/blob/main/webpack.config.js"
    click BUILD "https://github.com/ipfs/ipfs-companion/blob/main/tsconfig.json"
    click BUILD "https://github.com/ipfs/ipfs-companion/blob/main/package.json"
    click CI "https://github.com/ipfs/ipfs-companion/blob/main/.github/workflows/ci.yml"
    click CI "https://github.com/ipfs/ipfs-companion/blob/main/.github/workflows/e2e.yml"
    click CI "https://github.com/ipfs/ipfs-companion/blob/main/.github/workflows/generated-pr.yml"
    click CI "https://github.com/ipfs/ipfs-companion/blob/main/.github/workflows/stale.yml"
    click SCRIPTS "https://github.com/ipfs/ipfs-companion/tree/main/scripts/"
    click DOCKER "https://github.com/ipfs/ipfs-companion/tree/main/Dockerfile"
    click DOCKER "https://github.com/ipfs/ipfs-companion/blob/main/docker-compose.e2e.yml"
    click DOCKER "https://github.com/ipfs/ipfs-companion/tree/main/Makefile"

    %% Styles
    classDef extComp fill:#cce5ff,stroke:#2f6f9f,color:#000
    classDef local fill:#d4edda,stroke:#2f8f4f,color:#000
    classDef external fill:#e2e3e5,stroke:#6c757d,color:#000
    classDef dev fill:#fff3cd,stroke:#d39e00,color:#000
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