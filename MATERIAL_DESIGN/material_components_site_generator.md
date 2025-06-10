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
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExMTE0YTR4aTYyeGR2M3ZiMWg0eng0Z2dwcDEyM2lsM3h2NDUxZmV0ZyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/OPkk90UvmWRE5MOpmW/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----



# Material Components Site Generator
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
    'flowchart': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'lineColor': '#F8B229'
    }
  }
}%%
flowchart TD
    subgraph "Input Layer"
        I["Material Component Repositories\n(Markdown Files with Front Matter)"]:::input
    end

    subgraph "Processing Layer"
        BS["Build Script (scripts/build)"]:::process
        BH["Build Helpers (scripts/lib)"]:::process
        BS -->|"calls"| BH
    end

    subgraph "Templating Layer"
        TS["Jekyll Templating (jekyll-site-src)"]:::template
    end

    subgraph "iOS Documentation Flow"
        IOS["iOS API Docs (ios-api-docs-src)"]:::special
    end

    subgraph "Output Layer"
        O["Static Site Output (dist/)"]:::output
    end

    subgraph "Quality Assurance"
        T["Testing Suite (test)"]:::test
    end

    I -->|"processMarkdown"| BS
    BS -->|"transformContent"| TS
    BS -->|"applyMustache"| IOS
    TS -->|"generateHTML"| O
    IOS -->|"generateHTML"| O
    BS -->|"verify"| T

    click BS "https://github.com/material-components/material-components-site-generator/tree/master/scripts/build"
    click BH "https://github.com/material-components/material-components-site-generator/tree/master/scripts/lib"
    click TS "https://github.com/material-components/material-components-site-generator/tree/master/jekyll-site-src"
    click IOS "https://github.com/material-components/material-components-site-generator/tree/master/ios-api-docs-src"
    click T "https://github.com/material-components/material-components-site-generator/tree/master/test"

    classDef input fill:#FAD7A0,stroke:#D35400,stroke-width:2px;
    classDef process fill:#AED6F1,stroke:#2471A3,stroke-width:2px;
    classDef template fill:#A9DFBF,stroke:#27AE60,stroke-width:2px;
    classDef special fill:#F9E79F,stroke:#B7950B,stroke-width:2px;
    classDef output fill:#E8DAEF,stroke:#8E44AD,stroke-width:2px;
    classDef test fill:#D2B4DE,stroke:#7D3C98,stroke-width:2px;
    
```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
