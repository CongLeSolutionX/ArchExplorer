---
created: 2025-06-26 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/apple/swift-nio-transport-services
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


# swift-nio-transport-services repo project
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
title: "swift-nio-transport-services repo project"
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
    %% Application Layer
    subgraph "Application Layer"
        direction TB
        NIOTSHTTPClient["NIOTSHTTPClient"]:::application
        NIOTSHTTPServer["NIOTSHTTPServer"]:::application
    end

    %% Library Layer
    subgraph "NIOTransportServices Core Library"
        direction TB
        subgraph "Bootstraps"
            NIOTSConnectionBootstrap["NIOTSConnectionBootstrap"]:::library
            NIOTSListenerBootstrap["NIOTSListenerBootstrap"]:::library
            NIOTSDatagramConnectionBootstrap["NIOTSDatagramConnectionBootstrap"]:::library
            NIOTSDatagramListenerBootstrap["NIOTSDatagramListenerBootstrap"]:::library
            NIOTSBootstraps["Bootstraps Aggregator"]:::library
        end

        subgraph "Event Loop"
            NIOTSEventLoopGroup["NIOTSEventLoopGroup"]:::library
            NIOTSEventLoop["NIOTSEventLoop"]:::library
            DispatchQueueCyl[(DispatchQueue)]:::apple
        end

        subgraph "Channels & Pipeline"
            NIOTSConnectionChannel["NIOTSConnectionChannel"]:::library
            NIOTSListenerChannel["NIOTSListenerChannel"]:::library
            NIOTSDatagramConnectionChannel["NIOTSDatagramConnectionChannel"]:::library
            NIOTSDatagramListenerChannel["NIOTSDatagramListenerChannel"]:::library
            NIOFilterEmptyWritesHandler["NIOFilterEmptyWritesHandler"]:::library
            NIOTSChannelOptions["NIOTSChannelOptions"]:::library
            SocketAddressNWEndpoint["SocketAddress+NWEndpoint"]:::library
        end

        subgraph "Utilities"
            NIOTSErrors["NIOTSErrors"]:::library
            NIOTSSingletons["NIOTSSingletons"]:::library
            NIOTSNetworkEvents["NIOTSNetworkEvents"]:::library
            TCPOptions["TCPOptions+SocketChannelOption"]:::library
            UDPOptions["UDPOptions+SocketChannelOption"]:::library
            StateManagedChannel["StateManagedChannel"]:::library
            StateManagedListenerChannel["StateManagedListenerChannel"]:::library
            StateManagedNWConnectionChannel["StateManagedNWConnectionChannel"]:::library
        end
    end

    %% External Dependencies
    subgraph "Apple Frameworks"
        direction TB
        NWConnection["NWConnection"]:::apple
        NWListener["NWListener"]:::apple
        NWEndpoint["NWEndpoint"]:::apple
    end

    subgraph "SwiftNIO Core"
        direction TB
        SNIOEventLoopGroup["EventLoopGroup"]:::nio
        SNIOChannel["Channel"]:::nio
        SNIOBootstrap["Bootstrap"]:::nio
    end

    %% Connections
    NIOTSHTTPClient -->|"uses"| NIOTSConnectionBootstrap
    NIOTSHTTPServer -->|"uses"| NIOTSListenerBootstrap

    NIOTSConnectionBootstrap -->|"configures"| NIOTSBootstraps
    NIOTSListenerBootstrap -->|"configures"| NIOTSBootstraps
    NIOTSDatagramConnectionBootstrap -->|"configures"| NIOTSBootstraps
    NIOTSDatagramListenerBootstrap -->|"configures"| NIOTSBootstraps

    NIOTSBootstraps -->|"creates"| NIOTSEventLoopGroup
    NIOTSEventLoopGroup -->|"spawns"| NIOTSEventLoop
    NIOTSEventLoop -->|"runs on"| DispatchQueueCyl

    NIOTSConnectionBootstrap -->|"bind/connect"| NWConnection
    NIOTSListenerBootstrap -->|"bind"| NWListener
    NIOTSDatagramListenerBootstrap -->|"bind"| NWListener
    NIOTSDatagramConnectionBootstrap -->|"connect"| NWConnection

    NWConnection -->|"data bytes"| NIOTSConnectionChannel
    NWListener -->|"incoming"| NIOTSListenerChannel
    NWConnection -->|"data bytes"| NIOTSDatagramConnectionChannel
    NWListener -->|"incoming"| NIOTSDatagramListenerChannel

    NIOTSConnectionChannel -->|"pipeline"| NIOFilterEmptyWritesHandler
    NIOTSListenerChannel -->|"pipeline"| NIOFilterEmptyWritesHandler
    NIOTSDatagramConnectionChannel -->|"pipeline"| NIOFilterEmptyWritesHandler
    NIOTSDatagramListenerChannel -->|"pipeline"| NIOFilterEmptyWritesHandler

    NIOTSChannelOptions -->|"applied to"| NIOTSConnectionChannel
    SocketAddressNWEndpoint -->|"translates"| NWEndpoint

    %% Fallback to SwiftNIO Core
    NIOTSBootstraps -.->|"fallback"| SNIOBootstrap
    SNIOBootstrap -->|"socket path"| SNIOEventLoopGroup
    SNIOEventLoopGroup -->|"spawns"| SNIOEventLoopGroup

    %% Click Events
    click NIOTSHTTPClient "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTSHTTPClient/main.swift"
    click NIOTSHTTPServer "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTSHTTPServer/main.swift"
    click NIOTSEventLoop "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTransportServices/NIOTSEventLoop.swift"
    click NIOTSEventLoopGroup "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTransportServices/NIOTSEventLoopGroup.swift"
    click NIOTSConnectionChannel "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTransportServices/NIOTSConnectionChannel.swift"
    click NIOTSListenerChannel "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTransportServices/NIOTSListenerChannel.swift"
    click NIOTSDatagramConnectionChannel "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTransportServices/Datagram/NIOTSDatagramConnectionChannel.swift"
    click NIOTSDatagramListenerChannel "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTransportServices/Datagram/NIOTSDatagramListenerChannel.swift"
    click NIOTSConnectionBootstrap "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTransportServices/NIOTSConnectionBootstrap.swift"
    click NIOTSListenerBootstrap "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTransportServices/NIOTSListenerBootstrap.swift"
    click NIOTSDatagramConnectionBootstrap "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTransportServices/Datagram/NIOTSDatagramConnectionBootstrap.swift"
    click NIOTSDatagramListenerBootstrap "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTransportServices/Datagram/NIOTSDatagramListenerBootstrap.swift"
    click NIOTSBootstraps "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTransportServices/NIOTSBootstraps.swift"
    click NIOFilterEmptyWritesHandler "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTransportServices/NIOFilterEmptyWritesHandler.swift"
    click NIOTSChannelOptions "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTransportServices/NIOTSChannelOptions.swift"
    click TCPOptions "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTransportServices/TCPOptions+SocketChannelOption.swift"
    click UDPOptions "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTransportServices/UDPOptions+SocketChannelOption.swift"
    click NIOTSErrors "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTransportServices/NIOTSErrors.swift"
    click NIOTSSingletons "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTransportServices/NIOTSSingletons.swift"
    click NIOTSNetworkEvents "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTransportServices/NIOTSNetworkEvents.swift"
    click SocketAddressNWEndpoint "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTransportServices/SocketAddress+NWEndpoint.swift"
    click StateManagedChannel "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTransportServices/StateManagedChannel.swift"
    click StateManagedListenerChannel "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTransportServices/StateManagedListenerChannel.swift"
    click StateManagedNWConnectionChannel "https://github.com/apple/swift-nio-transport-services/blob/main/Sources/NIOTransportServices/StateManagedNWConnectionChannel.swift"

    %% Styles
    classDef application fill:#FFF89A,stroke:#333,stroke-width:1px
    classDef library fill:#7DE2D1,stroke:#333,stroke-width:1px
    classDef apple fill:#FFB56B,stroke:#333,stroke-width:1px
    classDef nio fill:#A4D0F5,stroke:#333,stroke-width:1px
```

---

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