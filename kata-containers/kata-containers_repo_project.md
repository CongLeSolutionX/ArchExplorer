---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/kata-containers/kata-containers
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExcHNvYjh0cGRqYjMxc2c3bGNzdmh3czJ4MHEyNXhkYTB3cGsxeGo2aiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/MXus9lyeUBYSO8K7CV/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# kata-containers repo project
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
title: "CHANGE_ME_DADDY"
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
    %% Host OS Layer
    subgraph "Host OS" 
        direction TB
        CD["containerd (CRI Plugin)"]:::external
        SHIM["Shimv2 (Go)"]:::go
        PROT_HOST["Protocols (gRPC/ttrpc)"]:::rust
        RUNTIME_GO["kata-runtime (Go)"]:::go
        RUNTIME_RS["kata-runtime (Rust)"]:::rust
        click SHIM "https://github.com/kata-containers/kata-containers/tree/main/src/runtime/pkg/containerd-shim-v2"
        click PROT_HOST "https://github.com/kata-containers/kata-containers/tree/main/src/runtime/protocols"
        click PROT_HOST "https://github.com/kata-containers/kata-containers/tree/main/src/libs/protocols"
        click RUNTIME_GO "https://github.com/kata-containers/kata-containers/tree/main/src/runtime"
        click RUNTIME_RS "https://github.com/kata-containers/kata-containers/tree/main/src/runtime-rs"
    end

    %% Hypervisor Layer
    subgraph "Hypervisor / VMM" 
        direction TB
        DRAGON["dragonball VMM"]:::rust
        QEMU["QEMU / Firecracker / Cloud-Hypervisor"]:::external
        PACK["Packaging & OS Builder"]:::tool
        click DRAGON "https://github.com/kata-containers/kata-containers/tree/main/src/dragonball"
        click PACK "https://github.com/kata-containers/kata-containers/tree/main/tools/packaging"
        click PACK "https://github.com/kata-containers/kata-containers/tree/main/tools/osbuilder"
    end

    %% Guest VM Layer
    subgraph "Guest VM" 
        direction TB
        GUEST_KERNEL["Guest Kernel"]:::guest
        AGENT["kata-agent"]:::rust
        CONTAINERS["Container Processes"]:::guest
        click AGENT "https://github.com/kata-containers/kata-containers/tree/main/src/agent"
    end

    %% Tools & Utilities
    subgraph "Host Utilities" 
        direction TB
        TOOL1["agent-ctl"]:::tool
        TOOL2["kata-ctl"]:::tool
        TOOL3["runk"]:::tool
        TOOL4["trace-forwarder"]:::tool
        TOOL5["genpolicy"]:::tool
        click TOOL1 "https://github.com/kata-containers/kata-containers/tree/main/src/tools/agent-ctl"
        click TOOL2 "https://github.com/kata-containers/kata-containers/tree/main/src/tools/kata-ctl"
        click TOOL3 "https://github.com/kata-containers/kata-containers/tree/main/src/tools/runk"
        click TOOL4 "https://github.com/kata-containers/kata-containers/tree/main/src/tools/trace-forwarder"
        click TOOL5 "https://github.com/kata-containers/kata-containers/tree/main/src/tools/genpolicy"
    end

    %% CI & Tests
    subgraph "CI & Tests" 
        direction TB
        WF["GitHub Workflows"]:::external
        CI["CI Scripts"]:::external
        TESTS["Unit & Integration Tests"]:::external
        click WF "https://github.com/kata-containers/kata-containers/tree/main/.github/workflows"
        click CI "https://github.com/kata-containers/kata-containers/tree/main/ci"
        click TESTS "https://github.com/kata-containers/kata-containers/tree/main/tests"
    end

    %% Relationships
    CD -->|"UNIX Socket"| SHIM
    SHIM -->|"gRPC/ttrpc"| RUNTIME_GO
    SHIM -->|"gRPC/ttrpc"| RUNTIME_RS
    RUNTIME_GO -->|"Launch VM"| QEMU
    RUNTIME_RS -->|"Launch VM"| QEMU
    RUNTIME_GO -->|"Launch VM"| DRAGON
    RUNTIME_RS -->|"Launch VM"| DRAGON
    QEMU -->|"virtio/vsock"| AGENT
    DRAGON -->|"virtio/vsock"| AGENT
    RUNTIME_GO <-->|"vsock channel"| AGENT
    RUNTIME_RS <-->|"vsock channel"| AGENT
    AGENT -->|"OCI setups"| GUEST_KERNEL
    RUNTIME_GO -->|"access packaging"| PACK
    RUNTIME_RS -->|"access packaging"| PACK

    %% Tools relationships
    RUNTIME_GO --> TOOL1
    RUNTIME_GO --> TOOL2
    RUNTIME_GO --> TOOL3
    RUNTIME_GO --> TOOL4
    RUNTIME_GO --> TOOL5

    %% CI relationships
    WF --> RUNTIME_GO
    WF --> RUNTIME_RS
    WF --> AGENT
    CI --> TESTS

    %% Styles
    classDef external fill:#f9f3,stroke:#333,stroke-width:1px
    classDef go fill:#bbf3,stroke:#333,stroke-width:1px
    classDef rust fill:#fbb3,stroke:#333,stroke-width:1px
    classDef tool fill:#bfb3,stroke:#333,stroke-width:1px
    classDef guest fill:#ffa3,stroke:#333,stroke-width:1px
    classDef host fill:#eef3,stroke:#333,stroke-width:1px
    classDef hyper fill:#fee3,stroke:#333,stroke-width:1px
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