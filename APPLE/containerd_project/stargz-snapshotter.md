---
created: 2025-06-26 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/containerd/stargz-snapshotter
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


# stargz-snapshotter repo project
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
title: "stargz-snapshotter repo project"
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
    %% External Systems
    subgraph "External Systems"
        direction TB
        Containerd["containerd"]:::external
        Registry["Container Registry (OCI/Docker)"]:::cloud
        IPFSCloud["IPFS Network"]:::cloud
    end

    %% Daemon / Plugin
    subgraph "Plugin Daemon (gRPC Snapshotter)" 
        direction TB
        DaemonMain["main.go"]:::runtime
        DaemonServer["server.go"]:::runtime
    end

    %% Service Layer
    subgraph "Service Layer"
        direction TB
        Service["service.go"]:::runtime
        PluginAPI["plugin.go"]:::runtime
        PluginCore["plugincore/plugin.go"]:::runtime
    end

    %% Resolver & Authentication
    subgraph "Resolver & Authentication"
        direction TB
        ResolverRegistry["registry.go"]:::runtime
        ResolverCRI["cri.go"]:::runtime
        KeychainDocker["dockerconfig.go"]:::runtime
        KeychainCRI["cri.go"]:::runtime
        KeychainKube["kubeconfig.go"]:::runtime
        KeychainConfig["keychainconfig.go"]:::runtime
    end

    %% Store Manager & Chunk Control API
    subgraph "Store Manager & Chunk Control"
        direction TB
        StoreManager["manager.go"]:::runtime
        StoreFS["fs.go"]:::runtime
        StoreRefs["refs.go"]:::runtime
        ControlProto["control.proto"]:::runtime
        ControlPB["control.pb.go"]:::runtime
    end

    %% Snapshot Orchestration
    Snapshot["snapshot.go"]:::runtime

    %% Filesystem Layer
    subgraph "Filesystem Layer"
        direction TB
        FSCore["fs.go"]:::runtime
        FSConfig["config.go"]:::runtime
        FSLayer["layer.go"]:::runtime
        FSReader["reader.go"]:::runtime
        FSRemote["resolver.go"]:::runtime
        FSSource["source.go"]:::runtime
    end

    %% Cache Layer
    Cache["cache.go"]:::runtime

    %% Analyzer / Prefetcher
    subgraph "Analyzer / Prefetcher"
        direction TB
        AnalyzerCore["analyzer.go"]:::prefetch
        Fanotify["fanotify.go"]:::prefetch
        Recorder["recorder.go"]:::prefetch
    end

    %% FUSE Manager
    subgraph "FUSE Manager"
        direction TB
        FuseMgr["fusemanager.go"]:::runtime
        FuseAPI["api.proto"]:::runtime
        FuseClient["client.go"]:::runtime
        FuseSvc["service.go"]:::runtime
    end

    %% CLI & Conversion Libraries
    subgraph "CLI & Conversion"
        direction TB
        CLI_Daemon["containerd-stargz-grpc"]:::cli
        CTRRemote["ctr-remote/main.go"]:::cli
        StargzStore["stargz-store/main.go"]:::cli
        FuseCLI["stargz-fuse-manager/main.go"]:::cli
        subgraph "Image Conversion Libs"
            direction TB
            Estargz["estargz.go"]:::cli
            ExternalTOC["externaltoc.go"]:::cli
            Gzip["gzip.go"]:::cli
            NativeConv["nativeconverter.go"]:::cli
            NC_Stargz["estargz.go"]:::cli
        end
    end

    %% Dev & CI
    DevCI["Scripts & Tests"]:::dev

    %% Interactions
    Containerd -->|gRPC SnapshotRequest| DaemonMain
    DaemonMain --> DaemonServer
    DaemonServer -->|calls| Service
    Service --> PluginAPI
    PluginAPI --> PluginCore
    Service --> ResolverRegistry
    Service --> ResolverCRI
    ResolverRegistry --> KeychainDocker
    ResolverRegistry --> KeychainCRI
    ResolverRegistry --> KeychainKube
    ResolverRegistry --> KeychainConfig
    Service --> StoreManager
    StoreManager --> StoreFS
    StoreManager --> StoreRefs
    StoreManager --> ControlProto
    StoreManager --> ControlPB
    Service --> Snapshot
    Snapshot --> FSCore
    FSCore --> FSConfig
    FSCore --> FSLayer
    FSLayer --> FSReader
    FSReader --> FSRemote
    FSRemote --> FSSource
    FSRemote -->|"HTTP(S)"| Registry
    FSRemote -->|IPFS| IPFSCloud
    FSReader --> Cache
    Cache --> FSReader
    AnalyzerCore --> Fanotify
    AnalyzerCore --> Recorder
    AnalyzerCore -->|prefetch| FSRemote
    CTRRemote --> Estargz
    CTRRemote --> ExternalTOC
    CTRRemote --> Gzip
    CTRRemote --> NativeConv
    CTRRemote --> NC_Stargz
    CLI_Daemon --> DaemonMain
    StargzStore -->|serves chunks| DaemonServer
    FuseCLI --> FuseMgr
    FuseMgr --> FuseAPI
    FuseMgr --> FuseClient
    FuseMgr --> FuseSvc
    CLI_Daemon -->|push/pull| Registry
    CTRRemote -->|push| Registry
    StargzStore -->|HTTP/gRPC| DaemonServer
    DevCI -->|uses| AnalyzerCore
    DevCI -->|tests| Cache
    DevCI -->|tests| FSCore

    %% Click Events
    click DaemonMain "https://github.com/containerd/stargz-snapshotter/blob/main/cmd/containerd-stargz-grpc/main.go"
    click DaemonServer "https://github.com/containerd/stargz-snapshotter/blob/main/cmd/containerd-stargz-grpc/server.go"
    click Service "https://github.com/containerd/stargz-snapshotter/blob/main/service/service.go"
    click PluginAPI "https://github.com/containerd/stargz-snapshotter/blob/main/service/plugin/plugin.go"
    click PluginCore "https://github.com/containerd/stargz-snapshotter/blob/main/service/plugincore/plugin.go"
    click ResolverRegistry "https://github.com/containerd/stargz-snapshotter/blob/main/service/resolver/registry.go"
    click ResolverCRI "https://github.com/containerd/stargz-snapshotter/blob/main/service/resolver/cri.go"
    click KeychainDocker "https://github.com/containerd/stargz-snapshotter/blob/main/service/keychain/dockerconfig/dockerconfig.go"
    click KeychainCRI "https://github.com/containerd/stargz-snapshotter/blob/main/service/keychain/cri/cri.go"
    click KeychainKube "https://github.com/containerd/stargz-snapshotter/blob/main/service/keychain/kubeconfig/kubeconfig.go"
    click KeychainConfig "https://github.com/containerd/stargz-snapshotter/blob/main/service/keychain/keychainconfig/keychainconfig.go"
    click StoreManager "https://github.com/containerd/stargz-snapshotter/blob/main/store/manager.go"
    click StoreFS "https://github.com/containerd/stargz-snapshotter/blob/main/store/fs.go"
    click StoreRefs "https://github.com/containerd/stargz-snapshotter/blob/main/store/refs.go"
    click ControlProto "https://github.com/containerd/stargz-snapshotter/blob/main/store/pb/control.proto"
    click ControlPB "https://github.com/containerd/stargz-snapshotter/blob/main/store/pb/control.pb.go"
    click Snapshot "https://github.com/containerd/stargz-snapshotter/blob/main/snapshot/snapshot.go"
    click FSCore "https://github.com/containerd/stargz-snapshotter/blob/main/fs/fs.go"
    click FSConfig "https://github.com/containerd/stargz-snapshotter/blob/main/fs/config/config.go"
    click FSLayer "https://github.com/containerd/stargz-snapshotter/blob/main/fs/layer/layer.go"
    click FSReader "https://github.com/containerd/stargz-snapshotter/blob/main/fs/reader/reader.go"
    click FSRemote "https://github.com/containerd/stargz-snapshotter/blob/main/fs/remote/resolver.go"
    click FSSource "https://github.com/containerd/stargz-snapshotter/blob/main/fs/source/source.go"
    click Cache "https://github.com/containerd/stargz-snapshotter/blob/main/cache/cache.go"
    click AnalyzerCore "https://github.com/containerd/stargz-snapshotter/blob/main/analyzer/analyzer.go"
    click Fanotify "https://github.com/containerd/stargz-snapshotter/blob/main/analyzer/fanotify/fanotify.go"
    click Recorder "https://github.com/containerd/stargz-snapshotter/blob/main/analyzer/recorder/recorder.go"
    click FuseMgr "https://github.com/containerd/stargz-snapshotter/blob/main/fusemanager/fusemanager.go"
    click FuseAPI "https://github.com/containerd/stargz-snapshotter/blob/main/fusemanager/api/api.proto"
    click FuseClient "https://github.com/containerd/stargz-snapshotter/blob/main/fusemanager/client.go"
    click FuseSvc "https://github.com/containerd/stargz-snapshotter/blob/main/fusemanager/service.go"
    click Estargz "https://github.com/containerd/stargz-snapshotter/blob/main/estargz/estargz.go"
    click ExternalTOC "https://github.com/containerd/stargz-snapshotter/blob/main/estargz/externaltoc/externaltoc.go"
    click Gzip "https://github.com/containerd/stargz-snapshotter/blob/main/estargz/gzip.go"
    click NativeConv "https://github.com/containerd/stargz-snapshotter/blob/main/nativeconverter/nativeconverter.go"
    click NC_Stargz "https://github.com/containerd/stargz-snapshotter/blob/main/nativeconverter/estargz/estargz.go"
    click CTRRemote "https://github.com/containerd/stargz-snapshotter/blob/main/cmd/ctr-remote/main.go"
    click StargzStore "https://github.com/containerd/stargz-snapshotter/blob/main/cmd/stargz-store/main.go"
    click FuseCLI "https://github.com/containerd/stargz-snapshotter/blob/main/cmd/stargz-fuse-manager/main.go"
    click DevCI "https://github.com/containerd/stargz-snapshotter/tree/main/script/"

    %% Styles
    classDef runtime fill:#e0f7fa,stroke:#006064,color:#004d40
    classDef prefetch fill:#fff3e0,stroke:#e65100,color:#bf360c
    classDef cli fill:#e8f5e9,stroke:#1b5e20,color:#2e7d32
    classDef cloud fill:#e3f2fd,stroke:#0d47a1,color:#0d47a1
    classDef external fill:#f3e5f5,stroke:#4a148c,color:#4a148c
    classDef dev fill:#fbe9e7,stroke:#bf360c,color:#bf360c

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