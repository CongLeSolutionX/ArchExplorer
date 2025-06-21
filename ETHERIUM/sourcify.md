---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/sourcify
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExanhvM24wZTYxY3E5cHR0MjR4YWNyaThvZmNqbzlqenoyYTI2anRsZSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/XI7zkv4X89kcsmLJnV/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# sourcify repo project
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
title: "sourcify repo project"
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
flowchart TB
    %% Clients
    subgraph "Clients"
        UI["Sourcify UI/CLI"]:::external
    end

    %% External Systems
    subgraph "External Systems"
        EVM["EVM Nodes"]:::external
        Etherscan["Etherscan & Chain RPC"]:::external
        IPFS["IPFS/Swarm"]:::external
        VerifierChains["Verifier-Alliance Chains"]:::external
    end

    %% Backend Services
    subgraph "Backend Services"
        Monitor["sourcify-monitor (TypeScript)"]:::service
        Server["sourcify-server (TypeScript/Express)"]:::service
    end

    %% Persistence Layer
    subgraph "Persistence"
        DB["PostgreSQL"]:::service
        ObjStorage["Object Storage (S3/Local FS)"]:::service
    end

    %% Verification Core
    subgraph "Verification Core"
        BC["bytecode-utils"]:::core
        CP["compilers (Solidity/Vyper wrappers)"]:::core
        CT["compilers-types"]:::core
        LS["lib-sourcify"]:::core
    end

    %% CI/CD & DevOps
    subgraph "CI/CD & DevOps"
        CircleCI[".circleci Workflows"]:::tool
        Scripts["scripts/"]:::tool
        DockerServer["services/server/Dockerfile"]:::tool
        DockerMonitor["services/monitor/Dockerfile"]:::tool
    end

    %% Data Flows
    UI -->|"HTTP/JSON"| Server
    UI -->|"HTTP/JSON"| Server
    EVM -.poll/RPC.-> Monitor
    Etherscan -.poll/EtherscanSDK.-> Monitor
    Monitor -->|"HTTP/JSON"| Server
    Server -->|"invokes"| BC
    Server -->|"invokes"| CP
    Server -->|"uses types from"| CT
    Server -->|"uses core lib"| LS
    Server -->|"store results"| DB
    Server -->|"store sources"| ObjStorage
    UI -->|"query via HTTP"| Server

    %% CI/CD flows
    CircleCI -->|build/deploy| DockerServer
    CircleCI -->|build/deploy| DockerMonitor
    CircleCI -->|run scripts| Scripts

    %% Click Events
    click Server "https://github.com/ethereum/sourcify/tree/staging/services/server"
    click Monitor "https://github.com/ethereum/sourcify/tree/staging/services/monitor"
    click DB "https://github.com/ethereum/sourcify/tree/staging/services/database"
    click LS "https://github.com/ethereum/sourcify/tree/staging/packages/lib-sourcify"
    click BC "https://github.com/ethereum/sourcify/tree/staging/packages/bytecode-utils"
    click CP "https://github.com/ethereum/sourcify/tree/staging/packages/compilers"
    click CT "https://github.com/ethereum/sourcify/tree/staging/packages/compilers-types"
    click CircleCI "https://github.com/ethereum/sourcify/blob/staging/.circleci"
    click Scripts "https://github.com/ethereum/sourcify/tree/staging/scripts/"
    click DockerServer "https://github.com/ethereum/sourcify/tree/staging/services/server/Dockerfile"
    click DockerMonitor "https://github.com/ethereum/sourcify/tree/staging/services/monitor/Dockerfile"

    %% Styles
    classDef service fill:#ADD8E6,stroke:#000,stroke-width:1px
    classDef core fill:#90EE90,stroke:#000,stroke-width:1px
    classDef external fill:#FFA500,stroke:#000,stroke-width:1px
    classDef tool fill:#FFD700,stroke:#000,stroke-width:1px
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
