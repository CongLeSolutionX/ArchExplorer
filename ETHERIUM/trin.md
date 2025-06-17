---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/trin
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExanZydm52NDcyNWIwMWtneG9uOWk4aGpseXQ1bHR4b3c1N2x3MnB6bSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/m3XqQ8QhuIUuQau7n5/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# trin repo project
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
title: "trin repo project"
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
    %% Binaries Group
    subgraph Binaries["Binaries"]
        Main_CLI("Main CLI<br/>(trin)"):::binary
        Exec_Engine("Execution Engine<br/>(trin-execution)"):::binary
        Portal_Bridge("Portal Bridge"):::binary
        E2HS_Writer("E2HS Writer"):::binary
    end

    %% Libraries/Crates Group
    subgraph Libraries_Crates["Libraries/Crates"]
        Portalnet("Networking<br/>(portalnet crate)"):::library
        RPC_API("RPC/JSON API"):::library
        ETH_API("Ethereum Protocol API"):::library
        EVM_Lib("EVM/Execution Logic<br/>(Library)"):::library
        Consensus("Consensus & Light Client"):::library
        Storage("Storage & State Management"):::library
        Validation("Validation"):::library
        Metrics_Lib("Metrics & Logging<br/>(Metrics Lib)"):::library
        Utils("Utilities & Common Libraries"):::utility
    end

    %% Execution Engine Extensions Group
    subgraph Execution_Engine_Extensions["Execution Engine Extensions"]
        EVM_Bin("EVM/Execution Logic<br/>(Bin Extension)"):::library
        Metrics_Config("Metrics & Logging<br/>(Config)"):::config
    end

    %% Documentation & Config Group
    subgraph Documentation_Config["Documentation & Config"]
        Documentation("Documentation"):::doc
    end

    %% Connections between Binaries and Libraries
    Main_CLI -->|"uses"| Portalnet
    Main_CLI -->|"calls"| RPC_API
    Portal_Bridge -->|"bridges"| Portalnet
    Portal_Bridge -->|"coordinates"| Consensus
    Exec_Engine -->|"executes"| EVM_Lib
    Exec_Engine -->|"extends"| EVM_Bin
    Exec_Engine -->|"configures"| Metrics_Config
    RPC_API -->|"abstracts"| ETH_API
    Consensus -->|"stores"| Storage
    Consensus -->|"validates"| Validation

    %% Utilities support arrows from libraries
    Portalnet -->|"utilizes"| Utils
    RPC_API -->|"utilizes"| Utils
    ETH_API -->|"utilizes"| Utils
    EVM_Lib -->|"utilizes"| Utils
    Consensus -->|"utilizes"| Utils
    Storage -->|"utilizes"| Utils
    Validation -->|"utilizes"| Utils
    Metrics_Lib -->|"utilizes"| Utils

    %% Metrics monitoring
    Main_CLI -->|"monitors"| Metrics_Lib
    Portal_Bridge -->|"monitors"| Metrics_Lib
    RPC_API -->|"monitors"| Metrics_Lib

    %% E2HS Writer connection
    E2HS_Writer -->|"writes to"| Storage

    %% Class Definitions
    classDef binary fill:#a0e7a0,stroke:#333,stroke-width:2px;
    classDef library fill:#a0c4ff,stroke:#333,stroke-width:2px;
    classDef config fill:#ffb3ba,stroke:#333,stroke-width:2px;
    classDef doc fill:#ffffba,stroke:#333,stroke-width:2px;
    classDef utility fill:#ffdfba,stroke:#333,stroke-width:2px;

    %% Click Events
    click Main_CLI "https://github.com/ethereum/trin/tree/master/bin/trin"
    
    click Exec_Engine "https://github.com/ethereum/trin/tree/master/bin/trin-execution"
    
    click Portal_Bridge "https://github.com/ethereum/trin/tree/master/bin/portal-bridge"
    

	%%%% Correction:
	%%%% using given mapping 'bin/trin-executive' not provided; using original mapping below.
    %%click E2HS_Writer "https://github.com/ethereum/trin/tree/master/bin/trin-executive"  
    
    %%%% However, mapping provided is 'bin/e2hs-writer'
    %%click E2HS_Writer "https://github.com/ethereum/trin/tree/master/bin/trin-e2hs-writer" 
    
    
    %% click E2HS_Writer "https://github.com/ethereum/trin/tree/master/bin/e2hs-writer"
    %%click Portalnet "https://github.com/ethereum/trin/tree/master/crates/portalnet"
    %%click RPC_API "https://github.com/ethereum/trin/tree/master/crates/rpc"
    %%click ETH_API "https://github.com/ethereum/trin/tree/master/crates/ethportal-api"
    %%click EVM_Lib "https://github.com/ethereum/trin/tree/master/crates/evm"
    %%click EVM_Bin "https://github.com/ethereum/trin/tree/master/bin/trin-execution/src/evm"
    %%click Consensus "https://github.com/ethereum/trin/tree/master/crates/light-client"
    %%click Storage "https://github.com/ethereum/trin/tree/master/crates/storage"
    %%click Validation "https://github.com/ethereum/trin/tree/master/crates/validation"
    %%click Metrics_Lib "https://github.com/ethereum/trin/tree/master/crates/metrics"
    
    %%click Metrics_Config "https://github.com/ethereum/trin/tree/master/bin/trin-execution/metrics"
    
    %%click Utils "https://github.com/ethereum/trin/tree/master/crates/utils"
    
    %%click Documentation "https://github.com/ethereum/trin/tree/master/book"

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