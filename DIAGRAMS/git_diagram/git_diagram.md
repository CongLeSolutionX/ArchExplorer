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
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExcmJ1dTBocm56YWVvanozZDFiNnQ0MnA1azRiOW00a3B2MGlrZmNwMyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/8Ajnlx0wUQsiIUdtqc/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----

# Git Diagram
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
title: "Git Diagram"
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
    %% CI/CD & Deployment Layer
    subgraph CI_CD_and_Deployment["CI/CD & Deployment"]
    style CI_CD_and_Deployment fill:#c2c3,stroke:#333,stroke-width:2px
        c1["CI/CD Pipeline"]:::cicd
        c2["Containerization & Nginx"]:::deployment
        c1 --> c2
    end

    %% Frontend Layer
    subgraph Frontend["Frontend"]
    style Frontend fill:#c533,stroke:#333,stroke-width:2px
        fe1["Next.js App Pages<br>(Routing)"]:::frontend
        fe2["Next.js UI Components"]:::frontend
        fe1 --> fe2
    end

    %% Backend Layer
    subgraph Backend["Backend"]
    style Backend fill:#c512,stroke:#333,stroke-width:2px
        be1["FastAPI Backend Server"]:::backend
        be2["API Routers"]:::backend
        be3["Prompt Engineering Module"]:::backend
        be4["AI Service Integration"]:::backend
        be5["GitHub Service Integration"]:::backend
        be1 --> be2
        be1 --> be3
        be3 --> be4
        be1 --> be5
    end

    %% Database Layer
    subgraph Database["Database"]
    style Database fill:#c222,stroke:#333,stroke-width:2px
        db["PostgreSQL Database"]:::database
    end

    %% Data Flow Connections
    fe1 -->|"HTTP Request"| be1
    be1 -->|"CRUD Operations"| db

    %% Styles
    classDef frontend fill:#cce5f,stroke:#004085,stroke-width:2px
    classDef backend fill:#d4edd,stroke:#155724,stroke-width:2px
    classDef database fill:#fff3c,stroke:#856404,stroke-width:2px
    classDef deployment fill:#f8d7d,stroke:#721c24,stroke-width:2px
    classDef cicd fill:#d1ecf,stroke:#0c5460,stroke-width:2px

    %% Click Events for Frontend Components
    click fe1 "https://github.com/ahmedkhaleel2004/gitdiagram/tree/main/src/app"
    click fe2 "https://github.com/ahmedkhaleel2004/gitdiagram/tree/main/src/components"

    %% Click Events for Backend Components
    click be1 "https://github.com/ahmedkhaleel2004/gitdiagram/tree/main/backend/app"
    click be2 "https://github.com/ahmedkhaleel2004/gitdiagram/tree/main/backend/app/routers"
    click be3 "https://github.com/ahmedkhaleel2004/gitdiagram/blob/main/backend/app/prompts.py"
    click be4 "https://github.com/ahmedkhaleel2004/gitdiagram/blob/main/backend/app/services/claude_service.py"
    click be5 "https://github.com/ahmedkhaleel2004/gitdiagram/blob/main/backend/app/services/github_service.py"

    %% Click Event for Database
    click db "https://github.com/ahmedkhaleel2004/gitdiagram/tree/main/src/server/db"

    %% Click Events for Deployment & CI/CD
    click c2 "https://github.com/ahmedkhaleel2004/gitdiagram/blob/main/docker-compose.yml"
    click c2 "https://github.com/ahmedkhaleel2004/gitdiagram/tree/main/backend/Dockerfile"
    click c2 "https://github.com/ahmedkhaleel2004/gitdiagram/tree/main/backend/nginx"
    click c1 "https://github.com/ahmedkhaleel2004/gitdiagram/tree/main/.github/workflows"

```

---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).


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


----
