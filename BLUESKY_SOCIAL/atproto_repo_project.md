---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/bluesky-social/atproto
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




# atproto repo project
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
title: "atproto repo project"
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
flowchart TD
    %% External & Client Layer
    subgraph "External & Client Layer"
        EC["External Clients (Web/Mobile)"]:::client
        API["API Library (@atproto/api)"]:::client
        XRPC_CLIENT["XRPC Client (@atproto/xrpc)"]:::client
        XRPC_SERVER["XRPC Server (@atproto/xrpc-server)"]:::library
    end

    EC -->|"APIcalls"| API
    API -->|"uses"| XRPC_CLIENT
    XRPC_CLIENT -->|"calls"| XRPC_SERVER

    %% Core Packages
    subgraph "Core Packages"
        COMMON["Common (@atproto/common)"]:::library
        COMMON_WEB["Common-Web (@atproto/common-web)"]:::library
        CRYPTO["Crypto (@atproto/crypto)"]:::library
        IDENTITY["Identity (@atproto/identity)"]:::library
        LEXICON["Lexicon (@atproto/lexicon)"]:::library
        REPO["Repo (@atproto/repo)"]:::library
        SYNTAX["Syntax (@atproto/syntax)"]:::library
    end

    %% Service Layers
    subgraph "Service Layers"
        %% PDS Service
        subgraph "PDS Service"
            PDS_CORE["PDS Core (packages/pds)"]:::service
            PDS_WRAPPER["PDS Wrapper (services/pds)"]:::service
            PDS_CORE --> PDS_WRAPPER
        end
        %% Bsky Service
        subgraph "Bsky Service"
            BSKY_CORE["Bsky Core (packages/bsky)"]:::service
            BSKY_WRAPPER["Bsky Wrapper (services/bsky)"]:::service
            BSKY_CORE --> BSKY_WRAPPER
        end
        %% Bsync Service
        subgraph "Bsync Service"
            BSYNC_CORE["Bsync Core (packages/bsync)"]:::service
            BSYNC_WRAPPER["Bsync Wrapper (services/bsync)"]:::service
            BSYNC_CORE --> BSYNC_WRAPPER
        end
        %% Ozone Service
        subgraph "Ozone Service"
            OZONE_CORE["Ozone Core (packages/ozone)"]:::service
            OZONE_WRAPPER["Ozone Wrapper (services/ozone)"]:::service
            OZONE_CORE --> OZONE_WRAPPER
        end
    end

    %% Schemas & Tests
    subgraph "Schemas & Tests"
        LEXICONS["Lexicons (Schemas)"]:::schema
        INTEROP["Interop Test Files"]:::schema
    end

    %% Infrastructure
    INFRA["CI/CD & Docker"]:::infra

    %% Relationships between layers
    XRPC_SERVER -->|"exposes"| PDS_WRAPPER
    XRPC_SERVER -->|"exposes"| BSKY_WRAPPER
    XRPC_SERVER -->|"exposes"| BSYNC_WRAPPER
    XRPC_SERVER -->|"exposes"| OZONE_WRAPPER

    %% Service wrappers using core libraries
    PDS_WRAPPER ---|"uses"| CRYPTO
    PDS_WRAPPER ---|"uses"| IDENTITY
    PDS_WRAPPER ---|"uses"| REPO
    PDS_WRAPPER ---|"validatesWith"| LEXICON

    BSKY_WRAPPER ---|"uses"| CRYPTO
    BSKY_WRAPPER ---|"uses"| IDENTITY
    BSKY_WRAPPER ---|"uses"| REPO
    BSKY_WRAPPER ---|"validatesWith"| LEXICON

    BSYNC_WRAPPER ---|"uses"| CRYPTO
    BSYNC_WRAPPER ---|"uses"| IDENTITY
    BSYNC_WRAPPER ---|"uses"| REPO
    BSYNC_WRAPPER ---|"validatesWith"| LEXICON

    OZONE_WRAPPER ---|"uses"| CRYPTO
    OZONE_WRAPPER ---|"uses"| IDENTITY
    OZONE_WRAPPER ---|"uses"| REPO
    OZONE_WRAPPER ---|"validatesWith"| LEXICON

    %% Lexicon relation to schemas
    LEXICON -->|"defines"| LEXICONS
    INTEROP -->|"tests"| LEXICONS

    %% Infrastructure supports the entire system
    INFRA ---|"build/deploy"| EC
    INFRA ---|"build/deploy"| API
    INFRA ---|"build/deploy"| XRPC_SERVER
    INFRA ---|"build/deploy"| PDS_WRAPPER
    INFRA ---|"build/deploy"| BSKY_WRAPPER
    INFRA ---|"build/deploy"| BSYNC_WRAPPER
    INFRA ---|"build/deploy"| OZONE_WRAPPER

    %% Class Definitions
    classDef library fill:#cce5ff,stroke:#004085,stroke-width:2px;
    classDef service fill:#d4edda,stroke:#155724,stroke-width:2px;
    classDef schema fill:#fff3cd,stroke:#856404,stroke-width:2px;
    classDef infra fill:#d1ecf1,stroke:#0c5460,stroke-width:2px;
    classDef client fill:#f8d7da,stroke:#721c24,stroke-width:2px;

    %% Click Events
    click API "https://github.com/bluesky-social/atproto/tree/main/packages/api"
    click COMMON "https://github.com/bluesky-social/atproto/tree/main/packages/common"
    click COMMON_WEB "https://github.com/bluesky-social/atproto/tree/main/packages/common-web"
    click CRYPTO "https://github.com/bluesky-social/atproto/tree/main/packages/crypto"
    click IDENTITY "https://github.com/bluesky-social/atproto/tree/main/packages/identity"
    click LEXICON "https://github.com/bluesky-social/atproto/tree/main/packages/lexicon"
    click REPO "https://github.com/bluesky-social/atproto/tree/main/packages/repo"
    click SYNTAX "https://github.com/bluesky-social/atproto/tree/main/packages/syntax"
    click XRPC_CLIENT "https://github.com/bluesky-social/atproto/tree/main/packages/xrpc"
    click XRPC_SERVER "https://github.com/bluesky-social/atproto/tree/main/packages/xrpc-server"
    click PDS_CORE "https://github.com/bluesky-social/atproto/tree/main/packages/pds"
    click PDS_WRAPPER "https://github.com/bluesky-social/atproto/tree/main/services/pds"
    click BSKY_CORE "https://github.com/bluesky-social/atproto/tree/main/packages/bsky"
    click BSKY_WRAPPER "https://github.com/bluesky-social/atproto/tree/main/services/bsky"
    click BSYNC_CORE "https://github.com/bluesky-social/atproto/tree/main/packages/bsync"
    click BSYNC_WRAPPER "https://github.com/bluesky-social/atproto/tree/main/services/bsync"
    click OZONE_CORE "https://github.com/bluesky-social/atproto/tree/main/packages/ozone"
    click OZONE_WRAPPER "https://github.com/bluesky-social/atproto/tree/main/services/ozone"
    click LEXICONS "https://github.com/bluesky-social/atproto/tree/main/lexicons"
    click INTEROP "https://github.com/bluesky-social/atproto/tree/main/interop-test-files"
    click INFRA "https://github.com/bluesky-social/atproto/blob/main/pnpm-workspace.yaml"
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