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
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExbm8zNzhhcDNmaWN4cHRhemVvNTd2OHY5ZmRtenlhM244OWdqcnlmeCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/PpVjpSOjZDn9lfPE2L/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Worldview
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
title: "Worldview"
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
    subgraph Client_Layer["Client Layer"]
        UI["UI:<br>Components & Containers"]:::ui
        SM["State Management<br>(Redux)"]:::logic
    end

    subgraph Mapping_Layer["Mapping Layer"]
        ME["Mapping Engine<br>(OpenLayers & MapUI)"]:::mapping
    end

    subgraph Infrastructure["Infrastructure"]
        BC["Build & Configuration"]:::build
        TC["Testing & QA"]:::test
        DC["Deployment & CI/CD"]:::deploy
    end

    External["External Data Services:<br>GIBS"]:::external

    UI -->|"state updates"| SM
    SM -->|"updates mapping"| ME
    UI -->|"user interactions"| ME

    BC -->|"prepares config"| UI
    DC -->|"triggers build"| BC
    TC -.->|"validates"| UI
    TC -.->|"validates"| SM
    TC -.->|"validates"| ME

    ME -->|"requests imagery"| External
    External -->|"sends images"| ME

    %% Click Events
    click UI "https://github.com/nasa-gibs/worldview/tree/main/web/"
    click UI "https://github.com/nasa-gibs/worldview/tree/main/web/js/components"
    click UI "https://github.com/nasa-gibs/worldview/tree/main/web/js/containers"
    click SM "https://github.com/nasa-gibs/worldview/tree/main/web/js/modules"
    click ME "https://github.com/nasa-gibs/worldview/tree/main/web/js/map"
    click ME "https://github.com/nasa-gibs/worldview/tree/main/web/js/ol"
    click ME "https://github.com/nasa-gibs/worldview/tree/main/web/js/mapUI"
    click BC "https://github.com/nasa-gibs/worldview/tree/main/tasks/"
    click BC "https://github.com/nasa-gibs/worldview/tree/main/config/"
    click BC "https://github.com/nasa-gibs/worldview/tree/main/schemas/"
    click TC "https://github.com/nasa-gibs/worldview/tree/main/e2e/"
    click TC "https://github.com/nasa-gibs/worldview/blob/main/jest.config.js"
    click TC "https://github.com/nasa-gibs/worldview/blob/main/playwright.config.js"
    click DC "https://github.com/nasa-gibs/worldview/tree/main/.github/"
    click DC "https://github.com/nasa-gibs/worldview/tree/main/Dockerfile"

    %% Styles
    classDef ui fill:#ADF4,stroke:#3498DB,stroke-width:2px
    classDef logic fill:#AED3,stroke:#27AE60,stroke-width:2px
    classDef mapping fill:#E7F9,stroke:#F1C40F,stroke-width:2px
    classDef build fill:#D4DE,stroke:#8E44AD,stroke-width:2px
    classDef test fill:#FCA21,stroke:#E74C3C,stroke-width:2px
    classDef deploy fill:#FCF2,stroke:#F39C12,stroke-width:2px
    classDef external fill:#D5E3,stroke:#2ECC71,stroke-width:2px
    
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

