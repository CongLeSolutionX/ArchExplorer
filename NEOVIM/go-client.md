---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/neovim/go-client
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




# go-client repo project
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
title: "go-client repo project"
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
    %% Examples
    subgraph "Examples" 
        direction TB
        RemoteClient["Standalone Remote Client"]:::example
        LuaPluginDemo["Lua Plugin Demo"]:::example
    end

    %% Core Layers
    GoApp["Go App/Plugin Entry Point"]:::external

    subgraph "High-Level API Client"
        direction TB
        APIClient["nvim package (API Client)"]:::api
    end

    subgraph "RPC Layer"
        direction TB
        RPCLayer["msgpack/rpc package"]:::rpc
    end

    subgraph "Serialization Codec"
        direction TB
        Codec["msgpack package"]:::serialization
    end

    subgraph "Transport Layer"
        direction TB
        Transport["Unix & Windows Transports"]:::transport
    end

    Neovim["Neovim Process"]:::external

    %% Plugin Helpers
    subgraph "Plugin Support (nvim/plugin)"
        direction TB
        PluginGo["plugin.go"]:::plugin
        PluginMain["main.go"]:::plugin
    end

    %% Test Harness
    nvimTest["nvimtest Test Harness"]:::test

    %% Connections for standalone client
    RemoteClient -->|"uses"| APIClient
    APIClient -->|"calls RPC"| RPCLayer
    RPCLayer -->|"encodes/decodes"| Codec
    Codec -->|"reads/writes []byte"| Transport
    Transport -->|"stdin/stdout or socket"| Neovim
    Neovim -->|"responses"| Transport
    Transport -->|"[]byte"| Codec
    Codec -->|"unpacked values"| RPCLayer
    RPCLayer -->|"RPC responses"| APIClient
    APIClient -->|"returns results"| RemoteClient

    %% Connections for plugin
    Neovim -->|"Msgpack-RPC calls"| RPCLayer
    RPCLayer -->|"dispatch to plugin"| PluginGo
    PluginGo -->|"invokes helper"| PluginMain
    PluginMain -->|"uses RPC server"| RPCLayer
    RPCLayer -->|"Msgpack-RPC"| Neovim

    %% Test harness connection
    nvimTest -->|"mocks Neovim on"| Transport

    %% Click events
    click RemoteClient "https://github.com/neovim/go-client/blob/main/examples/remote/helloremote/main.go"
    click LuaPluginDemo "https://github.com/neovim/go-client/blob/main/examples/remote/plugin/hello.lua"
    click APIClient "https://github.com/neovim/go-client/tree/main/nvim/"
    click RPCLayer "https://github.com/neovim/go-client/tree/main/msgpack/rpc/"
    click Codec "https://github.com/neovim/go-client/tree/main/msgpack/"
    click Transport "https://github.com/neovim/go-client/blob/main/nvim/nvim_unix.go"
    click PluginGo "https://github.com/neovim/go-client/blob/main/nvim/plugin/plugin.go"
    click PluginMain "https://github.com/neovim/go-client/blob/main/nvim/plugin/main.go"
    click nvimTest "https://github.com/neovim/go-client/blob/main/nvim/nvimtest/nvimtest.go"

    %% Styles
    classDef serialization fill:#e0f7fa,stroke:#00796b
    classDef rpc fill:#e0f2f1,stroke:#004d40
    classDef api fill:#e8f5e9,stroke:#1b5e20
    classDef transport fill:#fff3e0,stroke:#e65100
    classDef external fill:#eceff1,stroke:#607d8b
    classDef example fill:#fce4ec,stroke:#880e4f,stroke-dasharray: 5 5
    classDef plugin fill:#e1f5fe,stroke:#01579b
    classDef test fill:#f3e5f5,stroke:#6a1b9a

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