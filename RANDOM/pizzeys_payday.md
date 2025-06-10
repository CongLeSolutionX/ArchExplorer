---
created: 2025-03-28 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExbXFlaG9mc3gzc2tyZW5nODc5NjAwdTVhZXZlN2JuMXlpMzY4cnVhZiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/ADgfsbHcS62Jy/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Payday by Pizzeys
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
title: "Payday by Pizzeys"
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
    subgraph "Core Domain"
        INVOICE["Payday::Invoice"]:::core
        LINEITEM["Payday::LineItem"]:::core
    end

    subgraph "Rendering & Configuration"
        PDF["Payday::PDFRenderer"]:::service
        CONFIG["Payday::Config"]:::service
    end

    subgraph "Integration Modules"
        INV_MOD["Invoiceable Module"]:::integration
        LINE_MOD["LineItemable Module"]:::integration
    end

    subgraph "External Dependencies"
        PR["Prawn PDF Library"]:::external
        I18N["i18n Library"]:::external
    end

    %% Relationships
    INVOICE -->|"contains"| LINEITEM
    INVOICE -->|"render"| PDF
    CONFIG -->|"configures"| INVOICE
    CONFIG -->|"configures"| PDF
    INV_MOD -->|"extends"| INVOICE
    INV_MOD -->|"extends"| LINEITEM
    LINE_MOD -->|"extends"| INVOICE
    LINE_MOD -->|"extends"| LINEITEM
    PDF -->|"uses"| PR
    CONFIG -->|"supports"| I18N

    %% Click Events
    click INVOICE "https://github.com/pizzeys/payday/blob/master/lib/payday/invoice.rb"
    click LINEITEM "https://github.com/pizzeys/payday/blob/master/lib/payday/line_item.rb"
    click PDF "https://github.com/pizzeys/payday/blob/master/lib/payday/pdf_renderer.rb"
    click CONFIG "https://github.com/pizzeys/payday/blob/master/lib/payday/config.rb"
    click INV_MOD "https://github.com/pizzeys/payday/blob/master/lib/payday/invoiceable.rb"
    click LINE_MOD "https://github.com/pizzeys/payday/blob/master/lib/payday/line_itemable.rb"

    %% Styles
    classDef core fill:#AED6F1,stroke:#2980B9,stroke-width:2px;
    classDef service fill:#A9DFBF,stroke:#27AE60,stroke-width:2px;
    classDef integration fill:#F9E79F,stroke:#F1C40F,stroke-width:2px;
    classDef external fill:#F5B7B1,stroke:#E74C3C,stroke-width:2px;

```





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
