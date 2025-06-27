---
created: 2025-06-26 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/containerd/nri
---

<div align="center">
  <p>⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷</p>
  <i>This is a working draft in progress.</i>
  <br/>
  <img alt="Loading…" src="https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExeHJ4YXdtYjJpMDl0MzEwYmU4ZzBobG0waGNiN3MzNzR0d2R2NnMwNSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/26gssNOlBJKjEM3yo/giphy.gif"/>
  <br/>
  <blockquote>
	  <i>gif image is provided by <a href="https://giphy.com">Giphy</a></i>
  </blockquote>
  <p>⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷</p>

</div>


# nri repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for 👨‍🎓 <ins>educational purposes</ins> 👨‍🎓 (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), 📖 <ins> personal study </ins> 📖, and 🔖 <ins> reference </ins> 🔖.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


----

```mermaid
---
title: "nri repo project"
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
flowchart LR
    %% Layers
    subgraph "Container Runtime"
        CR["Container Runtime (containerd/CRI-O)"]:::runtime
    end

    subgraph "Adaptation Layer" 
        AL["NRI Adaptation Layer"]:::core
        SCK(("Unix Domain Socket")):::core
        AL -->|opens| SCK
    end

    subgraph "Core Protocol" 
        API["pkg/api (Protobuf & ttrpc)"]:::core
    end

    subgraph "Stub Library" 
        STUB["pkg/stub/stub.go"]:::plugins
    end

    subgraph "Plugins" 
        subgraph Validators/Mutators
            PV["Default Validator"]:::plugins
            PJ["Device Injector"]:::plugins
            PD["Differ"]:::plugins
            PH["Hook Injector"]:::plugins
            PL["Logger"]:::plugins
            PN["Network Device Injector"]:::plugins
            PN2["Network Logger"]:::plugins
            PT["Template Plugin"]:::plugins
            PU["Ulimit Adjuster"]:::plugins
            PA["v0.1.0 Adapter"]:::plugins
            PW["Wasm Plugin"]:::plugins
        end
    end

    subgraph "Runtime Tools" 
        OCI["OCI Spec Generator"]:::runtime
    end

    subgraph "CLI & Examples" 
        CLI["client.go"]:::external
        EX["examples/"]:::external
    end

    %% Handshake & Connection
    STUB -->|connects & handshake| SCK
    SCK -->|ttrpc/RegisterPlugin| AL
    AL -->|ttrpc/Configure & Subscribe| STUB

    %% Event Flow
    CR -.->|lifecycle events| AL
    AL -.->|fan-out events| STUB
    STUB -->|"PluginService.Call()"| PV
    STUB -->|"PluginService.Call()"| PJ
    STUB -->|"PluginService.Call()"| PD
    STUB -->|"PluginService.Call()"| PH
    STUB -->|"PluginService.Call()"| PL
    STUB -->|"PluginService.Call()"| PN
    STUB -->|"PluginService.Call()"| PN2
    STUB -->|"PluginService.Call()"| PT
    STUB -->|"PluginService.Call()"| PU
    STUB -->|"PluginService.Call()"| PA
    STUB -->|"PluginService.Call()"| PW

    %% Response Aggregation
    PV -->|RuntimeService.Response| AL
    PJ -->|RuntimeService.Response| AL
    PD -->|RuntimeService.Response| AL
    PH -->|RuntimeService.Response| AL
    PL -->|RuntimeService.Response| AL
    PN -->|RuntimeService.Response| AL
    PN2 -->|RuntimeService.Response| AL
    PT -->|RuntimeService.Response| AL
    PU -->|RuntimeService.Response| AL
    PA -->|RuntimeService.Response| AL
    PW -->|RuntimeService.Response| AL

    AL -->|apply adjustments| OCI

    %% CLI Interaction
    CLI -->|RuntimeService RPC| API
    EX -->|RuntimeService RPC| API

    %% Core to Adaptation
    API -->|used by| AL
    API -->|used by| STUB

    %% Click Events
    click CLI "https://github.com/containerd/nri/blob/main/client.go"
    click EX "https://github.com/containerd/nri/tree/main/examples/"
    click API "https://github.com/containerd/nri/tree/main/pkg/api/"
    click AL "https://github.com/containerd/nri/tree/main/pkg/adaptation/"
    click STUB "https://github.com/containerd/nri/blob/main/pkg/stub/stub.go"
    click OCI "https://github.com/containerd/nri/blob/main/pkg/runtime-tools/generate/generate.go"
    click PV "https://github.com/containerd/nri/tree/main/plugins/default-validator/"
    click PJ "https://github.com/containerd/nri/tree/main/plugins/device-injector/"
    click PD "https://github.com/containerd/nri/tree/main/plugins/differ/"
    click PH "https://github.com/containerd/nri/tree/main/plugins/hook-injector/"
    click PL "https://github.com/containerd/nri/tree/main/plugins/logger/"
    click PN "https://github.com/containerd/nri/tree/main/plugins/network-device-injector/"
    click PN2 "https://github.com/containerd/nri/tree/main/plugins/network-logger/"
    click PT "https://github.com/containerd/nri/tree/main/plugins/template/"
    click PU "https://github.com/containerd/nri/tree/main/plugins/ulimit-adjuster/"
    click PA "https://github.com/containerd/nri/tree/main/plugins/v010-adapter/"
    click PW "https://github.com/containerd/nri/tree/main/plugins/wasm/"
    click SK "https://github.com/containerd/nri/blob/main/skel/skel.go"
    click SCR "https://github.com/containerd/nri/tree/main/scripts/"
    click TYP "https://github.com/containerd/nri/blob/main/types/v1/types.go"

    %% Styles
    classDef core fill:#d5f5e3,stroke:#27ae60,color:#145a32
    classDef plugins fill:#fdebd0,stroke:#e67e22,color:#a04000
    classDef external fill:#d6eaf8,stroke:#3498db,color:#1b4f72
    classDef runtime fill:#ebdef0,stroke:#8e44ad,color:#4a235a

```

-----

```mermaid
---
title: "❓...CongLeSolutionX....❓"
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
>**Licenses:**
>
>- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
>- **Creative Commons Attribution-ShareAlike 4.0 International**: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) [![CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/88x31.png)](https://creativecommons.org/licenses/by-sa/4.0/) - Legal details in [LICENSE-CC-BY-SA-4.0](THE_PAST/LICENSE-CC-BY-SA-4.0) and at [Creative Commons official site](https://creativecommons.org/licenses/by-sa/4.0/).
>
---