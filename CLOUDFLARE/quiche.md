---
created: 2025-07-01 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/cloudflare/quiche
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




# quiche repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for 👨‍🎓 <ins>educational purposes</ins> 👨‍🎓 (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), 📖 <ins> personal study </ins> 📖, and 🔖 <ins> technical reference </ins> 🔖.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>



---

```mermaid
---
title: "quiche repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright © 2025 Cong Le. All Rights Reserved."
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
    subgraph "Layer 1: Foundational Crates"
        FP1["buffer-pool"]:::foundation
        DS["datagram-socket"]:::foundation
        OC["octets"]:::foundation
        QL["qlog"]:::foundation
    end

    subgraph "Core Transport Engine"
        QC["quiche core"]:::core
        CAPI["C API"]:::ffi
    end

    subgraph "Layer 3: High-Level Libraries"
        H3["h3i"]:::high
        TQ["tokio-quiche"]:::high
    end

    subgraph "Layer 4: Applications & Tools"
        CLI["CLI Apps (quiche-client/server)"]:::app
        FT["Fuzz Harness"]:::app
        TEST["tools/http3_test"]:::app
        CI["CI/CD Workflows"]:::infra
    end

    OS["OS Sockets & Timers"]:::external
    TLS["BoringSSL/OpenSSL"]:::external
    Tokio["Tokio Runtime"]:::external
    Logsink["Log Sink"]:::external
    CClients["C/C++ Clients"]:::external

    OS -->|“UDP packets & timer events”| DS
    DS -->|"datagrams"| QC
    QC -->|"send()"| DS
    QC -->|"QLOG events"| QL
    QL -->|"stream logs"| Logsink

    FP1 --> QC
    DS --> QC
    OC --> QC
    QL --> QC

    QC --> CAPI
    CAPI -. calls .-> CClients

    QC --> H3
    QC --> TQ
    TQ -->|“async I/O & timers”| Tokio

    H3 --> QC

    CLI --> QC
    CLI --> H3
    CLI --> TQ
    FT --> QC
    TEST --> QC
    CI --> FP1
    CI --> DS
    CI --> OC
    CI --> QL
    CI --> QC
    CI --> H3
    CI --> TQ
    CI --> CLI
    CI --> FT
    CI --> TEST

    TLS -->|"TLS backend"| QC

    classDef foundation fill:#AED6F1,stroke:#21618C,color:#1B4F72
    classDef core fill:#F1948A,stroke:#922B21,color:#641E16
    classDef high fill:#ABEBC6,stroke:#196F3D,color:#145A32
    classDef app fill:#F8C471,stroke:#B9770E,color:#7E5109
    classDef infra fill:#D7BDE2,stroke:#6C3483,color:#4A235A
    classDef external fill:#F5F5F5,stroke:#566573,color:#212F3D
    classDef ffi fill:#FFFFFF,stroke-dasharray: 5 5,stroke:#000000,color:#000000

    click FP1 "https://github.com/cloudflare/quiche/tree/master/buffer-pool/"
    click DS "https://github.com/cloudflare/quiche/tree/master/datagram-socket/"
    click OC "https://github.com/cloudflare/quiche/tree/master/octets/"
    click QL "https://github.com/cloudflare/quiche/tree/master/qlog/"
    click QC "https://github.com/cloudflare/quiche/tree/master/quiche/"
    click CAPI "https://github.com/cloudflare/quiche/blob/master/quiche/include/quiche.h"
    click H3 "https://github.com/cloudflare/quiche/tree/master/h3i/"
    click TQ "https://github.com/cloudflare/quiche/tree/master/tokio-quiche/"
    click CLI "https://github.com/cloudflare/quiche/tree/master/apps/"
    click FT "https://github.com/cloudflare/quiche/tree/master/fuzz/"
    click TEST "https://github.com/cloudflare/quiche/tree/master/tools/http3_test/"
    click CI "https://github.com/cloudflare/quiche/tree/master/.github/workflows/"
    click CI "https://github.com/cloudflare/quiche/blob/master/.gitlab-ci.yml"

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
copyright: "Copyright © 2025 Cong Le. All Rights Reserved."
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