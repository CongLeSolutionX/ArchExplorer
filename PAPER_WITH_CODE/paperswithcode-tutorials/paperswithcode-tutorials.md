---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Papers With Code - Tutorials
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
title: "Papers With Code - Tutorials"
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
    "flowchart": {"htmlLabels": true, 'curve': 'natural'},
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
    User("User/Contributor"):::contributor
    DR("Documentation Repository"):::repository
    README("README.md (Central Hub)"):::doc
    AP("add_paper.md"):::doc
    AR("add_results.md"):::doc
    AT("add_task.md"):::doc
    GHI("GitHub Issues"):::external

    User -->|"access"| DR
    DR -->|"contains"| README
    README -->|"linksTo"| AP
    README -->|"linksTo"| AR
    README -->|"linksTo"| AT
    README -->|"feedback"| GHI

    click DR "https://github.com/paperswithcode/tutorials/tree/main/project root"
    click README "https://github.com/paperswithcode/tutorials/blob/main/README.md"
    click AP "https://github.com/paperswithcode/tutorials/blob/main/add_paper.md"
    click AR "https://github.com/paperswithcode/tutorials/blob/main/add_results.md"
    click AT "https://github.com/paperswithcode/tutorials/blob/main/add_task.md"

    classDef contributor fill:#ffccc,stroke:#cc0000,stroke-width:2px
    classDef repository fill:#ffe6b,stroke:#cc6600,stroke-width:2px
    classDef doc fill:#cce5f,stroke:#004085,stroke-width:2px
    classDef external fill:#d4edd,stroke:#155724,stroke-width:2px,stroke-dasharray: 5,5

```

---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---