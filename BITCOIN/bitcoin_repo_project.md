---
created: 2025-06-11 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/bitcoin/bitcoin
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExcG5wbmIyM24xZW1oNzdsNWt0d3RyNW44bWx5emNidmk5c3poaWV2bCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/WT9wi81vtEhqt17SE4/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# bitcoin repo project
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
title: "libblkmaker repo project"
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
    %% Network Layer
    subgraph "P2P Network Layer"
        direction TB
        NetCore["net.h/.cpp"]:::network
        NetProc["net_processing.h/.cpp"]:::network
        ConnTypes["connection_types.h/.cpp"]:::network
        TxDL["txdownloadman_impl.h/.cpp"]:::network
    end

    %% Consensus & Validation
    subgraph "Consensus & Validation Engine"
        direction TB
        ConsensusDir["src/consensus/"]:::consensus
        ValidationCore["validation.h/.cpp"]:::consensus
        Kernel["src/kernel/"]:::consensus
    end

    %% Storage Layer
    subgraph "Storage Layer"
        direction TB
        DBWrap["dbwrapper.h/.cpp"]:::storage
        FlatFile["flatfile.h/.cpp"]:::storage
        TxDB["txdb.h/.cpp"]:::storage
        subgraph "LevelDB"
            direction TB
            WAL["Write Ahead Log (WAL)"]:::storage
            MemTable["MemTable"]:::storage
            ImmMem["Immutable MemTables"]:::storage
            SSTable["SSTable Files"]:::storage
            Compaction["Compaction Threads"]:::storage
            BlockCache["Block Cache"]:::storage
            TableCache["Table Cache"]:::storage
        end
    end

    %% API Layer
    subgraph "RPC & REST API Servers"
        direction TB
        RPC["src/rpc/"]:::api
        REST["rest.h/.cpp"]:::api
        HTTPServer["httpserver.h/.cpp"]:::api
    end

    %% Frontends
    subgraph "Frontends"
        direction TB
        CLI["Command-Line Tools"]:::frontend
        QtGUI["Qt GUI (src/qt/)"]:::frontend
    end

    %% Wallet Module
    Wallet["src/wallet/"]:::frontend

    %% IPC & Notifications
    subgraph "IPC & Notifications"
        direction TB
        IPC["src/ipc/"]:::external
        ZMQ["src/zmq/"]:::external
    end

    %% Scheduler & Background Tasks
    Scheduler["scheduler.h/.cpp"]:::external

    %% External Transports
    subgraph "External Transport Services"
        direction TB
        Tor["torcontrol.h/.cpp"]:::external
        I2P["i2p.h/.cpp"]:::external
    end

    %% Data and Control Flows
    NetCore -->|P2P messages| ConsensusDir
    NetProc -->|P2P messages| ConsensusDir
    ConnTypes -->|connection types| ConsensusDir
    TxDL -->|download tx| ConsensusDir

    ConsensusDir -->|validate blocks| DBWrap
    ValidationCore -->|verify TX| DBWrap
    Kernel -->|update UTXO| DBWrap

    DBWrap -->|WAL writes| WAL
    DBWrap -->|MemTable writes| MemTable
    MemTable -->|flush| ImmMem
    ImmMem -->|create| SSTable
    SSTable -->|merge| Compaction
    Compaction -->|optimize reads| SSTable
    SSTable -->|cache| BlockCache
    SSTable -->|cache| TableCache

    RPC -->|RPC calls| ConsensusDir
    REST -->|REST calls| ConsensusDir
    HTTPServer -->|HTTP| RPC

    CLI -->|commands| RPC
    QtGUI -->|gui calls| RPC

    Wallet -->|build TX| ConsensusDir
    Wallet -->|query UTXO| DBWrap

    ConsensusDir -->|events| ZMQ
    ZMQ -->|publish| External["Subscribers"]

    ConsensusDir -->|IPC events| IPC

    Scheduler -->|maintenance| DBWrap

    Tor -->|transport| NetCore
    I2P -->|transport| NetCore

    %% Click Events
    click NetCore "https://github.com/bitcoin/bitcoin/blob/master/src/net.h"
    click NetProc "https://github.com/bitcoin/bitcoin/blob/master/src/net_processing.h"
    click ConnTypes "https://github.com/bitcoin/bitcoin/blob/master/src/node/connection_types.h"
    click TxDL "https://github.com/bitcoin/bitcoin/blob/master/src/node/txdownloadman_impl.h"
    click ConsensusDir "https://github.com/bitcoin/bitcoin/tree/master/src/consensus/"
    click ValidationCore "https://github.com/bitcoin/bitcoin/blob/master/src/validation.h"
    click Kernel "https://github.com/bitcoin/bitcoin/tree/master/src/kernel/"
    click DBWrap "https://github.com/bitcoin/bitcoin/blob/master/src/dbwrapper.h"
    click FlatFile "https://github.com/bitcoin/bitcoin/blob/master/src/flatfile.h"
    click TxDB "https://github.com/bitcoin/bitcoin/blob/master/src/txdb.h"
    click RPC "https://github.com/bitcoin/bitcoin/tree/master/src/rpc/"
    click REST "https://github.com/bitcoin/bitcoin/blob/master/src/rest.h"
    click HTTPServer "https://github.com/bitcoin/bitcoin/blob/master/src/httpserver.h"
    click CLI "https://github.com/bitcoin/bitcoin/blob/master/src/bitcoind.cpp"
    click QtGUI "https://github.com/bitcoin/bitcoin/tree/master/src/qt/"
    click Wallet "https://github.com/bitcoin/bitcoin/tree/master/src/wallet/"
    click IPC "https://github.com/bitcoin/bitcoin/tree/master/src/ipc/"
    click ZMQ "https://github.com/bitcoin/bitcoin/tree/master/src/zmq/"
    click Scheduler "https://github.com/bitcoin/bitcoin/blob/master/src/scheduler.h"
    click Tor "https://github.com/bitcoin/bitcoin/blob/master/src/torcontrol.h"
    click I2P "https://github.com/bitcoin/bitcoin/blob/master/src/i2p.h"

    %% Styles
    classDef network fill:#ccffcc,stroke:#006600,color:#000;
    classDef consensus fill:#cce5ff,stroke:#004080,color:#000;
    classDef storage fill:#ffe5cc,stroke:#cc6600,color:#000;
    classDef api fill:#e5ccff,stroke:#800080,color:#000;
    classDef frontend fill:#ffffcc,stroke:#808000,color:#000;
    classDef external fill:#eeeeee,stroke:#666666,color:#000;
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