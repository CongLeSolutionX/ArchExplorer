---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ipfs/kubo
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




# kubo repo project
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
title: "kubo repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'linear' },
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#222B2B',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#2221',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '20px'
    }
  }
}%%
flowchart TD
    %% Frontend Interfaces
    subgraph "Frontend Interfaces"
        CLI["CLI (Entry Point)"]:::external
        HTTP["HTTP API Gateway"]:::external
        WebUI["WebUI Interface"]:::external
    end

    %% Backend Daemon
    subgraph "Backend Service"
        Daemon["IPFS Daemon/Node"]:::backend
    end

    %% Internal Subsystems
    subgraph "Subsystems"
        Core["Core Services (Command Parsing & Core API)"]:::internal
        Networking["Libp2p Networking (DHT, Bitswap)"]:::networking
        Storage["Data Storage (Repo & Config)"]:::storage
        Plugins["Plugin Manager"]:::plugin
        UnixFS_Client["UnixFS Client Support"]:::auxiliary
        UnixFS_Core["UnixFS Core Support"]:::auxiliary
        Blocks["Block Handling"]:::auxiliary
        Fuse["Fuse Mounting Service"]:::auxiliary
    end

    %% Testing Module
    Testing["Testing & Integration"]:::testing

    %% Connections from Frontend to Backend
    CLI -->|"sendsCommand"| Daemon
    HTTP -->|"apiRequest"| Daemon
    WebUI -->|"viaAPI"| HTTP

    %% Internal routing from Daemon to core subsystems
    Daemon -->|"executes"| Core
    Core -->|"handlesNetwork"| Networking
    Core -->|"accessesStorage"| Storage
    Core -->|"invokesPlugin"| Plugins
    Core -->|"processesUnixFS"| UnixFS_Client
    Core -->|"processesUnixFS"| UnixFS_Core
    Core -->|"managesBlocks"| Blocks
    Core -->|"mountsFuse"| Fuse

    %% Testing interacts with the Daemon
    Testing ---|"validates"| Daemon

    %% Click Events for Component Mapping
    click CLI "https://github.com/ipfs/kubo/tree/master/cmd/ipfs"
    click Core "https://github.com/ipfs/kubo/tree/master/core"
    click Storage "https://github.com/ipfs/kubo/tree/master/repo"
    click Networking "https://github.com/ipfs/kubo/tree/master/core/node/libp2p"
    click Networking "https://github.com/ipfs/kubo/tree/master/p2p"
    click Plugins "https://github.com/ipfs/kubo/tree/master/plugin"
    click UnixFS_Client "https://github.com/ipfs/kubo/blob/master/client/rpc/unixfs.go"
    click UnixFS_Core "https://github.com/ipfs/kubo/blob/master/core/coreiface/unixfs.go"
    click Blocks "https://github.com/ipfs/kubo/tree/master/blocks"
    click Fuse "https://github.com/ipfs/kubo/tree/master/fuse"
    click Testing "https://github.com/ipfs/kubo/tree/master/test"

    %% Styles
    classDef external fill:#FFD700,stroke:#DAA520,stroke-width:2px;
    classDef backend fill:#87CEFA,stroke:#4682B4,stroke-width:2px;
    classDef internal fill:#98FB98,stroke:#2E8B57,stroke-width:2px;
    classDef networking fill:#AFEEEE,stroke:#20B2AA,stroke-width:2px;
    classDef storage fill:#FFFACD,stroke:#BDB76B,stroke-width:2px;
    classDef plugin fill:#E6E6FA,stroke:#9370DB,stroke-width:2px;
    classDef auxiliary fill:#FFE4E1,stroke:#CD5C5C,stroke-width:2px;
    classDef testing fill:#F0E68C,stroke:#BDB76B,stroke-width:2px;
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