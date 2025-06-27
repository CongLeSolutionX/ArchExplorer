---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/apple/servicetalk
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExMTZ6OHF4bjJka2I4Z3QzbWlpNTU1cWkwbTc4YmdkYjk4ZjVhc2xsciZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/imjTC8KaAB1HW/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# service_talk
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## A Diagrammatic Guide 




```mermaid
---
title: "Apple - Service Talk"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "graph": {"htmlLabels": true, 'curve': 'natural'},
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#f231',
      'primaryTextColor': '#239',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TD

    %% External Requests
    Ext["External Clients"]:::core

    %% Public API Layer
    subgraph "Public API Layer"
        HTTP_API["HTTP Protocol API"]:::api
        GRPC_API["gRPC Protocol API"]:::api
    end

    %% Advanced Features / Client-Side Enhancements
    subgraph "Advanced Features"
        LB["Client‐Side Load Balancing"]:::adv
        EXP_LB["Experimental Load Balancing Provider"]:::adv
        DNS["DNS Discovery"]:::adv
    end

    %% Security and Routing
    subgraph "Security & Routing"
        HTTP_SEC["HTTP Security (Jersey)"]:::security
        HTTP_RTR["HTTP Routing (Jersey)"]:::security
    end

    %% Instrumentation and Observability
    subgraph "Instrumentation & Observability"
        LOG_MDC["Logging and MDC Utilities"]:::instr
        LOG_API["Logging API"]:::instr
        SLF4J["SLF4J Logging Internal"]:::instr
        OT_ASYNC["OpenTracing Async Context"]:::instr
        OT_HTTP["OpenTracing HTTP Filters"]:::instr
        OT_MEMORY["In-Memory Tracing"]:::instr
        OT_LOG4J2["OpenTracing Log4j2 Integration"]:::instr
        ZIPKIN["Zipkin Publisher for Tracing"]:::instr
    end

    %% Serialization / Encoding and Data
    subgraph "Serialization / Encoding"
        JACKSON["Serialization – Jackson"]:::serialization
        PROTOBUF["Serialization – Protobuf"]:::serialization
    end

    %% Transport Layer
    subgraph "Transport Layer"
        TRANSPORT_API["Transport API Layer"]:::transport
        NETTY_IMPL["Netty‐Based Transport Implementation"]:::transport
    end

    %% Core / Abstract Layers
    subgraph "Core & Configuration"
        CORE_UTIL["Core/Abstract APIs and Utilities"]:::core
        BOM["BOM/Configuration"]:::core
    end

    %% Test and Build Support
    TEST["Test and Build Support"]:::test

    %% External Dependency: Netty
    NETTY["Netty Framework"]:::transport

    %% Connections: External to Public API
    Ext -->|"initiates"| HTTP_API
    Ext -->|"initiates"| GRPC_API

    %% Public API interactions with Advanced Features
    HTTP_API -->|"uses"| LB
    GRPC_API -->|"uses"| LB
    LB -->|"delegatesTo"| EXP_LB
    LB -->|"integratesWith"| DNS

    %% Public API interacting with Security and Routing
    HTTP_API -->|"securedBy"| HTTP_SEC
    HTTP_API -->|"routedBy"| HTTP_RTR

    %% Public API interacting with Instrumentation
    HTTP_API -->|"observedBy"| LOG_API
    GRPC_API -->|"observedBy"| OT_ASYNC

    %% Public API interacting with Serialization
    HTTP_API -->|"serializesVia"| JACKSON
    HTTP_API -->|"serializesVia"| PROTOBUF
    GRPC_API -->|"serializesVia"| JACKSON
    GRPC_API -->|"serializesVia"| PROTOBUF

    %% Public API to Transport Layer flow
    HTTP_API -->|"calls"| HTTP_Netty["HTTP Netty Implementation"]:::transport
    GRPC_API -->|"calls"| gRPC_Netty["gRPC Netty Implementation"]:::transport

    %% Protocol Implementation to Transport API
    HTTP_Netty:::transport --> TRANSPORT_API
    gRPC_Netty:::transport --> TRANSPORT_API

    %% Transport API to Netty‐Based Transport Implementation and Netty Framework
    TRANSPORT_API --> NETTY_IMPL
    NETTY_IMPL --> NETTY

    %% Core & Configuration supports all layers (dotted connections)
    CORE_UTIL --- HTTP_API
    CORE_UTIL --- GRPC_API
    BOM --- TRANSPORT_API
    CORE_UTIL --- TRANSPORT_API

    %% Instrumentation connections to Transport Layer (observing lower layers)
    NETTY_IMPL -->|"tracedBy"| OT_HTTP

    %% Test and Build Support integrates with Core
    TEST --- CORE_UTIL
    TEST --- BOM

    %% Click Events
    click CORE_UTIL "https://github.com/apple/servicetalk/tree/main/servicetalk-annotations"
    click BOM "https://github.com/apple/servicetalk/tree/main/servicetalk-bom"
    click TRANSPORT_API "https://github.com/apple/servicetalk/tree/main/servicetalk-transport-api"
    click NETTY_IMPL "https://github.com/apple/servicetalk/tree/main/servicetalk-tcp-netty-internal"
    click HTTP_API "https://github.com/apple/servicetalk/tree/main/servicetalk-http-api"
    click HTTP_Netty "servicetalk-http-netty"
    click GRPC_API "https://github.com/apple/servicetalk/tree/main/servicetalk-grpc-api"
    click gRPC_Netty "servicetalk-grpc-netty"
    click JACKSON "https://github.com/apple/servicetalk/tree/main/servicetalk-data-jackson"
    click PROTOBUF "https://github.com/apple/servicetalk/tree/main/servicetalk-data-protobuf"
    click LB "https://github.com/apple/servicetalk/tree/main/servicetalk-loadbalancer"
    click EXP_LB "https://github.com/apple/servicetalk/tree/main/servicetalk-loadbalancer-experimental-provider"
    click DNS "https://github.com/apple/servicetalk/tree/main/servicetalk-dns-discovery-netty"
    click HTTP_SEC "https://github.com/apple/servicetalk/tree/main/servicetalk-http-security-jersey"
    click HTTP_RTR "https://github.com/apple/servicetalk/tree/main/servicetalk-http-router-jersey"
    click LOG_MDC "https://github.com/apple/servicetalk/tree/main/servicetalk-log4j2-mdc-utils"
    click LOG_API "https://github.com/apple/servicetalk/tree/main/servicetalk-logging-api"
    click SLF4J "https://github.com/apple/servicetalk/tree/main/servicetalk-logging-slf4j-internal"
    click OT_ASYNC "https://github.com/apple/servicetalk/tree/main/servicetalk-opentracing-asynccontext"
    click OT_HTTP "https://github.com/apple/servicetalk/tree/main/servicetalk-opentracing-http"
    click OT_MEMORY "https://github.com/apple/servicetalk/tree/main/servicetalk-opentracing-inmemory"
    click OT_LOG4J2 "https://github.com/apple/servicetalk/tree/main/servicetalk-opentracing-log4j2"
    click ZIPKIN "https://github.com/apple/servicetalk/tree/main/servicetalk-opentracing-zipkin-publisher"
    click TEST "https://github.com/apple/servicetalk/tree/main/servicetalk-test-resources"

    %% Styles
    classDef core fill:#e0f7f,stroke:#006064,stroke-width:2px
    classDef api fill:#f3e5f,stroke:#6a1b9a,stroke-width:2px
    classDef transport fill:#e1f5f,stroke:#0277bd,stroke-width:2px
    classDef serialization fill:#e8f5e,stroke:#2e7d32,stroke-width:2px
    classDef adv fill:#cd24,stroke:#f9a825,stroke-width:2px
    classDef security fill:#ffebe,stroke:#c62828,stroke-width:2px
    classDef instr fill:#f1f8e,stroke:#33691e,stroke-width:2px
    classDef test fill:#eceff,stroke:#607d8b,stroke-width:2px
    
```



---

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
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }

```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
