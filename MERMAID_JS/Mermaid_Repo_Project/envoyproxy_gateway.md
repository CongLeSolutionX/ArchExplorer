---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Envoy Proxy - gateway
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
title: "MERMAID-JS - Envoy Proxy - gateway"
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
    %% External Inputs
    subgraph External_Inputs["External Inputs"]
    style External_Inputs fill:#c222,stroke:#333,stroke-width:2px
        K8sCRDs["Kubernetes API (Gateway API CRDs)"]:::external
        CLI1["egctl CLI (cmd/egctl)"]:::cli
        CLI2["egctl CLI (internal/cmd/egctl)"]:::cli
    end

    %% Control Plane
    subgraph Control_Plane["Control Plane"]
    style Control_Plane fill:#c222,stroke:#333,stroke-width:2px
        GC["Gateway Controller"]:::control
        CT["Configuration Manager and Translator"]:::control

        subgraph xDS_Components["xDS Components"]
            XDS_S["xDS Server"]:::control
            XDS_C["xDS Cache"]:::control
        end

        subgraph Providers_and_Connectors["Providers & Connectors"]
            Prov1["File Provider"]:::control
            Prov2["Infrastructure Connector"]:::control
            Prov3["Kubernetes Connector"]:::control
        end

        subgraph Observability["Observability"]
            Metrics["Metrics"]:::admin
            Logging["Logging"]:::admin
        end
    end

    %% Data Plane
    subgraph Data_Plane["Data Plane"]
    style Data_Plane fill:#c222,stroke:#333,stroke-width:2px
        Envoy["Envoy Proxy"]:::data
    end

    %% Interactions
    K8sCRDs -->|"feeds"| GC
    CLI1 -->|"CLI commands"| GC
    CLI2 -->|"CLI commands"| GC

    Prov1 -->|"provides config"| GC
    Prov2 -->|"provides config"| GC
    Prov3 -->|"provides config"| GC

    GC -->|"sends config"| CT
    CT -->|"generates xDS snapshot"| XDS_S
    XDS_S -->|"caches snapshot"| XDS_C
    XDS_C -->|"pushes config"| Envoy

    Metrics --- GC
    Logging --- GC
    Metrics --- XDS_S
    Logging --- XDS_S

    CLI1 --- Metrics
    CLI2 --- Logging

    %% Click Events
    click GC "https://github.com/envoyproxy/gateway/tree/main/api/v1alpha1"
    click CT "https://github.com/envoyproxy/gateway/tree/main/internal/xds/translator"
    click XDS_S "https://github.com/envoyproxy/gateway/tree/main/internal/xds/server"
    click XDS_C "https://github.com/envoyproxy/gateway/tree/main/internal/xds/cache"
    click Prov1 "https://github.com/envoyproxy/gateway/tree/main/internal/provider"
    click Prov2 "https://github.com/envoyproxy/gateway/tree/main/internal/infrastructure"
    click Prov3 "https://github.com/envoyproxy/gateway/tree/main/internal/kubernetes"
    click CLI1 "https://github.com/envoyproxy/gateway/tree/main/cmd/egctl"
    click CLI2 "https://github.com/envoyproxy/gateway/tree/main/internal/cmd/egctl"
    click Envoy "https://github.com/envoyproxy/gateway/tree/main/cmd/envoy-gateway"

    %% Styles
    classDef control fill:#B3CDE,stroke:#005B96,stroke-width:2px
    classDef data fill:#FAD4A,stroke:#E6550D,stroke-width:2px
    classDef external fill:#CC33,stroke:#31A354,stroke-width:2px
    classDef cli fill:#D9D9F,stroke:#4B0082,stroke-width:2px
    classDef admin fill:#FEE0D,stroke:#C51B8A,stroke-width:2px

    class GC,CT,XDS_S,XDS_C,Prov1,Prov2,Prov3 control
    class Envoy data
    class K8sCRDs external
    class CLI1,CLI2 cli
    class Metrics,Logging admin



```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---