---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ipfs/boxo
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExaHNwdmJteDFidGlyMnE4MHFiYnU3ZG05dnQ1eHY5NDQ4dnlzNmtzdCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/qc5fbrb4qpupRA9r4o/giphy.gif)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# boxo repo project
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
title: "boxo repo project"
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
    %% Layer 1: Applications
    subgraph "Layer 1: Applications" 
        direction TB
        App["Custom Application"]:::frontend
        CLI1["CLI: boxo-migrate"]:::frontend
        CLI2["CLI: deprecator"]:::frontend
        Examples["Examples"]:::frontend
    end

    %% Layer 2: Facade
    subgraph "Layer 2: Boxo SDK Façade"
        direction TB
        BoxoFacade["Boxo SDK Facade"]:::facade
    end

    %% Layer 3: Protocol Modules
    subgraph "Layer 3: Protocol Modules"
        direction TB
        bitswap["Bitswap"]:::module
        routingHttp["Routing HTTP"]:::module
        routingOffline["Routing Offline"]:::module
        ipns["IPNS"]:::module
        namesys["Namesys"]:::module
        provider["Provider & Reprovider"]:::module
        exchangeOffline["Exchange Offline"]:::module
        pinner["Pinning: Pinner"]:::module
        pinnerRemote["Pinning: Remote"]:::module
        fetcher["Fetcher"]:::module
        chunker["Chunker"]:::module
        verifcid["Verifcid"]:::module
    end

    %% Layer 4: Data Layers
    subgraph "Layer 4: Data Layers"
        direction TB
        blockservice["BlockService"]:::data
        blockstore["Blockstore"]:::data
        datastore["Datastore"]:::data
        filestore["Filestore"]:::data
        merkledag["IPLD Merkle DAG"]:::data
        unixfs["IPLD UnixFS"]:::data
    end

    %% Layer 5: External Systems
    subgraph "Layer 5: External Systems"
        direction TB
        IPFSNetwork["IPFS Network Peers"]:::external
        DHT["DHT"]:::external
        HTTPGateway["HTTP Gateway Service"]:::external
        UnderlyingDS["Underlying Datastore"]:::external
    end

    %% Utilities/Internal
    subgraph "Internal Utilities"
        direction TB
        util["Util"]:::util
        tracing["Tracing"]:::util
        keystore["Keystore"]:::util
        mfs["MFS"]:::util
        files["Files"]:::util
        tar["Tar"]:::util
        path["Path Resolver"]:::util
        peering["Peering"]:::util
    end

    %% CLI & Examples to Facade
    App -->|uses| BoxoFacade
    CLI1 -->|uses| BoxoFacade
    CLI2 -->|uses| BoxoFacade
    Examples -->|uses| BoxoFacade

    %% Facade to Modules
    BoxoFacade --> bitswap
    BoxoFacade --> routingHttp
    BoxoFacade --> routingOffline
    BoxoFacade --> ipns
    BoxoFacade --> namesys
    BoxoFacade --> provider
    BoxoFacade --> exchangeOffline
    BoxoFacade --> pinner
    BoxoFacade --> pinnerRemote
    BoxoFacade --> fetcher
    BoxoFacade --> chunker
    BoxoFacade --> verifcid

    %% Data flows
    bitswap -->|fetches blocks| blockservice
    bitswap -->|sync| IPFSNetwork
    blockservice --> blockstore
    blockstore --> datastore
    blockstore --> filestore
    blockservice --> merkledag
    merkledag --> unixfs
    unixfs --> chunker

    %% Naming and Routing
    ipns --> namesys
    namesys --> DHT
    provider --> DHT
    exchangeOffline --> provider

    %% Pinning
    pinner --> blockstore
    pinnerRemote -->|remote API| blockstore

    %% Gateway
    HTTPGateway -->|HTTP requests| gatewayHandler["Gateway Handler"]:::module
    gatewayHandler --> blockservice
    gatewayHandler --> unixfs

    %% Utilities usage
    BoxoFacade --> util
    BoxoFacade --> tracing
    BoxoFacade --> keystore
    BoxoFacade --> mfs
    BoxoFacade --> files
    BoxoFacade --> tar
    BoxoFacade --> path
    BoxoFacade --> peering

    %% External datastore
    datastore --> UnderlyingDS

    %% Click Events
    click bitswap "https://github.com/ipfs/boxo/tree/main/bitswap/"
    click blockservice "https://github.com/ipfs/boxo/tree/main/blockservice/"
    click blockstore "https://github.com/ipfs/boxo/tree/main/blockstore/"
    click datastore "https://github.com/ipfs/boxo/tree/main/datastore/"
    click merkledag "https://github.com/ipfs/boxo/tree/main/ipld/merkledag/"
    click unixfs "https://github.com/ipfs/boxo/tree/main/ipld/unixfs/"
    click chunker "https://github.com/ipfs/boxo/tree/main/chunker/"
    click ipns "https://github.com/ipfs/boxo/tree/main/ipns/"
    click namesys "https://github.com/ipfs/boxo/tree/main/namesys/"
    click path "https://github.com/ipfs/boxo/tree/main/path/"
    click routingHttp "https://github.com/ipfs/boxo/tree/main/routing/http/"
    click routingOffline "https://github.com/ipfs/boxo/tree/main/routing/offline/"
    click provider "https://github.com/ipfs/boxo/tree/main/provider/"
    click exchangeOffline "https://github.com/ipfs/boxo/tree/main/exchange/offline/"
    click fetcher "https://github.com/ipfs/boxo/tree/main/fetcher/"
    click files "https://github.com/ipfs/boxo/tree/main/files/"
    click filestore "https://github.com/ipfs/boxo/tree/main/filestore/"
    click tar "https://github.com/ipfs/boxo/tree/main/tar/"
    click keystore "https://github.com/ipfs/boxo/tree/main/keystore/"
    click mfs "https://github.com/ipfs/boxo/tree/main/mfs/"
    click pinner "https://github.com/ipfs/boxo/tree/main/pinning/pinner/"
    click pinnerRemote "https://github.com/ipfs/boxo/tree/main/pinning/remote/"
    click peering "https://github.com/ipfs/boxo/tree/main/peering/"
    click gatewayHandler "https://github.com/ipfs/boxo/tree/main/gateway/"
    click tracing "https://github.com/ipfs/boxo/tree/main/tracing/"
    click util "https://github.com/ipfs/boxo/tree/main/util/"
    click verifcid "https://github.com/ipfs/boxo/tree/main/verifcid/"
    click CLI1 "https://github.com/ipfs/boxo/tree/main/cmd/boxo-migrate/"
    click CLI2 "https://github.com/ipfs/boxo/tree/main/cmd/deprecator/"
    click Examples "https://github.com/ipfs/boxo/tree/main/examples/"

    %% Styles
    classDef frontend fill:#FFDDAA,stroke:#333,stroke-width:1px
    classDef facade fill:#CCE5FF,stroke:#333,stroke-width:1px
    classDef module fill:#CCFFCC,stroke:#333,stroke-width:1px
    classDef data fill:#FFCCFF,stroke:#333,stroke-width:1px
    classDef external fill:#EEEECC,stroke:#333,stroke-width:1px
    classDef util fill:#FFF2CC,stroke:#333,stroke-width:1px
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