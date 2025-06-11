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
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExOXd2dGZnODB5ZHFrZzVzdTM5ZzhwdHFqb3pib2hmdjdhb2kzYjhsZyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/vTE78hxY9NmCI/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# cFS
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
title: "cFS"
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
    %% Layer 1: Hardware Layer
    subgraph Layer_1["Layer 1: Hardware Layer"]
        H["Hardware/OS"]:::hardware
    end

    %% Layer 2: Abstraction Layer
    subgraph Layer_2["Layer 2: Abstraction Layer"]
        OA["OSAL"]:::core
        PSPNode["PSP"]:::core
    end

    %% Layer 3: Core Flight Framework
    subgraph Layer_3["Layer 3: Core Flight Framework"]
        cfe["cFE<br>(Core Flight Executive)"]:::core
    end

    %% Layer 4: Flight Applications
    subgraph Layer_4_Flight_Applications["Layer 4: Flight Applications"]
        ciLab["ci_lab"]:::app
        sampleApp["sample_app"]:::app
        schLab["sch_lab"]:::app
        toLab["to_lab"]:::app
    end

    %% Layer 4: Shared Libraries
    subgraph Layer_4_Shared_Libraries["Layer 4: Shared Libraries"]
        sampleLib["sample_lib"]:::app
    end

    %% Layer 5: Tools & Ground Systems
    subgraph Layer_5["Layer 5: Tools & Ground Systems"]
        ground["cFS-GroundSystem"]:::tools
        elf2cfetbl["elf2cfetbl"]:::tools
        tblCRCTool["tblCRCTool"]:::tools
        cmake["CMakeLists.txt"]:::tools
    end

    %% Layer 6: CI/CD & Automated Testing
    subgraph Layer_6["Layer 6: CI/CD & Automated Testing"]
        workflows["Workflows"]:::cicd
        scripts["Scripts"]:::cicd
    end

    %% Connections between layers
    H -->|"provides"| OA
    H -->|"provides"| PSPNode
    OA -->|"interfaces"| cfe
    PSPNode -->|"interfaces"| cfe

    cfe -->|"runs"| ciLab
    cfe -->|"runs"| sampleApp
    cfe -->|"runs"| schLab
    cfe -->|"runs"| toLab

    sampleApp -->|"uses"| sampleLib

    cfe <==>|"Cmd_Tlm_Interface"| ground

    workflows -->|"build test"| cfe
    scripts -->|"build test"| cfe

    %% Styles
    classDef hardware fill:#9e9e,stroke:#424242,stroke-width:2px
    classDef core fill:#bbdefb,stroke:#0d47a1,stroke-width:2px
    classDef app fill:#c8e6c9,stroke:#1b5e20,stroke-width:2px
    classDef tools fill:#fff9c4,stroke:#f9a825,stroke-width:2px
    classDef cicd fill:#d1c4e9,stroke:#4a148c,stroke-width:2px

    %% Click Events
    click cfe "https://github.com/nasa/cfs/tree/main/cfe"
    click OA "https://github.com/nasa/cfs/tree/main/osal"
    click PSPNode "https://github.com/nasa/cfs/tree/main/psp"
    click ciLab "https://github.com/nasa/cfs/tree/main/apps/ci_lab"
    click sampleApp "https://github.com/nasa/cfs/tree/main/apps/sample_app"
    click schLab "https://github.com/nasa/cfs/tree/main/apps/sch_lab"
    click toLab "https://github.com/nasa/cfs/tree/main/apps/to_lab"
    click sampleLib "https://github.com/nasa/cfs/tree/main/libs/sample_lib"
    click ground "https://github.com/nasa/cfs/tree/main/tools/cFS-GroundSystem"
    click elf2cfetbl "https://github.com/nasa/cfs/tree/main/tools/elf2cfetbl"
    click tblCRCTool "https://github.com/nasa/cfs/tree/main/tools/tblCRCTool"
    click cmake "https://github.com/nasa/cfs/blob/main/tools/CMakeLists.txt"
    click workflows "https://github.com/nasa/cfs/tree/main/.github/workflows"
    click scripts "https://github.com/nasa/cfs/tree/main/.github/scripts"

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

