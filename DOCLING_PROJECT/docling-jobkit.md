---
created: 2025-03-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Docling Jobkit
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
title: "Docling Jobkit"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: base
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
    A["Client / Job Submitter<br>(ray job submit)"]:::client -->|"submit job"| B["Ray Cluster Head Node"]:::head
    B:::head -->|"distributes job"| C["Ray Worker Nodes"]:::worker

    subgraph Worker_Modules["Worker Modules"]
        D["Docling Jobkit – Ray Job Module"]:::module
        E["Docling Jobkit – Connectors Module"]:::module
    end
    
    C:::worker --> D:::module
    C:::worker --> E:::module
    D:::module -->|"uses"| E:::module

    F["Custom Runtime Environment<br>(runtime_env.yml)"]:::config -.-> C:::worker

    subgraph Documentation_and_Automation["Documentation & Automation"]
        G["Ray Cluster Deployment Documentation"]:::doc
        H["Ray Job Usage Documentation"]:::doc
        I["CI/CD and Release Automation"]:::doc
    end

    %% Click Events
    click D "docling_jobkit/ray_job/main.py"
    click E "docling_jobkit/connectors"
    click G "docs/ray-cluster-deployment"
    click H "docs/ray-job/README.md"
    click I ".github/workflows"

    %% Styles
    classDef client fill:#bbdefb,stroke:#0d47a1,stroke-width:2px
    classDef head fill:#c8e6c9,stroke:#1b5e20,stroke-width:2px
    classDef worker fill:#ffe082,stroke:#ff6f00,stroke-width:2px
    classDef module fill:#ffccbc,stroke:#d84315,stroke-width:2px
    classDef config fill:#e1bee7,stroke:#6a1b9a,stroke-width:2px
    classDef doc fill:#d1c4e9,stroke:#4a148c,stroke-width:2px
    
```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---