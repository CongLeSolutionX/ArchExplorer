---
created: 2025-06-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/mitre/heimdall2
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




# heimdall2 repo project
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

```mermaid
---
title: "heimdall2 repo project"
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
    %% User and Gateway
    Browser["User Web Browser"]:::client
    Gateway["NGINX Reverse Proxy/TLS"]:::gateway

    Browser -->|"HTTPS"| Gateway

    %% Frontend
    subgraph "Frontend Layer"
    direction TB
        SPA["Frontend: Vue.js + Vuex + Vuetify"]:::frontend
        Utilities["Utilities: AWS, Splunk, Tenable"]:::frontend
        Store["Vuex Store"]:::frontend
        Routes["Routes & Entry<br/>(router.ts, main.ts, App.vue)"]:::frontend
        Static["Static Assets & Samples"]:::frontend
        TestsFE["E2E & Unit Tests"]:::test
        SPA --> Utilities
        SPA --> Store
        SPA --> Routes
        SPA --> Static
        SPA --> TestsFE
    end
    Gateway -->|"serves SPA"| SPA

    %% Backend and Data Conversion
    subgraph "Backend Layer"
    direction TB
        API["Backend API:<br/>NestJS + Sequelize"]:::backend
        Config["Configuration<br/>(app_config.ts, database.ts)"]:::backend
        Migrations["Migrations & Seeders"]:::backend
        AuthN["AuthN Module"]:::backend
        AuthZ["AuthZ Module"]:::backend
        APIKey["API Key Module"]:::backend
        Users["User Module"]:::backend
        Evaluations["Evaluations Module"]:::backend
        Groups["Groups & Group Users"]:::backend
        Statistics["Statistics Module"]:::backend
        Tokens["Tokens Module"]:::backend
        Guards["Guards & Interceptors"]:::backend
        Pipes["Pipes & Filters"]:::backend

        API --> Config
        API --> Migrations
        API --> AuthN
        API --> AuthZ
        API --> APIKey
        API --> Users
        API --> Evaluations
        API --> Groups
        API --> Statistics
        API --> Tokens
        API --> Guards
        API --> Pipes
    end

    SPA -->|"REST API Calls"| API

    %% Database
    Database[("PostgreSQL Database")]:::database
    API -->|"SQL"| Database

    %% Shared Libraries
    subgraph "Shared Libraries"
    direction TB
        Common["Common Interfaces"]:::library
        HDF["HDF Converters"]:::library
        InSpec["InSpecJS"]:::library
    end
    API -->|"invoke"| HDF
    API -->|"invoke"| InSpec
    API -->|depends on| Common

    %% External Data Sources
    subgraph "External Services"
    direction TB
        S3["AWS S3"]:::external
        Splunk["Splunk HTTP API"]:::external
        Tenable["Tenable.SC API"]:::external
    end
    API -->|"AWS SDK"| S3
    API -->|"HTTP"| Splunk
    API -->|"HTTP"| Tenable

    %% Offline Lite Mode
    SPA -->|"<i>optional</i><br/>Lite Mode"| HDF

    %% Docker Compose & Infra
    subgraph "Infra & CI/CD"
    direction TB
        DockerCompose["Docker Compose"]:::infra
        DockerImg["Docker Images"]:::infra
        Helm["Kubernetes /<br/> Helm"]:::infra
        CICD["GitHub Actions CI/CD"]:::infra
    end
    DockerCompose --> Gateway
    DockerCompose --> API
    DockerCompose --> Database
    CICD --> DockerImg
    DockerImg --> DockerCompose
    CICD --> Helm

    %% Click Events
    click SPA "https://github.com/mitre/heimdall2/tree/master/apps/frontend"
    click Utilities "https://github.com/mitre/heimdall2/blob/master/apps/frontend/src/utilities/aws_util.ts"
    click Store "https://github.com/mitre/heimdall2/tree/master/apps/frontend/src/store"
    click Routes "https://github.com/mitre/heimdall2/blob/master/apps/frontend/src/router.ts"
    click Routes "https://github.com/mitre/heimdall2/blob/master/apps/frontend/src/main.ts"
    click Static "https://github.com/mitre/heimdall2/tree/master/apps/frontend/public/static"
    click TestsFE "https://github.com/mitre/heimdall2/tree/master/apps/frontend/tests"
    click API "https://github.com/mitre/heimdall2/tree/master/apps/backend/src"
    click Config "https://github.com/mitre/heimdall2/blob/master/apps/backend/config/app_config.ts"
    click Config "https://github.com/mitre/heimdall2/blob/master/apps/backend/db/database.ts"
    click Migrations "https://github.com/mitre/heimdall2/tree/master/apps/backend/migrations"
    click Migrations "https://github.com/mitre/heimdall2/tree/master/apps/backend/seeders"
    click AuthN "https://github.com/mitre/heimdall2/tree/master/apps/backend/src/authn"
    click AuthZ "https://github.com/mitre/heimdall2/tree/master/apps/backend/src/authz"
    click APIKey "https://github.com/mitre/heimdall2/tree/master/apps/backend/src/apikeys"
    click Users "https://github.com/mitre/heimdall2/tree/master/apps/backend/src/users"
    click Evaluations "https://github.com/mitre/heimdall2/tree/master/apps/backend/src/evaluations"
    click Groups "https://github.com/mitre/heimdall2/tree/master/apps/backend/src/groups"
    click Groups "https://github.com/mitre/heimdall2/tree/master/apps/backend/src/group-users"
    click Groups "https://github.com/mitre/heimdall2/tree/master/apps/backend/src/group-evaluations"
    click Statistics "https://github.com/mitre/heimdall2/tree/master/apps/backend/src/statistics"
    click Tokens "https://github.com/mitre/heimdall2/tree/master/apps/backend/src/token"
    click Guards "https://github.com/mitre/heimdall2/tree/master/apps/backend/src/guards"
    click Pipes "https://github.com/mitre/heimdall2/tree/master/apps/backend/src/pipes"
    click Common "https://github.com/mitre/heimdall2/tree/master/libs/common"
    click HDF "https://github.com/mitre/heimdall2/tree/master/libs/hdf-converters"
    click InSpec "https://github.com/mitre/heimdall2/tree/master/libs/inspecjs"
    click DockerCompose "https://github.com/mitre/heimdall2/blob/master/docker-compose.yml"
    click CICD "https://github.com/mitre/heimdall2/tree/master/.github/workflows"

    %% Styles
    classDef client fill:#AEDFF7,stroke:#0177BF,color:#000;
    classDef gateway fill:#F5E050,stroke:#D4A000,color:#000;
    classDef frontend fill:#B3E5FC,stroke:#0288D1,color:#000;
    classDef backend fill:#80CBC4,stroke:#00897B,color:#000;
    classDef database fill:#C8E6C9,stroke:#2E7D32,color:#000;
    classDef library fill:#EEEEEE,stroke:#9E9E9E,color:#000;
    classDef external fill:#FFCC80,stroke:#EF6C00,color:#000;
    classDef infra fill:#D1C4E9,stroke:#512DA8,color:#000;
    classDef test fill:#F8BBD0,stroke:#C2185B,color:#000;

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