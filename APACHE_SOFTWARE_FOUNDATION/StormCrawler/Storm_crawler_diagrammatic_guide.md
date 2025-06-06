---
created: 2025-06-04 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/apache/stormcrawler
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExN2g4OGtqNjR0bnF4dDFzZWwwOGQwdGZnY211eTg4Z2xiaTNyY214ayZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/wLa0m8uCyEZGhNS6dT/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----




# Storm Crawler - A diagrammatic guide to repo project

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
title: "A Diagrammatic Guide to the Storm Crawler Project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
  look: classic
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'securityLevel': 'loose',
    'flowchart': { 'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Comic Sans MS, cursive, sans-serif',
    'themeVariables': {
      'primaryColor': '#F3E333',
      'primaryTextColor': '#145A32',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EBDEF0',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '15px'
    }
  }
}%%
flowchart TB
    %% Maven Multi-Module
    subgraph Maven_Multi_Module_Project["Maven Multi-Module Project"]
    style Maven_Multi_Module_Project fill:#8226,stroke:#000,stroke-width:1px
    direction TB
        core_lib["Core<br/>(core)"]:::core
        archetype["Archetype<br/>(archetype)"]:::external
        external_mods["External Modules"]:::external
    end

    %% Core Pipeline
    subgraph StormCrawler_Core_Pipeline["StormCrawler Core Pipeline"]
    style StormCrawler_Core_Pipeline fill:#8116,stroke:#000,stroke-width:1px
    direction TB
        subgraph Spouts["Spouts"]
        style Spouts fill:#D119,stroke:#000,stroke-width:1px
        direction TB
            AQS["AbstractQueryingSpout"]:::core
            FS["FileSpout"]:::core
            MS["MemorySpout"]:::core
        end
        
        subgraph Fetcher_Bolts["Fetcher Bolts"]
        style Fetcher_Bolts fill:#D9F5,stroke:#000,stroke-width:1px
        direction TB
            SF["SimpleFetcherBolt"]:::core
            FB["FetcherBolt"]:::core
        end
        
        subgraph Parser_Bolts["Parser Bolts"]
        style Parser_Bolts fill:#EFF5,stroke:#000,stroke-width:1px
        direction TB
            JP["JSoupParserBolt"]:::core
            FP["FeedParserBolt"]:::core
            SP["SiteMapParserBolt"]:::core
        end
        
        subgraph Filters["Filters"]
        style Filters fill:#AAF5,stroke:#000,stroke-width:1px
        direction TB
            UF["URLFilterBolt"]:::core
        end
        
        subgraph Partitioning["Partitioning"]
        style Partitioning fill:#DD11,stroke:#000,stroke-width:1px
        direction TB
            UP["URLPartitionerBolt"]:::core
        end
        
        subgraph Indexing_Bolts["Indexing Bolts"]
        style Indexing_Bolts fill:#FF93,stroke:#000,stroke-width:1px
        direction TB
            AIB["AbstractIndexerBolt"]:::core
            SOI["StdOutIndexer"]:::core
            DI["DummyIndexer"]:::core
        end
        
        subgraph Status_Updaters["Status Updaters"]
        style Status_Updaters fill:#AAFF,stroke:#000,stroke-width:1px
        direction TB
            ASU["AbstractStatusUpdaterBolt"]:::core
            MSU["MemoryStatusUpdater"]:::core
            SOSU["StdOutStatusUpdater"]:::core
        end
        
        subgraph Scheduler_and_URLBuffer["Scheduler & URLBuffer"]
        style Scheduler_and_URLBuffer fill:#2DD9,stroke:#000,stroke-width:1px
        direction TB
            DS["DefaultScheduler"]:::core
            AS["AdaptiveScheduler"]:::core
            UB["URLBuffers"]:::core
        end
    end

    %% Protocols
    subgraph Protocols["Protocols"]
    style Protocols fill:#D311,stroke:#000,stroke-width:1px
    direction TB
        ProtocolAPI["Protocol API"]:::core
        HTTP["HttpProtocol"]:::core
        FileProt["FileProtocol"]:::core
        Selenium["SeleniumProtocol"]:::core
        PlaywrightProt["PlaywrightProtocol"]:::external
    end

    %% External Adapter Modules
    subgraph External_Adapter_Modules["External Adapter Modules"]
    style External_Adapter_Modules fill:#C911,stroke:#000,stroke-width:1px
    direction TB
        AWS["AWS<br/>(CloudSearch, S3)"]:::external
        SolrExt["Solr Adapter"]:::external
        OSExt["OpenSearch Adapter"]:::external
        SQLExt["SQL Adapter"]:::external
        TikaExt["Tika ParserBolt"]:::external
        WARC["WARC Spout/Output"]:::external
        URLF["URL Frontier gRPC"]:::external
    end

    %% Infrastructure & Services
    subgraph Infrastructure_and_External_Services["Infrastructure & External Services"]
    style Infrastructure_and_External_Services fill:#A99,stroke:#000,stroke-width:1px
    direction TB
        StormCluster["Apache Storm Cluster"]:::infra
        ZK["Zookeeper"]:::infra
        SolrStore["Solr/Elasticsearch/OpenSearch"]:::infra
        SQLDB["SQL Database"]:::infra
        S3["AWS S3 / HDFS"]:::infra
        CloudSearch["AWS CloudSearch"]:::infra
        TikaSvc["Tika Service"]:::infra
        Web["External Web"]:::infra
    end

    %% Data Flow
    AQS -->|tuples| SF
    FS -->|tuples| SF
    MS -->|tuples| SF
    SF -->|download| ProtocolAPI
    FB -->|download| ProtocolAPI
    ProtocolAPI -->|HTTP/Selenium/Playwright| Web
    ProtocolAPI -->|file| FileProt
    HTTP --> ProtocolAPI
    FileProt --> ProtocolAPI
    Selenium --> ProtocolAPI
    PlaywrightProt --> ProtocolAPI

    SF --> JP
    SF --> FP
    SF --> SP
    JP --> UF
    FP --> UF
    SP --> UF
    UF --> UP
    UP --> AIB
    UP --> SOI
    UP --> DI
    AIB --> ASU
    SOI --> ASU
    DI --> ASU

    %% External indexers connections
    SolrExt -->|indexing API| SolrStore
    OSExt -->|indexing API| SolrStore
    AWS -->|CloudSearch API| CloudSearch
    SQLExt -->|SQL API| SQLDB

    %% Connect core indexers to external indexers
    AIB --> SolrExt
    AIB --> OSExt
    AIB --> AWS
    AIB --> SQLExt

    %% Status Updaters to stores
    ASU --> StormCluster
    MSU --> StormCluster
    SOSU --> StormCluster
    URLF --> StormCluster
    SolrExt --> StormCluster
    OSExt --> StormCluster
    SQLExt --> StormCluster

    ASU --> ZK
    URLF --> ZK

    ASU --> SQLDB
    ASU --> SolrStore
    ASU --> S3

    %% Scheduler feedback
    ASU --> DS
    DS --> AQS
    DS --> FS
    AS --> AQS
    AS --> MS
    UB --> AQS

    %% Archetype connection
    archetype --> core_lib

    %% Storm run
    core_lib --> StormCluster

    %% Click events
    click AQS "https://github.com/apache/stormcrawler/blob/main/core/src/main/java/org/apache/stormcrawler/persistence/AbstractQueryingSpout.java"
    click FS "https://github.com/apache/stormcrawler/blob/main/core/src/main/java/org/apache/stormcrawler/spout/FileSpout.java"
    click MS "https://github.com/apache/stormcrawler/blob/main/core/src/main/java/org/apache/stormcrawler/spout/MemorySpout.java"
    click FB "https://github.com/apache/stormcrawler/blob/main/core/src/main/java/org/apache/stormcrawler/bolt/FetcherBolt.java"
    click SF "https://github.com/apache/stormcrawler/blob/main/core/src/main/java/org/apache/stormcrawler/bolt/SimpleFetcherBolt.java"
    click JP "https://github.com/apache/stormcrawler/blob/main/core/src/main/java/org/apache/stormcrawler/bolt/JSoupParserBolt.java"
    click FP "https://github.com/apache/stormcrawler/blob/main/core/src/main/java/org/apache/stormcrawler/bolt/FeedParserBolt.java"
    click SP "https://github.com/apache/stormcrawler/blob/main/core/src/main/java/org/apache/stormcrawler/bolt/SiteMapParserBolt.java"
    click UF "https://github.com/apache/stormcrawler/blob/main/core/src/main/java/org/apache/stormcrawler/bolt/URLFilterBolt.java"
    click UP "https://github.com/apache/stormcrawler/blob/main/core/src/main/java/org/apache/stormcrawler/bolt/URLPartitionerBolt.java"
    click AIB "https://github.com/apache/stormcrawler/blob/main/core/src/main/java/org/apache/stormcrawler/indexing/AbstractIndexerBolt.java"
    click SOI "https://github.com/apache/stormcrawler/blob/main/core/src/main/java/org/apache/stormcrawler/indexing/StdOutIndexer.java"
    click DI "https://github.com/apache/stormcrawler/blob/main/core/src/main/java/org/apache/stormcrawler/indexing/DummyIndexer.java"
    click SolrExt "https://github.com/apache/stormcrawler/blob/main/external/solr/src/main/java/org/apache/stormcrawler/solr/bolt/IndexerBolt.java"
    click OSExt "https://github.com/apache/stormcrawler/blob/main/external/opensearch/src/main/java/org/apache/stormcrawler/opensearch/bolt/IndexerBolt.java"
    click AWS "https://github.com/apache/stormcrawler/blob/main/external/aws/src/main/java/org/apache/stormcrawler/aws/bolt/CloudSearchIndexerBolt.java"
    click SQLExt "https://github.com/apache/stormcrawler/blob/main/external/sql/src/main/java/org/apache/stormcrawler/sql/IndexerBolt.java"
    click ASU "https://github.com/apache/stormcrawler/blob/main/core/src/main/java/org/apache/stormcrawler/persistence/AbstractStatusUpdaterBolt.java"
    click MSU "https://github.com/apache/stormcrawler/blob/main/core/src/main/java/org/apache/stormcrawler/persistence/MemoryStatusUpdater.java"
    click SOSU "https://github.com/apache/stormcrawler/blob/main/core/src/main/java/org/apache/stormcrawler/persistence/StdOutStatusUpdater.java"
    click URLF "https://github.com/apache/stormcrawler/blob/main/external/urlfrontier/src/main/java/org/apache/stormcrawler/urlfrontier/StatusUpdaterBolt.java"
    click SolrStore "https://github.com/apache/stormcrawler/blob/main/external/solr/src/main/java/org/apache/stormcrawler/solr/persistence/StatusUpdaterBolt.java"
    click OSExt "https://github.com/apache/stormcrawler/blob/main/external/opensearch/src/main/java/org/apache/stormcrawler/opensearch/persistence/StatusUpdaterBolt.java"
    click SQLExt "https://github.com/apache/stormcrawler/blob/main/external/sql/src/main/java/org/apache/stormcrawler/sql/StatusUpdaterBolt.java"
    click DS "https://github.com/apache/stormcrawler/blob/main/core/src/main/java/org/apache/stormcrawler/persistence/DefaultScheduler.java"
    click AS "https://github.com/apache/stormcrawler/blob/main/core/src/main/java/org/apache/stormcrawler/persistence/AdaptiveScheduler.java"
    click UB "https://github.com/apache/stormcrawler/tree/main/core/src/main/java/org/apache/stormcrawler/persistence/urlbuffer"
    click ProtocolAPI "https://github.com/apache/stormcrawler/blob/main/core/src/main/java/org/apache/stormcrawler/protocol/Protocol.java"
    click HTTP "https://github.com/apache/stormcrawler/blob/main/core/src/main/java/org/apache/stormcrawler/protocol/httpclient/HttpProtocol.java"
    click FileProt "https://github.com/apache/stormcrawler/blob/main/core/src/main/java/org/apache/stormcrawler/protocol/file/FileProtocol.java"
    click Selenium "https://github.com/apache/stormcrawler/blob/main/core/src/main/java/org/apache/stormcrawler/protocol/selenium/SeleniumProtocol.java"
    click PlaywrightProt "https://github.com/apache/stormcrawler/blob/main/external/playwright/src/main/java/org/apache/stormcrawler/protocol/playwright/HttpProtocol.java"
    click archetype "https://github.com/apache/stormcrawler/tree/main/archetype/src/main/resources/archetype-resources"

    %% Styles
    classDef core fill:#ADD8E6,stroke:#000,stroke-width:1px
    classDef external fill:#FFA500,stroke:#000,stroke-width:1px
    classDef infra fill:#D3D3D3,stroke:#000,stroke-width:1px
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
