---
created: 2025-03-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# MiniWall
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
title: "MiniWall"
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
    Server["Apache HTTP Server"]
    
    subgraph "Browser UI / Frontend"
        indexUI["index.html"]
        miniWallHTML["MiniWall_vent_paper.html"]
    end

    subgraph "JavaScript Modules"
        setupJS["setup_MiniWall_vent_paper.js"]
        utilsJS["utils_object.js"]
    end

    subgraph "Static Assets"
        Data["data"]
        Images["miniWall/images_paper"]
    end

    Server -->|"delivers"| indexUI
    Server -->|"delivers"| miniWallHTML

    indexUI -->|"loads"| setupJS
    indexUI -->|"loads"| utilsJS

    miniWallHTML -->|"includes"| setupJS
    miniWallHTML -->|"includes"| utilsJS

    setupJS -->|"retrieves"| Images
    setupJS -->|"retrieves"| Data
    utilsJS -->|"processes"| Data

    class Server server
    class indexUI,miniWallHTML ui
    class setupJS,utilsJS js
    class Data,Images assets

    click indexUI "https://github.com/nasa/miniwall/blob/master/index.html"
    click miniWallHTML "https://github.com/nasa/miniwall/blob/master/miniWall/MiniWall_vent_paper.html"
    click setupJS "https://github.com/nasa/miniwall/blob/master/miniWall/setup_MiniWall_vent_paper.js"
    click utilsJS "https://github.com/nasa/miniwall/blob/master/miniWall/utils_object.js"
    click Data "https://github.com/nasa/miniwall/tree/master/data/"
    click Images "https://github.com/nasa/miniwall/tree/master/miniWall/images_paper"

    classDef server fill:#FFA7,stroke:#8B0000,stroke-width:2px;
    classDef ui fill:#ADE5,stroke:#00008B,stroke-width:2px;
    classDef js fill:#9EE9,stroke:#006400,stroke-width:2px;
    classDef assets fill:#D3DD,stroke:#696969,stroke-width:2px;
    
```


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---