---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/apple/foundationdb
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExODlya2UzYnJxa3pldXp6cmZhNmpwcWg5eDB1YnBtdzl3dzcyNGhpMiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/12Luqxxo5WlSSY/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# foundationdb
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## A Diagrammatic Guide 




```mermaid
---
title: "Apple - Foundation DB"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "flowchart": {"htmlLabels": true, 'curve': 'natural'},
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#f231',
      'primaryTextColor': '#239',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TB
    %% Style definitions
    classDef client fill:#9925,stroke:#333,stroke-width:2px
    classDef server fill:#87CB,stroke:#333,stroke-width:2px
    classDef storage fill:#DE82,stroke:#333,stroke-width:2px
    classDef monitoring fill:#FD72,stroke:#333,stroke-width:2px
    classDef core fill:#B1CD,stroke:#333,stroke-width:2px
    classDef transaction fill:#F992,stroke:#333,stroke-width:2px

    %% Client Layer
    subgraph Client_Layer["Client Layer"]
        C_API["C Binding"]:::client
        Java["Java Binding"]:::client
        Python["Python Binding"]:::client
        Go["Go Binding"]:::client
        Ruby["Ruby Binding"]:::client
    end

    %% Server Components
    subgraph Server_Components["Server Components"]
        CC["Cluster Controller"]:::server
        CP["Commit Proxy"]:::server
        SS["Storage Server"]:::server
        TLog["Transaction Log"]:::server
        Master["Master"]:::server
        Resolver["Resolver"]:::server
        Coord["Coordinators"]:::server
    end

    %% Storage Layer
    subgraph Storage_Layer[Storage Layer""]
        KVStore["Key-Value Store"]:::storage
        RocksDB["RocksDB Backend"]:::storage
        StorageMetrics["Storage Metrics"]:::storage
        DataDist["Data Distribution"]:::storage
    end

    %% Transaction System
    subgraph Transaction_System["Transaction System"]
        DbContext["Database Context"]:::transaction
        RYW["Read Your Writes"]:::transaction
        CommitTx["Commit Transaction"]:::transaction
        ConflictSet["Conflict Detection"]:::transaction
    end

    %% Monitoring & Management
    subgraph Monitoring_System["Monitoring System"]
        Status["Status Reporter"]:::monitoring
        MetricLogger["Metric Logger"]:::monitoring
        BackupSystem["Backup System"]:::monitoring
        BackupAgent["Backup Agent"]:::monitoring
    end

    %% Core Infrastructure
    subgraph Core_Infra["Core Infrastructure"]
        ActorFramework["Actor Framework"]:::core
        NetworkLayer["Network Layer"]:::core
        CoreClient["Core Client"]:::core
    end

    %% Relationships
    ClientLayer --> CP
    ClientLayer --> SS
    CP --> Resolver
    CP --> TLog
    TLog --> SS
    CC --> Master
    Master --> CP
    SS --> StorageLayer
    CP --> TransactionSystem
    MonitoringSystem --> ServerComponents

    %% Click events
    click C_API "https://github.com/apple/foundationdb/tree/main/bindings/c/"
    click Java "https://github.com/apple/foundationdb/tree/main/bindings/java/"
    click Python "https://github.com/apple/foundationdb/tree/main/bindings/python/"
    click Go "https://github.com/apple/foundationdb/tree/main/bindings/go/"
    click Ruby "https://github.com/apple/foundationdb/tree/main/bindings/ruby/"
    click CC "https://github.com/apple/foundationdb/blob/main/fdbserver/ClusterController.actor.cpp"
    click CP "https://github.com/apple/foundationdb/blob/main/fdbserver/CommitProxyServer.actor.cpp"
    click SS "https://github.com/apple/foundationdb/blob/main/fdbserver/storageserver.actor.cpp"
    click TLog "https://github.com/apple/foundationdb/blob/main/fdbserver/TLogServer.actor.cpp"
    click Master "https://github.com/apple/foundationdb/blob/main/fdbserver/masterserver.actor.cpp"
    click Resolver "https://github.com/apple/foundationdb/blob/main/fdbserver/Resolver.actor.cpp"
    click Coord "https://github.com/apple/foundationdb/blob/main/fdbserver/Coordination.actor.cpp"
    click KVStore "https://github.com/apple/foundationdb/blob/main/fdbserver/KeyValueStoreMemory.actor.cpp"
    click RocksDB "https://github.com/apple/foundationdb/blob/main/fdbserver/KeyValueStoreRocksDB.actor.cpp"
    click StorageMetrics "https://github.com/apple/foundationdb/blob/main/fdbserver/StorageMetrics.actor.cpp"
    click DataDist "https://github.com/apple/foundationdb/blob/main/fdbserver/DataDistribution.actor.cpp"
    click DbContext "https://github.com/apple/foundationdb/blob/main/fdbclient/DatabaseContext.cpp"
    click RYW "https://github.com/apple/foundationdb/blob/main/fdbclient/ReadYourWrites.actor.cpp"
    click CommitTx "https://github.com/apple/foundationdb/blob/main/fdbclient/CommitTransaction.h"
    click ConflictSet "https://github.com/apple/foundationdb/blob/main/fdbserver/ConflictSet.h"
    click Status "https://github.com/apple/foundationdb/blob/main/fdbserver/Status.actor.cpp"
    click MetricLogger "https://github.com/apple/foundationdb/blob/main/fdbserver/MetricLogger.actor.cpp"
    click BackupSystem "https://github.com/apple/foundationdb/tree/main/fdbbackup/"
    click BackupAgent "https://github.com/apple/foundationdb/blob/main/fdbclient/BackupAgent.actor.h"
    click ActorFramework "https://github.com/apple/foundationdb/tree/main/flow/"
    click NetworkLayer "https://github.com/apple/foundationdb/tree/main/fdbrpc/"
    click CoreClient "https://github.com/apple/foundationdb/tree/main/fdbclient/"

    %% Legend
    subgraph Legend
        Client["Client Components"]:::client
        ServerComp["Server Components"]:::server
        StorageComp["Storage Components"]:::storage
        MonitoringComp["Monitoring Components"]:::monitoring
        CoreComp["Core Infrastructure"]:::core
        TxComp["Transaction Components"]:::transaction
    end
    
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
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
