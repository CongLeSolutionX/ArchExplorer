---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/apple/pkl
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExY2Vvcng2ZDc2ZHNtY2k2aTU1bDJjNXVjOTl5aHBndThvbW9zbmpsaSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/KGhpQ5NMoWKQurlHwI/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# pkl
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for 👨‍🎓 <ins>educational purposes</ins> 👨‍🎓 (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), 📖 <ins> personal study </ins> 📖, and 🔖 <ins> technical reference </ins> 🔖.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


---




```mermaid
---
title: "Apple - pkl"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright © 2025 Cong Le. All Rights Reserved."
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
    "graph": {"htmlLabels": true, 'curve': 'natural'},
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
    %% External Nodes
    U["User Input"]:::external
    Gs["Gradle Build<br>(buildSrc & Config)"]:::external

    %% Core Language Processing Layer
    subgraph Core_Language_Processing["Core Language Processing"]
        A["Core Engine<br>(Parser,AST,Evaluator,ModuleResolver)"]:::core
        B["Standard Library<br>(JSON,YAML,XML,etc.)"]:::core
    end

    %% Interfaces Layer
    subgraph Interfaces["Interfaces"]
        C["CLI<br>(Interactive/Scriptable)"]:::interface
        D["Executor<br>(Remote/Embedded)"]:::interface
        E["Server<br>(Execution Service)"]:::interface
        F["Build Integration<br>(Gradle Plugin)"]:::interface
    end

    %% Tooling Layer
    subgraph Tooling["Tooling"]
        G["Java Code Generation"]:::tooling
        H["Kotlin Code Generation"]:::tooling
        I["Commons CLI Support"]:::tooling
        J["Documentation Generator"]:::tooling
        K["Additional Tools & Plugins"]:::tooling
    end

    %% Data Flows & Relationships
    U -->|"triggers"| C
    U -->|"triggers"| F

    Gs -->|"configures"| A
    Gs -->|"configures"| C
    Gs -->|"configures"| F
    Gs -->|"configures"| G
    Gs -->|"configures"| H
    Gs -->|"configures"| I
    Gs -->|"configures"| J

    C -->|"invokes"| A
    F -->|"invokes"| A

    A -->|"imports"| B

    A -->|"executes"| D
    A -->|"executes"| E

    A -->|"generates"| G
    A -->|"generates"| H
    A -->|"supports"| I
    A -->|"provides info"| J

    A -->|"integrates with"| K

    %% Click Events
    click A "https://github.com/apple/pkl/tree/main/pkl-core"
    click B "https://github.com/apple/pkl/tree/main/stdlib"
    click C "https://github.com/apple/pkl/tree/main/pkl-cli"
    click D "https://github.com/apple/pkl/tree/main/pkl-executor"
    click E "https://github.com/apple/pkl/tree/main/pkl-server"
    click F "https://github.com/apple/pkl/tree/main/pkl-gradle"
    click G "https://github.com/apple/pkl/tree/main/pkl-codegen-java"
    click H "https://github.com/apple/pkl/tree/main/pkl-codegen-kotlin"
    click I "https://github.com/apple/pkl/tree/main/pkl-commons-cli"
    click J "https://github.com/apple/pkl/tree/main/pkl-doc"
    click K "https://github.com/apple/pkl/tree/main/pkl-tools"

    %% Styles
    classDef core fill:#f8d7d,stroke:#721c24,stroke-width:2px
    classDef interface fill:#d4edd,stroke:#155724,stroke-width:2px
    classDef tooling fill:#d1ecf,stroke:#0c5460,stroke-width:2px
    classDef external fill:#fff3c,stroke:#856404,stroke-width:2px
    
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
    
  My_Meme ~~~ Closing_quote
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }

```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
