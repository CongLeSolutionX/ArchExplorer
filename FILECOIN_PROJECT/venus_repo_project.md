---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/filecoin-project/venus
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExMnF2dWN0czd0djAwaHhrMGFpbTB2cnFtdTgwaGNlZWJjY2I3aXhrYyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/b4R6VJ3y942mHySNta/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# venus repo project
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
title: "venus repo project"
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
    subgraph "CLI Layer"
        CLI["CLI (cmd/)"]:::external
    end

    subgraph "API/Gateway"
        RPC["JSON-RPC Server"]:::api
        INS["Inspector API"]:::api
    end

    subgraph "Node Core"
        CORE["Core Loader & Registry"]:::core
        subgraph "Core Subsystems"
            CHAINSTORE["Chain Store"]:::storage
            CHAINSYNC["ChainSync"]:::core
            CONSENSUS["Consensus Engine"]:::core
            MSGPOOL["MessagePool"]:::core
            MARKET["Market Manager"]:::core
            PAYCH["Payment Channel Manager"]:::core
            WALLET["Wallet Manager"]:::core
            FVMRT["FVM Actor Runtime"]:::core
            VM["VM Dispatch & Runtime"]:::core
            NET["Network Stack"]:::network
            BEACON["Drand Beacon"]:::network
            CONFIG["Config & Repository"]:::storage
            METRIC["Metrics & Logging"]:::storage
            SHAPI["Shared API Definitions"]:::core
            SHACT["Shared Actors & Types"]:::core
            SHBS["Shared Blockstore & Datastore"]:::storage
            SHLP2P["Shared libp2p Exchange"]:::network
        end
    end

    cloud["P2P Network & Peers"]:::external
    FFI["Native Proof FFI Bindings"]:::native
    SCRIPTS["Dev Tools & Scripts"]:::external
    ASSETS["Fixtures & Assets"]:::storage

    CLI -->|calls RPC| RPC
    CLI -->|calls Inspector| INS
    RPC -->|invokes| CORE
    INS -->|invokes| CORE
    CORE --> CHAINSYNC
    CORE --> CONSENSUS
    CORE --> MSGPOOL
    CORE --> MARKET
    CORE --> PAYCH
    CORE --> WALLET
    CORE --> FVMRT
    CORE --> VM
    CORE --> NET
    CORE --> BEACON
    CORE --> CONFIG
    CORE --> METRIC
    CORE --> SHAPI
    CORE --> SHACT
    CORE --> SHBS
    CORE --> SHLP2P

    CHAINSYNC <--> CHAINSTORE
    CHAINSYNC <--> NET
    CONSENSUS --> FFI
    MSGPOOL <--> NET
    MARKET --> CHAINSTORE
    MARKET <--> NET
    PAYCH --> WALLET
    PAYCH --> CHAINSTORE
    FVMRT --> CHAINSTORE
    FVMRT --> VM
    VM --> CHAINSTORE
    NET <--> cloud
    BEACON --> cloud
    CONFIG --> ASSETS
    METRIC -->|"exports to Prometheus/Zap"| cloud
    SCRIPTS --> CLI

    click CLI "https://github.com/filecoin-project/venus/tree/master/cmd/"
    click RPC "https://github.com/filecoin-project/venus/blob/master/app/node/rpc.go"
    click INS "https://github.com/filecoin-project/venus/blob/master/app/node/inspector_api.go"
    click CORE "https://github.com/filecoin-project/venus/blob/master/app/node/builder.go"
    click CHAINSTORE "https://github.com/filecoin-project/venus/tree/master/pkg/chain/"
    click CHAINSYNC "https://github.com/filecoin-project/venus/tree/master/pkg/chainsync/"
    click CONSENSUS "https://github.com/filecoin-project/venus/tree/master/pkg/consensus/"
    click MSGPOOL "https://github.com/filecoin-project/venus/tree/master/pkg/messagepool/"
    click MARKET "https://github.com/filecoin-project/venus/tree/master/pkg/market/"
    click PAYCH "https://github.com/filecoin-project/venus/tree/master/pkg/paychmgr/"
    click WALLET "https://github.com/filecoin-project/venus/tree/master/pkg/wallet/"
    click FVMRT "https://github.com/filecoin-project/venus/tree/master/pkg/fvm/"
    click VM "https://github.com/filecoin-project/venus/tree/master/pkg/vm/"
    click NET "https://github.com/filecoin-project/venus/tree/master/pkg/net/"
    click BEACON "https://github.com/filecoin-project/venus/tree/master/pkg/beacon/"
    click CONFIG "https://github.com/filecoin-project/venus/tree/master/pkg/config/"
    click CONFIG "https://github.com/filecoin-project/venus/tree/master/pkg/repo/"
    click METRIC "https://github.com/filecoin-project/venus/tree/master/pkg/metrics/"
    click METRIC "https://github.com/filecoin-project/venus/tree/master/pkg/journal/"
    click SHAPI "https://github.com/filecoin-project/venus/tree/master/venus-shared/api/"
    click SHACT "https://github.com/filecoin-project/venus/tree/master/venus-shared/actors/"
    click SHACT "https://github.com/filecoin-project/venus/tree/master/venus-shared/types/"
    click SHBS "https://github.com/filecoin-project/venus/tree/master/venus-shared/blockstore/"
    click SHLP2P "https://github.com/filecoin-project/venus/tree/master/venus-shared/libp2p/exchange/"
    click FFI "https://github.com/filecoin-project/venus/tree/master/extern/filecoin-ffi/"
    click SCRIPTS "https://github.com/filecoin-project/venus/tree/master/venus-devtool/"
    click SCRIPTS "https://github.com/filecoin-project/venus/tree/master/scripts/"
    click ASSETS "https://github.com/filecoin-project/venus/tree/master/fixtures/assets/"

    classDef api fill:#bbdefb,stroke:#1e88e5
    classDef core fill:#c8e6c9,stroke:#388e3c
    classDef storage fill:#ffe0b2,stroke:#f57c00
    classDef network fill:#d1c4e9,stroke:#7e57c2
    classDef native fill:#fff59d,stroke:#fbc02d
    classDef external fill:#ef9a9a,stroke:#d32f2f
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