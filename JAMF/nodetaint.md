---
created: 2025-03-23 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# nodetaint
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


```mermaid
---
title: "JamF - Nodetaint"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: default
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'lineColor': '#F8B229'
    }
  }
}%%
flowchart TD
    subgraph "CI/CD and Deployment"
        A["Build and CI/CD Automation"]:::cicd
        B["Helm Deployment Artifacts"]:::deployment
        A -->|"triggers"| B
    end

    subgraph "Controller Layer"
        C["nodetaint Controller"]:::controller
        D["Configuration Module"]:::config
        D -->|"supplies config"| C
        B -->|"deploys"| C
    end

    subgraph "Kubernetes Environment"
        E["Kubernetes API/Control Plane"]:::k8s
        subgraph "Cluster Nodes"
            F["Node (with initial taint)"]:::node
            G["Daemonset Pods (Critical)"]:::daemonset
        end
    end

    C -->|"watchesevents"| E
    E -->|"updatesnode taints"| F
    E -->|"monitorspod readiness"| G

    %% Click events
    click C "https://github.com/wish/nodetaint/blob/master/main.go"
    click C "https://github.com/wish/nodetaint/blob/master/config/controller.go"
    click D "https://github.com/wish/nodetaint/blob/master/config/config.go"
    click B "https://github.com/wish/nodetaint/tree/master/chart/"
    click B "https://github.com/wish/nodetaint/tree/master/chart/templates/"
    click A "https://github.com/wish/nodetaint/blob/master/.github/workflows/build.yml"

    %% Styles
    classDef controller fill:#C8E6C9,stroke:#388E3C,stroke-width:2px;
    classDef config fill:#FFF59D,stroke:#FBC02D,stroke-width:2px;
    classDef k8s fill:#BBDEFB,stroke:#1976D2,stroke-width:2px;
    classDef node fill:#FFE0B2,stroke:#F57C00,stroke-width:2px;
    classDef daemonset fill:#FFCDD2,stroke:#D32F2F,stroke-width:2px;
    classDef deployment fill:#D1C4E9,stroke:#7E57C2,stroke-width:2px;
    classDef cicd fill:#B2DFDB,stroke:#00796B,stroke-width:2px

```





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---