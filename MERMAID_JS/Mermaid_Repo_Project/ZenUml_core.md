---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is an ongoing document collecting notes on the topics for personal educational purposes and references. 
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExeHJ4YXdtYjJpMDl0MzEwYmU4ZzBobG0waGNiN3MzNzR0d2R2NnMwNSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/26gssNOlBJKjEM3yo/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----

# ZenUml - core
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
title: "MERMAID-JS - ZenUml - core"
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
    DSL["DSL Input<br>(Markdown)"]:::input
    DSL -->|"parses to"| ParserM

    subgraph Parser_Module["Parser Module"]
    style Parser_Module fill:#c222,stroke:#333,stroke-width:2px
        Grammar["Grammar Definitions"]:::parserChild
        Antlr["Antlr-Generated Parser Files"]:::parserChild
        Enhancements["Parser Enhancements & Submodules"]:::parserChild
        Grammar -->|"contributes to"| Intermediate
        Antlr -->|"contributes to"| Intermediate
        Enhancements -->|"contributes to"| Intermediate
    end
    ParserM[" "]:::module
    ParserM -->|"generates"| Intermediate

    Intermediate["Intermediate Representation"]:::data
    Intermediate -->|"renders to"| RendererM

    subgraph Renderer_Module["Renderer Module"]
    style Renderer_Module fill:#c222,stroke:#333,stroke-width:2px
        VueComp["Vue.js Components<br>(Diagram Frame, Sequencing, Tutorial, etc.)"]:::rendererChild
    end
    RendererM[" "]:::module
    RendererM --> VueComp

    VueComp -->|"loads assets from"| Assets
    VueComp -->|"applies styles from"| Themes

    Utilities["Utility & Support Layers"]:::utility
    Utilities -->|"supports"| ParserM
    Utilities -->|"supports"| RendererM

    subgraph Utility_and_Support["Utility and Support"]
    style Utility_and_Support fill:#c222,stroke:#333,stroke-width:2px
        Utils["Utility Functions"]:::utilityChild
        Position["Positioning & Layout Calculations"]:::utilityChild
        Plugins["Plugin Enhancements"]:::utilityChild
        Store["State Management<br>(Store)"]:::utilityChild
    end

    Testing["Tests<br>(Cypress & Unit)"]:::ci
    Testing -->|"tests"| ParserM
    Testing -->|"tests"| RendererM

    CICD["CI/CD Pipeline"]:::ci
    CICD -->|"deploys"| RendererM

    Integration["Integration & Embedding<br>(Examples, Docs)"]:::integration
    Integration -->|"embeds widget in"| RendererM

    %% Click Events
    click Grammar "https://github.com/zenuml/core/tree/main/src/g4"
    click Antlr "https://github.com/zenuml/core/tree/main/src/generated-parser"
    click Enhancements "https://github.com/zenuml/core/tree/main/src/parser"
    click VueComp "https://github.com/zenuml/core/tree/main/src/components"
    click Assets "https://github.com/zenuml/core/tree/main/src/assets"
    click Themes "https://github.com/zenuml/core/tree/main/src/themes"
    click Testing "https://github.com/zenuml/core/tree/main/test/unit"
    click CICD "https://github.com/zenuml/core/tree/main/.github/workflows"
    click Integration "https://github.com/zenuml/core/tree/main/Integration"
    click Utils "https://github.com/zenuml/core/tree/main/src/utils"
    click Position "https://github.com/zenuml/core/tree/main/src/positioning"
    click Plugins "https://github.com/zenuml/core/tree/main/src/plugins"
    click Store "https://github.com/zenuml/core/tree/main/src/store"

    %% Styles
    classDef module fill:#BBDE3,stroke:#0D47A1,stroke-width:2px
    classDef parserChild fill:#E325,stroke:#0D47A1,stroke-width:1px
    classDef rendererChild fill:#E5E5,stroke:#1B5E20,stroke-width:1px
    classDef asset fill:#FF52,stroke:#4A148C,stroke-width:1px
    classDef ci fill:#FCB5,stroke:#BF360C,stroke-width:1px
    classDef integration fill:#F2E2,stroke:#FF6F00,stroke-width:1px
    classDef utility fill:#E2E2,stroke:#424242,stroke-width:1px
    classDef utilityChild fill:#F5F5F,stroke:#616161,stroke-width:1px
    classDef input fill:#FFC3,stroke:#F9A825,stroke-width:1px
    classDef data fill:#DCEDC,stroke:#558B2F,stroke-width:1px
    
```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
