---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is an ongoing document collecting notes for personal educational purposes and references. 
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExMGoyOGFxamNyZm9uanNrbG94c2M2ZHA4am1hcDVlZWZyeDkzajdveiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/htSV2Ktelwcp34rvlK/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Mermaid 
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
title: "MERMAID-JS - mermaid"
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
    "graph": { "htmlLabels": true, 'curve': 'linear' },
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
graph TB
    %% Styles and classes
    classDef core fill:#27f4,stroke:#2374ab,color:white
    classDef parser fill:#4af2,stroke:#48a9a6,color:white
    classDef renderer fill:#4ad7,stroke:#4ad7d1,color:white
    classDef integration fill:#cc52,stroke:#c4fff9,color:black
    classDef security fill:#f6b2,stroke:#ff6b6b,color:white
    classDef theme fill:#4ec2,stroke:#4ecdc4,color:white
    classDef diagram fill:#4b25,stroke:#45b7d1,color:white

    %% Main Components
    Core["🔧 Core Engine"]:::core
    click Core "https://github.com/mermaid-js/mermaid/blob/develop/packages/mermaid/src/mermaidAPI.ts"
    
    Config["⚙️ Configuration"]:::core
    click Config "https://github.com/mermaid-js/mermaid/blob/develop/packages/mermaid/src/config.ts"
    
    DiagramAPI["📊 Diagram API"]:::core
    click DiagramAPI "https://github.com/mermaid-js/mermaid/tree/develop/packages/mermaid/src/diagram-api/"

    %% Parser Layer
    subgraph Parser["Parser Layer"]
    style Parser fill:#c222,stroke:#333,stroke-width:2px
        Jison["📝 Jison Parser"]:::parser
        click Jison "https://github.com/mermaid-js/mermaid/tree/develop/packages/parser/"
        Langium["📝 Langium Parser"]:::parser
        click Langium "https://github.com/mermaid-js/mermaid/tree/develop/packages/parser/src/language/"
    end

    %% Rendering Layer
    subgraph Rendering["Rendering Layer"]
    style Rendering fill:#c222,stroke:#333,stroke-width:2px
        RenderUtil["🎨 Rendering Utilities"]:::renderer
        click RenderUtil "https://github.com/mermaid-js/mermaid/tree/develop/packages/mermaid/src/rendering-util/"
        RenderElements["🎨 Rendering Elements"]:::renderer
        click RenderElements "https://github.com/mermaid-js/mermaid/tree/develop/packages/mermaid/src/rendering-util/rendering-elements/"
        LayoutAlgo["📐 Layout Algorithms"]:::renderer
        click LayoutAlgo "https://github.com/mermaid-js/mermaid/tree/develop/packages/mermaid/src/rendering-util/layout-algorithms/"
    end

    %% Integration Layer
    subgraph Integration["Integration Layer"]
    style Integration fill:#c222,stroke:#333,stroke-width:2px
        Community["🌐 Community Integrations"]:::integration
        click Community "https://github.com/mermaid-js/mermaid/blob/develop/docs/ecosystem/integrations-community.md"
        CreateInt["🔧 Integration Creation"]:::integration
        click CreateInt "https://github.com/mermaid-js/mermaid/blob/develop/docs/ecosystem/integrations-create.md"
        Testing["🧪 Integration Tests"]:::integration
        click Testing "https://github.com/mermaid-js/mermaid/tree/develop/cypress/integration/"
    end

    %% Security Layer
    Security["🔒 Security & Sanitization"]:::security
    click Security "https://github.com/mermaid-js/mermaid/blob/develop/packages/mermaid/src/utils/sanitizeDirective.ts"

    %% Theme System
    subgraph Themes["Theme System"]
    style Themes fill:#c222,stroke:#333,stroke-width:2px
        ThemeBase["🎨 Base Theme"]:::theme
        click ThemeBase "https://github.com/mermaid-js/mermaid/blob/develop/packages/mermaid/src/themes/theme-base.js"
        ThemeDefault["🎨 Default Theme"]:::theme
        click ThemeDefault "https://github.com/mermaid-js/mermaid/blob/develop/packages/mermaid/src/themes/theme-default.js"
    end

    %% Diagram Types
    subgraph Diagrams["Diagram Types"]
    style Diagrams fill:#c222,stroke:#333,stroke-width:2px
        Flowchart["📊 Flowchart"]:::diagram
        click Flowchart "https://github.com/mermaid-js/mermaid/tree/develop/packages/mermaid/src/diagrams/flowchart/"
        Sequence["⏱️ Sequence"]:::diagram
        click Sequence "https://github.com/mermaid-js/mermaid/tree/develop/packages/mermaid/src/diagrams/sequence/"
        Class["📋 Class"]:::diagram
        click Class "https://github.com/mermaid-js/mermaid/tree/develop/packages/mermaid/src/diagrams/class/"
        State["🔄 State"]:::diagram
        click State "https://github.com/mermaid-js/mermaid/tree/develop/packages/mermaid/src/diagrams/state/"
    end

    %% Relationships
    Core --> Parser
    Core --> Rendering
    Core --> Integration
    Core --> Security
    Core --> Themes
    Core --> Diagrams
    Config --> Core
    DiagramAPI --> Core
    Parser --> Rendering
    Rendering --> Integration

    %% Legend
    subgraph Legend["Legend"]
    style Legend fill:#c222,stroke:#333,stroke-width:2px
        L1["🔧 Core Components"]:::core
        L2["📝 Parser Components"]:::parser
        L3["🎨 Rendering Components"]:::renderer
        L4["🌐 Integration Components"]:::integration
        L5["🔒 Security Components"]:::security
        L6["🎨 Theme Components"]:::theme
        L7["📊 Diagram Components"]:::diagram
    end
    
```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
