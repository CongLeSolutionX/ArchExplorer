---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExd3NiOXNiY2lkMncweTZwOWVlZ2lwdXZiaHB1djNnMm5jYzZ4bTJxcyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/cvbGraL8NJJZu/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Desgin System
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
title: "CA GOV - Design System"
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
    %% Component Library and its individual components
    CL_LIB["Component Library"]:::dev
    subgraph Components["Components"]
        direction TB
            ACC["Accordion<br>(src,test,dist)"]:::dev
            BTS["Back-to-Top<br>(src,test,dist)"]:::dev
    end

    %% Documentation Site
    DS["Documentation Site (11ty,markdown)"]:::dev

    %% CI/CD Pipeline with its sub-components
    subgraph CI_CD_Pipeline["CI/CD Pipeline"]
        direction TB
            GHW["GitHub Workflows"]:::automation
            PRE["Pre-commit Hooks"]:::automation
    end

    %% Testing Framework
    subgraph Testing_Framework["Testing Framework"]
        direction TB
            UT["Unit Tests"]:::test
            E2E["End-to-End Tests<br>(Playwright,axe)"]:::test
    end

    %% External Publishing
    EP["External Publishing<br>(npm,CDN,AWS)"]:::external

    %% Relationships & Data Flow
    CL_LIB -->|"autogen"| DS
    CL_LIB -->|"commit triggers"| GHW
    CL_LIB -->|"commit triggers"| PRE
    GHW -->|"run tests"| UT
    GHW -->|"run tests"| E2E
    PRE -->|"verify"| UT
    GHW -->|"deploy artifacts"| EP

    %% Click Events
    click CL_LIB "https://github.com/cagov/design-system/tree/main//components"
    click ACC "https://github.com/cagov/design-system/tree/main//components/accordion"
    click BTS "https://github.com/cagov/design-system/tree/main//components/back-to-top"
    click DS "https://github.com/cagov/design-system/tree/main//docs"
    click GHW "https://github.com/cagov/design-system/tree/main//github/workflows"
    click PRE "https://github.com/cagov/design-system/tree/main//.husky/pre-commit"
    click E2E "https://github.com/cagov/design-system/blob/main//playwright.config.mjs"

    %% Styles
    classDef dev fill:#a6c3,stroke:#1f78b4,stroke-width:2px
    classDef automation fill:#bf83,stroke:#33a02c,stroke-width:2px
    classDef test fill:#fb44,stroke:#e31a1c,stroke-width:2px
    classDef external fill:#f522,stroke:#ff7f00,stroke-width:2px
    
```


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
