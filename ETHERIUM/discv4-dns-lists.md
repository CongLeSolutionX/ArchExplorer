---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/discv4-dns-lists
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExODJ3OThodjN2YWQzdGVkM3draHpnb3p3ZGFtdWJ0Y3E5eTFhMWxqaSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/QtvaPwpypcCAUu1PTy/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# discv4-dns-lists repo project
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
title: "discv4-dns-lists repo project"
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
    %% External Discovery DHT
    DiscoveryDHT["Discovery DHT"]:::external

    %% Compute Components
    Crawler["Crawler (Go-Ethereum devp2p)"]:::compute
    FilterEngine["Filter Engine"]:::compute

    %% Storage Components
    RawJSON["Raw JSON Store<br/>(all.json)"]:::storage

    %% DNS Components
    DNSPublisher["DNS Publisher"]:::dns

    %% Clients
    Clients["Ethereum Clients / Tooling"]:::external

    %% Pipeline Flow
    DiscoveryDHT -->|crawls nodes| Crawler
    Crawler -->|writes all.json| RawJSON
    RawJSON -->|reads all.json| FilterEngine
    FilterEngine -->|emits nodes.json & enrtree-info.json| DNSZoneDirs
    DNSZoneDirs -->|served via DNS| DNSPublisher
    DNSPublisher -->|responds with JSON| Clients

    %% DNS Zone Directories Cluster
    subgraph "DNS Zone Directories"
        direction TB
        subgraph "all.mainnet.ethdisco.net"
            enr_all_mainnet["enrtree-info.json"]:::storage
            nodes_all_mainnet["nodes.json"]:::storage
        end
        subgraph "all.sepolia.ethdisco.net"
            enr_all_sepolia["enrtree-info.json"]:::storage
            nodes_all_sepolia["nodes.json"]:::storage
        end
        subgraph "all.holesky.ethdisco.net"
            enr_all_holesky["enrtree-info.json"]:::storage
            nodes_all_holesky["nodes.json"]:::storage
        end
        subgraph "all.hoodi.ethdisco.net"
            enr_all_hoodi["enrtree-info.json"]:::storage
            nodes_all_hoodi["nodes.json"]:::storage
        end
        subgraph "les.mainnet.ethdisco.net"
            enr_les_mainnet["enrtree-info.json"]:::storage
            nodes_les_mainnet["nodes.json"]:::storage
        end
        subgraph "les.sepolia.ethdisco.net"
            enr_les_sepolia["enrtree-info.json"]:::storage
            nodes_les_sepolia["nodes.json"]:::storage
        end
        subgraph "snap.mainnet.ethdisco.net"
            enr_snap_mainnet["enrtree-info.json"]:::storage
            nodes_snap_mainnet["nodes.json"]:::storage
        end
        subgraph "snap.sepolia.ethdisco.net"
            enr_snap_sepolia["enrtree-info.json"]:::storage
            nodes_snap_sepolia["nodes.json"]:::storage
        end
        subgraph "snap.holesky.ethdisco.net"
            enr_snap_holesky["enrtree-info.json"]:::storage
            nodes_snap_holesky["nodes.json"]:::storage
        end
        subgraph "snap.hoodi.ethdisco.net"
            enr_snap_hoodi["enrtree-info.json"]:::storage
            nodes_snap_hoodi["nodes.json"]:::storage
        end
    end

    %% Documentation
    README["README.md"]:::doc
    LICENSE["LICENSE"]:::doc

    %% Click Events
    click RawJSON "https://github.com/ethereum/discv4-dns-lists/blob/master/all.json"
    click enr_all_mainnet "https://github.com/ethereum/discv4-dns-lists/blob/master/all.mainnet.ethdisco.net/enrtree-info.json"
    click nodes_all_mainnet "https://github.com/ethereum/discv4-dns-lists/blob/master/all.mainnet.ethdisco.net/nodes.json"
    click enr_all_sepolia "https://github.com/ethereum/discv4-dns-lists/blob/master/all.sepolia.ethdisco.net/enrtree-info.json"
    click nodes_all_sepolia "https://github.com/ethereum/discv4-dns-lists/blob/master/all.sepolia.ethdisco.net/nodes.json"
    click enr_all_holesky "https://github.com/ethereum/discv4-dns-lists/blob/master/all.holesky.ethdisco.net/enrtree-info.json"
    click nodes_all_holesky "https://github.com/ethereum/discv4-dns-lists/blob/master/all.holesky.ethdisco.net/nodes.json"
    click enr_all_hoodi "https://github.com/ethereum/discv4-dns-lists/blob/master/all.hoodi.ethdisco.net/enrtree-info.json"
    click nodes_all_hoodi "https://github.com/ethereum/discv4-dns-lists/blob/master/all.hoodi.ethdisco.net/nodes.json"
    click enr_les_mainnet "https://github.com/ethereum/discv4-dns-lists/blob/master/les.mainnet.ethdisco.net/enrtree-info.json"
    click nodes_les_mainnet "https://github.com/ethereum/discv4-dns-lists/blob/master/les.mainnet.ethdisco.net/nodes.json"
    click enr_les_sepolia "https://github.com/ethereum/discv4-dns-lists/blob/master/les.sepolia.ethdisco.net/enrtree-info.json"
    click nodes_les_sepolia "https://github.com/ethereum/discv4-dns-lists/blob/master/les.sepolia.ethdisco.net/nodes.json"
    click enr_snap_mainnet "https://github.com/ethereum/discv4-dns-lists/blob/master/snap.mainnet.ethdisco.net/enrtree-info.json"
    click nodes_snap_mainnet "https://github.com/ethereum/discv4-dns-lists/blob/master/snap.mainnet.ethdisco.net/nodes.json"
    click enr_snap_sepolia "https://github.com/ethereum/discv4-dns-lists/blob/master/snap.sepolia.ethdisco.net/enrtree-info.json"
    click nodes_snap_sepolia "https://github.com/ethereum/discv4-dns-lists/blob/master/snap.sepolia.ethdisco.net/nodes.json"
    click enr_snap_holesky "https://github.com/ethereum/discv4-dns-lists/blob/master/snap.holesky.ethdisco.net/enrtree-info.json"
    click nodes_snap_holesky "https://github.com/ethereum/discv4-dns-lists/blob/master/snap.holesky.ethdisco.net/nodes.json"
    click enr_snap_hoodi "https://github.com/ethereum/discv4-dns-lists/blob/master/snap.hoodi.ethdisco.net/enrtree-info.json"
    click nodes_snap_hoodi "https://github.com/ethereum/discv4-dns-lists/blob/master/snap.hoodi.ethdisco.net/nodes.json"
    click README "https://github.com/ethereum/discv4-dns-lists/blob/master/README.md"
    click LICENSE "https://github.com/ethereum/discv4-dns-lists/tree/master/LICENSE"

    %% Styles
    classDef compute fill:#ADD8E6,stroke:#000,stroke-width:1px
    classDef storage fill:#90EE90,stroke:#000,stroke-width:1px
    classDef external fill:#F0E68C,stroke:#000,stroke-width:1px
    classDef dns fill:#FFD700,stroke:#000,stroke-width:1px
    classDef doc fill:#D3D3D3,stroke:#000,stroke-width:1px

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
