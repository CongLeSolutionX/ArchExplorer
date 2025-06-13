---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/grishka/Smithereen
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExaDFjNmo5a2QzdXdueGRidXJicnowbWVjeWlmYjZjNmZhYzg2Z2hkMCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/EYo6rhSUxI5bVqkX87/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# grishka_Smithereen repo project
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---

```mermaid
---
title: "grishka_Smithereen repo project"
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
flowchart TD
    %% Clients Layer
    Clients("Clients (Browser/Mobile)"):::client
    click Clients "https://github.com/grishka/smithereen/tree/master/src/main/resources/public"
    click Clients "https://github.com/grishka/smithereen/tree/master/src/main/web"

    %% Reverse Proxy
    Proxy("Reverse Proxy (Nginx/Caddy)"):::proxy
    click Proxy "https://github.com/grishka/smithereen/blob/master/examples/nginx.conf"
    click Proxy "https://github.com/grishka/smithereen/tree/master/examples/Caddyfile"

    %% JVM Application
    subgraph "Smithereen JVM Application"
    %% :::app
        SA("SmithereenApplication\n(Entry Point)"):::app
        click SA "https://github.com/grishka/smithereen/blob/master/src/main/java/smithereen/SmithereenApplication.java"

        subgraph "Routes Layer"
            Routes("SparkJava Routes"):::app
            click Routes "https://github.com/grishka/smithereen/tree/master/src/main/java/smithereen/routes"
        end

        subgraph "Controllers Layer"
            Controllers("Controllers"):::app
            click Controllers "https://github.com/grishka/smithereen/tree/master/src/main/java/smithereen/controllers"
        end

        subgraph "Service Modules"
            AP("ActivityPub Module"):::service
            click AP "https://github.com/grishka/smithereen/tree/master/src/main/java/smithereen/activitypub"
            click AP "https://github.com/grishka/smithereen/tree/master/src/main/java/smithereen/activitypub/handlers"
            click AP "https://github.com/grishka/smithereen/tree/master/src/main/java/smithereen/activitypub/objects"
            click AP "https://github.com/grishka/smithereen/tree/master/src/main/java/smithereen/activitypub/tasks"

            Mailer("SMTP Mailer"):::service
            click Mailer "https://github.com/grishka/smithereen/blob/master/src/main/java/smithereen/Mailer.java"
            click Mailer "https://github.com/grishka/smithereen/blob/master/src/main/java/smithereen/storage/MailStorage.java"

            HTTPClient("ExtendedHttpClient"):::service
            click HTTPClient "https://github.com/grishka/smithereen/blob/master/src/main/java/smithereen/http/ExtendedHttpClient.java"

            Background("BackgroundTaskRunner"):::service
            click Background "https://github.com/grishka/smithereen/blob/master/src/main/java/smithereen/util/BackgroundTaskRunner.java"
        end

        subgraph "Storage Layer"
            Storage("Storage Module"):::storage
            click Storage "https://github.com/grishka/smithereen/tree/master/src/main/java/smithereen/storage"

            subgraph "SQL Layer"
                SQL("SQL DAO & Schema"):::storage
                click SQL "https://github.com/grishka/smithereen/tree/master/src/main/java/smithereen/storage/sql"
                click SQL "https://github.com/grishka/smithereen/blob/master/schema.sql"
                click SQL "https://github.com/grishka/smithereen/blob/master/src/main/java/smithereen/storage/DatabaseSchemaUpdater.java"
            end

            subgraph "Media Drivers"
                Media("Media Drivers"):::storage
                click Media "https://github.com/grishka/smithereen/tree/master/src/main/java/smithereen/storage/media"
                click Media "https://github.com/grishka/smithereen/blob/master/src/main/java/smithereen/storage/media/LocalMediaFileStorageDriver.java"
                click Media "https://github.com/grishka/smithereen/blob/master/src/main/java/smithereen/storage/media/S3MediaFileStorageDriver.java"
            end

            ImgProxy("Imgproxy Integration"):::service
            click ImgProxy "https://github.com/grishka/smithereen/blob/master/src/main/java/smithereen/storage/ImgProxy.java"
            click ImgProxy "https://github.com/grishka/smithereen/blob/master/ci/build_imgproxy.sh"

            LibVips("Native libvips"):::service
            click LibVips "https://github.com/grishka/smithereen/tree/master/src/main/java/smithereen/libvips"
        end

        subgraph "Templating & Config"
            Templates("Twig Templates"):::app
            click Templates "https://github.com/grishka/smithereen/tree/master/src/main/resources/templates"
            click Templates "https://github.com/grishka/smithereen/blob/master/src/main/java/smithereen/templates/Templates.java"

            Config("Configuration"):::app
            click Config "https://github.com/grishka/smithereen/blob/master/src/main/java/smithereen/Config.java"
            click Config "https://github.com/grishka/smithereen/blob/master/examples/config.properties"
            click Config "https://github.com/grishka/smithereen/blob/master/examples/config_docker.properties"
        end
    end

    %% External Components
    DB["MySQL Database"]:::db
    ObjStore["Object Storage\n(S3 or Local FS)"]:::storage
    ImgproxyService["Imgproxy Service"]:::external
    SMTP["SMTP Server"]:::external
    Peers["Federated ActivityPub Peers"]:::external

    %% Connections
    Clients -->|"HTTP/HTTPS<br/>(static & dynamic)"| Proxy
    Proxy -->|Static Assets| Clients
    Proxy -->|Proxy HTTP| SA

    SA -->|Initializes| Routes
    Routes -->|calls| Controllers
    Controllers -->|uses| AP
    Controllers -->|uses| Mailer
    Controllers -->|uses| Storage
    Controllers -->|renders| Templates

    AP -->|"HTTP POST/GET\n(ActivityPub)"| Peers
    Mailer -->|SMTP| SMTP
    HTTPClient -->|HTTP| Peers

    SA -->|loads| LibVips
    SA -->|schedules| Background

    Controllers -->|JDBC| DB
    Storage -->|JDBC| DB

    Controllers -->|S3 API or FS I/O| ObjStore
    Storage -->|Media I/O| ObjStore

    Controllers -->|requests| ImgproxyService
    Proxy -->|redirects image resize| ImgproxyService

    Background -->|async| AP
    Background -->|async| Mailer
    Background -->|async| Storage

    %% Styles
    classDef client fill:#FFD47F,stroke:#333,stroke-width:1px;
    classDef proxy fill:#A0D8EF,stroke:#333,stroke-width:1px,stroke-dasharray: 5 5;
    classDef app fill:#E2F0D9,stroke:#333,stroke-width:1px;
    classDef service fill:#FDE2E1,stroke:#333,stroke-width:1px;
    classDef storage fill:#FFF5BA,stroke:#333,stroke-width:1px;
    classDef db fill:#D5A6BD,stroke:#333,stroke-width:1px;
    classDef external fill:#D0E0E3,stroke:#333,stroke-width:1px,stroke-dasharray: 2 2;
```

-----


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
