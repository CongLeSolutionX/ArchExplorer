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
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExMXVjejV3dnVjc2o5MXd3eXBvcDR1cHlzbHQ1Z2R6YjY0ZHpmdjJ6OCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/hL9q5k9dk9l0wGd4e0/giphy.gif)
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
> The materials are intended for educational purposes (<ins>sometimes, entertainment purposes</ins>), personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


----

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
    %% Client Layer
    subgraph "Client (Browser)" 
        direction TB
        StaticAssets["Static Assets"]:::frontend
        Templates["Templates"]:::frontend
    end

    %% Edge Layer
    NGINX["NGINX Reverse Proxy"]:::server

    %% Web Server
    subgraph "Web Server"
        direction TB
        Gunicorn["Gunicorn WSGI"]:::server
        Procfile["Procfile"]:::server
        Entrypoint["entrypoint.sh"]:::server
        Dockerfile["Dockerfile"]:::server
        Runtime["runtime.txt"]:::server
        GunicornCfg["gunicorn-cfg.py"]:::server
        Supervisor["supervisord.conf"]:::server
        SupervisorDocker["supervisord-docker.conf"]:::server
    end

    %% Application Layer
    subgraph "Flask Application" 
        direction TB
        CoreRun["run.py"]:::server
        Init["__init__.py"]:::server
        Config["config.py"]:::server
        Constants["constants.py"]:::server

        subgraph "Blueprints"
            direction TB
            BaseBP["Base"]:::server
            AdminBP["Administration"]:::server
            AnalysisBP["Analysis"]:::server
            ProjectsBP["Projects"]:::server
            RulesBP["Rules"]:::server
        end
    end

    %% Data Stores
    subgraph "Database & Migrations"
        direction TB
        DB["Relational Database"]:::datastore
        MigrationsDir["migrations"]:::datastore
        AlembicIni["alembic.ini"]:::datastore
        Versions["versions"]:::datastore
    end

    subgraph "Task Queue & Worker"
        direction TB
        Redis["Redis (Broker)"]:::datastore
        Celery["Celery Worker"]:::server
    end

    %% Third-Party Tools
    subgraph "Third-Party Analysis Engines"
        direction TB
        AppInspector["Application Inspector"]:::external
        SCC["SCC (LOC Counter)"]:::external
    end

    %% Artifact Storage
    Storage["Scan Outputs (media/)"]:::datastore

    %% Deployment Orchestration
    DockerCompose["docker-compose.yml"]:::server

    %% Connections
    StaticAssets -->|"Serves UI"| NGINX
    Templates -->|"Serves UI"| NGINX
    NGINX -->|"HTTP"| Gunicorn
    Gunicorn -->|"WSGI"| CoreRun
    CoreRun -->|"Loads"| Init
    CoreRun -->|"Loads"| Config
    CoreRun -->|"Loads"| Constants

    CoreRun -->|"Controller Calls"| BaseBP
    CoreRun -->|"Controller Calls"| AdminBP
    CoreRun -->|"Controller Calls"| AnalysisBP
    CoreRun -->|"Controller Calls"| ProjectsBP
    CoreRun -->|"Controller Calls"| RulesBP

    AnalysisBP -->|"Enqueue Task (AMQP/Redis)"| Redis
    Redis -->|"Pull Task"| Celery
    Celery -->|"CLI Call"| AppInspector
    Celery -->|"CLI Call"| SCC
    Celery -->|"Store Results (SQL)"| DB
    Celery -->|"Store Files"| Storage

    CoreRun -->|"Query/Write (SQL)"| DB
    CoreRun -->|"Read Results"| DB

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
    classDef frontend fill:#ADD8E6,stroke:#333,stroke-width:1px
    classDef server fill:#90EE90,stroke:#333,stroke-width:1px
    classDef datastore fill:#F4A460,stroke:#333,stroke-width:1px
    classDef external fill:#D3D3D3,stroke:#333,stroke-width:1px

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