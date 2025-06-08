---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ipfs/service-worker-gateway
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExd3VwcHgzZWxnbTc3eWUwd2NpdnEwem9wdWVxemZ1eDE1aHpmZmlhdSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/N35rW3vRNeaDC/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# service-worker-gateway repo project
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
title: "service-worker-gateway repo project"
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
flowchart TB
    %% Frontend Layer
    subgraph "Frontend: Browser"
        direction TB
        IndexHTML["public/index.html"]:::frontend
        ReactApp["React SPA (src/app.tsx)"]:::frontend
        SWRegister["SW Registration (src/ipfs-sw-first-hit.ts)"]:::frontend
    end

    %% Service Worker Layer
    subgraph "Service Worker"
        direction TB
        SWCore["SW Core (src/sw.ts)"]:::sw
        Utils["SW Utils (src/service-worker-utils.ts)"]:::sw
        Helia["Helia IPFS Node"]:::sw
        VF["Verified-Fetch (src/lib/get-verified-fetch.ts)"]:::sw
        Routing["Routing & Gateway Logic"]:::sw
        ConfigDB["Config & Storage (src/lib/config-db.ts)"]:::sw
    end

    %% Backend Layer
    subgraph "Backend: Static Server / Reverse Proxy"
        direction TB
        NodeServe["Node Server (serve.ts / build.js)"]:::backend
        GoServer["Go Server (main.go)"]:::backend
        PublicAssets["Public Assets (public/)"]:::backend
    end

    %% External Systems
    subgraph "External Systems"
        direction TB
        IPFSP2P["IPFS P2P Network"]:::external
        HTTPGW["HTTP Gateways"]:::external
        CI["CI/CD Pipeline (.github/workflows/)"]:::external
    end

    %% Data Flows
    ReactApp -->|"register SW"| SWRegister
    ReactApp -->|"GET /"| NodeServe
    NodeServe -->|"serves index.html & bundles"| IndexHTML
    GoServer -->|"serves assets & proxy"| PublicAssets
    NodeServe --> PublicAssets
    SWRegister -->|"activates"| SWCore
    SWCore --> VF
    VF --> Helia
    Helia --> IPFSP2P
    SWCore --> HTTPGW
    SWCore -->|"respond with content"| ReactApp
    ReactApp <-->|"postMessage: updateConfig"| SWCore
    NodeServe -->|"subdomain proxy requests"| GoServer
    CI --> ReactApp
    CI --> SWCore
    CI --> NodeServe
    CI --> GoServer

    %% Click Events
    click ReactApp "https://github.com/ipfs/service-worker-gateway/blob/main/src/app.tsx"
    click SWRegister "https://github.com/ipfs/service-worker-gateway/blob/main/src/ipfs-sw-first-hit.ts"
    click IndexHTML "https://github.com/ipfs/service-worker-gateway/blob/main/public/index.html"
    click SWCore "https://github.com/ipfs/service-worker-gateway/blob/main/src/sw.ts"
    click Utils "https://github.com/ipfs/service-worker-gateway/blob/main/src/service-worker-utils.ts"
    click VF "https://github.com/ipfs/service-worker-gateway/blob/main/src/lib/get-verified-fetch.ts"
    click ConfigDB "https://github.com/ipfs/service-worker-gateway/blob/main/src/lib/config-db.ts"

    %% Styles
    classDef frontend fill:#D0E8FF,stroke:#0366d6,color:#000
    classDef sw fill:#FFECD0,stroke:#D9822B,color:#000
    classDef backend fill:#D0FFD6,stroke:#237E2E,color:#000
    classDef external fill:#EDEDED,stroke:#888888,color:#000
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