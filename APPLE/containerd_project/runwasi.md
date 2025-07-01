---
created: 2025-06-26 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/containerd/runwasi
---

<div align="center">
  <p>⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷</p>
  <i>This is a working draft in progress.</i>
  <br/>
  <img alt="Loading…" src="https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExaHJzMDhqNWl4ZHhocXIzOHpham44NXJ1cXB4dWtvOWZ3OXZyd2JtMiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/d688ZL279Z4GB4mdj6/giphy.gif"/>
  <br/>
  <blockquote>
	  <i>gif image is provided by <a href="https://giphy.com">Giphy</a></i>
  </blockquote>
  <p>⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷</p>

</div>


# runwasi repo project
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
title: "runwasi repo project"
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
    subgraph External_Clients["External Clients"]
    style External_Clients fill:#F2F2,stroke:#333,stroke-width:1px, color: #FFFF
	  direction LR
        CTR["ctr CLI"]:::external
        KUBE["Kubernetes CRI<br/>(kubelet)"]:::external
        REG["Container Image Registry"]:::external
    end

    %% Containerd Layer
    Containerd["Containerd Daemon"]:::external

    %% Shim Plugin Layer
    ShimCore["containerd-shim-wasm"]:::shim
    click ShimCore "https://github.com/containerd/runwasi/tree/main/crates/containerd-shim-wasm"

    %% Shimkit Library
    Shimkit["containerd-shimkit"]:::library
    click Shimkit "https://github.com/containerd/runwasi/tree/main/crates/containerd-shimkit"

    %% Sandbox
    Sandbox["Sandbox<br/>(WASM Execution)"]:::library

    %% Runtime Adapters
    subgraph WASM_Engine_Adapters["WASM Engine Adapters"]
    style WASM_Engine_Adapters fill:#23F2,stroke:#333,stroke-width:1px, color: #FFFF
	  direction LR
        Wasmtime["Wasmtime Adapter"]:::adapter
        click Wasmtime "https://github.com/containerd/runwasi/tree/main/crates/containerd-shim-wasmtime"
        Wasmer["Wasmer Adapter"]:::adapter
        click Wasmer "https://github.com/containerd/runwasi/tree/main/crates/containerd-shim-wasmer"
        WAMR["WAMR Adapter"]:::adapter
        click WAMR "https://github.com/containerd/runwasi/tree/main/crates/containerd-shim-wamr"
        WasmEdge["WasmEdge Adapter"]:::adapter
        click WasmEdge "https://github.com/containerd/runwasi/tree/main/crates/containerd-shim-wasmedge"
    end

    Module["WASI Module"]:::module
    click Module "https://github.com/containerd/runwasi/tree/main/crates/wasi-demo-app"

    %% OS / Sys Abstractions
    OS["OS /<br/> Sys Calls"]:::os

    subgraph Supporting_Tooling["Supporting Tooling"]
    style Supporting_Tooling fill:#2BF2,stroke:#333,stroke-width:1px, color: #FFFF
	  direction LR
        OCI["OCI Image Builder"]:::tooling
        click OCI "https://github.com/containerd/runwasi/tree/main/crates/oci-tar-builder"
        
        Stress["Stress-Test Harness"]:::tooling
        click Stress "https://github.com/containerd/runwasi/tree/main/crates/stress-test"
        
        Bench["Benchmark Suite"]:::tooling
        click Bench "https://github.com/containerd/runwasi/tree/main/benches/containerd-shim-benchmarks"
        
        Docs["Documentation"]:::tooling
        click Docs "https://github.com/containerd/runwasi/blob/main/docs/src/developer/architecture.md"
        
        TestK8s["K8s Examples"]:::tooling
        click TestK8s "https://github.com/containerd/runwasi/tree/main/test/k8s"
        
        TestK3s["K3s Examples"]:::tooling
        click TestK3s "https://github.com/containerd/runwasi/tree/main/test/k3s"
        
        Scripts["Build & CI Scripts"]:::tooling
        click Scripts "https://github.com/containerd/runwasi/tree/main/scripts"
        
        CI["CI Workflows"]:::tooling
        click CI "https://github.com/containerd/runwasi/tree/main/.github/workflows"
    end

    %% Data Flows
    CTR -->|gRPC CRI| Containerd
    KUBE -->|gRPC CRI| Containerd
    Containerd -->|ttrpc handshake| ShimCore
    ShimCore -->|uses| Shimkit
    ShimCore -->|orchestrates| Sandbox
    Sandbox -->|selects| Wasmtime
    Sandbox -->|selects| Wasmer
    Sandbox -->|selects| WAMR
    Sandbox -->|selects| WasmEdge
    Wasmtime -->|runs WASM| Module
    Wasmer -->|runs WASM| Module
    WAMR -->|runs WASM| Module
    WasmEdge -->|runs WASM| Module
    Module -->|WASI syscalls| OS
    OS -->|host calls| _["Underlying Host"]:::os

    Containerd -->|status/results| CTR
    Containerd -->|status/results| KUBE

    %% Styles
    classDef external fill:#1B4F72,stroke:#2E86C1
    classDef shim fill:#145A32,stroke:#27AE60
    classDef library fill:#7D6608,stroke:#F1C40F
    classDef adapter fill:#7E5109,stroke:#EB984E
    classDef module fill:#512E5F,stroke:#8E44AD
    classDef os fill:#2C3E50,stroke:#797D7F
    classDef tooling fill:#566573,stroke:#AEB6BF

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
