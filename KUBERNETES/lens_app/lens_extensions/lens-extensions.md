---
created: 2025-03-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Lens App - Lens Extensions
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
title: "Lens App - Lens Extensions"
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
    catalog["Lens Extensions Catalog<br>(README.md)"]:::internal
    vendor["Vendor Extensions"]:::internal
    community["Community Extensions"]:::internal
    experimental["Experimental & Fun & Demos"]:::internal
    incompatible["Incompatible Extensions"]:::internal
    vendorExt["Vendor Extension<br>(External)"]:::external
    communityExt["Community Extension<br>(External)"]:::external
    experimentalExt["Experimental Extension<br>(External)"]:::external
    incompatibleExt["Incompatible Extension<br>(External)"]:::external
    contributor["External Contributor"]:::external

    catalog -->|"categorizes"| vendor
    catalog -->|"categorizes"| community
    catalog -->|"categorizes"| experimental
    catalog -->|"categorizes"| incompatible

    vendor -->|"points to"| vendorExt
    community -->|"points to"| communityExt
    experimental -->|"points to"| experimentalExt
    incompatible -->|"points to"| incompatibleExt

    contributor -->|"contribution"| catalog

    click catalog "https://github.com/lensapp/lens-extensions/blob/main/README.md"

    classDef internal fill:#cce5f,stroke:#004085,stroke-width:2px
    classDef external fill:#d4edd,stroke:#155724,stroke-width:2px
    
```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---