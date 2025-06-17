---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/go-ethereum
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExanZydm52NDcyNWIwMWtneG9uOWk4aGpseXQ1bHR4b3c1N2x3MnB6bSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/m3XqQ8QhuIUuQau7n5/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# go-ethereum repo project
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
title: "go-ethereum repo project"
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
    %% Subgraph for Node Client & Executables
    subgraph "Node Client & Executables"
        geth["geth"]:::executables
        clef["clef"]:::executables
        devp2p["devp2p"]:::executables
        abigen["abigen"]:::executables
        evmExec["evm"]:::executables
        rlpdump["rlpdump"]:::executables
    end

    %% Subgraph for Networking & P2P Layer
    subgraph "Networking & P2P Layer"
        p2pNet["P2P Networking"]:::networking
    end

    %% Subgraph for RPC & API Services
    subgraph "RPC & API Services"
        rpcServer["RPC Server"]:::rpc
        ethApi["Eth API"]:::rpc
        graphQL["GraphQL API"]:::rpc
    end

    %% Subgraph for Consensus Engine
    subgraph "Consensus Engine"
        consensusMod["Consensus Module"]:::consensus
        blockchainCore["Blockchain Core"]:::consensus
        miningMod["Mining Module"]:::consensus
    end

    %% Subgraph for Data Storage & State Management
    subgraph "Data Storage & State Management"
        stateTrie["State Trie/Database"]:::state
        rawdb["Raw DB"]:::state
        trieDB["Trie DB"]:::state
    end

    %% Subgraph for Ethereum Virtual Machine
    subgraph "Ethereum Virtual Machine"
        evm["EVM Execution"]:::evm
    end

    %% Subgraph for Cryptography & Identity
    subgraph "Cryptography & Identity"
        cryptoLib["Crypto Library"]:::crypto
        accounts["Accounts"]:::crypto
        signer["Signer"]:::crypto
    end

    %% Connections Between Components
    %% Node Client interactions
    geth -->|"orchestrates"| p2pNet
    p2pNet -->|"networking"| geth
    geth -->|"initiates"| consensusMod

    %% RPC & API interaction with Consensus Engine
    rpcServer -->|"calls"| consensusMod
    ethApi -->|"calls"| consensusMod
    rpcServer -->|"triggers"| evm
    ethApi -->|"triggers"| evm
    graphQL -->|"queries"| evm

    %% Consensus Engine internal flows
    consensusMod -->|"updates"| blockchainCore
    blockchainCore -->|"coordinates"| miningMod

    %% Consensus Engine to Data Storage & State Management
    consensusMod -->|"writes"| stateTrie
    consensusMod -->|"writes"| rawdb
    consensusMod -->|"writes"| trieDB

    %% Data Storage feeds into EVM execution
    stateTrie -->|"provides state"| evm

    %% Cryptography links
    cryptoLib -->|"validates"| consensusMod
    cryptoLib -->|"secures"| rpcServer
    cryptoLib -->|"supports"| accounts
    cryptoLib -->|"supports"| signer

    %% Style Classes
    classDef executables fill:#cce5ff,stroke:#004085,stroke-width:2px;
    classDef networking fill:#d4edda,stroke:#155724,stroke-width:2px;
    classDef rpc fill:#e2e3e5,stroke:#383d41,stroke-width:2px;
    classDef consensus fill:#fff3cd,stroke:#856404,stroke-width:2px;
    classDef state fill:#d1ecf1,stroke:#0c5460,stroke-width:2px;
    classDef evm fill:#f8d7da,stroke:#721c24,stroke-width:2px;
    classDef crypto fill:#fefbd8,stroke:#b08d57,stroke-width:2px;

    %% Click Events for Node Client & Executables
    click geth "https://github.com/ethereum/go-ethereum/tree/master/cmd/geth"
    click clef "https://github.com/ethereum/go-ethereum/tree/master/cmd/clef"
    click devp2p "https://github.com/ethereum/go-ethereum/tree/master/cmd/devp2p"
    click abigen "https://github.com/ethereum/go-ethereum/tree/master/cmd/abigen"
    click evmExec "https://github.com/ethereum/go-ethereum/tree/master/cmd/evm"
    click rlpdump "https://github.com/ethereum/go-ethereum/tree/master/cmd/rlpdump"

    %% Click Event for Networking & P2P Layer
    click p2pNet "https://github.com/ethereum/go-ethereum/tree/master/p2p"

    %% Click Events for Consensus Engine
    click consensusMod "https://github.com/ethereum/go-ethereum/tree/master/consensus"
    click blockchainCore "https://github.com/ethereum/go-ethereum/tree/master/core"
    click miningMod "https://github.com/ethereum/go-ethereum/blob/master/miner/miner.go"

    %% Click Event for Ethereum Virtual Machine
    click evm "https://github.com/ethereum/go-ethereum/tree/master/core/vm"

    %% Click Events for Data Storage & State Management
    click stateTrie "https://github.com/ethereum/go-ethereum/tree/master/core/state"
    click rawdb "https://github.com/ethereum/go-ethereum/tree/master/core/rawdb"
    click trieDB "https://github.com/ethereum/go-ethereum/tree/master/trie"

    %% Click Events for RPC & API Services
    click rpcServer "https://github.com/ethereum/go-ethereum/tree/master/rpc"
    click ethApi "https://github.com/ethereum/go-ethereum/tree/master/internal/ethapi"
    click graphQL "https://github.com/ethereum/go-ethereum/tree/master/graphql"

    %% Click Events for Cryptography & Identity
    click cryptoLib "https://github.com/ethereum/go-ethereum/tree/master/crypto"
    click accounts "https://github.com/ethereum/go-ethereum/tree/master/accounts"
    click signer "https://github.com/ethereum/go-ethereum/tree/master/signer"
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