---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/dropbox/incubator-superset-internal
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




# incubator-superset-internal repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes (<ins>sometimes, entertainment purposes</ins>), personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>



---

```mermaid
---
title: "incubator-superset-internal repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright © 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'linear'},
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#22BB',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EEF2',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '15px'
    }
  }
}%%
flowchart TD
    %% CI/CD & Deployment
    subgraph "CI/CD & Deployment"
        CI["GitHub Actions & Helm Charts"]:::infra
    end

    %% User Layer
    subgraph "User Layer"
        Browser["User Browser"]:::frontend
    end

    %% Frontend Layer
    subgraph "Frontend Layer"
        NGINX["NGINX (Static Assets)"]:::infra
        ReactSPA["React/TypeScript SPA"]:::frontend
        CLI["CLI Tools"]:::backend
    end

    %% Backend Layer
    subgraph "Backend/API Layer"
        FlaskAPI["Flask API"]:::backend
        Views["superset/views/"]:::backend
    end

    %% Data Stores & Brokers
    subgraph "Data & Caching Layer"
        Postgres["Postgres Metadata DB"]:::datastore
        Models["superset/models/"]:::datastore
        Migrations["superset/migrations/"]:::datastore
        Redis["Redis Cache"]:::datastore
        CacheKeys["superset/cachekeys/"]:::datastore
        CacheMgr["superset/utils/cache_manager.py"]:::datastore
        RabbitMQ["RabbitMQ Broker"]:::datastore
    end

    %% Workers & Real-time Services
    subgraph "Workers & Real-Time Services"
        CeleryApp["superset/tasks/celery_app.py"]:::worker
        Tasks["superset/tasks/"]:::worker
        WebSocket["WebSocket Service"]:::worker
        SDK["Embedded SDK"]:::worker
        CLIpkg["superset/cli/"]:::worker
        CLIentry["superset/cli/main.py"]:::worker
    end

    %% External Systems
    subgraph "External SQL Engines"
        SQLEngines["superset/db_engine_specs/"]:::external
    end

    %% CI/CD -> Deployment
    CI -->|deploy| NGINX

    %% User interactions
    Browser -->|loads assets| NGINX
    NGINX -->|serves SPA| ReactSPA
    Browser -->|opens SPA| ReactSPA

    %% SPA -> API
    ReactSPA -->|"REST API (JSON)"| FlaskAPI

    %% API internal structure
    FlaskAPI --> Views

    %% API -> Metadata DB
    FlaskAPI -->|SQL over DB-API| Postgres
    Postgres --> Models
    Postgres --> Migrations

    %% API -> Cache & Broker
    FlaskAPI -->|"Cache GET/SET"| Redis
    Redis --> CacheKeys
    Redis --> CacheMgr
    FlaskAPI -->|enqueue tasks| RabbitMQ

    %% Workers
    RabbitMQ -->|consume tasks| CeleryApp
    CeleryApp --> Tasks
    CeleryApp -->|"SQL over DB-API"| SQLEngines
    CeleryApp -->|Cache SET| Redis

    %% Real-time & SDK & CLI
    Browser -->|WebSocket| WebSocket
    FlaskAPI -->|WebSocket Auth| WebSocket
    Browser -->|Embed Charts| SDK
    CLIpkg --> CLIentry

    %% External engines
    FlaskAPI -->|SQL over DB-API| SQLEngines

    %% Click Events
    click ReactSPA "https://github.com/dropbox/incubator-superset-internal/tree/master/superset-frontend/"
    click FlaskAPI "https://github.com/dropbox/incubator-superset-internal/blob/master/superset/app.py"
    click Views "https://github.com/dropbox/incubator-superset-internal/tree/master/superset/views/"
    click Models "https://github.com/dropbox/incubator-superset-internal/tree/master/superset/models/"
    click Migrations "https://github.com/dropbox/incubator-superset-internal/tree/master/superset/migrations/"
    click SQLEngines "https://github.com/dropbox/incubator-superset-internal/tree/master/superset/db_engine_specs/"
    click CacheKeys "https://github.com/dropbox/incubator-superset-internal/tree/master/superset/cachekeys/"
    click CacheMgr "https://github.com/dropbox/incubator-superset-internal/blob/master/superset/utils/cache_manager.py"
    click CeleryApp "https://github.com/dropbox/incubator-superset-internal/blob/master/superset/tasks/celery_app.py"
    click Tasks "https://github.com/dropbox/incubator-superset-internal/tree/master/superset/tasks/"
    click WebSocket "https://github.com/dropbox/incubator-superset-internal/tree/master/superset-websocket/"
    click SDK "https://github.com/dropbox/incubator-superset-internal/tree/master/superset-embedded-sdk/"
    click CLIpkg "https://github.com/dropbox/incubator-superset-internal/tree/master/superset/cli/"
    click CLIentry "https://github.com/dropbox/incubator-superset-internal/blob/master/superset/cli/main.py"

    %% Styles
    classDef frontend fill:#9f6,stroke:#333,stroke-width:1px
    classDef backend fill:#6cf,stroke:#333,stroke-width:1px
    classDef datastore fill:#f96,stroke:#333,stroke-width:1px
    classDef worker fill:#c9f,stroke:#333,stroke-width:1px
    classDef infra fill:#ccc,stroke:#333,stroke-width:1px
    classDef external fill:#aaa,stroke:#333,stroke-width:1px

```

---


<!-- 
```mermaid
%% Current Mermaid version
info
```  -->


```mermaid
---
title: "C<char>o&#770;</char>ngL<char>e&#770;</char>SolutionX"
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
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX/CongLeSolutionX' target='_blank'>Click here if you care about the profile of a tech guy seeking for job 🙏🏼</a>"}}

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