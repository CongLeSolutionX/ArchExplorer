---
created: 2025-06-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/withgraphite/docs
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


# docs repo project
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
title: "docs repo project"
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
    %% Documentation Site
    subgraph "Documentation Site"
        DS1[".gitbook/"]:::service
        DS2["README.md"]:::service
        DS3["SUMMARY.md"]:::service
        DS4["Getting Started"]:::service
        DS5["Reference (PAT Permissions)"]:::service
        DS6["Auth Guide"]:::service
    end

    %% Developer Environment
    subgraph "Developer Environment"
        CLI["Graphite CLI"]:::client
        Git["Git (Local Repo)"]:::service
    end

    %% External Service
    GH["GitHub API & Hosting"]:::external

    %% Graphite Backend
    subgraph "Graphite Backend"
        APIGW["API Gateway (GraphQL/REST)"]:::service
        subgraph "Microservices"
            SM["Stack Management Service"]:::service
            PR["PR Orchestration Service"]:::service
            NOTIF["Notification Service"]:::service
            AUTH["Auth & Authorization Service"]:::service
        end
    end

    %% Datastore Layer
    subgraph "Datastore Layer"
        PG["PostgreSQL DB"]:::datastore
        REDIS["Redis Cache"]:::datastore
        MQ["Message Queue (Kafka/RabbitMQ)"]:::datastore
    end

    %% Web Dashboard
    subgraph "Web Dashboard"
        DASH["Graphite Dashboard SPA"]:::client
        ASSETS["Static Asset Host (CDN)"]:::service
    end

    %% Supporting Infrastructure
    subgraph "Supporting Infrastructure"
        CICD["CI/CD Pipeline"]:::infra
        MON["Monitoring & Logging"]:::infra
    end

    %% Connections
    CLI -->|"uses Git plumbing"| Git
    CLI -->|"fetch/create PRs"| GH
    CLI -->|"auth, config, stacks"| APIGW
    DASH -->|"API calls"| APIGW
    DASH -->|"serves assets"| ASSETS
    ASSETS -->|"CDN delivery"| DASH

    APIGW -->|"read/write users & stacks"| PG
    APIGW -->|"cache sessions & rate limit"| REDIS
    APIGW -->|"publish events"| MQ
    APIGW -->|"sync PR status"| GH
    APIGW -->|"handles auth"| AUTH

    MQ -.->|"async tasks"| NOTIF
    MQ -.->|"async tasks"| PR
    MQ -.->|"async tasks"| SM

    CICD -->|"deploy services"| APIGW
    CICD -->|"deploy dashboard"| DASH
    MON -->|"monitor metrics/logs"| APIGW
    MON -->|"monitor metrics/logs"| DASH
    MON -->|"monitor metrics/logs"| MQ

    %% Documentation Site to components
    DS4 --> CLI
    DS4 --> DASH

    %% Click Events
    click CLI "https://github.com/withgraphite/docs/tree/main/guides/graphite-cli/"
    click DASH "https://github.com/withgraphite/docs/tree/main/guides/graphite-dashboard/"
    click DS4 "https://github.com/withgraphite/docs/tree/main/getting-started/"
    click DS6 "https://github.com/withgraphite/docs/blob/main/guides/graphite-cli/authenticating-the-cli/using-a-github-personal-access-token.md"
    click DS5 "https://github.com/withgraphite/docs/blob/main/reference/pat-permissions.md"
    click DS1 "https://github.com/withgraphite/docs/tree/main/.gitbook/"
    click DS2 "https://github.com/withgraphite/docs/blob/main/README.md"
    click DS3 "https://github.com/withgraphite/docs/blob/main/SUMMARY.md"

    %% Styles
    classDef client fill:#bbdefb,stroke:#000
    classDef service fill:#c8e6c9,stroke:#000
    classDef datastore fill:#ffe0b2,stroke:#000
    classDef external fill:#e0e0e0,stroke:#000
    classDef infra fill:#d1c4e9,stroke:#000
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