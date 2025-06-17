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
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExNTJ1c29tdmJqYmszNzVzank1cmJlczV6czd1aHpscnlnbDgwazd0eiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/l3q2xK6E4Ost3fWFi/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# T-mats
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
title: "T-mats"
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
flowchart TD
    %% Interface and Setup Layer
    subgraph Interface_and_Setup["Interface and Setup"]
        A1["Simulation Environment (Simulink)"]:::sim
        A2["Documentation and Support"]:::doc
    end

    %% Simulation Core Layer
    subgraph Simulation_Core["Simulation Core"]
        B1["T‑MATS Core Library Blocks"]:::core
        subgraph "Core Components"
            B1a["Turbomachinery Blocks"]:::core
            B1b["Control Modules"]:::core
            B1c["Solver Modules"]:::core
            B1d["Thermodynamic Calculators"]:::core
        end
        B2["MEX Modules"]:::mex
        B3["MATLAB Scripts"]:::mex
    end

    %% Auxiliary Tools Layer
    subgraph Auxiliary_Tools["Auxiliary Tools"]
        C1["Auxiliary Tools & User Interfaces"]:::aux
        C2["Test Beds / Example Models"]:::test
    end

    %% Connections
    A1 -->|"uses"| B1
    B1 -->|"contains"| B1a
    B1 -->|"contains"| B1b
    B1 -->|"contains"| B1c
    B1 -->|"contains"| B1d
    B1 -->|"optimized by"| B2
    B1 -->|"enhanced by"| B3
    B1 -->|"interfaces with"| C1
    A1 -->|"demonstrations in"| C2
    A2 -->|"details for"| A1
    A2 -->|"guidance for"| B1
    A2 -->|"assists"| C1

    %% Styles
    classDef sim fill:#F9E6,stroke:#333,stroke-width:2px
    classDef doc fill:#E6F7,stroke:#333,stroke-width:2px
    classDef core fill:#CFA5,stroke:#333,stroke-width:2px
    classDef mex fill:#FFC3,stroke:#333,stroke-width:2px
    classDef aux fill:#CEF3,stroke:#333,stroke-width:2px
    classDef test fill:#FDE3,stroke:#333,stroke-width:2px

    %% Click Events
    click A1 "https://github.com/nasa/t-mats/tree/master/Trunk/TMATS_Examples"
    click B1 "https://github.com/nasa/t-mats/tree/master/Trunk/TMATS_Library"
    click B2 "https://github.com/nasa/t-mats/tree/master/Trunk/TMATS_Library/MEX"
    click B3 "https://github.com/nasa/t-mats/tree/master/Trunk/TMATS_Library/MATLAB_Scripts"
    click C1 "https://github.com/nasa/t-mats/tree/master/Trunk/TMATS_Tools"
    click C2 "https://github.com/nasa/t-mats/tree/master/Resources/Testing/TestBeds"
    click A2 "https://github.com/nasa/t-mats/blob/master/README.md"
    click A2 "https://github.com/nasa/t-mats/blob/master/Trunk/TMATS_Users_Guide_TM-2014-216638.pdf"

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
