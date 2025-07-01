---
created: 2025-06-26 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/containerd/rust-extensions
---

<div align="center">
  <p>⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷</p>
  <i>This is a working draft in progress.</i>
  <br/>
  <img alt="Loading…" src="https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExcGFqMGFhN2NraXc4Z251bGU0NTQ4ajFha2pnNTB5YXQ4emFybWliZyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/y1MLeSPFMuMrmNMBLN/giphy.gif"/>
  <br/>
  <blockquote>
	  <i>gif image is provided by <a href="https://giphy.com">Giphy</a></i>
  </blockquote>
  <p>⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷</p>

</div>

---

# rust-extensions repo project
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
title: "rust-extensions repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright © 2025 Cong Le. All Rights Reserved."
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
    subgraph External_Services["External Services"]
    style External_Services fill:#F2F2,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        Client["containerd-client (gRPC client)"]:::client
        RuncCLI["runc CLI (OCI runtime)"]:::external
    end

    %% Core Daemon
    Containerd["containerd daemon"]:::external

    %% Rust Plugins (loaded by containerd)
    subgraph Containerd_Plugins["Containerd Plugins"]
    style Containerd_Plugins fill:#32F2,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        RuncShim["containerd-runc-shim"]:::plugin
        Logging["containerd-shim-logging"]:::plugin
        Snapshots["containerd-snapshots"]:::plugin
    end

    %% Rust Libraries/Crates
    subgraph Rust_Crates["Rust Crates"]
    style Rust_Crates fill:#222,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        ShimProtos["containerd-shim-protos"]:::lib
        ShimFW["containerd-shim (framework)"]:::lib
        RuncWrap["runc (wrapper)"]:::lib
    end

    %% External to Containerd
    Client -->|"gRPC"| Containerd
    Containerd -->|"gRPC"| Logging
    Containerd -->|"gRPC"| Snapshots
    Containerd -->|"TTRPC"| RuncShim
    RuncShim -->|"uses TTRPC protocol definitions"| ShimProtos
    RuncShim -->|"built on framework"| ShimFW
    ShimFW -->|"defines protocol via TTRPC"| ShimProtos
    RuncShim -->|"invokes via wrapper"| RuncWrap
    RuncWrap -->|"CLI exec"| RuncCLI

    %% Code Generation Dependencies
    ShimProtos -.->|"build.rs generates bindings"| ShimFW
    ShimProtos -.-> ShimProtos
    ShimProtos -.-> Logging
    ShimProtos -.-> Snapshots

    %% Click Events
    click ShimProtos "https://github.com/containerd/rust-extensions/tree/main/crates/shim-protos/"
    click ShimProtos "https://github.com/containerd/rust-extensions/blob/main/crates/shim-protos/Cargo.toml"
    click ShimProtos "https://github.com/containerd/rust-extensions/blob/main/crates/shim-protos/build.rs"
    click ShimProtos "https://github.com/containerd/rust-extensions/blob/main/crates/shim-protos/src/lib.rs"
    click ShimFW "https://github.com/containerd/rust-extensions/tree/main/crates/shim/"
    click ShimFW "https://github.com/containerd/rust-extensions/blob/main/crates/shim/Cargo.toml"
    click ShimFW "https://github.com/containerd/rust-extensions/blob/main/crates/shim/src/lib.rs"
    click ShimFW "https://github.com/containerd/rust-extensions/blob/main/crates/shim/src/monitor.rs"
    click ShimFW "https://github.com/containerd/rust-extensions/blob/main/crates/shim/src/publisher.rs"
    click ShimFW "https://github.com/containerd/rust-extensions/blob/main/crates/shim/src/util.rs"
    click RuncShim "https://github.com/containerd/rust-extensions/tree/main/crates/runc-shim/"
    click RuncShim "https://github.com/containerd/rust-extensions/blob/main/crates/runc-shim/Cargo.toml"
    click RuncShim "https://github.com/containerd/rust-extensions/blob/main/crates/runc-shim/build.rs"
    click RuncShim "https://github.com/containerd/rust-extensions/blob/main/crates/runc-shim/src/main.rs"
    click RuncShim "https://github.com/containerd/rust-extensions/blob/main/crates/runc-shim/src/runc.rs"
    click Client "https://github.com/containerd/rust-extensions/tree/main/crates/client/"
    click Client "https://github.com/containerd/rust-extensions/blob/main/crates/client/Cargo.toml"
    click Client "https://github.com/containerd/rust-extensions/blob/main/crates/client/build.rs"
    click Client "https://github.com/containerd/rust-extensions/blob/main/crates/client/src/lib.rs"
    click Client "https://github.com/containerd/rust-extensions/tree/main/crates/client/examples/"
    click Logging "https://github.com/containerd/rust-extensions/tree/main/crates/logging/"
    click Logging "https://github.com/containerd/rust-extensions/blob/main/crates/logging/Cargo.toml"
    click Logging "https://github.com/containerd/rust-extensions/blob/main/crates/logging/src/lib.rs"
    click Logging "https://github.com/containerd/rust-extensions/blob/main/crates/logging/examples/journal.rs"
    click Snapshots "https://github.com/containerd/rust-extensions/tree/main/crates/snapshots/"
    click Snapshots "https://github.com/containerd/rust-extensions/blob/main/crates/snapshots/Cargo.toml"
    click Snapshots "https://github.com/containerd/rust-extensions/blob/main/crates/snapshots/build.rs"
    click Snapshots "https://github.com/containerd/rust-extensions/blob/main/crates/snapshots/src/lib.rs"
    click Snapshots "https://github.com/containerd/rust-extensions/blob/main/crates/snapshots/src/convert.rs"
    click Snapshots "https://github.com/containerd/rust-extensions/blob/main/crates/snapshots/src/wrap.rs"
    click RuncWrap "https://github.com/containerd/rust-extensions/tree/main/crates/runc/"
    click RuncWrap "https://github.com/containerd/rust-extensions/blob/main/crates/runc/Cargo.toml"
    click RuncWrap "https://github.com/containerd/rust-extensions/blob/main/crates/runc/src/lib.rs"
    click RuncWrap "https://github.com/containerd/rust-extensions/blob/main/crates/runc/src/asynchronous/runc.rs"
    click RuncWrap "https://github.com/containerd/rust-extensions/blob/main/crates/runc/src/synchronous/runc.rs"
    click InstallProto "https://github.com/containerd/rust-extensions/blob/main/scripts/install-protobuf.sh"
    click UpdateVendor "https://github.com/containerd/rust-extensions/blob/main/scripts/update-vendor.sh"

    subgraph Legend["Legend"]
    style Legend fill:#2BB2,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        ext["External Services"]:::external
        plug["Containerd Plugins"]:::plugin
        libc["Rust Crates"]:::lib
        cli["Client Libraries"]:::client
    end

    classDef external fill:#A8E6,stroke:#000,stroke-width:1px
    classDef plugin fill:#9E92,stroke:#000,stroke-width:1px
    classDef client fill:#F555,stroke:#000,stroke-width:1px
    classDef lib fill:#F682,stroke:#000,stroke-width:1px

```

----

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
