---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/github/docs
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExd3VwcHgzZWxnbTc3eWUwd2NpdnEwem9wdWVxemZ1eDE1aHpmZmlhdSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/N35rW3vRNeaDC/giphy.gif)
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
> The materials are intended for educational purposes, personal study, and reference.
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
    %% Content & Data Layer
    subgraph "Content & Data Layer"
        ContentStore["Content Store\n(Markdown, data, assets)"]:::content
        DataStore["Data Store\n(YAML/JSON/CSV)"]:::content
        Assets["Assets\n(Images, static files)"]:::content
        subgraph "Pipelines"
            CR["content-render"]:::content
            CL["content-linter"]:::content
            DD["data-directory"]:::content
            AP["automated-pipelines"]:::content
            GHES["ghes-releases"]:::content
        end
    end

    %% Application Layer
    subgraph "Application Layer"
        NextServer["Next.js Server\n(Frontend & API Routes)"]:::compute

        subgraph "Frontend"
            Frame["Frame & Layout"]:::compute
            Pages["Pages\n([version]/[product] routes)"]:::compute
            Landings["Static Landings"]:::compute
            Versions["Version Picker"]:::compute
            Languages["Language Middleware"]:::compute
        end

        subgraph "API Services"
            ArticleAPI["Article API"]:::compute
            RESTAPI["REST API"]:::compute
            GraphQLAPI["GraphQL API"]:::compute
            SearchAPI["Search API"]:::compute
            AuditAPI["Audit Logs API"]:::compute
            Webhooks["Webhooks API"]:::compute
            SecretScan["Secret Scanning API"]:::compute
        end

        subgraph "Shared Libraries"
            CR2["content-render"]:::compute
            CL2["content-linter"]:::compute
            DD2["data-directory"]:::compute
        end

        subgraph "Observability & Middleware"
            Observability["Observability\n(StatsD, failbot)"]:::compute
            Shield["Shielding Middleware"]:::compute
            Tracking["Tracking Middleware"]:::compute
        end

        subgraph "Tests & Monitoring"
            Tests["Tests\n(Playwright, Vitest)"]:::compute
            Fixtures["Fixtures"]:::compute
            Vitest["Vitest Config"]:::compute
        end
    end

    %% Infrastructure Layer
    subgraph "Infrastructure Layer"
        CI["GitHub Actions CI/CD"]:::infra
        CQ["Custom Actions"]:::infra
        Dockerfile["Dockerfile"]:::infra
        DC["docker-compose.yaml"]:::infra
        DevContainer[".devcontainer"]:::infra
        K8s["Kubernetes Cluster"]:::infra
        Moda["Feature Flags"]:::infra
        CDN["CDN / Fastly"]:::external
        ES["Elasticsearch Cluster"]:::external
        S3["S3 / Minio"]:::external
    end

    %% Data & Build Flows
    ContentStore --> CR --> NextServer
    DataStore --> DD --> NextServer
    Assets --> NextServer
    CL --> NextServer

    %% Developer & CI/CD
    Developer["Developer Commit"]:::external --> CI
    CI --> Dockerfile
    CI --> DC
    CI --> Tests
    CI --> CQ
    CQ --> Tests
    CI -->|build image| K8s

    %% Deployment
    K8s --> NextServer

    %% Client Requests
    Client["Client Browser"]:::external --> CDN
    CDN --> NextServer
    NextServer -->|serves pages & JSON| CDN

    %% API calls
    NextServer --> ArticleAPI
    NextServer --> RESTAPI
    NextServer --> GraphQLAPI
    NextServer --> SearchAPI
    NextServer --> AuditAPI
    NextServer --> Webhooks
    NextServer --> SecretScan

    SearchAPI --> ES
    NextServer --> S3

    %% Shared libs & middleware usage
    NextServer --> CR2
    NextServer --> CL2
    NextServer --> DD2
    NextServer --> Observability
    NextServer --> Shield
    NextServer --> Tracking

    %% Testing
    CI --> Fixtures
    CI --> Vitest

    %% Classes and Styles
    classDef content fill:#cce5ff,stroke:#004085,color:#004085
    classDef compute fill:#d4edda,stroke:#155724,color:#155724
    classDef infra fill:#e2e3e5,stroke:#383d41,color:#383d41
    classDef external fill:#fff3cd,stroke:#856404,color:#856404

    %% Click Events
    click ContentStore "https://github.com/github/docs/tree/main/content/"
    click DataStore "https://github.com/github/docs/tree/main/data/"
    click Assets "https://github.com/github/docs/tree/main/assets/"
    click CR "https://github.com/github/docs/tree/main/src/content-render/"
    click CL "https://github.com/github/docs/tree/main/src/content-linter/"
    click DD "https://github.com/github/docs/tree/main/src/data-directory/"
    click AP "https://github.com/github/docs/tree/main/src/automated-pipelines/"
    click GHES "https://github.com/github/docs/tree/main/src/ghes-releases/"
    click Frame "https://github.com/github/docs/tree/main/src/frame/"
    click Pages "https://github.com/github/docs/tree/main/src/pages/"
    click Landings "https://github.com/github/docs/tree/main/src/landings/"
    click Versions "https://github.com/github/docs/tree/main/src/versions/"
    click Languages "https://github.com/github/docs/tree/main/src/languages/"
    click ArticleAPI "https://github.com/github/docs/tree/main/src/article-api/"
    click RESTAPI "https://github.com/github/docs/tree/main/src/rest/"
    click GraphQLAPI "https://github.com/github/docs/tree/main/src/graphql/"
    click SearchAPI "https://github.com/github/docs/tree/main/src/search/"
    click AuditAPI "https://github.com/github/docs/tree/main/src/audit-logs/"
    click Webhooks "https://github.com/github/docs/tree/main/src/webhooks/"
    click SecretScan "https://github.com/github/docs/tree/main/src/secret-scanning/"
    click Observability "https://github.com/github/docs/tree/main/src/observability/"
    click Shield "https://github.com/github/docs/tree/main/src/shielding/"
    click Tracking "https://github.com/github/docs/tree/main/src/tracking/"
    click Tests "https://github.com/github/docs/tree/main/src/tests/"
    click Fixtures "https://github.com/github/docs/tree/main/src/fixtures/"
    click Vitest "https://github.com/github/docs/blob/main/vitest.config.ts"
    click CI "https://github.com/github/docs/tree/main/.github/workflows/"
    click CQ "https://github.com/github/docs/tree/main/.github/actions/"
    click Dockerfile "https://github.com/github/docs/tree/main/Dockerfile"
    click DC "https://github.com/github/docs/blob/main/docker-compose.yaml"
    click DevContainer "https://github.com/github/docs/tree/main/.devcontainer/"
    click K8s "https://github.com/github/docs/tree/main/config/kubernetes/"
    click Moda "https://github.com/github/docs/tree/main/config/moda/"
    
```

------

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