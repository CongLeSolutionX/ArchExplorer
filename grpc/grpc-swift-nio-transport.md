---
created: 2025-06-27 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/grpc/grpc-swift-nio-transport
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




# grpc-swift-nio-transport repo project
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
title: "grpc-swift-nio-transport repo project"
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
flowchart TD
    %% Integration Tests
    subgraph "Integration Tests" 
        Interop["gRPC Interop Tests"]:::tests
        Performance["gRPC Performance Tests"]:::tests
    end
    click Interop "https://github.com/grpc/grpc-swift-nio-transport/tree/main/IntegrationTests/grpc-interop-tests"
    click Performance "https://github.com/grpc/grpc-swift-nio-transport/tree/main/IntegrationTests/grpc-performance-tests"

    %% Application Layer
    Application["gRPC Swift Client & Server"]:::application

    %% Core Transport Layer
    subgraph "GRPCNIOTransportCore" 
        Core["Core Transport Abstraction"]:::core
        subgraph "Core Modules"
            Client["Client"]:::core
            Server["Server"]:::core
            Compression["Compression Interfaces"]:::core
            Internal["Internal Utilities"]:::core
        end
    end
    click Core "https://github.com/grpc/grpc-swift-nio-transport/tree/main/Sources/GRPCNIOTransportCore"
    click Client "https://github.com/grpc/grpc-swift-nio-transport/tree/main/Sources/GRPCNIOTransportCore/Client"
    click Server "https://github.com/grpc/grpc-swift-nio-transport/tree/main/Sources/GRPCNIOTransportCore/Server"
    click Compression "https://github.com/grpc/grpc-swift-nio-transport/tree/main/Sources/GRPCNIOTransportCore/Compression"
    click Internal "https://github.com/grpc/grpc-swift-nio-transport/tree/main/Sources/GRPCNIOTransportCore/Internal"

    %% Zlib Compressor
    Zlib["CGRPCNIOTransportZlib"]:::zlib
    click Zlib "https://github.com/grpc/grpc-swift-nio-transport/tree/main/Sources/CGRPCNIOTransportZlib"

    %% HTTP/2 Framing Layer
    subgraph "GRPCNIOTransportHTTP2"
        HTTP2["HTTP/2 Framing & Parsing"]:::http2
    end
    click HTTP2 "https://github.com/grpc/grpc-swift-nio-transport/tree/main/Sources/GRPCNIOTransportHTTP2"

    %% Platform Transports
    subgraph "Platform Transports"
        Posix["HTTP2TransportPosix"]:::platform
        TS["HTTP2TransportTransportServices"]:::platform
    end
    click Posix "https://github.com/grpc/grpc-swift-nio-transport/tree/main/Sources/GRPCNIOTransportHTTP2Posix"
    click TS "https://github.com/grpc/grpc-swift-nio-transport/tree/main/Sources/GRPCNIOTransportHTTP2TransportServices"

    %% SwiftNIO Core
    SwiftNIO["SwiftNIO Core\n(EventLoopGroup, ChannelPipeline,\nNIOHTTP2Handler, SocketChannel)"]:::swiftnio

    %% Network
    Network["Network (TCP/TLS)"]:::network

    %% Dev Scripts
    Dev["dev/ Scripts"]:::dev
    click Dev "https://github.com/grpc/grpc-swift-nio-transport/tree/main/dev/"

    %% Data Flow
    Interop -->|uses public API| Application
    Performance -->|uses public API| Application
    Application -->|GRPCChannel API| Core
    Core -->|CompressionProtocol| Compression
    Compression -->|C calls| Zlib
    Core -->|framed messages| HTTP2
    HTTP2 -->|HTTP/2 frames| Posix
    HTTP2 -->|HTTP/2 frames| TS
    Posix -->|bootstrap + TLS| SwiftNIO
    TS -->|bootstrap + TLS| SwiftNIO
    SwiftNIO -->|TCP/TLS| Network

    %% Styles
    classDef application fill:#D7BDE2,stroke:#884EA0,color:#1A5276;
    classDef core fill:#AED6F1,stroke:#2874A6,color:#1B2631;
    classDef zlib fill:#D5D8DC,stroke:#7F8C8D,color:#1B2631,shape:cylinder;
    classDef http2 fill:#A9DFBF,stroke:#229954,color:#1B2631;
    classDef platform fill:#F5CBA7,stroke:#CA6F1E,color:#1B2631;
    classDef swiftnio fill:#FCF3CF,stroke:#B7950B,color:#1B2631;
    classDef network fill:#F5B7B1,stroke:#C0392B,color:#1B2631,shape:cylinder;
    classDef tests fill:#E8DAEF,stroke:#6C3483,color:#1B2631,stroke-dasharray: 5 5;
    classDef dev fill:#F2F3F4,stroke:#717D7E,color:#1B2631,stroke-dasharray: 2 2;

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
    
  Closing_quote ~~~ My_Meme
    
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