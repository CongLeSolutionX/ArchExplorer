---
created: 2025-06-26 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/containerd/ttrpc-rust
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


# ttrpc-rust repo project
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
title: "ttrpc-rust repo project"
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
flowchart TB
    %% Build-Time Tools
    subgraph "Build-Time Tools"
        Developer[(Developer)]:::external
        Proto[".proto Files"]:::external
        Developer --> Proto
        Proto --> Protoc["protoc"]:::build
        Protoc --> PluginBin["ttrpc_rust_plugin"]:::build
        subgraph "Protoc Plugin (compiler/)"
            PluginBin
            CodegenPL["codegen.rs"]:::build
            Prost["prost_codegen.rs"]:::build
            UtilMod["util/mod.rs"]:::build
            Scope["util/scope.rs"]:::build
            Writer["util/writer.rs"]:::build
        end
        Proto --> CodegenCrate["ttrpc-codegen"]:::build
        subgraph "Standalone Codegen (ttrpc-codegen/)"
            Parser["parser.rs"]:::build
            Model["model.rs"]:::build
            Convert["convert.rs"]:::build
            StrLit["str_lit.rs"]:::build
            Lib["lib.rs"]:::build
        end
        PluginBin --> Generated["Generated Rust Code"]:::build
        CodegenCrate --> Generated
        Generated --> Cargo["cargo build"]:::build
    end

    %% Core Runtime Library
    subgraph "Core Runtime Library (src/)"
        subgraph Shared
            LibRs["lib.rs"]:::core
            Common["common.rs"]:::core
            Context["context.rs"]:::core
            Error["error.rs"]:::core
            Macros["macros.rs"]:::core
            ProtoMod["proto.rs"]:::core
        end
        subgraph "Sync Stack"
            SyncMod["mod.rs"]:::core
            SyncClient["client.rs"]:::core
            SyncServer["server.rs"]:::core
            Channel["channel.rs"]:::core
            SyncUtils["utils.rs"]:::core
            UnixNet["unix/net.rs"]:::core
            WinNet["windows/net.rs"]:::core
        end
        subgraph "Async Stack"
            AsyncMod["mod.rs"]:::core
            AsyncClient["client.rs"]:::core
            AsyncServer["server.rs"]:::core
            Connection["connection.rs"]:::core
            Stream["stream.rs"]:::core
            Shutdown["shutdown.rs"]:::core
            AsyncUtils["utils.rs"]:::core
            TransMod["transport/mod.rs"]:::core
            TrUnix["transport/unix.rs"]:::core
            TrVsock["transport/vsock.rs"]:::core
            TrWin["transport/windows.rs"]:::core
        end
    end

    %% Runtime Flow
    subgraph "Runtime Flow"
        AppCli["Client App"]:::example
        AppSrv["Server App"]:::example
        AppCli -->|"calls API"| LibRs
        AppSrv -->|"calls API"| LibRs
        LibRs -->|"uses Sync"| SyncClient
        LibRs -->|"uses Async"| AsyncClient
        SyncClient --> UnixNet
        SyncClient --> WinNet
        SyncClient --> TrVsock
        AsyncClient --> TrUnix
        AsyncClient --> TrVsock
        AsyncClient --> TrWin
        AppSrv --> SyncServer
        AppSrv --> AsyncServer
        SyncServer --> UnixNet
        AsyncServer --> TransMod
    end

    %% Examples
    subgraph Examples
        ExSyncCli["example/client.rs"]:::example
        ExSyncSrv["example/server.rs"]:::example
        ExAsyncCli["example/async-client.rs"]:::example
        ExAsyncSrv["example/async-server.rs"]:::example
        ExAsyncStrCli["example/async-stream-client.rs"]:::example
        ExAsyncStrSrv["example/async-stream-server.rs"]:::example
        BuildEx["example/build.rs"]:::example
    end

    %% Connections between build and core
    Cargo --> LibRs

    %% Click Events for Plugin
    click PluginBin "https://github.com/containerd/ttrpc-rust/blob/master/compiler/src/bin/ttrpc_rust_plugin.rs"
    click CodegenPL "https://github.com/containerd/ttrpc-rust/blob/master/compiler/src/codegen.rs"
    click Prost "https://github.com/containerd/ttrpc-rust/blob/master/compiler/src/prost_codegen.rs"
    click UtilMod "https://github.com/containerd/ttrpc-rust/blob/master/compiler/src/util/mod.rs"
    click Scope "https://github.com/containerd/ttrpc-rust/blob/master/compiler/src/util/scope.rs"
    click Writer "https://github.com/containerd/ttrpc-rust/blob/master/compiler/src/util/writer.rs"

    %% Click Events for Standalone Codegen
    click Parser "https://github.com/containerd/ttrpc-rust/blob/master/ttrpc-codegen/src/parser.rs"
    click Model "https://github.com/containerd/ttrpc-rust/blob/master/ttrpc-codegen/src/model.rs"
    click Convert "https://github.com/containerd/ttrpc-rust/blob/master/ttrpc-codegen/src/convert.rs"
    click StrLit "https://github.com/containerd/ttrpc-rust/blob/master/ttrpc-codegen/src/str_lit.rs"
    click Lib "https://github.com/containerd/ttrpc-rust/blob/master/ttrpc-codegen/src/lib.rs"

    %% Click Events for Core Runtime
    click LibRs "https://github.com/containerd/ttrpc-rust/blob/master/src/lib.rs"
    click Common "https://github.com/containerd/ttrpc-rust/blob/master/src/common.rs"
    click Context "https://github.com/containerd/ttrpc-rust/blob/master/src/context.rs"
    click Error "https://github.com/containerd/ttrpc-rust/blob/master/src/error.rs"
    click Macros "https://github.com/containerd/ttrpc-rust/blob/master/src/macros.rs"
    click ProtoMod "https://github.com/containerd/ttrpc-rust/blob/master/src/proto.rs"
    click SyncMod "https://github.com/containerd/ttrpc-rust/blob/master/src/sync/mod.rs"
    click SyncClient "https://github.com/containerd/ttrpc-rust/blob/master/src/sync/client.rs"
    click SyncServer "https://github.com/containerd/ttrpc-rust/blob/master/src/sync/server.rs"
    click Channel "https://github.com/containerd/ttrpc-rust/blob/master/src/sync/channel.rs"
    click SyncUtils "https://github.com/containerd/ttrpc-rust/blob/master/src/sync/utils.rs"
    click UnixNet "https://github.com/containerd/ttrpc-rust/blob/master/src/sync/sys/unix/net.rs"
    click WinNet "https://github.com/containerd/ttrpc-rust/blob/master/src/sync/sys/windows/net.rs"
    click AsyncMod "https://github.com/containerd/ttrpc-rust/blob/master/src/asynchronous/mod.rs"
    click AsyncClient "https://github.com/containerd/ttrpc-rust/blob/master/src/asynchronous/client.rs"
    click AsyncServer "https://github.com/containerd/ttrpc-rust/blob/master/src/asynchronous/server.rs"
    click Connection "https://github.com/containerd/ttrpc-rust/blob/master/src/asynchronous/connection.rs"
    click Stream "https://github.com/containerd/ttrpc-rust/blob/master/src/asynchronous/stream.rs"
    click Shutdown "https://github.com/containerd/ttrpc-rust/blob/master/src/asynchronous/shutdown.rs"
    click AsyncUtils "https://github.com/containerd/ttrpc-rust/blob/master/src/asynchronous/utils.rs"
    click TransMod "https://github.com/containerd/ttrpc-rust/blob/master/src/asynchronous/transport/mod.rs"
    click TrUnix "https://github.com/containerd/ttrpc-rust/blob/master/src/asynchronous/transport/unix.rs"
    click TrVsock "https://github.com/containerd/ttrpc-rust/blob/master/src/asynchronous/transport/vsock.rs"
    click TrWin "https://github.com/containerd/ttrpc-rust/blob/master/src/asynchronous/transport/windows.rs"

    %% Click Events for Examples
    click ExSyncCli "https://github.com/containerd/ttrpc-rust/blob/master/example/client.rs"
    click ExSyncSrv "https://github.com/containerd/ttrpc-rust/blob/master/example/server.rs"
    click ExAsyncCli "https://github.com/containerd/ttrpc-rust/blob/master/example/async-client.rs"
    click ExAsyncSrv "https://github.com/containerd/ttrpc-rust/blob/master/example/async-server.rs"
    click ExAsyncStrCli "https://github.com/containerd/ttrpc-rust/blob/master/example/async-stream-client.rs"
    click ExAsyncStrSrv "https://github.com/containerd/ttrpc-rust/blob/master/example/async-stream-server.rs"
    click BuildEx "https://github.com/containerd/ttrpc-rust/blob/master/example/build.rs"

    %% Styling
    classDef build fill:#D0E8FF,stroke:#069;
    classDef external fill:#F0F0F0,stroke:#999;
    classDef core fill:#E8F8E0,stroke:#2E8B57;
    classDef example fill:#FFE8C0,stroke:#E08;

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