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
  <img alt="Loading…" src="https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExeHJ4YXdtYjJpMDl0MzEwYmU4ZzBobG0waGNiN3MzNzR0d2R2NnMwNSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/26gssNOlBJKjEM3yo/giphy.gif"/>
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
    %% External Clients
    subgraph "External Clients"
        CTR["ctr CLI"]:::external
        KUBE["Kubernetes CRI (kubelet)"]:::external
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
    Sandbox["Sandbox (WASM Execution)"]:::library

    %% Runtime Adapters
    subgraph "WASM Engine Adapters"
        Wasmtime["Wasmtime Adapter"]:::adapter
        click Wasmtime "https://github.com/containerd/runwasi/tree/main/crates/containerd-shim-wasmtime"
        Wasmer["Wasmer Adapter"]:::adapter
        click Wasmer "https://github.com/containerd/runwasi/tree/main/crates/containerd-shim-wasmer"
        WAMR["WAMR Adapter"]:::adapter
        click WAMR "https://github.com/containerd/runwasi/tree/main/crates/containerd-shim-wamr"
        WasmEdge["WasmEdge Adapter"]:::adapter
        click WasmEdge "https://github.com/containerd/runwasi/tree/main/crates/containerd-shim-wasmedge"
    end

    %% WASM Module
    Module["WASI Module"]:::module
    click Module "https://github.com/containerd/runwasi/tree/main/crates/wasi-demo-app"

    %% OS / Sys Abstractions
    OS["OS / Sys Calls"]:::os

    %% Supporting Tooling
    subgraph "Supporting Tooling"
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
    OS -->|host calls| _[Underlying Host]:::os

    Containerd -->|status/results| CTR
    Containerd -->|status/results| KUBE

    %% Styles
    classDef external fill:#AED6F1,stroke:#2E86C1,color:#1B4F72
    classDef shim fill:#ABEBC6,stroke:#27AE60,color:#145A32
    classDef library fill:#FCF3CF,stroke:#F1C40F,color:#7D6608
    classDef adapter fill:#FAD7A0,stroke:#EB984E,color:#7E5109
    classDef module fill:#D7BDE2,stroke:#8E44AD,color:#512E5F
    classDef os fill:#D5D8DC,stroke:#797D7F,color:#2C3E50
    classDef tooling fill:#F2F4F4,stroke:#AEB6BF,color:#566573

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