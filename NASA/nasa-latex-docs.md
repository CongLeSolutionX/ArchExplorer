---
created: 2025-03-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExdmZ6dzhwd3M3cWpkcTB3ZmVlZDVkbWE0MzNjOWxsYnUzYWYwNm9rcSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/S8rWeMk5v022c6Z9nS/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# nasa-latex-docs
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
title: "NASA Latex Docs"
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
    'graph': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#2ff9',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph TD
    subgraph Build_Automation_and_Compilation["Build Automation & Compilation"]
        BP["Python Build Script"]:::automation
        LM["Latexmk Configuration"]:::automation
    end

    subgraph Templates_and_Document_Examples["Templates & Document Examples"]
        T["Templates Directory"]:::template
        TP["Template Parameters"]:::template
    end

    subgraph Document_Content_and_Assets["Document Content & Assets"]
        DC["Main LaTeX Document & Resources"]:::content
        CIT["Citation Files"]:::content
    end

    subgraph Export_and_Auxiliary_Assets["Export & Auxiliary Assets"]
        EXP["Exported Documents"]:::export
        IMG["Images<br>(Logos and Coversheet)"]:::export
    end

    subgraph Additional_Packages_and_Custom_LaTeX_Commands["Additional Packages & Custom LaTeX Commands"]
        PKG["Custom Packages & Style Files"]:::packages
        CLS["LaTeX Class File"]:::packages
    end

    %% Flow connections
    BP -->|"triggers"| DC
    TP -->|"configures"| T
    T -->|"provides template for"| DC
    DC -->|"utilizes"| CLS
    DC -->|"includes"| PKG
    DC -->|"integrates"| CIT
    DC -->|"incorporates"| IMG
    BP -->|"invokes"| LM
    DC -->|"exports to"| EXP

    %% Click events for components
    click BP "https://github.com/nasa/nasa-latex-docs/blob/master/support/buildPDF.py"
    click LM "https://github.com/nasa/nasa-latex-docs/tree/master/support/latexmk/latexmkrc"
    click T "https://github.com/nasa/nasa-latex-docs/tree/master/support/templates"
    click TP "https://github.com/nasa/nasa-latex-docs/blob/master/support/templates/doc-params.tex"
    click DC "https://github.com/nasa/nasa-latex-docs/tree/master/support/document"
    click CIT "https://github.com/nasa/nasa-latex-docs/tree/master/support/citations/aiaa"
    click EXP "https://github.com/nasa/nasa-latex-docs/tree/master/support/export"
    click IMG "https://github.com/nasa/nasa-latex-docs/tree/master/support/images"
    click PKG "https://github.com/nasa/nasa-latex-docs/tree/master/support/packages"
    click CLS "https://github.com/nasa/nasa-latex-docs/blob/master/support/nasa-latex-docs.cls"

    %% Styles
    classDef automation fill:#F9C7,stroke:#000,stroke-width:2px
    classDef template fill:#90BE,stroke:#000,stroke-width:2px
    classDef content fill:#F984,stroke:#000,stroke-width:2px
    classDef export fill:#5775,stroke:#000,stroke-width:2px
    classDef packages fill:#277D,stroke:#000,stroke-width:2px

```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
