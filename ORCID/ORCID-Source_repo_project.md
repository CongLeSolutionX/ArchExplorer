---
created: 2025-06-09 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/orcid/orcid-source
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExcHcwcGc0aDlqY2s4NnM5ejZyM3J3dWZicGdzMnRkeXppN3ZydnRldyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3o6gbchrcNIt4Ma8Tu/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# ORCID-Source repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>

---



## A Diagrammatic Guide 


----

```mermaid
---
title: "ORCID-Source repo project"
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
    %% User
    UserBrowser["User Browser\n(AngularJS)"]:::ui

    subgraph "Frontend Layer"
        LBcfg["orcid-lb\n(HAProxy)"]:::api
        HAProxyCfg["orcid-haprouter\n(HAProxy)"]:::api
        WebProxy["orcid-web-proxy\n(Nginx)"]:::api
        FrontendSPA["orcid-web-frontend\n(AngularJS SPA)"]:::ui
        FrontServer["orcid-web\n(FreeMarker)"]:::ui
    end

    subgraph "API Layer"
        PublicAPI["orcid-api-web\n(Spring MVC, Jersey)"]:::api
        PubReadAPI["orcid-pub-web\n(Spring MVC)"]:::api
        InternalAPI["orcid-internal-api\n(Spring MVC)"]:::api
    end

    subgraph "Core Layer"
        Core["orcid-core\n(Spring Services)"]:::core
        APICommon["orcid-api-common"]:::core
        Utils["orcid-utils"]:::core
    end

    subgraph "Async Layer"
        ActiveMQ["ActiveMQ\n(JMS Broker)"]:::messaging
        MsgListener["orcid-message-listener"]:::background
        ActivitiesIndexer["orcid-activities-indexer"]:::background
        Scheduler["orcid-scheduler-web\n(Scheduled Jobs)"]:::background
        Solr["Solr Cores\n(Org, Profile)"]:::messaging
    end

    subgraph "Data Layer"
        Persistence["orcid-persistence\n(JPA, Liquibase)"]:::persistence
        Postgres["Postgres DB"]:::persistence
        RedisStore["Redis\n(Cache/Session)"]:::persistence
    end

    subgraph "External Services"
        S3["S3 Messaging"]:::external
        CrossRef["CrossRef API"]:::external
        FundRef["FundRef API"]:::external
        ROR["ROR API"]:::external
        Figshare["Figshare API"]:::external
    end

    subgraph "Infrastructure"
        DockerCompose["Docker Compose\n(Dockerfile, docker-compose.yml)"]:::infra
        Jenkinsfile["Jenkinsfile"]:::infra
        GitHubWF[".github/workflows"]:::infra
        SolrConfig["solr-config"]:::infra
        RedisScripts["/redis"]:::infra
        DefaultEnv["default.env"]:::infra
        Entrypoint["entrypoint.sh"]:::infra
        DeployScript["deploy.sh"]:::infra
        RunTests["run-tests.sh"]:::infra
    end

    %% Connections
    UserBrowser --> LBcfg
    LBcfg --> HAProxyCfg
    HAProxyCfg --> WebProxy
    WebProxy --> FrontendSPA
    FrontendSPA --> FrontServer
    FrontendSPA --> PublicAPI
    Frontserver --> PublicAPI
    FrontendSPA --> PubReadAPI
    FrontServer --> PubReadAPI
    FrontendSPA --> InternalAPI
    FrontServer --> InternalAPI

    PublicAPI --> Core
    PubReadAPI --> Core
    InternalAPI --> Core

    Core --> Persistence
    Persistence --> Postgres
    Core --> RedisStore
    RedisStore --> Core

    Core --> ActiveMQ
    ActiveMQ --> MsgListener
    ActiveMQ --> ActivitiesIndexer
    MsgListener --> Solr
    ActivitiesIndexer --> Solr

    Scheduler --> Core
    Scheduler --> MsgListener
    Scheduler --> ActivitiesIndexer

    Core --> S3
    Core --> CrossRef
    Core --> FundRef
    Core --> ROR
    Core --> Figshare

    Core --> APICommon
    Core --> Utils

    DockerCompose --> LBcfg
    DockerCompose --> WebProxy
    DockerCompose --> FrontendSPA
    DockerCompose --> FrontServer
    DockerCompose --> PublicAPI
    DockerCompose --> PubReadAPI
    DockerCompose --> InternalAPI
    DockerCompose --> Core
    DockerCompose --> Persistence
    DockerCompose --> ActiveMQ
    DockerCompose --> MsgListener
    DockerCompose --> ActivitiesIndexer
    DockerCompose --> Scheduler
    DockerCompose --> Solr
    DockerCompose --> RedisStore

    Jenkinsfile --> DockerCompose
    GitHubWF --> DockerCompose
    SolrConfig --> Solr
    RedisScripts --> RedisStore
    DefaultEnv --> DockerCompose
    Entrypoint --> DockerCompose
    DeployScript --> DockerCompose
    RunTests --> DockerCompose

    %% Click Events
    click FrontendSPA "https://github.com/orcid/orcid-source/tree/main//orcid-web-frontend"
    click FrontServer "https://github.com/orcid/orcid-source/tree/main//orcid-web"
    click WebProxy "https://github.com/orcid/orcid-source/tree/main//orcid-web-proxy"
    click LBcfg "https://github.com/orcid/orcid-source/tree/main//orcid-lb"
    click HAProxyCfg "https://github.com/orcid/orcid-source/tree/main//orcid-haprouter"
    click PublicAPI "https://github.com/orcid/orcid-source/tree/main//orcid-api-web"
    click PubReadAPI "https://github.com/orcid/orcid-source/tree/main//orcid-pub-web"
    click InternalAPI "https://github.com/orcid/orcid-source/tree/main//orcid-internal-api"
    click Core "https://github.com/orcid/orcid-source/tree/main//orcid-core"
    click Persistence "https://github.com/orcid/orcid-source/tree/main//orcid-persistence"
    click ActiveMQ "https://github.com/orcid/orcid-source/tree/main//orcid-activemq"
    click MsgListener "https://github.com/orcid/orcid-source/tree/main//orcid-message-listener"
    click ActivitiesIndexer "https://github.com/orcid/orcid-source/tree/main//orcid-activities-indexer"
    click Scheduler "https://github.com/orcid/orcid-source/tree/main//orcid-scheduler-web"
    click APICommon "https://github.com/orcid/orcid-source/tree/main//orcid-api-common"
    click Utils "https://github.com/orcid/orcid-source/tree/main//orcid-utils"
    click DockerCompose "https://github.com/orcid/orcid-source/blob/main/docker-compose.yml"
    click Jenkinsfile "https://github.com/orcid/orcid-source/tree/main/Jenkinsfile"
    click GitHubWF "https://github.com/orcid/orcid-source/tree/main/.github/workflows"
    click SolrConfig "https://github.com/orcid/orcid-source/tree/main//solr-config"
    click RedisScripts "https://github.com/orcid/orcid-source/tree/main//redis"
    click DefaultEnv "https://github.com/orcid/orcid-source/blob/main/default.env"
    click Entrypoint "https://github.com/orcid/orcid-source/blob/main/entrypoint.sh"
    click DeployScript "https://github.com/orcid/orcid-source/blob/main/deploy.sh"
    click RunTests "https://github.com/orcid/orcid-source/blob/main/run-tests.sh"

    %% Styles
    classDef ui fill:#E3F2FD,stroke:#2196F3,color:#0D47A1,stroke-width:1px
    classDef api fill:#E8F5E9,stroke:#4CAF50,color:#1B5E20,stroke-width:1px
    classDef core fill:#FFF3E0,stroke:#FB8C00,color:#E65100,stroke-width:1px
    classDef persistence fill:#F3E5F5,stroke:#9C27B0,color:#4A148C,stroke-width:1px
    classDef messaging fill:#FFFDE7,stroke:#FBC02D,color:#F57F17,stroke-width:1px
    classDef background fill:#FFF9C4,stroke:#FDD835,color:#F9A825,stroke-width:1px
    classDef external fill:#ECEFF1,stroke:#90A4AE,color:#607D8B,stroke-dasharray: 5 5,stroke-width:1px
    classDef infra fill:#ECEFF1,stroke:#546E7A,color:#263238,stroke-width:1px

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
