---
created: 2025-06-26 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/apple/swift-nio-ssh
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


# swift-nio-ssh repo project
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
title: "swift-nio-ssh repo project"
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
    %% External Dependencies
    subgraph "External Dependencies"
        SwiftNIO["SwiftNIO"]:::external
        SwiftCrypto["Swift Crypto"]:::external
    end

    %% Transport Layer
    subgraph "Transport Layer"
        ByteBuffer["ByteBuffer+SSH Adapter"]:::transport
        Parser["SSHPacketParser"]:::transport
        Serializer["SSHPacketSerializer"]:::transport
        subgraph "TransportProtection"
            AESGCM["AESGCM"]:::transport
            SSHTP["SSHTransportProtection"]:::transport
        end
    end

    %% Core Library
    subgraph "Core Library"
        NIOSSHHandler["NIOSSHHandler"]:::core
        subgraph "State Machines & Multiplexing"
            ConnSM["Connection State Machine"]:::core
            KexSM["Key Exchange State Machine"]:::core
            AuthSM["User Authentication State Machine"]:::core
            AuthDel["UserAuthDelegate"]:::core
            Multiplexer["SSHChannelMultiplexer"]:::core
            ChildSM["ChildChannelStateMachine"]:::core
            ChannelData["SSHChannelData"]:::core
        end
    end

    %% Sample Executables
    subgraph "Sample Executables"
        Client["NIOSSHClient"]:::exec
        Server["NIOSSHServer"]:::exec
        Perf["NIOSSHPerformanceTester"]:::exec
    end

    %% Configuration & Delegates
    SSHClientConfig["SSHClientConfiguration"]:::core
    SSHServerConfig["SSHServerConfiguration"]:::core
    GlobalReqDel["GlobalRequestDelegate"]:::core

    %% Data Flow
    SwiftNIO --> ByteBuffer
    ByteBuffer --> Parser
    Parser --> AESGCM
    AESGCM --> SSHTP
    SSHTP --> Serializer
    Serializer --> ByteBuffer

    SSHTP --> NIOSSHHandler
    NIOSSHHandler --> ConnSM
    NIOSSHHandler --> KexSM
    NIOSSHHandler --> AuthSM
    NIOSSHHandler --> Multiplexer

    Multiplexer --> ChildSM
    ChildSM --> ChannelData
    ChannelData --> Client
    ChannelData --> Server
    ChannelData --> Perf

    %% Delegate Callbacks
    Client -.-> AuthSM
    Server -.-> AuthSM
    Client -.-> GlobalReqDel
    Server -.-> GlobalReqDel

    %% Configuration Injection
    SSHClientConfig --> Client
    SSHServerConfig --> Server
    GlobalReqDel --> NIOSSHHandler

    %% Click Events
    click SwiftNIO "https://github.com/apple/swift-nio-ssh/blob/main/Package.swift"
    click SwiftCrypto "https://github.com/apple/swift-nio-ssh/blob/main/Package.swift"
    click ByteBuffer "https://github.com/apple/swift-nio-ssh/blob/main/Sources/NIOSSH/ByteBuffer+SSH.swift"
    click Parser "https://github.com/apple/swift-nio-ssh/blob/main/Sources/NIOSSH/SSHPacketParser.swift"
    click Serializer "https://github.com/apple/swift-nio-ssh/blob/main/Sources/NIOSSH/SSHPacketSerializer.swift"
    click AESGCM "https://github.com/apple/swift-nio-ssh/blob/main/Sources/NIOSSH/TransportProtection/AESGCM.swift"
    click SSHTP "https://github.com/apple/swift-nio-ssh/blob/main/Sources/NIOSSH/TransportProtection/SSHTransportProtection.swift"
    click NIOSSHHandler "https://github.com/apple/swift-nio-ssh/blob/main/Sources/NIOSSH/NIOSSHHandler.swift"
    click ConnSM "https://github.com/apple/swift-nio-ssh/blob/main/Sources/NIOSSH/Connection State Machine/SSHConnectionStateMachine.swift"
    click KexSM "https://github.com/apple/swift-nio-ssh/blob/main/Sources/NIOSSH/Key Exchange/SSHKeyExchangeStateMachine.swift"
    click AuthSM "https://github.com/apple/swift-nio-ssh/blob/main/Sources/NIOSSH/User Authentication/UserAuthenticationStateMachine.swift"
    click AuthDel "https://github.com/apple/swift-nio-ssh/blob/main/Sources/NIOSSH/User Authentication/UserAuthDelegate.swift"
    click Multiplexer "https://github.com/apple/swift-nio-ssh/blob/main/Sources/NIOSSH/Child Channels/SSHChannelMultiplexer.swift"
    click ChildSM "https://github.com/apple/swift-nio-ssh/blob/main/Sources/NIOSSH/Child Channels/ChildChannelStateMachine.swift"
    click ChannelData "https://github.com/apple/swift-nio-ssh/blob/main/Sources/NIOSSH/Child Channels/SSHChannelData.swift"
    click SSHClientConfig "https://github.com/apple/swift-nio-ssh/blob/main/Sources/NIOSSH/SSHClientConfiguration.swift"
    click SSHServerConfig "https://github.com/apple/swift-nio-ssh/blob/main/Sources/NIOSSH/SSHServerConfiguration.swift"
    click GlobalReqDel "https://github.com/apple/swift-nio-ssh/blob/main/Sources/NIOSSH/GlobalRequestDelegate.swift"
    click Client "https://github.com/apple/swift-nio-ssh/tree/main/Sources/NIOSSHClient"
    click Server "https://github.com/apple/swift-nio-ssh/tree/main/Sources/NIOSSHServer"
    click Perf "https://github.com/apple/swift-nio-ssh/tree/main/Sources/NIOSSHPerformanceTester"

    %% Styles
    classDef external fill:#CCCCCC,stroke:#333,stroke-width:1px;
    classDef transport fill:#FFD700,stroke:#333,stroke-width:1px;
    classDef core fill:#ADD8E6,stroke:#333,stroke-width:1px;
    classDef exec fill:#90EE90,stroke:#333,stroke-width:1px;
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