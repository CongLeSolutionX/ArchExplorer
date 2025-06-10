---
created: 2025-04-01 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExYXVxMnJiOXAyemkzMjNxd21tanFoOWszNG43dzNlMWthMnN3OWdzbCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3ohhwC8NtCMYXlSHBu/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Material Components
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
title: "CHANGE_ME_DADDY"
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
    'graph': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'lineColor': '#F8B229'
    }
  }
}%%
graph TD
    A("Material Components Shared Documentation"):::central

    subgraph "Internal Components"
        B("General Documentation & Policies"):::doc
        subgraph "Docsite Component"
            E("Config (.mdc-docsite.yml)"):::config
            F("Site Generator (docsite)"):::site
            E --> F
        end
        subgraph "Documentation Policies & Guidelines"
            C1("ISSUE_TEMPLATE.md"):::policy
            C2("PULL_REQUEST_TEMPLATE.md"):::policy
            C3("CONTRIBUTING_TEMPLATE.md"):::policy
        end
        subgraph "Auxiliary Files"
            D1("LICENSE"):::aux
            D2("AUTHORS"):::aux
        end
        B -->|"StaticSiteGeneration"| E
    end

    subgraph "External Repositories"
        G("Material Components Android"):::external
        H("Material Components iOS"):::external
        I("Material Components Web"):::external
        J("Material Components Flutter"):::external
    end

    A --> B
    A --> C1
    A --> D1
    A --> G
    A --> H
    A --> I
    A --> J

    click A "https://github.com/material-components/material-components/blob/develop/README.md"
    click E "https://github.com/material-components/material-components/blob/develop/.mdc-docsite.yml"
    click F "https://github.com/material-components/material-components/blob/develop/docsite/docsite-index.md"
    click C1 "https://github.com/material-components/material-components/blob/develop/ISSUE_TEMPLATE.md"
    click C2 "https://github.com/material-components/material-components/blob/develop/PULL_REQUEST_TEMPLATE.md"
    click C3 "https://github.com/material-components/material-components/blob/develop/CONTRIBUTING_TEMPLATE.md"
    click D1 "https://github.com/material-components/material-components/tree/develop/LICENSE"
    click D2 "https://github.com/material-components/material-components/tree/develop/AUTHORS"

    classDef central fill:#FFDDCC,stroke:#D2691E,stroke-width:2px;
    classDef doc fill:#DDEEFF,stroke:#000000,stroke-width:1px;
    classDef policy fill:#D1E8E2,stroke:#31708F,stroke-width:1px;
    classDef aux fill:#F2E6D9,stroke:#8B4513,stroke-width:1px;
    classDef external fill:#CFFFCF,stroke:#228B22,stroke-width:1px;
    classDef config fill:#E6CCFF,stroke:#800080,stroke-width:1px;
    classDef site fill:#B3E5FC,stroke:#0288D1,stroke-width:1px;
    
```


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
