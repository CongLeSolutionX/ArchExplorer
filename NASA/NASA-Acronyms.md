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
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExaWtqb29keDk2eWMwa2QwaDg4dGwzdGJ6MjlkMGswY21qN3c0dHA0cyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3oKIP74xPaiSgFyT0A/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# NASA-Acronyms
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
title: "NASA-Acronyms"
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
    %% Data Layer
    subgraph Data_Layer["Data Layer"]
        DN1["acronyms.json"]:::data
        DN2["lists Folder"]:::data
    end

    %% Application Layer
    subgraph Application_Layer["Application Layer"]
        AP["Search Engine / Processing Module<br>(NASA_Acronyms.py)"]:::app
    end

    %% Presentation Layer
    subgraph Presentation_Layer["Presentation Layer"]
        WF["Web Frontend<br>(nasaacronyms.com & script.js)"]:::front
        BE["Browser Extensions<br>(Chrome/Firefox & manifest.json)"]:::front
    end

    %% Distribution
    subgraph Distribution["Distribution"]
        DIST["Deployment Artifact<br>(nasaAcronyms-1.9.zip)"]:::dist
    end

    %% Relationships
    DN1 -->|"feeds"| AP
    DN2 -->|"feeds"| AP
    AP -->|"serves"| WF
    AP -->|"serves"| BE
    WF -- "send query" --> AP
    AP -->|"packaged"| DIST

    %% Click Events
    click DN1 "https://github.com/nasa/nasa-acronyms/blob/master/acronyms.json"
    click DN2 "https://github.com/nasa/nasa-acronyms/tree/master/lists/"
    click AP "https://github.com/nasa/nasa-acronyms/blob/master/NASA-Acronyms.py"
    click WF "https://github.com/nasa/nasa-acronyms/blob/master/script.js"
    click BE "https://github.com/nasa/nasa-acronyms/blob/master/manifest.json"
    click DIST "https://github.com/nasa/nasa-acronyms/blob/master/nasaAcronyms-1.9.zip"

    %% Styles
    classDef data fill:#ADC2,stroke:#000,stroke-width:1px
    classDef app fill:#ECD2,stroke:#000,stroke-width:1px
    classDef front fill:#FFE2,stroke:#000,stroke-width:1px
    classDef dist fill:#FAA4,stroke:#000,stroke-width:1px
    
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
