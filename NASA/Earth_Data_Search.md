---
created: 2025-03-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExbHEwOTMycmU2dXJ1OG5paGtkMzQ1bWFvejFtZGlhbXJqbnh2eTU1MCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/WlBUAWG03Zic8/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Earth Data Search
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
title: "Earth Data Search"
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
    'flowchart': {'htmlLabels': true, 'linear': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#2ff9',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TD
    %% Presentation Layer
    subgraph "Presentation Layer"
        StaticAssets["React/Vite - Static Assets"]:::frontend
    end

    %% API Layer
    subgraph "API Layer"
        APIGateway["API Gateway"]:::api
        LambdaEDL["Lambda - EDL Login"]:::lambda
        LambdaCMR["Lambda - CMR Granule Search"]:::lambda
        LambdaPM["Lambda - Project Management"]:::lambda
    end

    %% Data & Infrastructure Layer
    subgraph "Data & Infrastructure Layer"
        PostgresDB["PostgreSQL DB"]:::db
        SQS["SQS Queue"]:::queue
        StepFunctions["Step Functions"]:::step
        AWSInfra["AWS Infrastructure (CDK)"]:::infra
    end

    %% External Services
    subgraph "External Services"
        EDLService["Earthdata Login API"]:::external
        CMRService["CMR API"]:::external
        GIBSService["GIBS API"]:::external
    end

    %% User Interaction
    User["User Browser"]:::frontend

    %% Data Flow
    User --> |"accesses"| StaticAssets
    StaticAssets --> |"requests"| APIGateway
    APIGateway -->|"routes to"| LambdaEDL
    APIGateway -->|"routes to"| LambdaCMR
    APIGateway -->|"routes to"| LambdaPM

    LambdaEDL -->|"reads/writes"| PostgresDB
    LambdaCMR -->|"reads/writes"| PostgresDB
    LambdaPM -->|"reads/writes"| PostgresDB

    LambdaEDL -->|"calls"| EDLService
    LambdaCMR -->|"calls"| CMRService
    LambdaPM -->|"queues to"| SQS
    LambdaPM -->|"orchestrates"| StepFunctions
    LambdaPM -->|"calls"| GIBSService

    %% AWS Infrastructure management
    AWSInfra -.->|manages| APIGateway
    AWSInfra -.->|manages| LambdaEDL
    AWSInfra -.->|manages| LambdaCMR
    AWSInfra -.->|manages| LambdaPM
    AWSInfra -.->|manages| PostgresDB
    AWSInfra -.->|manages| SQS
    AWSInfra -.->|manages| StepFunctions

    %% Click Events
    click StaticAssets "https://github.com/nasa/earthdata-search/tree/main/static/"
    click LambdaEDL "https://github.com/nasa/earthdata-search/tree/main/serverless/src/edlLogin"
    click LambdaCMR "https://github.com/nasa/earthdata-search/tree/main/serverless/src/cmrGranuleSearch"
    click LambdaPM "https://github.com/nasa/earthdata-search/tree/main/serverless/src/"
    click AWSInfra "https://github.com/nasa/earthdata-search/tree/main/cdk/"
    click PostgresDB "https://github.com/nasa/earthdata-search/tree/main/migrations/"
    click EDLService "https://github.com/nasa/earthdata-search/tree/main/serverless/src/edlLogin"
    click CMRService "https://github.com/nasa/earthdata-search/tree/main/serverless/src/cmrGranuleSearch"
    click GIBSService "https://github.com/nasa/earthdata-search/tree/main/serverless/src/"

    %% Styles
    classDef frontend fill:#f9f3,stroke:#333,stroke-width:2px;
    classDef api fill:#bbf3,stroke:#333,stroke-width:2px;
    classDef lambda fill:#ff93,stroke:#333,stroke-width:2px;
    classDef db fill:#dfd3,stroke:#333,stroke-width:2px;
    classDef queue fill:#fdd3,stroke:#333,stroke-width:2px;
    classDef step fill:#ffd3,stroke:#333,stroke-width:2px;
    classDef infra fill:#cfc3,stroke:#333,stroke-width:2px;
    classDef external fill:#fcc3,stroke:#333,stroke-width:2px;
    
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

  Closing_quote ~~~ My_Meme
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }

```

---
> **Licenses:**
>
> - **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
> - **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).
> 
---

