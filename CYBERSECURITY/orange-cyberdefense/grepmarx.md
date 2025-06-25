---
created: 2025-06-25 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/Orange-Cyberdefense/grepmarx
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExNHQzZTk5eTNldTY0MXl5cGQxY2lzbjZlYXRyb2U2YjluM3UxZGF5ZCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/077i6AULCXc0FKTj9s/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# grepmarx repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for 👨‍🎓 <ins>educational purposes</ins> 👨‍🎓 (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), 📖 <ins> personal study </ins> 📖, and 🔖 <ins> reference </ins> 🔖.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


---

```mermaid
---
title: "grepmarx repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
  look: handDrawn
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'American Typewriter, monospace',
    'logLevel': 'fatal',
    'themeVariables': {
      'primaryColor': '#22BB',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#E2F1',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '20px'
    }
  }
}%%
flowchart TB
    subgraph Client_Layer["Client Layer (Browser)"]
    style Client_Layer fill:#F2F2,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        StaticAssets["Static Assets"]:::frontend
        Templates["Templates"]:::frontend
    end

    %% Edge Layer
    NGINX["NGINX Reverse Proxy"]:::server

    subgraph Web_Server["Web Server"]
    style Web_Server fill:#FBF2,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        Gunicorn["Gunicorn WSGI"]:::server
        Procfile["<b>Procfile</b>"]:::server
        Entrypoint["<b>entrypoint.sh</b>"]:::server
        Dockerfile["<b>Dockerfile</b>"]:::server
        Runtime["<b>runtime.txt</b>"]:::server
        GunicornCfg["<b>gunicorn-cfg.py</b>"]:::server
        Supervisor["<b>supervisord.conf</b>"]:::server
        SupervisorDocker["<b>supervisord-docker.conf</b>"]:::server
    end

    subgraph Flask_Application["Flask Application Layer"]
    style Flask_Application fill:#2BF2,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        CoreRun["<b>run.py</b>"]:::server
        Init["<b>__init__.py</b>"]:::server
        Config["<b>config.py</b>"]:::server
        Constants["<b>constants.py</b>"]:::server

        subgraph Blueprints["Blueprints"]
        style Blueprints fill:#2BB2,stroke:#333,stroke-width:1px, color: #FFFF
        direction TB
            BaseBP["Base"]:::server
            AdminBP["Administration"]:::server
            AnalysisBP["Analysis"]:::server
            ProjectsBP["Projects"]:::server
            RulesBP["Rules"]:::server
        end
    end

    %% Data Stores
    subgraph Database_and_Migrations["Database & Migrations"]
    style Database_and_Migrations fill:#BBF5,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        DB["Relational Database"]:::datastore
        MigrationsDir["migrations"]:::datastore
        AlembicIni["<b>alembic.ini</b>"]:::datastore
        Versions["versions"]:::datastore
    end

    subgraph Task_Queue_and_Worker["Task Queue & Worker"]
    style Task_Queue_and_Worker fill:#B2F5,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        Redis["Redis<br/>(Broker)"]:::datastore
        Celery["Celery Worker"]:::server
    end

    %% Third-Party Tools
    subgraph Third_Party_Analysis_Engines["Third-Party Analysis Engines"]
    style Third_Party_Analysis_Engines fill:#FBF5,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        AppInspector["Application Inspector"]:::external
        SCC["SCC<br/>(LOC Counter)"]:::external
    end

    %% Artifact Storage
    Storage["Scan Outputs<br/>(<b>media/</b>)"]:::datastore

    %% Deployment Orchestration
    DockerCompose["<b>docker-compose.yml</b>"]:::server

    %% Connections
    StaticAssets -->|"serves UI"| NGINX
    Templates -->|"serves UI"| NGINX
    NGINX -->|"HTTP"| Gunicorn
    Gunicorn -->|"WSGI"| CoreRun
    CoreRun -->|"loads"| Init
    CoreRun -->|"loads"| Config
    CoreRun -->|"loads"| Constants

    CoreRun -->|"Controller calls"| BaseBP
    CoreRun -->|"Controller calls"| AdminBP
    CoreRun -->|"Controller calls"| AnalysisBP
    CoreRun -->|"Controller calls"| ProjectsBP
    CoreRun -->|"Controller calls"| RulesBP

    AnalysisBP -->|"enqueue task<br/>(AMQP/Redis)"| Redis
    Redis -->|"pull task"| Celery
    Celery -->|"CLI call"| AppInspector
    Celery -->|"CLI call"| SCC
    Celery -->|"store results<br/>(SQL)"| DB
    Celery -->|"store files"| Storage

    CoreRun -->|"query/write<br/>(SQL)"| DB
    CoreRun -->|"read results"| DB

    DockerCompose --> NGINX
    DockerCompose --> Gunicorn
    DockerCompose --> Redis
    DockerCompose --> DB
    DockerCompose --> Celery

    %% Click Events
    click StaticAssets "https://github.com/orange-cyberdefense/grepmarx/tree/main/app/base/static"
    click Templates "https://github.com/orange-cyberdefense/grepmarx/tree/main/app/base/templates"
    click NGINX "https://github.com/orange-cyberdefense/grepmarx/blob/main/nginx/grepmarx.conf"
    click GunicornCfg "https://github.com/orange-cyberdefense/grepmarx/blob/main/gunicorn-cfg.py"
    click Supervisor "https://github.com/orange-cyberdefense/grepmarx/blob/main/supervisord.conf"
    click SupervisorDocker "https://github.com/orange-cyberdefense/grepmarx/blob/main/supervisord-docker.conf"
    click Procfile "https://github.com/orange-cyberdefense/grepmarx/tree/main/Procfile"
    click Entrypoint "https://github.com/orange-cyberdefense/grepmarx/blob/main/entrypoint.sh"
    click Dockerfile "https://github.com/orange-cyberdefense/grepmarx/tree/main/Dockerfile"
    click Runtime "https://github.com/orange-cyberdefense/grepmarx/blob/main/runtime.txt"
    click CoreRun "https://github.com/orange-cyberdefense/grepmarx/blob/main/run.py"
    click Init "https://github.com/orange-cyberdefense/grepmarx/blob/main/app/__init__.py"
    click Config "https://github.com/orange-cyberdefense/grepmarx/blob/main/app/config.py"
    click Constants "https://github.com/orange-cyberdefense/grepmarx/blob/main/app/constants.py"
    click BaseBP "https://github.com/orange-cyberdefense/grepmarx/tree/main/app/base"
    click AdminBP "https://github.com/orange-cyberdefense/grepmarx/tree/main/app/administration"
    click AnalysisBP "https://github.com/orange-cyberdefense/grepmarx/tree/main/app/analysis"
    click ProjectsBP "https://github.com/orange-cyberdefense/grepmarx/tree/main/app/projects"
    click RulesBP "https://github.com/orange-cyberdefense/grepmarx/tree/main/app/rules"
    click MigrationsDir "https://github.com/orange-cyberdefense/grepmarx/tree/main/migrations"
    click AlembicIni "https://github.com/orange-cyberdefense/grepmarx/blob/main/migrations/alembic.ini"
    click Versions "https://github.com/orange-cyberdefense/grepmarx/tree/main/migrations/versions"
    click Celery "https://github.com/orange-cyberdefense/grepmarx/blob/main/app/celery_worker.py"
    click AppInspector "https://github.com/orange-cyberdefense/grepmarx/tree/main/app/third-party/app-inspector"
    click SCC "https://github.com/orange-cyberdefense/grepmarx/tree/main/app/third-party/scc"
    click Storage "https://github.com/orange-cyberdefense/grepmarx/tree/main/media"
    click DockerCompose "https://github.com/orange-cyberdefense/grepmarx/blob/main/docker-compose.yml"

    %% Styles
    classDef frontend fill:#A2A6,stroke:#333,stroke-width:1px
    classDef server fill:#9E92,stroke:#333,stroke-width:1px
    classDef datastore fill:#F462,stroke:#333,stroke-width:1px
    classDef external fill:#D3B3,stroke:#333,stroke-width:1px

```

----


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
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }



```

---
>**Licenses:**
>
>- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
>- **Creative Commons Attribution-ShareAlike 4.0 International**: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) [![CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/88x31.png)](https://creativecommons.org/licenses/by-sa/4.0/) - Legal details in [LICENSE-CC-BY-SA-4.0](THE_PAST/LICENSE-CC-BY-SA-4.0) and at [Creative Commons official site](https://creativecommons.org/licenses/by-sa/4.0/).
>
---
