---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/web3.py
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExZ285cXdiaHlxZjc0NWd5b2o0MzBwdmI5djI5OWtxcmV0aXZpcGg0MyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/da1NBqrI3J91vkaXRu/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# web3.py repo project
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
title: "web3.py repo project"
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
    %% API Layer
    subgraph "API Layer"
        Web3["Web3 Client"]:::core
        Eth["Eth Module"]:::core
        Net["Net Module"]:::core
        Contract["Contract Module"]:::core
        Beacon["Beacon Module"]:::core
        Tracing["Tracing Module"]:::core
        Geth["Geth Module"]:::core
        Tools["Tools Module"]:::core
    end

    %% Middleware Layer
    subgraph "Middleware Layer"
        Formatting["Formatting Middleware"]:::core
        Signing["Signing Middleware"]:::core
        GasStrategy["Gas Price Strategy"]:::core
        BufferedGas["Buffered Gas Estimate"]:::core
        FilterMW["Filter Middleware"]:::core
        Name2Addr["Name-to-Address Middleware"]:::core
        POA["Proof-of-Authority Middleware"]:::core
        StaleCheck["Stale-Check Middleware"]:::core
        Validation["Validation Middleware"]:::core
        AttrDict["AttrDict Middleware"]:::core
    end

    %% Provider Layer
    subgraph "Provider Layer"
        BaseProvider["Base Provider"]:::pluggable
        HTTP["HTTPProvider"]:::pluggable
        IPC["IPCProvider"]:::pluggable
        WS["WebSocketProvider"]:::pluggable
        EthTester["EthTesterProvider"]:::pluggable
        Auto["Auto Provider"]:::pluggable
        Persistent["Persistent Connections"]:::pluggable
    end

    %% ENS Resolution
    subgraph "ENS Resolution"
        ENSPkg["ENS Package"]:::pluggable
        ENSUtils["ENS Utils"]:::pluggable
    end

    %% Utility Libraries
    subgraph "Utility Libraries"
        ABIEnc["ABI Encoding/Decoding"]:::core
        Caching["Caching Utilities"]:::core
        HTTPSess["HTTP Session Manager"]:::core
        Filters["Event/Filter Builder"]:::core
        TypeConv["Type Conversion & Validation"]:::core
    end

    %% External Systems
    EthereumNode(("Ethereum Node")):::external
    Offchain(("Offchain Resolver / IPFS")):::external

    %% Connections API -> Middleware
    Web3 -->|uses| Formatting
    Web3 -->|uses| Signing
    Web3 -->|uses| GasStrategy
    Web3 -->|uses| BufferedGas
    Web3 -->|uses| FilterMW
    Web3 -->|uses| Name2Addr
    Web3 -->|uses| POA
    Web3 -->|uses| StaleCheck
    Web3 -->|uses| Validation
    Web3 -->|uses| AttrDict

    %% Middleware chain flow
    Formatting --> Signing --> GasStrategy --> BufferedGas --> FilterMW --> Name2Addr --> POA --> StaleCheck --> Validation --> AttrDict --> BaseProvider

    %% ENS Integration
    ENSPkg -->|normalizes| Name2Addr
    ENSUtils -->|supports| Name2Addr

    %% Provider layer
    BaseProvider --> HTTP
    BaseProvider --> IPC
    BaseProvider --> WS
    BaseProvider --> EthTester
    BaseProvider --> Auto
    BaseProvider --> Persistent

    %% Provider to External
    HTTP -->|RPC/HTTP| EthereumNode
    IPC -->|IPC| EthereumNode
    WS -->|WebSocket| EthereumNode
    EthTester -->|Simulated Node| EthereumNode
    Auto -->|auto-select| EthereumNode
    Persistent -->|persistent conn| EthereumNode

    %% Utilities injection
    ABIEnc -->|encodes| Contract
    Caching -->|caches| BaseProvider
    HTTPSess -->|manages| HTTP
    Filters -->|builds| FilterMW
    TypeConv -->|validates| Validation

    %% API Modules usage
    Eth -->|api| Web3
    Net -->|api| Web3
    Contract -->|api| Web3
    Beacon -->|api| Web3
    Tracing -->|api| Web3
    Geth -->|api| Web3
    Tools -->|api| Web3

    %% External resolvers
    Name2Addr -->|offchain lookup| Offchain

    %% Click Events
    click Web3 "https://github.com/ethereum/web3.py/blob/main/web3/main.py"
    click Eth "https://github.com/ethereum/web3.py/blob/main/web3/eth/eth.py"
    click Eth "https://github.com/ethereum/web3.py/blob/main/web3/eth/base_eth.py"
    click Net "https://github.com/ethereum/web3.py/blob/main/web3/net.py"
    click Contract "https://github.com/ethereum/web3.py/blob/main/web3/contract/contract.py"
    click Contract "https://github.com/ethereum/web3.py/blob/main/web3/contract/base_contract.py"
    click Beacon "https://github.com/ethereum/web3.py/blob/main/web3/beacon/beacon.py"
    click Beacon "https://github.com/ethereum/web3.py/blob/main/web3/beacon/async_beacon.py"
    click Tracing "https://github.com/ethereum/web3.py/blob/main/web3/tracing.py"
    click Geth "https://github.com/ethereum/web3.py/blob/main/web3/geth.py"
    click Tools "https://github.com/ethereum/web3.py/blob/main/web3/tools/benchmark/main.py"
    click BaseProvider "https://github.com/ethereum/web3.py/blob/main/web3/providers/base.py"
    click HTTP "https://github.com/ethereum/web3.py/blob/main/web3/providers/rpc/rpc.py"
    click HTTP "https://github.com/ethereum/web3.py/blob/main/web3/providers/rpc/async_rpc.py"
    click IPC "https://github.com/ethereum/web3.py/blob/main/web3/providers/ipc.py"
    click WS "https://github.com/ethereum/web3.py/blob/main/web3/providers/legacy_websocket.py"
    click EthTester "https://github.com/ethereum/web3.py/blob/main/web3/providers/eth_tester/main.py"
    click Auto "https://github.com/ethereum/web3.py/blob/main/web3/providers/auto.py"
    click Persistent "https://github.com/ethereum/web3.py/blob/main/web3/providers/persistent/persistent.py"
    click Formatting "https://github.com/ethereum/web3.py/blob/main/web3/middleware/formatting.py"
    click Signing "https://github.com/ethereum/web3.py/blob/main/web3/middleware/signing.py"
    click GasStrategy "https://github.com/ethereum/web3.py/blob/main/web3/middleware/gas_price_strategy.py"
    click BufferedGas "https://github.com/ethereum/web3.py/blob/main/web3/middleware/buffered_gas_estimate.py"
    click FilterMW "https://github.com/ethereum/web3.py/blob/main/web3/middleware/filter.py"
    click Name2Addr "https://github.com/ethereum/web3.py/blob/main/web3/middleware/names.py"
    click POA "https://github.com/ethereum/web3.py/blob/main/web3/middleware/proof_of_authority.py"
    click StaleCheck "https://github.com/ethereum/web3.py/blob/main/web3/middleware/stalecheck.py"
    click Validation "https://github.com/ethereum/web3.py/blob/main/web3/middleware/validation.py"
    click AttrDict "https://github.com/ethereum/web3.py/blob/main/web3/middleware/attrdict.py"
    click ENSPkg "https://github.com/ethereum/web3.py/blob/main/ens/ens.py"
    click ENSPkg "https://github.com/ethereum/web3.py/blob/main/ens/_normalization.py"
    click ENSUtils "https://github.com/ethereum/web3.py/blob/main/web3/_utils/ens.py"
    click ABIEnc "https://github.com/ethereum/web3.py/blob/main/web3/_utils/abi.py"
    click ABIEnc "https://github.com/ethereum/web3.py/blob/main/web3/utils/abi.py"
    click Caching "https://github.com/ethereum/web3.py/blob/main/web3/_utils/caching/caching_utils.py"
    click Caching "https://github.com/ethereum/web3.py/blob/main/web3/utils/caching.py"
    click HTTPSess "https://github.com/ethereum/web3.py/blob/main/web3/_utils/http_session_manager.py"
    click Filters "https://github.com/ethereum/web3.py/blob/main/web3/_utils/filters.py"
    click Filters "https://github.com/ethereum/web3.py/blob/main/web3/_utils/events.py"
    click TypeConv "https://github.com/ethereum/web3.py/blob/main/web3/_utils/type_conversion.py"
    click TypeConv "https://github.com/ethereum/web3.py/blob/main/web3/_utils/validation.py"

    %% Styles
    classDef core fill:#E3F2FD,stroke:#2196F3,stroke-width:2px
    classDef pluggable fill:#E8F5E9,stroke:#4CAF50,stroke-width:2px
    classDef external fill:#FFF3E0,stroke:#FB8C00,stroke-width:2px
    classDef external text:#000
    class Web3,Eth,Net,Contract,Beacon,Tracing,Geth,Tools,Formatting,Signing,GasStrategy,BufferedGas,FilterMW,Name2Addr,POA,StaleCheck,Validation,AttrDict,ABIEnc,Caching,HTTPSess,Filters,TypeConv core
    class BaseProvider,HTTP,IPC,WS,EthTester,Auto,Persistent,ENSPkg,ENSUtils pluggable
    class EthereumNode,Offchain external

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
