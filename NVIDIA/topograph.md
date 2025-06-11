---
created: 2025-03-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExajNzeTF0OXY3em84bG5jYWdtYjh3cHd6bTNna2tnYWF0N2xiZ2ptbSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3q0h46XjxT0kdCih6M/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Topograph
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
title: "CHANGE_ME_DADDY"
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
    "graph": { "htmlLabels": false, 'curve': 'linear' },
    'themeVariables': {
        'fontFamily': 'Fantasy',
        'fontSize': '20px',
        'primaryColor': '#ffff',
        'primaryTextColor': '#55ff',
        'primaryBorderColor': '#7c2',
        'lineColor': '#F8B229',
        'secondaryColor': '#006100',
        'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TD
    %% External client
    Client["Client/Cluster Environment"]:::external

    %% Main services
    node_api["API Server<br>(HTTP endpoints)"]:::service
    node_observer["Node Observer<br>(Kubernetes watch)"]:::service
    node_grpc["gRPC Communication<br>(pkg/protos)"]:::protocol
    node_provider["Provider<br>(CSP integration)"]:::service
    node_engine["Engine<br>(Topology transformation)"]:::service

    %% Deployment & Configuration subgraph
    subgraph Deployment_and_Configuration["Deployment & Configuration"]
        configFile["Config File"]:::deployment
        helmObs["Helm Chart<br>(Node Observer)"]:::deployment
        helmTopo["Helm Chart<br>(Topograph)"]:::deployment
    end

    %% Data flow
    Client -->|"sends request"| node_api
    node_observer -->|"notifies"| node_api
    node_api -->|"uses GRPC"| node_grpc
    node_grpc -->|"fetches data"| node_provider
    node_provider -->|"sends topology"| node_engine
    node_engine -->|"responses"| Client

    %% Deployment links (dashed)
    configFile -.-> node_api
    configFile -.-> node_engine
    helmObs -.-> node_observer
    helmTopo -.-> node_api

    %% Click Events
    click node_api "https://github.com/nvidia/topograph/blob/main/cmd/topograph/main.go"
    click node_observer "https://github.com/nvidia/topograph/blob/main/cmd/node-observer/main.go"
    click node_provider "https://github.com/nvidia/topograph/tree/main/pkg/providers"
    click node_engine "https://github.com/nvidia/topograph/tree/main/pkg/engines"
    click node_grpc "https://github.com/nvidia/topograph/tree/main/pkg/protos"
    click configFile "https://github.com/nvidia/topograph/blob/main/config/topograph-config.yaml"
    click helmObs "https://github.com/nvidia/topograph/tree/main/charts/node-observer"
    click helmTopo "https://github.com/nvidia/topograph/tree/main/charts/topograph"

    %% Styles
    classDef external fill:#f9c7,stroke:#333,stroke-width:2px
    classDef service fill:#90be,stroke:#333,stroke-width:2px
    classDef protocol fill:#f941,stroke:#333,stroke-width:2px
    classDef deployment fill:#5775,stroke:#333,stroke-width:2px, color:#fff
    
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
