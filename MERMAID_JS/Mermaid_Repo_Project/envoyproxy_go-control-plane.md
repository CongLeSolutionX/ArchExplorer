---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is an ongoing document collecting notes for personal educational purposes and references. 
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExeHJ4YXdtYjJpMDl0MzEwYmU4ZzBobG0waGNiN3MzNzR0d2R2NnMwNSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/26gssNOlBJKjEM3yo/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----

# Envoy Proxy - go-control-plane
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
title: "MERMAID-JS - Envoy Proxy - go-control-plane"
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
    "flowchart": { "htmlLabels": true, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TD
    Envoy_Clients["Envoy Clients<br>(Envoy Clients)"]:::client
    
    subgraph API_Server["API Server"]
    style API_Server fill:#c222,stroke:#333,stroke-width:2px
        SOTW_Endpoint["SOTW Endpoint<br>(SOTW Endpoint)"]:::api
        Delta_Endpoint["Delta Endpoint<br>(Delta Endpoint)"]:::api
        Stream_Endpoint["Stream Endpoint<br>(Stream Endpoint)"]:::api
    end

    subgraph Configuration_Caches["Configuration Caches"]
    style Configuration_Caches fill:#c222,stroke:#333,stroke-width:2px
        Snapshot_Cache["Snapshot Cache<br>(Snapshot Cache)"]:::cache
        Linear_Cache["Linear Cache<br>(Linear Cache)"]:::cache
        Mux_Cache["Mux Cache<br>(Mux Cache)"]:::cache
    end

    Configuration_Input["Configuration Input<br>(Configuration Input)"]:::cache

    subgraph Supporting_Modules["Supporting Modules"]
    style Supporting_Modules fill:#c222,stroke:#333,stroke-width:2px
        Logging["Logging<br>(Logging)"]:::support
        Conversion["Conversion<br>(Conversion)"]:::support
        Resource_Definitions["Resource Definitions<br>(Resource Definitions)"]:::support
    end

    subgraph Auxiliary_Services["Auxiliary Services"]
    style Auxiliary_Services fill:#c222,stroke:#333,stroke-width:2px
        REST_Service["REST Service<br>(REST Service)"]:::aux
        Integration_Tests_Examples["Integration Tests/Examples<br>(Integration Tests/Examples)"]:::aux
        Ratelimit_Service["Ratelimit Service<br>(Ratelimit Service)"]:::aux
    end

    Envoy_Clients -->|"SOTW request"| SOTW_Endpoint
    Envoy_Clients -->|"Delta request"| Delta_Endpoint
    
    SOTW_Endpoint -->|"uses"| Snapshot_Cache
    Delta_Endpoint -->|"uses"| Linear_Cache
    Stream_Endpoint -->|"uses"| Mux_Cache

    Configuration_Input -->|"populates"| Snapshot_Cache
    Configuration_Input -->|"populates"| Linear_Cache
    Configuration_Input -->|"populates"| Mux_Cache

    Logging -->|"supports"| SOTW_Endpoint
    Conversion -->|"supports"| Delta_Endpoint
    Resource_Definitions -->|"supports"| Stream_Endpoint

    SOTW_Endpoint -->|"exposes"| REST_Service
    Delta_Endpoint -->|"integrates"| Integration_Tests_Examples
    SOTW_Endpoint -->|"integrates"| Ratelimit_Service

    click SOTW_Endpoint "pkg/server/sotw/v3"
    click Delta_Endpoint "pkg/server/delta/v3"
    click Stream_Endpoint "pkg/server/stream/v3"
    click Snapshot_Cache "pkg/cache/v3/simple.go"
    click Linear_Cache "pkg/cache/v3/linear.go"
    click Mux_Cache "pkg/cache/v3/mux.go"
    click Envoy_Clients "pkg/client/sotw/v3/client.go"
    click Logging "pkg/log/log.go"
    click Conversion "pkg/conversion/struct.go"
    click Resource_Definitions "pkg/resource/v3/resource.go"
    click REST_Service "pkg/server/rest/v3/server.go"
    click Integration_Tests_Examples "internal/example"
    click Ratelimit_Service "ratelimit/service/ratelimit/v3"

    classDef client fill:#fe73,stroke:#333,stroke-width:2px;
    classDef api fill:#ad64,stroke:#333,stroke-width:2px;
    classDef cache fill:#adf2,stroke:#333,stroke-width:2px;
    classDef support fill:#fd45,stroke:#333,stroke-width:2px;
    classDef aux fill:#dbd3,stroke:#333,stroke-width:2px;
    
```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
