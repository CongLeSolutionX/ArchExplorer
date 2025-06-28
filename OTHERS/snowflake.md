---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/keroserene/snowflake
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExZmdoYWhxb3c2NmR6OGZoMzN5NWxqNjJmbmVxd3U0NDFobjc4ZHdvNyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/xUA7bjPYcgAvwq5CKc/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# keroserene - snowflake repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes (<ins>sometimes, entertainment purposes</ins>), personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


---

```mermaid
flowchart TB
    %% External Services
    DomainFront["Domain Fronting CDN"]:::external
    TorNetwork["Tor Network (Relays)"]:::external

    %% Broker Component
    subgraph "Broker Service"
        Broker["Broker HTTP API (domain-fronted), port 443"]:::signaling
    end

    %% Client and Proxy and Server
    subgraph "Snowflake Components"
        TorClient["Tor Pluggable-Transport Client"]:::datapath
        VolunteerProxy["Volunteer Proxy (Browser/Go)"]:::datapath
        TorPTServer["Tor PT Server (WebRTC Relay)"]:::serverlayer
    end

    %% Common Libraries
    CommonLib["Common Libraries"]:::common

    %% Optional Probetest
    Probetest["Probetest NAT Probe Service"]:::test

    %% Flows
    DomainFront -->|"HTTPS/AMP Signaling"| Broker
    Broker -->|"Proxy Offers (ICE candidates)"| TorClient
    TorClient -->|"WebRTC ICE Negotiation"| VolunteerProxy
    TorClient <-->|"DataChannel (DTLS/SCTP)"| VolunteerProxy
    VolunteerProxy -->|"Tor cells over WebRTC"| TorPTServer
    TorPTServer -->|"Tor cells"| TorNetwork

    %% Dependencies on common libraries
    CommonLib --> Broker
    CommonLib --> TorClient
    CommonLib --> VolunteerProxy
    CommonLib --> TorPTServer

    %% Probetest Connection
    Probetest -.->|"NAT probing tests"| CommonLib

    %% Click Events
    click Broker "https://github.com/keroserene/snowflake/blob/master/broker/broker.go"
    click TorClient "https://github.com/keroserene/snowflake/blob/master/client/snowflake.go"
    click VolunteerProxy "https://github.com/keroserene/snowflake/blob/master/proxy/main.go"
    click TorPTServer "https://github.com/keroserene/snowflake/blob/master/server/server.go"
    click CommonLib "https://github.com/keroserene/snowflake/tree/master/common/"
    click Probetest "https://github.com/keroserene/snowflake/blob/master/probetest/probetest.go"

    %% Styles
    classDef signaling fill:#cce5ff,stroke:#004085,color:#004085
    classDef datapath fill:#d4edda,stroke:#155724,color:#155724
    classDef serverlayer fill:#ffe5b4,stroke:#ff8c00,color:#ff8c00
    classDef external fill:#e2e3e5,stroke:#6c757d,color:#6c757d
    classDef common fill:#f8d7da,stroke:#721c24,color:#721c24
    classDef test fill:#d1ecf1,stroke:#0c5460,color:#0c5460
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
><b>Licenses</b>:
>
>- <b>MIT License</b>:  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
>- <b>Creative Commons Attribution-ShareAlike 4.0 International</b>: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) [![CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/88x31.png)](https://creativecommons.org/licenses/by-sa/4.0/) - Legal details in [LICENSE-CC-BY-SA-4.0](THE_PAST/LICENSE-CC-BY-SA-4.0) and at [Creative Commons official site](https://creativecommons.org/licenses/by-sa/4.0/).
>
---
