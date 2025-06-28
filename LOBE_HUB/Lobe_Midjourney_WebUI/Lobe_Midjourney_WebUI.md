---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExanp1djJjMWRrdW1lc2t2dDY0djJ2bXozMDlsdHNqbGNtdzgwbjJuZyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/mcdVjcUtgJz9603joH/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----



# Lobe Midjourney WebUI
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
title: "Lobe Hub - Lobe Midjourney WebUI"
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
    "flowchart": {"htmlLabels": true, 'curve': 'natural'},
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
    %% Frontend Client Subgraph
    subgraph Frontend_Client["Frontend Client - Next.js App"]
    style Frontend_Client fill:#fcc1,stroke:#333,stroke-width:2px
        PC["Page Component"]:::ui
        LC["Layout Component"]:::ui
        HP["Home Page"]:::ui
        IP["iFrame Page"]:::ui
        MD["Metadata"]:::ui
        HC["Header Component"]:::ui
        UIC["UI Components"]:::ui
        AN["Analytics"]:::ui
        PM["Preview Module"]:::ui
        PEM["PromptEditor Module"]:::ui
        TM["TaskList Module"]:::ui
        GS["Global Store"]:::state
        MS["Midjourney Store"]:::state
        LF["Localization Files"]:::local
        CL["Code Localization"]:::local
    end

    %% Backend API Subgraph
    subgraph Backend_API_Routes["Backend API Routes"]
    style Backend_API_Routes fill:#fcc1,stroke:#333,stroke-width:2px
        FAPI["File Services API"]:::api
        MAPI["Midjourney API"]:::api
    end

    %% Services & Config Subgraph
    subgraph Services_and_Configurations["Services & Configurations"]
    style Services_and_Configurations fill:#fcc1,stroke:#333,stroke-width:2px
        MDS["Midjourney Service"]:::service
        FS["File Service"]:::service
        SS["Storage Service"]:::service
        CONF["Configuration"]:::service
    end

    %% Infrastructure and Build Tools Subgraph
    subgraph Infrastructure_and_Build_Tools["Infrastructure & Build Tools"]
    style Infrastructure_and_Build_Tools fill:#fcc1,stroke:#333,stroke-width:2px
        NC["next.config.mjs"]:::infra
        TC["tsconfig.json"]:::infra
        ESL[".eslintrc.js"]:::infra
        PRE[".prettierrc.js"]:::infra
        CI["CI/CD Workflows"]:::infra
    end

    %% Connections: Frontend to Backend API
    UIC -->|"calls"| FAPI
    UIC -->|"calls"| MAPI

    %% Connections: Backend API to External Service
    MAPI -->|"delegates"| MDS

    %% Connections: API updating state management
    FAPI ---|"updates"| GS
    MAPI ---|"updates"| MS

    %% Connections: Feature Modules interacting with State
    PM ---|"triggers state update"| GS
    PEM ---|"triggers state update"| GS
    TM ---|"triggers state update"| MS

    %% Connections: Localization and Config feeding Frontend
    CONF ---|"configures"| UIC
    LF ---|"localizes"| UIC
    CL ---|"localizes"| UIC

    %% Connections: Frontend Core Components interlinking
    PC --> LC
    LC --> HP
    HP --> HC
    HC --> UIC
    UIC --> AN

    %% Click Events for Frontend Client
    click PC "https://github.com/lobehub/lobe-midjourney-webui/blob/main/src/app/page.tsx"
    click LC "https://github.com/lobehub/lobe-midjourney-webui/blob/main/src/app/layout.tsx"
    click HP "https://github.com/lobehub/lobe-midjourney-webui/blob/main/src/app/home/index.tsx"
    click IP "https://github.com/lobehub/lobe-midjourney-webui/blob/main/src/app/iframe/page.tsx"
    click MD "https://github.com/lobehub/lobe-midjourney-webui/blob/main/src/app/metadata.ts"
    click HC "https://github.com/lobehub/lobe-midjourney-webui/blob/main/src/app/home/Header.tsx"
    click UIC "https://github.com/lobehub/lobe-midjourney-webui/tree/main/src/components"
    click AN "https://github.com/lobehub/lobe-midjourney-webui/tree/main/src/components/Analytics"
    click PM "https://github.com/lobehub/lobe-midjourney-webui/tree/main/src/features/Preview"
    click PEM "https://github.com/lobehub/lobe-midjourney-webui/tree/main/src/features/PromptEditor"
    click TM "https://github.com/lobehub/lobe-midjourney-webui/tree/main/src/features/TaskList"
    click GS "https://github.com/lobehub/lobe-midjourney-webui/tree/main/src/store/global"
    click MS "https://github.com/lobehub/lobe-midjourney-webui/tree/main/src/store/midjourney"
    click LF "https://github.com/lobehub/lobe-midjourney-webui/tree/main/locales"
    click CL "https://github.com/lobehub/lobe-midjourney-webui/tree/main/src/locales"

    %% Click Events for Backend API Routes
    click FAPI "https://github.com/lobehub/lobe-midjourney-webui/blob/main/src/app/api/files/image/route.ts"
    click MAPI "https://github.com/lobehub/lobe-midjourney-webui/blob/main/src/app/api/midjourney/route.ts"

    %% Click Events for Services & Configurations
    click MDS "https://github.com/lobehub/lobe-midjourney-webui/blob/main/src/services/midjourney.ts"
    click FS "https://github.com/lobehub/lobe-midjourney-webui/blob/main/src/services/file.ts"
    click SS "https://github.com/lobehub/lobe-midjourney-webui/blob/main/src/services/storage.ts"
    click CONF "https://github.com/lobehub/lobe-midjourney-webui/tree/main/src/config"

    %% Click Events for Infrastructure & Build Tools
    click NC "https://github.com/lobehub/lobe-midjourney-webui/blob/main/next.config.mjs"
    click TC "https://github.com/lobehub/lobe-midjourney-webui/blob/main/tsconfig.json"
    click ESL "https://github.com/lobehub/lobe-midjourney-webui/blob/main/.eslintrc.js"
    click PRE "https://github.com/lobehub/lobe-midjourney-webui/blob/main/.prettierrc.js"
    click CI "https://github.com/lobehub/lobe-midjourney-webui/tree/main/.github/workflows"

    %% Styles
    classDef ui fill:#a3d5f,stroke:#1f78b4,stroke-width:2px
    classDef api fill:#ffecd,stroke:#f16c28,stroke-width:2px
    classDef state fill:#d0f0c,stroke:#4a7c59,stroke-width:2px
    classDef service fill:#fddde,stroke:#e31a1c,stroke-width:2px
    classDef infra fill:#eeeee,stroke:#666666,stroke-width:2px
    classDef local fill:#fff2c,stroke:#b58900,stroke-width:2px
    
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
