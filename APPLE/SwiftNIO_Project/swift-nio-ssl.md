---
created: 2025-06-26 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/apple/swift-nio-ssl
---

<div align="center">
  <p>⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷</p>
  <i>This is a working draft in progress.</i>
  <br/>
  <img alt="Loading…" src="https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExc3FwZDdnaXl4ZGZyaDYwMmx1ZDdtMmF6YnBmaXNwNHVyMnVvYTFkOSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/vc0vReKfhmsYSzS9ua/giphy.gif"/>
  <br/>
  <blockquote>
	  <i>gif image is provided by <a href="https://giphy.com">Giphy</a></i>
  </blockquote>
  <p>⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷</p>

</div>


# swift-nio-ssl repo project
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
title: "swift-nio-ssl repo project"
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
    %% Main vertical stack
    A["User Application<br/>(ClientBootstrap/ServerBootstrap)"]:::swift
    B["SwiftNIO<br/>ChannelPipeline"]:::external
    C["NIOSSL Handlers<br/>(NIOSSLClientHandler/NIOSSLServerHandler)"]:::swift
    D["NIOSSLContext &<br/>TLSConfiguration"]:::swift
    E["CNIOBoringSSL<br/>(Swift Wrapper)"]:::swift
    F["CNIOBoringSSLShims<br/>(C Shim)"]:::shim
    G["BoringSSL C Library<br/>(crypto & gen)"]:::c

    A --> B
    B --> C
    C --> D
    D --> E
    E --> F
    F --> G

    %% Side: Tests & Samples
    subgraph "Tests & Samples"
        H["Sample HTTP/1 Client"]:::swift
        I["Sample TLS Server"]:::swift
        J["Performance Tester Tools"]:::swift
        K["Unit & Integration Tests"]:::dashed
        L["Integration Test Harness"]:::dashed
    end

    H --> B
    I --> B
    J --> B
    K --> C
    K --> D
    L --> C

    %% Benchmarks
    subgraph "Benchmarks"
        M["Benchmark Suite"]:::swift
    end
    M --> C

    %% CI & Docker
    subgraph "CI & Infrastructure"
        N["CI/CD Workflows"]:::dashed
        O["Docker Configurations"]:::dashed
    end
    N --> K
    N --> M
    N --> G
    O --> G

    %% Click Events
    click G "https://github.com/apple/swift-nio-ssl/tree/main/Sources/CNIOBoringSSL/crypto"
    click G "https://github.com/apple/swift-nio-ssl/tree/main/Sources/CNIOBoringSSL/gen"
    click F "https://github.com/apple/swift-nio-ssl/blob/main/Sources/CNIOBoringSSLShims/include/CNIOBoringSSLShims.h"
    click F "https://github.com/apple/swift-nio-ssl/blob/main/Sources/CNIOBoringSSLShims/shims.c"
    click E "https://github.com/apple/swift-nio-ssl/blob/main/Sources/CNIOBoringSSL/include/module.modulemap"
    click E "https://github.com/apple/swift-nio-ssl/tree/main/Sources/CNIOBoringSSL/include"
    click D "https://github.com/apple/swift-nio-ssl/tree/main/Sources/NIOSSL"
    click H "https://github.com/apple/swift-nio-ssl/blob/main/Sources/NIOSSLHTTP1Client/main.swift"
    click I "https://github.com/apple/swift-nio-ssl/blob/main/Sources/NIOTLSServer/main.swift"
    click J "https://github.com/apple/swift-nio-ssl/tree/main/Sources/NIOSSLPerformanceTester"
    click K "https://github.com/apple/swift-nio-ssl/tree/main/Tests/NIOSSLTests"
    click L "https://github.com/apple/swift-nio-ssl/blob/main/IntegrationTests/run-tests.sh"
    click M "https://github.com/apple/swift-nio-ssl/tree/main/Benchmarks/Benchmarks/NIOSSLBenchmarks"
    click N "https://github.com/apple/swift-nio-ssl/blob/main/.github/workflows/main.yml"
    click O "https://github.com/apple/swift-nio-ssl/tree/main/docker/Dockerfile"

    %% Styles
    classDef swift fill:#ADD8E6,stroke:#333,stroke-width:1px
    classDef c fill:#90EE90,stroke:#333,stroke-width:1px
    classDef shim fill:#FFFFE0,stroke:#333,stroke-width:1px
    classDef external fill:#D3D3D3,stroke:#333,stroke-width:1px
    classDef dashed stroke:#333,stroke-dasharray:5 5,fill:#fff,stroke-width:1px
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
