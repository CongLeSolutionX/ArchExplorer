---
created: 2025-06-26 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/containerd/ttrpc
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


# ttrpc repo project
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


---

```mermaid
---
title: "ttrpc repo project"
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
    %% Build-Time Code Generation
    subgraph "Build-Time Code Generation" 
        direction TB
        PROTOS[".proto Definitions"]:::codegen
        PROTOS -->|used by| PROTOC["protoc"]:::external
        PROTOC -->|loads plugins| PLUGINGEN["plugin/generator.go"]:::codegen
        PROTOC -->|loads plugin| PROTOCTTRPC["protoc-gen-go-ttrpc"]:::codegen
        PROTOC -->|loads plugin| PROTOCGOGO["protoc-gen-gogottrpc"]:::codegen
        PROTOC -->|generates| GENCODE["Generated Code (.pb.go, _ttrpc.pb.go)"]:::artifact
    end

    %% Runtime Library
    subgraph "Runtime Library" 
        direction TB
        PROTOCOL["PROTOCOL.md"]:::doc
        CODEC["codec.go"]:::runtime
        PROTOCOL --> CODEC
        CHANNEL["channel.go"]:::runtime
        CLIENT["client.go"]:::runtime
        SERVER["server.go"]:::runtime
        STREAMSUP["stream.go"]:::runtime
        STREAMSRV["stream_server.go"]:::runtime
        INTERCEPT["interceptor.go"]:::runtime
        META["metadata.go"]:::runtime
        ERRORS["errors.go"]:::runtime
        CONFIG["config.go"]:::runtime
        SERVICES["services.go"]:::runtime
        %% Runtime flow
        CLIENT -->|Invoke| INTERCEPT
        INTERCEPT -->|calls| CHANNEL
        CHANNEL -->|dispatch| SERVER
        SERVER -->|routes| SERVICES
        SERVER -->|wrap via| INTERCEPT
        CHANNEL --> CODEC
    end

    %% Application & Tests
    subgraph "Application & Tests"
        direction TB
        EX_PROTO["example/example.proto"]:::app
        EX_PB["example/example.pb.go"]:::artifact
        EX_TTRPC["example/example_ttrpc.pb.go"]:::artifact
        EX_MAIN["example/cmd/main.go"]:::app
        EX_HAND_L["example/cmd/handshaker_linux.go"]:::app
        EX_HAND_O["example/cmd/handshaker_other.go"]:::app
        INT_PROTO["integration/streaming/test.proto"]:::app
        INT_PB["integration/streaming/test.pb.go"]:::artifact
        INT_TTRPC["integration/streaming/test_ttrpc.pb.go"]:::artifact
        INT_TEST["integration/streaming/streaming_test.go"]:::app
        INT_INTERNAL["internal/test.pb.go"]:::artifact
        SCRIPT["script/install-protobuf"]:::app
        %% Application flow
        PROTOS --> EX_PROTO
        EX_PROTO --> EX_PB
        EX_PROTO --> EX_TTRPC
        EX_MAIN -->|imports| GENCODE
        EX_MAIN -->|imports| CLIENT
        INT_PROTO --> INT_PB
        INT_PROTO --> INT_TTRPC
        INT_TEST -->|uses| INT_TTRPC
        SCRIPT -->|setup| PROTOC
    end

    %% External Dependencies
    subgraph "External Dependencies"
        direction TB
        GOCTX["Go context package"]:::external
        GOGOPROTO["gogo-protobuf runtime"]:::external
        PROTOC
        PROTOBUILD["Protobuild.toml"]:::external
        MAKE["Makefile"]:::external
        GOCTX --> CLIENT
        GOGOPROTO --> GENCODE
        PROTOBUILD --> PROTOC
        MAKE --> PROTOC
    end

    %% Connections
    PROTOS --> PROTOC
    GENCODE -->|compiled with| CLIENT
    GENCODE -->|compiled with| SERVER
    GENCODE -->|used by| EX_MAIN

    %% Click Events
    click PROTOCTTRPC "https://github.com/containerd/ttrpc/tree/main/cmd/protoc-gen-go-ttrpc/"
    click PROTOCGOGO "https://github.com/containerd/ttrpc/tree/main/cmd/protoc-gen-gogottrpc/"
    click PLUGINGEN "https://github.com/containerd/ttrpc/blob/main/plugin/generator.go"
    click CODEC "https://github.com/containerd/ttrpc/blob/main/codec.go"
    click CHANNEL "https://github.com/containerd/ttrpc/blob/main/channel.go"
    click CLIENT "https://github.com/containerd/ttrpc/blob/main/client.go"
    click SERVER "https://github.com/containerd/ttrpc/blob/main/server.go"
    click STREAMSUP "https://github.com/containerd/ttrpc/blob/main/stream.go"
    click STREAMSRV "https://github.com/containerd/ttrpc/blob/main/stream_server.go"
    click INTERCEPT "https://github.com/containerd/ttrpc/blob/main/interceptor.go"
    click META "https://github.com/containerd/ttrpc/blob/main/metadata.go"
    click ERRORS "https://github.com/containerd/ttrpc/blob/main/errors.go"
    click CONFIG "https://github.com/containerd/ttrpc/blob/main/config.go"
    click SERVICES "https://github.com/containerd/ttrpc/blob/main/services.go"
    click PROTOCOL "https://github.com/containerd/ttrpc/blob/main/PROTOCOL.md"
    click GOMOD "https://github.com/containerd/ttrpc/blob/main/go.mod"
    click GOSUM "https://github.com/containerd/ttrpc/blob/main/go.sum"
    click MAKE "https://github.com/containerd/ttrpc/tree/main/Makefile"
    click PROTOBUILD "https://github.com/containerd/ttrpc/blob/main/Protobuild.toml"
    click EX_PROTO "https://github.com/containerd/ttrpc/blob/main/example/example.proto"
    click EX_PB "https://github.com/containerd/ttrpc/blob/main/example/example.pb.go"
    click EX_TTRPC "https://github.com/containerd/ttrpc/blob/main/example/example_ttrpc.pb.go"
    click EX_MAIN "https://github.com/containerd/ttrpc/blob/main/example/cmd/main.go"
    click EX_HAND_L "https://github.com/containerd/ttrpc/blob/main/example/cmd/handshaker_linux.go"
    click EX_HAND_O "https://github.com/containerd/ttrpc/blob/main/example/cmd/handshaker_other.go"
    click INT_PROTO "https://github.com/containerd/ttrpc/blob/main/integration/streaming/test.proto"
    click INT_PB "https://github.com/containerd/ttrpc/blob/main/integration/streaming/test.pb.go"
    click INT_TTRPC "https://github.com/containerd/ttrpc/blob/main/integration/streaming/test_ttrpc.pb.go"
    click INT_TEST "https://github.com/containerd/ttrpc/blob/main/integration/streaming/streaming_test.go"
    click INT_INTERNAL "https://github.com/containerd/ttrpc/blob/main/internal/test.pb.go"
    click PROTO_STATUS "https://github.com/containerd/ttrpc/blob/main/proto/status.proto"
    click PROTO_REQ "https://github.com/containerd/ttrpc/blob/main/proto/request.proto"
    click REQ_PB "https://github.com/containerd/ttrpc/blob/main/proto/request.pb.go"
    click SCRIPT "https://github.com/containerd/ttrpc/tree/main/script/install-protobuf"

    %% Styles
    classDef codegen fill:#D6EFFF,stroke:#0384fc,color:#000;
    classDef runtime fill:#daffd6,stroke:#35b536,color:#000;
    classDef app fill:#fff5b1,stroke:#d4b000,color:#000;
    classDef external fill:#eeeeee,stroke:#999999,color:#000;
    classDef artifact fill:#ffffff,stroke:#6666ff,color:#000,stroke-dasharray: 5 5;
    classDef doc fill:#ffe6e6,stroke:#ff4d4d,color:#000;
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