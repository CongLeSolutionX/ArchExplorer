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

# Envoy Proxy - java-control-plane
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
title: "MERMAID-JS - Envoy Proxy - java-control-plane"
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
    %% External Client
    EP["Envoy Proxy/External Client"]:::external

    %% API Module
    subgraph API_Module["API Module"]
    style API_Module fill:#c222,stroke:#333,stroke-width:2px
        API["API & Protobuf Contracts"]:::contracts
    end

    %% Cache Module
    subgraph Cache_Module["Cache Module"]
    style Cache_Module fill:#c222,stroke:#333,stroke-width:2px
        CACHE["Snapshot Cache"]:::service
    end

    %% Server Module
    subgraph Server_Module["Server Module"]
    style Server_Module fill:#c222,stroke:#333,stroke-width:2px
        SERVER["Discovery Server<br>(gRPC endpoints)"]:::service
    end

    %% Supporting Tools/Build Infrastructure
    subgraph CI_CD_and_Release_Tools["CI/CD & Release Tools"]
    style CI_CD_and_Release_Tools fill:#c222,stroke:#333,stroke-width:2px
        BCS["buildscripts"]:::infra
        CIRC[".circleci"]:::infra
        TOOLS["tools"]:::infra
        GITHUB[".github"]:::infra
    end

    %% Tests
    subgraph Tests["Tests"]
    style Tests fill:#c222,stroke:#333,stroke-width:2px
        TESTS["Tests"]:::tests
    end

    %% Environment technologies annotation
    ENV["Environment:<br>Java 8+, Maven"]:::note

    %% Connections
    EP -->|"sends request"| SERVER
    SERVER -->|"fetch config"| CACHE
    CACHE -->|"deliver snapshot"| SERVER

    API ---|"defines contracts"| SERVER
    API ---|"defines contracts"| CACHE

    %% Optionally link supporting tools and tests as auxiliary components
    SERVER ---|"CI/CD integration"| BCS
    SERVER ---|"CI/CD integration"| CIRC
    SERVER ---|"CI/CD integration"| TOOLS
    SERVER ---|"CI/CD integration"| GITHUB

    SERVER ---|"tested by"| TESTS
    CACHE ---|"tested by"| TESTS
    API ---|"tested by"| TESTS

    ENV

    %% Click Events
    click API "https://github.com/envoyproxy/java-control-plane/tree/main/api/"
    click CACHE "https://github.com/envoyproxy/java-control-plane/tree/main/cache/"
    click SERVER "https://github.com/envoyproxy/java-control-plane/tree/main/server/"
    click BCS "https://github.com/envoyproxy/java-control-plane/tree/main/buildscripts/"
    click CIRC "https://github.com/envoyproxy/java-control-plane/tree/main/.circleci/"
    click TOOLS "https://github.com/envoyproxy/java-control-plane/tree/main/tools/"
    click GITHUB "https://github.com/envoyproxy/java-control-plane/tree/main/.github/"
    click TESTS "https://github.com/envoyproxy/java-control-plane/tree/main/test/"

    %% Styles
    classDef external fill:#f6a3,stroke:#333,stroke-width:2px
    classDef service fill:#fcc5,stroke:#333,stroke-width:2px
    classDef contracts fill:#cfc3,stroke:#333,stroke-width:2px
    classDef infra fill:#cef5,stroke:#333,stroke-width:2px
    classDef tests fill:#ecf4,stroke:#333,stroke-width:2px
    classDef note fill:#ffc4,stroke:#333,stroke-width:2px
    
```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
