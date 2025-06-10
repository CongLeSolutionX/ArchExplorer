---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExMjBpMHFxcHZhbTBsbXVtdHBxaXFyc21ycGp2ZG11MTRoNW02N2diMiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/87TcngvEXQ14Q/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# National Security Agency - Datawave

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
title: "NATIONAL SECURITY AGENCY - Datawave"
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
flowchart TD
    %% External Layer
    EC("External Clients"):::external
    ExtData("External Raw Data Sources"):::external

    %% API Layer Subgraph
    subgraph API_Layer["API Layer"]
    style API_Layer fill:#cc23,stroke:#333,stroke-width:2px
        APIG("API Gateway / Web Services"):::api
        Client("Client Applications & Gateways"):::api
    end

    %% Processing Components
    QueryE("Query Engine"):::service
    Micro("Microservices Layer"):::service
    IngestionP("Ingestion Pipelines"):::ingestion
    Accumulo("Apache Accumulo Data Store"):::db
    Common("Common/Utility Library"):::utility
    Deploy("Deployment & CI/CD"):::deploy

    %% Data Flow Connections
    EC -->|"API requests"| APIG
    APIG -->|"routes to"| QueryE
    APIG -->|"routes to"| Micro
    APIG -->|"serves"| Client
    QueryE -->|"reads from"| Accumulo
    Micro -->|"reads/writes"| Accumulo
    IngestionP -->|"writes to"| Accumulo
    ExtData -->|"feeds"| IngestionP
    Common -->|"supports"| QueryE
    Common -->|"supports"| Micro
    Deploy -->|"builds"| APIG
    Deploy -->|"builds"| QueryE
    Deploy -->|"builds"| Micro
    Deploy -->|"builds"| IngestionP

    %% Click Events for Ingestion Pipelines
    click IngestionP "https://github.com/nationalsecurityagency/datawave/tree/integration/warehouse/ingest-core"
    click IngestionP "https://github.com/nationalsecurityagency/datawave/tree/integration/warehouse/ingest-csv"
    click IngestionP "https://github.com/nationalsecurityagency/datawave/tree/integration/warehouse/ingest-json"
    click IngestionP "https://github.com/nationalsecurityagency/datawave/tree/integration/warehouse/ingest-nyctlc"
    click IngestionP "https://github.com/nationalsecurityagency/datawave/tree/integration/warehouse/ingest-ssdeep"
    click IngestionP "https://github.com/nationalsecurityagency/datawave/tree/integration/warehouse/ingest-wikipedia"
    click IngestionP "https://github.com/nationalsecurityagency/datawave/tree/integration/warehouse/accumulo-extensions"

    %% Click Events for Query Engine
    click QueryE "https://github.com/nationalsecurityagency/datawave/tree/integration/core/query"
    click QueryE "https://github.com/nationalsecurityagency/datawave/tree/integration/warehouse/query-core"

    %% Click Event for Apache Accumulo Data Store (including in-memory mode)
    click Accumulo "https://github.com/nationalsecurityagency/datawave/tree/integration/core/in-memory-accumulo"

    %% Click Events for Microservices & API Layer
    click Micro "https://github.com/nationalsecurityagency/datawave/tree/integration/microservices"
    click Micro "https://github.com/nationalsecurityagency/datawave/tree/integration/web-services"

    %% Click Events for Core Utilities and Common Libraries
    click Common "https://github.com/nationalsecurityagency/datawave/tree/integration/core/utils/accumulo-utils"
    click Common "https://github.com/nationalsecurityagency/datawave/tree/integration/core/utils/common-utils"
    click Common "https://github.com/nationalsecurityagency/datawave/tree/integration/core/utils/metadata-utils"
    click Common "https://github.com/nationalsecurityagency/datawave/tree/integration/core/base-rest-responses"

    %% Click Events for Client Applications and Gateways
    click Client "https://github.com/nationalsecurityagency/datawave/tree/integration/web-services/client"
    click Client "https://github.com/nationalsecurityagency/datawave/tree/integration/web-services/rest-api"
    click Client "https://github.com/nationalsecurityagency/datawave/tree/integration/microservices/starters/datawave"

    %% Styles
    classDef external fill:#FFCCC,stroke:#CC0000,stroke-width:2px
    classDef api fill:#CFE2F,stroke:#1155CC,stroke-width:2px
    classDef service fill:#D9EAD,stroke:#38761D,stroke-width:2px
    classDef db fill:#FFF2C,stroke:#BF9000,stroke-width:2px
    classDef ingestion fill:#EAD1D,stroke:#B35979,stroke-width:2px
    classDef utility fill:#FFF2C,stroke:#8E7CC3,stroke-width:2px
    classDef deploy fill:#D9D2E,stroke:#8E7CC3,stroke-width:2px
    
```


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
