---
created: 2025-06-27 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/grpc/grpc
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




# grpc repo project
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
title: "grpc repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'linear'},
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#22BB',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EEF2',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '15px'
    }
  }
}%%
flowchart LR
    %% Layers
    subgraph "Code-Generation & Build"
        direction TB
        Protoc["Protoc + gRPC Plugins"]:::codegen
        GeneratedStubs["Generated Stubs"]:::codegen
    end

    subgraph "Language Wrappers & Runtimes"
        direction TB
        CppRuntime["C++ Runtime/Wrapper"]:::language
        PythonRuntime["Python grpcio (_cygrpc)"]:::language
        PhpExt["PHP grpc extension"]:::language
        PhpLib["PHP grpc library"]:::language
        RubyExt["Ruby grpc extension"]:::language
        RubyLib["Ruby grpc library"]:::language
        CsharpTools["C# Grpc.Tools"]:::language
        ObjCClient["Objective-C GRPCClient"]:::language
        ObjCProtoRPC["Objective-C ProtoRPC"]:::language
    end

    subgraph "Shared C++ Core"
        direction TB
        CoreSurface["Core Surface API"]:::core
        CompletionQueue["CompletionQueue"]:::core
        Channel["Channel"]:::core
        Call["Call"]:::core
        Metadata["Metadata"]:::core
        Filters["Pluggable Filters & Credentials"]:::core
        subgraph "Upb / Protobuf Support"
            direction TB
            UPB["UPB"]:::core
            Proto["Proto Encoding"]:::core
        end
    end

    subgraph "Transport Modules"
        direction TB
        HTTP2["HTTP/2 Transport"]:::transport
        Inproc["In-Proc Transport"]:::transport
        Chaotic["Chaotic Good Transport"]:::transport
    end

    subgraph "Event Engine"
        direction TB
        Posix["POSIX Engine (epoll)"]:::engine
        CFRunLoop["CFRunLoop Engine"]:::engine
    end

    subgraph "External Services"
        direction TB
        DNSCAres["DNS Resolver (c-ares)"]:::external
        DNSNative["Native DNS Resolver"]:::external
        xDS["xDS Control Plane"]:::external
        CertTLS["TLS Certificate Providers"]:::external
        CertFileWatcher["File Watcher Cert Provider"]:::external
    end

    %% Application Flow
    UserApp["User Application"]:::external
    UserApp -->|"invokes stub"| GeneratedStubs
    GeneratedStubs -->|"calls stub"| CppRuntime
    GeneratedStubs -->|" "| PythonRuntime
    GeneratedStubs -->|" "| PhpExt
    GeneratedStubs -->|" "| PhpLib
    GeneratedStubs -->|" "| RubyExt
    GeneratedStubs -->|" "| RubyLib
    GeneratedStubs -->|" "| CsharpTools
    GeneratedStubs -->|" "| ObjCClient
    GeneratedStubs -->|" "| ObjCProtoRPC

    %% Runtime to Core
    CppRuntime -->|"marshals RPC"| CoreSurface
    PythonRuntime -->|"marshals RPC"| CoreSurface
    PhpExt -->|"marshals RPC"| CoreSurface
    PhpLib -->|"marshals RPC"| CoreSurface
    RubyExt -->|"marshals RPC"| CoreSurface
    RubyLib -->|"marshals RPC"| CoreSurface
    CsharpTools -->|"marshals RPC"| CoreSurface
    ObjCClient -->|"marshals RPC"| CoreSurface
    ObjCProtoRPC -->|"marshals RPC"| CoreSurface

    %% Core internal
    CoreSurface --> CompletionQueue
    CompletionQueue --> HTTP2
    CompletionQueue --> Inproc
    CompletionQueue --> Chaotic
    HTTP2 --> Posix
    HTTP2 --> CFRunLoop

    %% Network
    Posix -->|"sends over socket"| Network["OS Socket / Network"]
    CFRunLoop -->|"sends over socket"| Network

    Network -->|"response"| HTTP2
    HTTP2 --> CoreSurface
    CoreSurface -->|"response"| PythonRuntime
    CoreSurface -->|"response"| CppRuntime
    CoreSurface -->|"response"| PhpExt
    CoreSurface -->|"response"| PhpLib
    CoreSurface -->|"response"| RubyExt
    CoreSurface -->|"response"| RubyLib
    CoreSurface -->|"response"| CsharpTools
    CoreSurface -->|"response"| ObjCClient
    CoreSurface -->|"response"| ObjCProtoRPC

    %% Control Plane & Resolvers
    DNSCAres --> CoreSurface
    DNSNative --> CoreSurface
    xDS --> CoreSurface
    CertTLS --> CoreSurface
    CertFileWatcher --> CoreSurface

    %% Build flow
    Protoc --> GeneratedStubs

    %% Click Events
    click Protoc "https://github.com/grpc/grpc/tree/master/src/compiler"
    click CppRuntime "https://github.com/grpc/grpc/tree/master/src/cpp"
    click PythonRuntime "https://github.com/grpc/grpc/tree/master/src/python/grpcio"
    click PhpExt "https://github.com/grpc/grpc/tree/master/src/php/ext/grpc"
    click PhpLib "https://github.com/grpc/grpc/tree/master/src/php/lib/Grpc"
    click RubyExt "https://github.com/grpc/grpc/tree/master/src/ruby/ext/grpc"
    click RubyLib "https://github.com/grpc/grpc/tree/master/src/ruby/lib/grpc"
    click CsharpTools "https://github.com/grpc/grpc/blob/master/src/csharp/Grpc.Tools"
    click ObjCClient "https://github.com/grpc/grpc/tree/master/src/objective-c/GRPCClient"
    click ObjCProtoRPC "https://github.com/grpc/grpc/tree/master/src/objective-c/ProtoRPC"
    click CoreSurface "https://github.com/grpc/grpc/tree/master/src/core"
    click UPB "https://github.com/grpc/grpc/tree/master/third_party/upb"
    click Proto "https://github.com/grpc/grpc/tree/master/src/proto"
    click DNSCAres "https://github.com/grpc/grpc/tree/master/src/core/resolver/dns/c_ares"
    click DNSNative "https://github.com/grpc/grpc/blob/master/src/core/lib/event_engine/ares_resolver.cc"
    click xDS "https://github.com/grpc/grpc/tree/master/src/core/xds"
    click CertTLS "https://github.com/grpc/grpc/tree/master/src/core/credentials/transport/tls"
    click CertFileWatcher "https://github.com/grpc/grpc/blob/master/src/core/xds/grpc/file_watcher_certificate_provider_factory.cc"
    click HTTP2 "https://github.com/grpc/grpc/tree/master/src/core/ext/transport/chttp2"
    click Inproc "https://github.com/grpc/grpc/tree/master/src/core/ext/transport/inproc"
    click Chaotic "https://github.com/grpc/grpc/tree/master/src/core/ext/transport/chaotic_good"
    click Posix "https://github.com/grpc/grpc/tree/master/src/core/lib/event_engine/posix_engine"
    click CFRunLoop "https://github.com/grpc/grpc/tree/master/src/core/lib/event_engine/cf_engine"

    %% Styles
    classDef codegen fill:#c8e6c9,stroke:#2e7d32,color:#2e7d32
    classDef language fill:#bbdefb,stroke:#1565c0,color:#1565c0
    classDef core fill:#ffe0b2,stroke:#ef6c00,color:#e65100
    classDef transport fill:#ffcdd2,stroke:#c62828,color:#b71c1c
    classDef engine fill:#e1bee7,stroke:#6a1b9a,color:#4a148c
    classDef external fill:#cfd8dc,stroke:#455a64,color:#263238

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