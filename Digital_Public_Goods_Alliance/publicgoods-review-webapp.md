---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/DPGAlliance/publicgoods-review-webapp
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




# publicgoods-review-webapp repo project
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
title: "publicgoods-review-webapp repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright © 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'linear'},
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#22BB',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EEF2',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '15px'
    }
  }
}%%
flowchart TD
    %% External Client
    Client["Browser/Mobile"]:::external

    %% Infrastructure Layer
    subgraph "Infrastructure"
      LB["Load Balancer"]:::compute
      WS["Web Server<br/>(Apache/nginx)"]:::compute
    end

    Client -->|HTTPS Request| LB --> WS

    %% Entry Point and Routing
    WS --> FP["index.php"]:::compute
    click FP "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/index.php"
    WS --> HT[".htaccess"]:::compute
    click HT "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/.htaccess"
    FP --> Router["Router"]:::compute
    click Router "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/system/core/Router.php"

    %% CodeIgniter Front Controller
    subgraph "CodeIgniter Front Controller"
      CI["CodeIgniter.php"]:::compute
      click CI "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/system/core/CodeIgniter.php"
      ConfigCI["config.php"]:::config
      click ConfigCI "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/application/config/config.php"
    end
    FP --> CI
    CI --> Router

    %% Routing to Controllers
    Router --> Controllers

    %% PHP Application Layer
    subgraph "PHP Application"
      subgraph "Controllers"
        Admin["Admin"]:::backend
        click Admin "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/application/controllers/Admin.php"
        Api["Api"]:::backend
        click Api "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/application/controllers/Api.php"
        CronsC["Crons"]:::backend
        click CronsC "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/application/controllers/Crons.php"
        Expert["Expert"]:::backend
        click Expert "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/application/controllers/Expert.php"
        Front["Frontpage"]:::backend
        click Front "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/application/controllers/Frontpage.php"
        Pub["General_public"]:::backend
        click Pub "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/application/controllers/General_public.php"
        Rev["Reviewer"]:::backend
        click Rev "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/application/controllers/Reviewer.php"
        UsersC["Users"]:::backend
        click UsersC "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/application/controllers/Users.php"
        Welcome["Welcome"]:::backend
        click Welcome "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/application/controllers/Welcome.php"
        Fresh["Fresh_application"]:::backend
        click Fresh "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/application/controllers/Fresh_application.php"
      end

      subgraph "Models"
        AppModel["Application_model"]:::backend
        click AppModel "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/application/models/Application_model.php"
        SecModel["Section_model"]:::backend
        click SecModel "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/application/models/Section_model.php"
        UsersModel["Users_model"]:::backend
        click UsersModel "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/application/models/Users_model.php"
      end

      subgraph "Views"
        AdminV["views/admin/"]:::frontend
        click AdminV "https://github.com/dpgalliance/publicgoods-review-webapp/tree/main/application/views/admin/"
        AppV["views/applicant/"]:::frontend
        click AppV "https://github.com/dpgalliance/publicgoods-review-webapp/tree/main/application/views/applicant/"
        ExpV["views/expert/"]:::frontend
        click ExpV "https://github.com/dpgalliance/publicgoods-review-webapp/tree/main/application/views/expert/"
        PubV["views/public/"]:::frontend
        click PubV "https://github.com/dpgalliance/publicgoods-review-webapp/tree/main/application/views/public/"
        RevV["views/reviewer/"]:::frontend
        click RevV "https://github.com/dpgalliance/publicgoods-review-webapp/tree/main/application/views/reviewer/"
        EmailV["views/emails/"]:::frontend
        click EmailV "https://github.com/dpgalliance/publicgoods-review-webapp/tree/main/application/views/emails/"
        ErrV["views/errors/"]:::frontend
        click ErrV "https://github.com/dpgalliance/publicgoods-review-webapp/tree/main/application/views/errors/"
      end
    end

    %% Static Assets
    subgraph "Static Assets"
    %% :::frontend
      CSS["assets/css/"] 
      click CSS "https://github.com/dpgalliance/publicgoods-review-webapp/tree/main/assets/css/"
      JS["assets/js/"] 
      click JS "https://github.com/dpgalliance/publicgoods-review-webapp/tree/main/assets/js/"
      Img["assets/images/"] 
      click Img "https://github.com/dpgalliance/publicgoods-review-webapp/tree/main/assets/images/"
      Sel2["assets/select2/"] 
      click Sel2 "https://github.com/dpgalliance/publicgoods-review-webapp/tree/main/assets/select2/"
      Fonts["assets/bsfonts/"] 
      click Fonts "https://github.com/dpgalliance/publicgoods-review-webapp/tree/main/assets/bsfonts/"
    end
    Client -->|GET assets| CSS & JS & Img & Sel2 & Fonts

    %% Backing Services
    subgraph "Backing Services"
      DB["MySQL/PostgreSQL DB"]:::storage
      click DB "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/application/config/database.php"
      click DB "https://github.com/dpgalliance/publicgoods-review-webapp/tree/main/system/database/drivers/mysql/"
      Cache["Memcached/Redis"]:::storage
      click Cache "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/application/config/memcached.php"
      click Cache "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/system/libraries/Cache/drivers/Cache_memcached.php"
      click Cache "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/system/libraries/Cache/drivers/Cache_redis.php"
      FS["File Storage<br/>(/files/applicant_uploads)"]:::storage
      click FS "https://github.com/dpgalliance/publicgoods-review-webapp/tree/main/files/applicant_uploads/"
      EmailService["SMTP/API Email Service"]:::external
      click EmailService "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/application/config/email.php"
      click EmailService "https://github.com/dpgalliance/publicgoods-review-webapp/blob/main/system/libraries/Email.php"
    end

    %% Third-Party & Logging
    TP["Third-Party Integrations"]:::external
    click TP "https://github.com/dpgalliance/publicgoods-review-webapp/tree/main/application/third_party/"
    Logs["Application Logs"]:::storage
    click Logs "https://github.com/dpgalliance/publicgoods-review-webapp/tree/main/application/logs/"

    %% Data Flows
    Controllers -->|Query Builder| Models
    Controllers -->|Render| Views
    Controllers -->|SELECT/INSERT| DB
    Controllers -->|CACHE READ/WRITE| Cache
    Controllers -->|SAVE FILE| FS
    Controllers -->|SEND EMAIL| EmailService
    Controllers -->|LOG| Logs
    Controllers -->|CALL API| TP

    %% Cron Jobs
    CronScheduler["OS-level Cron"]:::external
    CronScheduler -->|HTTP/CLI trigger| CronsC

    %% Legend Styles
    classDef compute fill:#D0E6FF,stroke:#004A99,color:#000;
    classDef backend fill:#FFEECC,stroke:#CC6600,color:#000;
    classDef frontend fill:#E8F5E9,stroke:#2E7D32,color:#000;
    classDef storage fill:#E1F5FE,stroke:#0277BD,color:#000;
    classDef external fill:#FFF3E0,stroke:#E65100,color:#000;
    classDef config fill:#F3E5F5,stroke:#6A1B9A,color:#000;

```

----


<!-- 
```mermaid
%% Current Mermaid version
info
```  -->


```mermaid
---
title: "C<char>o&#770;</char>ngL<char>e&#770;</char>SolutionX"
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
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX/CongLeSolutionX' target='_blank'>Click here if you care about the profile of a tech guy seeking for job 🙏🏼</a>"}}

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