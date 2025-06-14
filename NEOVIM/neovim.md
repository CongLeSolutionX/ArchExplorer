---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/neovim/neovim
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




# neovim repo project
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
title: "neovim repo project"
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
    %% Build System
    subgraph "Build System"
        Build["Build System"]:::build
    end
    click Build "https://github.com/neovim/neovim/tree/master/cmake/"

    %% Core Process
    subgraph "Neovim Core"
        Core["Neovim Core"]:::core
        Event["Event Loop (libuv)"]:::core
        API["API Subsystem"]:::core
        Eval["Eval Subsystem (Vimscript)"]:::core
        Lua["Lua Subsystem (Lua VM)"]:::core
        RPC["msgpack_rpc Server"]:::core
        OS["Platform Layer"]:::core
        Lib["Utility Data Structures"]:::core
        Gen["Codegen (Schema)"]:::core
        MPack["Internal MessagePack lib"]:::core
    end
    click Core "https://github.com/neovim/neovim/tree/master/src/nvim/"
    click Event "https://github.com/neovim/neovim/tree/master/src/nvim/event/"
    click API "https://github.com/neovim/neovim/tree/master/src/nvim/api/"
    click Eval "https://github.com/neovim/neovim/tree/master/src/nvim/eval/"
    click Lua "https://github.com/neovim/neovim/tree/master/src/nvim/lua/"
    click RPC "https://github.com/neovim/neovim/tree/master/src/nvim/msgpack_rpc/"
    click OS "https://github.com/neovim/neovim/tree/master/src/nvim/os/"
    click Lib "https://github.com/neovim/neovim/tree/master/src/nvim/lib/"
    click Gen "https://github.com/neovim/neovim/tree/master/src/gen/"
    click MPack "https://github.com/neovim/neovim/tree/master/src/mpack/"

    %% Runtime Loader
    subgraph "Runtime Loader"
        Runtime["Runtime Loader"]:::runtime
    end
    click Runtime "https://github.com/neovim/neovim/tree/master/runtime/"

    %% Frontends and Clients
    subgraph "Frontends/Clients"
        TUI["Built-in TUI"]:::frontend
        GUI["External GUI Clients"]:::frontend
        UIClient["In-Process UI Client"]:::frontend
        PH["Plugin Hosts"]:::frontend
    end
    click TUI "https://github.com/neovim/neovim/tree/master/src/nvim/tui/"
    click UIClient "https://github.com/neovim/neovim/blob/master/src/nvim/ui_client.c"
    click PH "https://github.com/neovim/neovim/blob/master/src/nvim/ui_compositor.c"

    %% Test Harness
    subgraph "Test Harness"
        TH["Test Harness"]:::test
    end
    click TH "https://github.com/neovim/neovim/tree/master/test/"

    %% Dependencies
    subgraph "Dependencies"
        Deps["Vendored Libraries"]:::deps
    end
    click Deps "https://github.com/neovim/neovim/tree/master/deps/"

    %% Connections
    Core -->|"initializes"| Event
    Core -->|"exposes C API"| API
    Core -->|"starts RPC Server"| RPC
    Core -->|"initializes interpreter"| Eval
    Core -->|"initializes VM"| Lua
    Core -->|"loads core libs"| Lib
    Core -->|"runs codegen"| Gen
    Core -->|"uses MsgPack"| MPack
    Core -->|"abstracts OS"| OS

    Core -->|"loads runtime scripts"| Runtime
    Runtime -->|"Vimscript files"| Eval
    Runtime -->|"Lua scripts"| Lua

    Event -->|"I/O for RPC/jobs"| RPC

    API <-->|"invokes"| Eval
    API <-->|"invokes"| Lua

    TUI -->|"RPC over stdio"| RPC
    GUI -->|"RPC over TCP"| RPC
    UIClient -->|"RPC in-process"| RPC
    PH -->|"RPC plugin host"| RPC

    TH -->|"RPC over stdio"| RPC

    Deps -->|"provides libuv"| Event
    Deps -->|"provides UTF8proc, Tree-sitter"| Lib
    Deps -->|"provides dependencies"| MPack
    Deps -->|"provides CMake modules"| Build

    %% Styles
    classDef core fill:#cfe2f3,stroke:#07689f,stroke-width:1px;
    classDef frontend fill:#d9ead3,stroke:#38761d,stroke-width:1px;
    classDef runtime fill:#fff2cc,stroke:#b45f06,stroke-width:1px;
    classDef deps fill:#eeeeee,stroke:#666666,stroke-width:1px;
    classDef build fill:#ead1dc,stroke:#a64d79,stroke-width:1px;
    classDef test fill:#fce5cd,stroke:#bf9000,stroke-width:1px;
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