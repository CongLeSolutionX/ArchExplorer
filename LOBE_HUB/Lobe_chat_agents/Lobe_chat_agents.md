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



# Lobe Chat Agents
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
title: "Lobe Hub - Lobe Chat Agents"
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
flowchart TB
    %% Data Layer
    subgraph Data_Layer["Data Layer"]
    style Data_Layer fill:#c226,stroke:#333,stroke-width:2px
        A1["Agent Definitions (src/*.json)"]:::data
        A2["Agent Templates (agent-template.json & agent-template-full.json)"]:::data
        A3["Internationalization (locales/)"]:::data
        A4["i18n Configuration (.i18nrc.js)"]:::data
    end

    %% Build & Processing Layer
    subgraph Build_and_Processing_Layer["Build & Processing Layer"]
    style Build_and_Processing_Layer fill:#c226,stroke:#333,stroke-width:2px
        P1["Build Scripts (scripts/build.ts, format.ts, updateAwesome.ts)"]:::process
        P2["Testing Scripts (scripts/test.ts, testLocale.ts)"]:::process
        P3["Schema Definitions (schema/lobeAgentSchema_v1.json)"]:::process
        P4["Script-based Schema Extensions (scripts/schema/)"]:::process
    end

    %% CI/CD Automation Layer
    subgraph CI_CD_Automation["CI/CD Automation"]
    style CI_CD_Automation fill:#c226,stroke:#333,stroke-width:2px
        C1["CI/CD Config (.github workflows, package.json, tsconfig.json, .npmrc, .gitignore)"]:::automation
    end

    %% Deployment & Integration Layer
    subgraph Deployment_and_Integration["Deployment & Integration"]
    style Deployment_and_Integration fill:#c2263,stroke:#333,stroke-width:2px
        D1["Deployed Agent Index Endpoint (Vercel)"]:::deployment
        D2["External Consumers (Lobe Chat UI & Plugin Index)"]:::deployment
    end

    %% Data Flow Connections
    A1 -->|"provides data"| P1
    A2 -->|"provides templates"| P1
    A3 -->|"localization data"| P1
    A4 -->|"i18n settings"| P1

    %% Supportive connections within Processing Layer
    P2 -.->|"testing supports"| P1
    P3 -.->|"schema validates"| P1
    P4 -.->|"schema extensions"| P1

    %% Deployment Pipeline Flow
    P1 -->|"triggers build"| C1
    C1 -->|"deploys update"| D1
    D1 -->|"consumed by"| D2

    %% Click Events
    click A1 "https://github.com/lobehub/lobe-chat-agents/tree/main/src/"
    click A2 "https://github.com/lobehub/lobe-chat-agents/blob/main/agent-template.json"
    click A3 "https://github.com/lobehub/lobe-chat-agents/tree/main/locales/"
    click A4 "https://github.com/lobehub/lobe-chat-agents/blob/main/.i18nrc.js"
    click P1 "https://github.com/lobehub/lobe-chat-agents/tree/main/scripts/"
    click P2 "https://github.com/lobehub/lobe-chat-agents/blob/main/scripts/test.ts"
    click P3 "https://github.com/lobehub/lobe-chat-agents/blob/main/schema/lobeAgentSchema_v1.json"
    click P4 "https://github.com/lobehub/lobe-chat-agents/tree/main/scripts/schema/"
    click C1 "https://github.com/lobehub/lobe-chat-agents/tree/main/.github/"

    %% Styles
    classDef data fill:#AED6F,stroke:#1B4F72,stroke-width:2px
    classDef process fill:#A9DFB,stroke:#196F3D,stroke-width:2px
    classDef automation fill:#F9E79,stroke:#B9770E,stroke-width:2px
    classDef deployment fill:#F5B7B,stroke:#922B21,stroke-width:2px

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
