---
created: 2025-03-24 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExcWwxc29rZmVjZTN0d3Zkdzd0OWhhajRoOTlxbDd2MWY0cXN4N2N1cyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/l0He4fJxPCbfqv7Xi/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# css-blocks
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
title: "LinkedIn - CSS Blocks"
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
    'flowchart': {'htmlLabels': true, 'curve': 'basis' },
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
flowchart LR
    %% Core & Processing
    subgraph Core_and_Processing["Core & Processing"]
        Core["Core Engine<br>(@css-blocks/core)"]:::core
    end

    %% CLI & Build Tools
    subgraph CLI_and_Build_Tools["CLI & Build Tools"]
        CLI["CLI<br>(@css-blocks/cli)"]:::integration
    end

    %% Template & Build Integrations
    subgraph Template_and_Build_Integrations["Template & Build Integrations"]
        Webpack["Webpack Plugin<br>(@css-blocks/webpack)"]:::integration
        Broccoli["Broccoli Plugin<br>(@css-blocks/broccoli)"]:::integration
        JSX["JSX Integration<br>(@css-blocks/jsx)"]:::integration
        Glimmer["Glimmer Integration<br>(@css-blocks/glimmer)"]:::integration
        
        subgraph Ember_Integrations["Ember Integrations"]
            EmberFramework["Ember Framework Support<br>(@css-blocks/ember)"]:::integration
            EmberApp["Ember App Runtime<br>(@css-blocks/ember-app)"]:::integration
            EmberCLI["Ember CLI Adapter<br>(@css-blocks/ember-cli)"]:::integration
            EmberUtils["Ember Utilities<br>(@css-blocks/ember-utils)"]:::integration
        end
    end

    %% Language Server & Editor Tools
    subgraph Language_Server_and_Editor_Tools["Language Server & Editor Tools"]
        LangServer["Language Server<br>(@css-blocks/language-server)"]:::tools
        VSCode["VS Code Extension<br>(@css-blocks/vscode)"]:::tools
    end

    %% Utilities & Configuration
    subgraph Utilities_and_Configuration["Utilities & Configuration"]
        Config["Configurations<br>(@css-blocks/config)"]:::utility
        CodeStyle["Code Style<br>(@css-blocks/code-style)"]:::utility
        TestUtils["Test Utilities<br>(@css-blocks/test-utils)"]:::utility
        BEMUtil["BEM Conversion Utility<br>(@css-blocks/bem-to-blocks)"]:::utility
    end

    %% Ancillary Tools & Documentation
    subgraph Ancillary_Tools_and_Documentation["Ancillary Tools & Documentation"]
        Website["Website/Documentation<br>(@css-blocks/website)"]:::doc
        ArchDoc["Architecture Document<br>(ARCHITECTURE.md)"]:::doc
    end

    %% Relationships: Integrations and utilities depend on the Core Engine
    CLI -->|"uses"| Core
    Webpack -->|"wraps"| Core
    Broccoli -->|"wraps"| Core
    JSX -->|"integrates with"| Core
    Glimmer -->|"integrates with"| Core

    EmberFramework -->|"integrates with"| Core
    EmberApp -->|"integrates with"| Core
    EmberCLI -->|"integrates with"| Core
    EmberUtils -->|"integrates with"| Core

    LangServer -->|"analyzes"| Core
    VSCode -->|"interfacesWith"| Core

    Config -->|"configures"| Core
    CodeStyle -->|"styles"| Core
    TestUtils -->|"tests"| Core
    BEMUtil -->|"converts"| Core

    Website -->|"documents"| Core
    ArchDoc -->|"details"| Core

    %% Click Events
    click Core "https://github.com/linkedin/css-blocks/tree/master/packages/@css-blocks/core"
    click CLI "https://github.com/linkedin/css-blocks/tree/master/packages/@css-blocks/cli"
    click Webpack "https://github.com/linkedin/css-blocks/tree/master/packages/@css-blocks/webpack"
    click Broccoli "https://github.com/linkedin/css-blocks/tree/master/packages/@css-blocks/broccoli"
    click JSX "https://github.com/linkedin/css-blocks/tree/master/packages/@css-blocks/jsx"
    click Glimmer "https://github.com/linkedin/css-blocks/tree/master/packages/@css-blocks/glimmer"
    click EmberFramework "https://github.com/linkedin/css-blocks/tree/master/packages/@css-blocks/ember"
    click EmberApp "https://github.com/linkedin/css-blocks/tree/master/packages/@css-blocks/ember-app"
    click EmberCLI "https://github.com/linkedin/css-blocks/tree/master/packages/@css-blocks/ember-cli"
    click EmberUtils "https://github.com/linkedin/css-blocks/tree/master/packages/@css-blocks/ember-utils"
    click LangServer "https://github.com/linkedin/css-blocks/tree/master/packages/@css-blocks/language-server"
    click VSCode "https://github.com/linkedin/css-blocks/tree/master/packages/@css-blocks/vscode"
    click Config "https://github.com/linkedin/css-blocks/tree/master/packages/@css-blocks/config"
    click CodeStyle "https://github.com/linkedin/css-blocks/tree/master/packages/@css-blocks/code-style"
    click TestUtils "https://github.com/linkedin/css-blocks/tree/master/packages/@css-blocks/test-utils"
    click BEMUtil "https://github.com/linkedin/css-blocks/tree/master/packages/@css-blocks/bem-to-blocks"
    click Website "https://github.com/linkedin/css-blocks/tree/master/packages/@css-blocks/website"
    click ArchDoc "https://github.com/linkedin/css-blocks/blob/master/ARCHITECTURE.md"

    %% Styles
    classDef core fill:#fcc9,stroke:#333,stroke-width:2px;
    classDef integration fill:#cff2,stroke:#333,stroke-width:2px;
    classDef tools fill:#cfc3,stroke:#333,stroke-width:2px;
    classDef utility fill:#fcf3,stroke:#333,stroke-width:2px;
    classDef doc fill:#ffc3,stroke:#333,stroke-width:2px
    
```


---

<!-- 
```mermaid
%% Current Mermaid version
info
```  -->


```mermaid
---
title: "CongLeSolutionX"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%{
  init: {
    'flowchart': { 'htmlLabels': false },
    'fontFamily': 'Bradley Hand',
    'themeVariables': {
      'primaryColor': '#fc82',
      'primaryTextColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#81c784',
      'secondaryTextColor': '#6C3483',
      'lineColor': '#F8B229',
      'fontSize': '20px'
    }
  }
}%%
flowchart LR
  My_Meme@{ img: "https://raw.githubusercontent.com/CongLeSolutionX/CongLeSolutionX/refs/heads/main/assets/images/My-meme-light-bulb-question-marks.png", label: "Ăn uống gì chưa ngừi đẹp?", pos: "b", w: 200, h: 150, constraint: "off" }

  Closing_quote@{ shape: braces, label: "...searching insights in the process of formulating better questions..." }

  Closing_quote ~~~ My_Meme
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }

```

---
> **Licenses:**
>
> - **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
> - **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).
> 
---
