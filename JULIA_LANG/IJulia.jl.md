---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/JuliaLang/IJulia.jl
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




# IJulia.jl repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes (<ins>sometimes, entertainment purposes</ins>), personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


---

```mermaid
---
title: "IJulia.jl repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#F5E3',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EEF5',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD'
    }
  }
}%%
flowchart TD
    %% Layer 1: Clients
    subgraph "Layer 1: Clients"
        NB["Jupyter Notebook"]:::external
        JL["JupyterLab"]:::external
        NA["nteract"]:::external
    end

    %% Layer 2: Server
    Manager["jupyter-client / Kernel Manager"]:::external

    %% Connections from Clients to Manager
    NB -->|"HTTP/WebSocket"| Manager
    JL -->|"HTTP/WebSocket"| Manager
    NA -->|"HTTP/WebSocket"| Manager

    %% Kernel Launch Entrypoint
    Entrypoint["Kernel Process Entrypoint"]:::messaging
    click Entrypoint "https://github.com/julialang/ijulia.jl/blob/master/src/IJulia.jl"

    %% Kernel Init & Lifecycle
    Init["Initialization (init.jl)"]:::messaging
    click Init "https://github.com/julialang/ijulia.jl/blob/master/src/init.jl"
    KernelMod["Lifecycle (kernel.jl)"]:::messaging
    click KernelMod "https://github.com/julialang/ijulia.jl/blob/master/src/kernel.jl"

    Manager --> Entrypoint
    Entrypoint --> Init
    Entrypoint --> KernelMod

    %% ZeroMQ Messaging
    ZeroMQ["ZeroMQ Sockets"]:::messaging

    Manager --> ZeroMQ

    %% Layer 3: IJulia Kernel Process
    subgraph "Layer 3: IJulia Kernel Process"
        EL["Event Loop"]:::messaging
        click EL "https://github.com/julialang/ijulia.jl/blob/master/src/eventloop.jl"

        Parser["Message Parser"]:::messaging
        click Parser "https://github.com/julialang/ijulia.jl/blob/master/src/msg.jl"
        Dispatcher["Dispatcher / Handlers"]:::messaging
        click Dispatcher "https://github.com/julialang/ijulia.jl/blob/master/src/handlers.jl"

        Exec["Code Execution Handler"]:::execution
        click Exec "https://github.com/julialang/ijulia.jl/blob/master/src/execute_request.jl"
        Inline["Inline Execution Handler"]:::execution
        click Inline "https://github.com/julialang/ijulia.jl/blob/master/src/inline.jl"
        Magics["Magic Commands Support"]:::execution
        click Magics "https://github.com/julialang/ijulia.jl/blob/master/src/magics.jl"
        Comm["Comm Channels Manager"]:::execution
        click Comm "https://github.com/julialang/ijulia.jl/blob/master/src/comm_manager.jl"
        Display["Display Subsystem"]:::execution
        click Display "https://github.com/julialang/ijulia.jl/blob/master/src/display.jl"
        JupyterUtils["Jupyter Protocol Utilities"]:::execution
        click JupyterUtils "https://github.com/julialang/ijulia.jl/blob/master/src/jupyter.jl"
        Stdio["Standard I/O Integration"]:::execution
        click Stdio "https://github.com/julialang/ijulia.jl/blob/master/src/stdio.jl"

        Heartbeat["Heartbeat Service"]:::security
        click Heartbeat "https://github.com/julialang/ijulia.jl/blob/master/src/heartbeat.jl"
        HMAC["Security / HMAC"]:::security
        click HMAC "https://github.com/julialang/ijulia.jl/blob/master/src/hmac.jl"
    end

    %% Connections within Kernel Process
    Init --> EL
    KernelMod --> EL
    ZeroMQ --> EL
    EL --> Parser
    Parser --> Dispatcher

    Dispatcher --> Exec
    Dispatcher --> Inline
    Dispatcher --> Magics
    Dispatcher --> Comm
    Dispatcher --> Display
    Dispatcher --> JupyterUtils
    Dispatcher --> Stdio

    EL --> Heartbeat
    EL --> HMAC

    %% Layer 4: Julia Runtime
    subgraph "Layer 4: Julia Runtime"
        REPL["Julia REPL / Runtime"]:::execution
    end

    Exec --> REPL
    Inline --> REPL
    Magics --> REPL

    %% Optional Layer 5: Python/Jupyter via Conda
    Conda["Conda-managed Python/Jupyter"]:::external

    %% Build & Deploy
    subgraph "Build & Deployment"
        Build["Kernelspec Build Scripts"]:::build
        click Build "https://github.com/julialang/ijulia.jl/blob/master/deps/build.jl"
        click Build "https://github.com/julialang/ijulia.jl/blob/master/deps/kspec.jl"
    end

    %% CI, Docs, Tests
    subgraph "CI & Docs & Tests"
        CI["CI Workflows"]:::build
        click CI "https://github.com/julialang/ijulia.jl/blob/master/.github/workflows/CI.yml"
        click CI "https://github.com/julialang/ijulia.jl/blob/master/.github/workflows/Docs.yml"
        click CI "https://github.com/julialang/ijulia.jl/blob/master/.github/workflows/TagBot.yml"
        Docs["Documentation Source"]:::external
        click Docs "https://github.com/julialang/ijulia.jl/tree/master/docs/src"
        Tests["Unit Tests"]:::tests
        click Tests "https://github.com/julialang/ijulia.jl/tree/master/test/"
    end

    %% Optional Connections
    Entrypoint --> Build
    Entrypoint --> Tests
    Entrypoint --> Docs
    Entrypoint --> CI
    Build --> Conda

    %% Classes
    classDef external fill:#eeeeee,stroke:#888888,color:#333333;
    classDef messaging fill:#cce5ff,stroke:#3399ff,color:#003366;
    classDef execution fill:#d4edda,stroke:#28a745,color:#155724;
    classDef security fill:#fff3cd,stroke:#ffecb5,color:#856404;
    classDef build fill:#e2d4f0,stroke:#a46fb1,color:#4e2150;
    classDef tests fill:#f0f0f0,stroke:#bbbbbb,color:#666666;

```

-----

<!-- 
```mermaid
%% Current Mermaid version
info
```  -->


```mermaid
---
title: "C<char>o&#770;</char>ngL<char>e&#770;</char>SolutionX"
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
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX/CongLeSolutionX' target='_blank'>Click here if you care about the profile of a tech guy seeking for job 🙏🏼</a>"}}

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