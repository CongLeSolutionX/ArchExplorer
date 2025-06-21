---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/hive
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExamV1ajI2MmtzZW5ocTNkNmg4enV6OWtyenVwcWx6eWpsem8zajBlZCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/eVSqI3mZYfaDIXYsnS/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----



# hive repo project
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
title: "hive repo project"
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
    %% Layers
    subgraph "Orchestrator Layer"
    direction TB
        CLI["hive CLI (Go)"]:::orchestrator
        Hivechain["hivechain CLI (EVM Test Runner)"]:::orchestrator
        LibDocker["libdocker"]:::library
        LibHive["libhive"]:::library
    end

    subgraph "Infrastructure Layer"
    direction TB
        DockerDaemon["Docker Daemon"]:::infra
        subgraph "Execution-Layer Clients"
            direction TB
            Geth["geth container"]:::container
            Erigon["erigon container"]:::container
        end
        subgraph "Consensus-Layer Clients"
        direction TB
            LighthouseBN["Lighthouse BN container"]:::container
            PrysmVC["Prysm VC container"]:::container
        end
    end

    subgraph "Simulation Layer"
    direction TB
        subgraph "Go Simulators"
        direction TB
            SimEth["Ethereum JSON-RPC & Engine API Simulator"]:::simulator
            SimEth2["ETH2 Consensus Simulator"]:::simulator
            SimDevP2P["DevP2P Simulator"]:::simulator
            SimSmoke["Smoke-test Simulator"]:::simulator
            HivesimGo["hivesim (Go)"]:::simulator
        end
        subgraph "Rust Simulator"
        direction TB
            HivesimRs["hivesim-rs (Rust)"]:::simulator
        end
    end

    subgraph "Proxy Layer"
    direction TB
        Hiveproxy["hiveproxy"]:::proxy
    end

    subgraph "Presentation Layer"
    direction TB
        Hiveview["hiveview UI Server"]:::presentation
        Assets["Static Assets (HTML/CSS/JS)"]:::presentation
    end

    %% Relationships
    CLI -->|"uses"| LibDocker
    CLI -->|"uses"| LibHive
    Hivechain -->|"uses"| LibDocker
    LibDocker -->|"controls"| DockerDaemon
    DockerDaemon -->|"spins up"| Geth
    DockerDaemon -->|"spins up"| Erigon
    DockerDaemon -->|"spins up"| LighthouseBN
    DockerDaemon -->|"spins up"| PrysmVC

    Hivechain -->|"invokes tests"| SimEth
    Hivechain -->|" "| SimEth2
    Hivechain -->|" "| SimDevP2P
    Hivechain -->|" "| SimSmoke
    Hivechain -->|" "| HivesimGo
    Hivechain -->|" "| HivesimRs

    SimEth -->|"RPC/Engine API"| Geth
    SimEth -->|"RPC/Engine API via proxy"| Hiveproxy
    Hiveproxy -->|"forwards"| Geth
    SimEth2 -->|"Consensus API"| LighthouseBN
    SimDevP2P -->|"DevP2P"| Geth
    SimSmoke -->|"Smoke Tests"| PrysmVC
    HivesimGo -->|"Engine API"| Erigon
    HivesimRs -->|"Engine API"| LighthouseBN

    Hivechain -->|"test results"| LibHive
    LibHive -->|"logs/metrics"| CLI

    Hiveview -->|"polls API"| CLI
    Hiveview -->|"serves assets"| Assets

    %% Click events
    click CLI "https://github.com/ethereum/hive/blob/master/hive.go"
    click Hivechain "https://github.com/ethereum/hive/blob/master/cmd/hivechain/main.go"
    click Hiveview "https://github.com/ethereum/hive/blob/master/cmd/hiveview/main.go"
    click LibDocker "https://github.com/ethereum/hive/blob/master/internal/libdocker/docker.go"
    click LibDocker "https://github.com/ethereum/hive/blob/master/internal/libdocker/container.go"
    click LibHive "https://github.com/ethereum/hive/blob/master/internal/libhive/run.go"
    click LibHive "https://github.com/ethereum/hive/blob/master/internal/libhive/testmanager.go"
    click SimEth "https://github.com/ethereum/hive/tree/master/simulators/ethereum/"
    click SimEth2 "https://github.com/ethereum/hive/tree/master/simulators/eth2/"
    click SimDevP2P "https://github.com/ethereum/hive/blob/master/simulators/devp2p/main.go"
    click SimSmoke "https://github.com/ethereum/hive/tree/master/simulators/smoke/"
    click HivesimGo "https://github.com/ethereum/hive/blob/master/hivesim/hive.go"
    click HivesimRs "https://github.com/ethereum/hive/blob/master/hivesim-rs/src/lib.rs"
    click Hiveproxy "https://github.com/ethereum/hive/blob/master/hiveproxy/proxy.go"
    click Hiveproxy "https://github.com/ethereum/hive/blob/master/hiveproxy/checklive.go"
    click Assets "https://github.com/ethereum/hive/blob/master/cmd/hiveview/assets/index.html"
    click Assets "https://github.com/ethereum/hive/blob/master/cmd/hiveview/assets/lib/app-common.js"

    %% Styles
    classDef orchestrator fill:#D0E8FF,stroke:#0284C7,stroke-width:1px
    classDef infra fill:#F0F0F0,stroke:#888888,stroke-width:1px
    classDef container fill:#E8E8E8,stroke:#555555,stroke-width:1px
    classDef simulator fill:#E6FFE6,stroke:#28A745,stroke-width:1px
    classDef proxy fill:#FFF5E6,stroke:#FF8C00,stroke-width:1px
    classDef presentation fill:#F0E6FF,stroke:#6B21A8,stroke-width:1px
    classDef library fill:#E6F7FF,stroke:#1C64F2,stroke-width:1px

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
