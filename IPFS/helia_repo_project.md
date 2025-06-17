---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ipfs/helia
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


# helia repo project
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
title: "helia repo project"
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
  %% Consumer
  subgraph "Consumer"
    U["User/Application"]
  end

  %% Supplemental Modules
  subgraph "Supplemental Modules" 
    M1["@helia/unixfs"]:::module
    M2["@helia/ipns"]:::module
    M3["@helia/dag-json"]:::module
    M4["@helia/dag-cbor"]:::module
    M5["@helia/car"]:::module
    M6["@helia/mfs"]:::module
    M7["@helia/strings"]:::module
    M8["@helia/json"]:::module
    M9["@helia/routers"]:::module
  end

  %% Helia Core
  subgraph "Helia Core" 
    IF["packages/interface"]:::core
    H1["packages/helia"]:::core
    H2["packages/http"]:::core
    DS["Datastore"]:::core
    BS["Blockstore"]:::core
    BB["BlockBrokers"]:::core
    BS1["Bitswap"]:::core
    TG["TrustlessGateways"]:::core
    subgraph "libp2p & Protocols"
      LP["libp2p"]:::core
      DHT["DHT"]:::core
      PubSub["PubSub"]:::core
      IPNI["IPNI"]:::core
      Reframe["Reframe"]:::core
    end
  end

  %% External Systems
  subgraph "External Systems"
    Storage["LevelDB/FS/IDB/S3"]:::external
    Network["Network (P2P)"]:::external
  end

  %% Interop Tests
  IT["Interop Test Suite"]:::module

  %% Connections
  U -->|uses| M1
  U -->|uses| M2
  U -->|uses| M3
  U -->|uses| M4
  U -->|uses| M5
  U -->|uses| M6
  U -->|uses| M7
  U -->|uses| M8
  U -->|uses| M9

  M1 -->|calls| IF
  M2 -->|calls| IF
  M3 -->|calls| IF
  M4 -->|calls| IF
  M5 -->|calls| IF
  M6 -->|calls| IF
  M7 -->|calls| IF
  M8 -->|calls| IF
  M9 -->|calls| IF

  IF -->|implements| H1
  IF -->|implements| H2

  H1 -->|uses| DS
  H1 -->|uses| BS
  H2 -->|fallback for| BS

  DS -->|store metadata| Storage
  BS -->|delegates| BB

  BB -->|p2p| BS1
  %% BB -.fallback.->|http| TG

  BS1 -->|over| LP
  TG -->|reads/writes| Storage

  LP --> DHT
  LP --> PubSub
  LP --> IPNI
  LP --> Reframe

  DHT -->|network| Network
  PubSub -->|network| Network
  IPNI -->|network| Network
  Reframe -->|network| Network

  IT -->|tests| IF
  IT -->|tests| H1
  IT -->|tests| H2

  %% Click Events
  click IF "https://github.com/ipfs/helia/tree/main/packages/interface"
  click H1 "https://github.com/ipfs/helia/tree/main/packages/helia"
  click H2 "https://github.com/ipfs/helia/tree/main/packages/http"
  click BB "https://github.com/ipfs/helia/tree/main/packages/block-brokers"
  click BS1 "https://github.com/ipfs/helia/tree/main/packages/bitswap"
  click TG "https://github.com/ipfs/helia/tree/main/packages/block-brokers/src/trustless-gateway"
  click DS "https://github.com/ipfs/helia/blob/main/packages/utils/src/storage.ts"
  click BS "https://github.com/ipfs/helia/blob/main/packages/interface/src/blocks.ts"
  click LP "https://github.com/ipfs/helia/blob/main/packages/helia/src/utils/libp2p.ts"
  click LP "https://github.com/ipfs/helia/blob/main/packages/helia/src/utils/libp2p-defaults.browser.ts"
  click LP "https://github.com/ipfs/helia/blob/main/packages/helia/src/utils/libp2p-defaults.ts"
  click LP "https://github.com/ipfs/helia/blob/main/packages/helia/src/helia-p2p.ts"
  click M1 "https://github.com/ipfs/helia/tree/main/packages/unixfs"
  click M2 "https://github.com/ipfs/helia/tree/main/packages/ipns"
  click M3 "https://github.com/ipfs/helia/tree/main/packages/dag-json"
  click M4 "https://github.com/ipfs/helia/tree/main/packages/dag-cbor"
  click M5 "https://github.com/ipfs/helia/tree/main/packages/car"
  click M6 "https://github.com/ipfs/helia/tree/main/packages/mfs"
  click M7 "https://github.com/ipfs/helia/tree/main/packages/strings"
  click M8 "https://github.com/ipfs/helia/tree/main/packages/json"
  click M9 "https://github.com/ipfs/helia/tree/main/packages/routers"
  click IT "https://github.com/ipfs/helia/tree/main/packages/interop"

  %% Styles
  classDef core fill:#2196f3,stroke:#000,color:#fff
  classDef module fill:#4caf50,stroke:#000,color:#fff
  classDef external fill:#9e9e9e,stroke:#000,color:#fff
  %% class DS,BB,TG stroke-dasharray: 5 5
  %% class TG dashed external
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