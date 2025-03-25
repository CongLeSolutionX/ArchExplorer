---
created: 2025-03-24 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# School of SRE
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
title: "LinkedIn - School of SRE"
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
    'graph': { 'htmlLabels': false, 'curve': 'linear' },
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
graph TD
    %% Content Layer
    subgraph Content_Layer["Content Layer"]
        CR["Content Repository<br>(Courses)"]:::content
        L101["Level 101 Content"]:::content
        L102["Level 102 Content"]:::content
        CD["Community & Documentation"]:::community
    end

    %% Build & Process Layer
    subgraph Build_and_Process_Layer["Build & Process Layer"]
        cfg["MkDocs Config<br>(mkdocs.yml)"]:::build
        mkd["Static Site Generator<br>(MkDocs)"]:::build
        ov["Custom Overrides"]:::build
        st["Custom Stylesheets"]:::build
        gs["Generated Static Site"]:::build
    end

    %% Deployment Layer
    subgraph Deployment_Layer["Deployment Layer"]
        cicd["CI/CD Pipeline"]:::deployment
        host["Hosted Site"]:::deployment
    end

    %% Relationships and Data Flow
    CR -->|"provides Markdown"| mkd
    L101 -->|"content"| mkd
    L102 -->|"content"| mkd
    CR -->|"triggers update"| cicd
    cfg -->|"configuration"| mkd
    ov -->|"custom HTML"| mkd
    st -->|"custom styling"| mkd
    cicd -->|"automated build"| mkd
    mkd -->|"builds site"| gs
    gs -->|"deploys to"| host

    %% Community not directly part of flow but related to content
    CD ---|"governance"| CR

    %% Click Events for Component Mapping
    click CR "https://github.com/linkedin/school-of-sre/tree/main/courses/"
    click L101 "https://github.com/linkedin/school-of-sre/tree/main/courses/level101/"
    click L102 "https://github.com/linkedin/school-of-sre/tree/main/courses/level102/"
    click cfg "https://github.com/linkedin/school-of-sre/blob/main/mkdocs.yml"
    click ov "https://github.com/linkedin/school-of-sre/tree/main/overrides/"
    click ov "https://github.com/linkedin/school-of-sre/tree/main/overrides/partials/"
    click st "https://github.com/linkedin/school-of-sre/blob/main/courses/stylesheets/custom.css"
    click cicd "https://github.com/linkedin/school-of-sre/tree/main/.github/workflows/"
    click cicd "https://github.com/linkedin/school-of-sre/blob/main/.github/workflows/gh-deploy.yml"
    click CD "https://github.com/linkedin/school-of-sre/tree/main/LICENSE"
    click CD "https://github.com/linkedin/school-of-sre/tree/main/NOTICE"
    click CD "https://github.com/linkedin/school-of-sre/blob/main/CONTRIBUTING.md"
    click CD "https://github.com/linkedin/school-of-sre/blob/main/courses/CODE_OF_CONDUCT.md"

    %% Styles
    classDef content fill:#FFC1,stroke:#2471A3,stroke-width:2px;
    classDef build fill:#BFB32,stroke:#28B463,stroke-width:2px;
    classDef deployment fill:#F79F,stroke:#D4AC0D,stroke-width:2px;
    classDef community fill:#FBB5,stroke:#C0392B,stroke-width:2px
    
```


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---