---
created: 2025-07-01 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/cloudflare/cloudflared
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




# cloudflared repo project
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



-----

```mermaid
---
title: "cloudflared repo project"
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
    %% Subgraph: User Interface & CLI
    subgraph "User Interface & CLI"
        CLI["cmd/cloudflared (CLI Entry Point)"]:::cli
    end

    %% Subgraph: API & Cloudflare Communication
    subgraph "API & Cloudflare Communication"
        CFAPI["cfapi (Cloudflare API)"]:::api
        Carrier["carrier (WebSocket Channeling)"]:::api
    end

    %% Subgraph: Tunnel Management & Control
    subgraph "Tunnel Management & Control"
        Tunnel["cmd/cloudflared/tunnel"]:::tunnel
        Management["management (Tunnel Management)"]:::tunnel
        Supervisor["supervisor (Session Supervisor)"]:::tunnel
        Orchestration["orchestration (Control & Routing)"]:::tunnel
        TunnelRPC["tunnelrpc (RPC Interface)"]:::tunnel
    end

    %% Subgraph: Connection & Network Protocols
    subgraph "Connection & Network Protocols"
        Connection["connection (General Connection)"]:::connection
        QUIC["quic (QUIC Protocol)"]:::connection
        WebSocket["websocket (WebSocket Protocol)"]:::connection
    end

    %% Subgraph: Ingress & Origin Proxying
    subgraph "Ingress & Origin Proxying"
        Ingress["ingress (Traffic Proxying)"]:::ingress
    end

    %% Subgraph: Diagnostics, Metrics, and Logging
    subgraph "Diagnostics & Observability"
        Diagnostic["diagnostic (System Diagnostics)"]:::diagnostics
        Logger["logger (Logging)"]:::diagnostics
        Metrics["metrics (Performance Metrics)"]:::diagnostics
        Tracing["tracing (Request Tracing)"]:::diagnostics
        Overwatch["overwatch (Monitoring)"]:::diagnostics
    end

    %% Subgraph: Supporting / Auxiliary Components
    subgraph "Supporting Components"
        Credentials["credentials (TLS & Credential Management)"]:::supporting
        Flow["flow (Rate Limiting)"]:::supporting
        Retry["retry (Retry Mechanism)"]:::supporting
        TLSConfig["tlsconfig (TLS Configuration)"]:::supporting
    end

    %% External Entities
    Cloudflare["Cloudflare Network"]:::external
    Origin["Origin Servers"]:::external

    %% Connections between major components
    CLI -->|"dispatches"| Tunnel
    CLI -->|"invokes"| CFAPI

    Tunnel -->|"initiates"| Management
    Management -->|"supervises"| Supervisor
    Supervisor -->|"orchestrates"| Orchestration
    Orchestration -->|"handles"| TunnelRPC

    Orchestration -->|"setsUp"| Connection
    Connection -->|"uses"| QUIC
    Connection -->|"uses"| WebSocket

    CFAPI -->|"authenticates"| Carrier
    Tunnel ---|"requestsCreds"| CFAPI

    CFAPI -->|"communicates"| Cloudflare
    Carrier -->|"channels"| Cloudflare

    Cloudflare -->|"forwardsTraffic"| Ingress
    Ingress -->|"proxies"| Origin

    %% Monitoring arrows from components to Diagnostics
    CLI -->|"monitoredBy"| Diagnostic
    CFAPI -->|"monitoredBy"| Diagnostic
    Tunnel -->|"monitoredBy"| Diagnostic
    Connection -->|"monitoredBy"| Diagnostic
    Ingress -->|"monitoredBy"| Diagnostic

    %% Supporting components usage (dashed arrows)
    CFAPI -.->|"uses"| Credentials
    CFAPI -.->|"uses"| TLSConfig
    Ingress -.->|"uses"| Flow
    Tunnel -.->|"uses"| Retry

    %% Click Events
    click CLI "https://github.com/cloudflare/cloudflared/tree/master/cmd/cloudflared"
    click CFAPI "https://github.com/cloudflare/cloudflared/tree/master/cfapi/"
    click Carrier "https://github.com/cloudflare/cloudflared/tree/master/carrier/"
    click Tunnel "https://github.com/cloudflare/cloudflared/tree/master/cmd/cloudflared/tunnel"
    click Management "https://github.com/cloudflare/cloudflared/tree/master/management/"
    click Supervisor "https://github.com/cloudflare/cloudflared/tree/master/supervisor/"
    click Orchestration "https://github.com/cloudflare/cloudflared/tree/master/orchestration/"
    click TunnelRPC "https://github.com/cloudflare/cloudflared/tree/master/tunnelrpc/"
    click Connection "https://github.com/cloudflare/cloudflared/tree/master/connection/"
    click QUIC "https://github.com/cloudflare/cloudflared/tree/master/quic/"
    click WebSocket "https://github.com/cloudflare/cloudflared/tree/master/websocket/"
    click Ingress "https://github.com/cloudflare/cloudflared/tree/master/ingress/"
    click Diagnostic "https://github.com/cloudflare/cloudflared/tree/master/diagnostic/"
    click Logger "https://github.com/cloudflare/cloudflared/tree/master/logger/"
    click Metrics "https://github.com/cloudflare/cloudflared/tree/master/metrics/"
    click Tracing "https://github.com/cloudflare/cloudflared/tree/master/tracing/"
    click Overwatch "https://github.com/cloudflare/cloudflared/tree/master/overwatch/"
    click Credentials "https://github.com/cloudflare/cloudflared/tree/master/credentials/"
    click Flow "https://github.com/cloudflare/cloudflared/tree/master/flow/"
    click Retry "https://github.com/cloudflare/cloudflared/tree/master/retry/"
    click TLSConfig "https://github.com/cloudflare/cloudflared/tree/master/tlsconfig/"

    %% Styles
    classDef cli fill:#a3e4d7,stroke:#239B56,stroke-width:2px;
    classDef api fill:#aed6f1,stroke:#2874A6,stroke-width:2px;
    classDef tunnel fill:#82e0aa,stroke:#28B463,stroke-width:2px;
    classDef connection fill:#85C1E9,stroke:#1F618D,stroke-width:2px;
    classDef ingress fill:#BB8FCE,stroke:#8E44AD,stroke-width:2px;
    classDef diagnostics fill:#F9E79F,stroke:#B7950B,stroke-width:2px;
    classDef supporting fill:#D5DBDB,stroke:#7F8C8D,stroke-width:2px;
    classDef external fill:#F5B7B1,stroke:#C0392B,stroke-width:2px;

```

-----

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