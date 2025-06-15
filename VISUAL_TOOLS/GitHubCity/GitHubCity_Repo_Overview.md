---
created: 2025-03-25 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExejVqYjVpcWdncHBvOW8wdGZucDc5cjdrYTVnaXFvNnR5Y3owajdpbyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/pK4av7uBK3I4M/giphy.gif)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# GitHub City - Repo Overview
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>

---

## A Diagrammatic Guide 


```mermaid
---
title: "GitHub City"
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
    'graph': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'textColor': '#F8B229',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph TD
    %% Frontend/UI
    subgraph "Frontend/UI"
        FE1["index.html"]:::frontend
        FE2["style.scss"]:::frontend
    end

    %% Rendering Engine
    subgraph "Rendering Engine"
        RE1["main.js"]:::render
        RE2["scene.js"]:::render
    end

    %% Business Logic
    subgraph "Business Logic"
        BL1["algo.js"]:::logic
        BL2["api.js"]:::logic
    end

    %% Assets (3D Models)
    subgraph "Assets (3D Models)"
        SA1["assets (3D Models)"]:::assets
    end

    %% Configuration & Tooling
    subgraph "Configuration & Tooling"
        CT1["constants.js"]:::config
        CT2[".eslintrc.js"]:::config
        CT3[".prettierrc.js"]:::config
        CT4[".stylelintrc.js"]:::config
        CT5["package.json"]:::config
        CT6["package-lock.json"]:::config
        CT7["GitHub Workflows & Husky"]:::config
    end

    %% External Service
    EG["GitHub API"]:::external

    %% Relationships
    FE1 -->|"loads"| RE1
    RE1 -->|"initializes"| RE2
    RE1 -->|"orchestrates"| BL1
    BL1 -->|"generatesCity"| RE2
    BL2 -->|"fetchesData"| EG
    RE2 -->|"loadsModels"| SA1

    %% Configuration support (dotted arrows)
    CT5 -.->|"supports"| FE1
    CT5 -.->|"supports"| RE1
    CT5 -.->|"supports"| BL1
    CT5 -.->|"supports"| BL2

    %% Legend (see comments below)
    %% Legend:
    %% - Frontend/UI (yellow): index.html, style.scss
    %% - Rendering Engine (light blue): main.js, scene.js
    %% - Business Logic (light green): algo.js, api.js
    %% - Assets (khaki): assets folder containing 3D models
    %% - Configuration & Tooling (grey): constants.js, build and linter configs, package files, GitHub workflows & Husky
    %% - External Service (salmon): GitHub API

    %% Click Events
    click FE1 "https://github.com/honzaap/githubcity/blob/main/index.html"
    click FE2 "https://github.com/honzaap/githubcity/blob/main/style.scss"
    click RE1 "https://github.com/honzaap/githubcity/blob/main/main.js"
    click RE2 "https://github.com/honzaap/githubcity/blob/main/scene.js"
    click BL1 "https://github.com/honzaap/githubcity/blob/main/algo.js"
    click BL2 "https://github.com/honzaap/githubcity/blob/main/api.js"
    click SA1 "https://github.com/honzaap/githubcity/tree/main/assets"
    click CT1 "https://github.com/honzaap/githubcity/blob/main/constants.js"
    click CT2 "https://github.com/honzaap/githubcity/blob/main/.eslintrc.js"
    click CT3 "https://github.com/honzaap/githubcity/blob/main/.prettierrc.js"
    click CT4 "https://github.com/honzaap/githubcity/blob/main/.stylelintrc.js"
    click CT5 "https://github.com/honzaap/githubcity/blob/main/package.json"
    click CT6 "https://github.com/honzaap/githubcity/blob/main/package-lock.json"
    click CT7 "https://github.com/honzaap/githubcity/tree/main/GitHub Workflows & Husky"

    %% Styles
    classDef frontend fill:#ccc3,stroke:#333,stroke-width:2px;
    classDef render fill:#ade6,stroke:#333,stroke-width:2px;
    classDef logic fill:#eef2,stroke:#333,stroke-width:2px;
    classDef assets fill:#ffc2,stroke:#333,stroke-width:2px;
    classDef config fill:#ded3,stroke:#333,stroke-width:2px;
    classDef external fill:#fec9,stroke:#333,stroke-width:2px
    
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
