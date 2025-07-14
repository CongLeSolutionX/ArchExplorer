---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/DPGAlliance/dpg-resources
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




# dpg-resources repo project
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
title: "dpg-resources repo project"
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
flowchart TB
    %% Content authoring and repository
    subgraph "Content Authoring & Repo"
        Developer["Developer"]:::devpipe
        Repo["Content Repository"]:::devpipe
        GovReadme["README.md"]:::devpipe
        GovContrib["CONTRIBUTING.md"]:::devpipe
        GovLicense["LICENSE.txt"]:::devpipe
        DocsFolder["docs/"]:::devpipe
        Guides["Markdown Guides & Templates"]:::devpipe
        Assets["Static Assets"]:::devpipe
        PlatIndep["Platform Independence Section"]:::devpipe
    end

    Developer -->|git push| Repo
    Repo -->|contains governance & content| GovReadme
    Repo --> GovContrib
    Repo --> GovLicense
    Repo --> DocsFolder
    DocsFolder --> Guides
    DocsFolder --> Assets
    DocsFolder --> PlatIndep

    %% CI/CD Pipeline
    Repo -->|trigger build| CICD["CI/CD Pipeline"]:::devpipe
    subgraph "CI/CD Pipeline"
        Lint["Lint & Link Check"]:::devpipe
        Test["Test"]:::devpipe
        Build["Build Static Site"]:::devpipe
    end
    CICD --> Lint
    Lint --> Test
    Test --> Build

    %% Static site generation and hosting
    Build -->|generate HTML/CSS/JS| SSG["Static-Site Generator"]:::devpipe
    SSG -->|deploy artifacts| Host["Hosting / CDN"]:::hosting
    Host -->|serve via HTTP GET| Browser["End-User Browser"]:::user
    Browser -->|fetch external DPG API| ExtAPI["External DPG API"]:::external

    %% Embedded example reference
    DocsFolder --> ExampleRoot["MongoDB-Express REST API Example"]:::devpipe
    subgraph "Embedded Example: MongoDB-Express REST API"
        ExampleRoot
        subgraph App
            AppDir["app/"]:::devpipe
            AppPkg["package.json"]:::devpipe
            AppSrc["src/"]:::devpipe
            AppPublic["public/"]:::devpipe
        end
        subgraph Server
            ServerDir["server/"]:::devpipe
            ServerPkg["package.json"]:::devpipe
            Posts["routes/posts.mjs"]:::devpipe
            Conn["db/conn.mjs"]:::devpipe
        end
        DockerCompose["docker-compose.yml"]:::devpipe
        DemoVideo["demo.mp4"]:::devpipe
    end

    ExampleRoot --> AppDir
    ExampleRoot --> ServerDir
    ExampleRoot --> DockerCompose
    ExampleRoot --> DemoVideo
    AppDir --> AppPkg
    AppDir --> AppSrc
    AppDir --> AppPublic
    ServerDir --> ServerPkg
    ServerDir --> Posts
    ServerDir --> Conn

    %% Click Events
    click DocsFolder "https://github.com/dpgalliance/dpg-resources/tree/main/docs/"
    click GovReadme "https://github.com/dpgalliance/dpg-resources/blob/main/README.md"
    click GovContrib "https://github.com/dpgalliance/dpg-resources/blob/main/CONTRIBUTING.md"
    click GovLicense "https://github.com/dpgalliance/dpg-resources/blob/main/LICENSE.txt"
    click Guides "https://github.com/dpgalliance/dpg-resources/blob/main/docs/*.md"
    click Assets "https://github.com/dpgalliance/dpg-resources/tree/main/docs/assets/"
    click PlatIndep "https://github.com/dpgalliance/dpg-resources/blob/main/docs/platform-independence/README.md"
    click ExampleRoot "https://github.com/dpgalliance/dpg-resources/tree/main/docs/platform-independence/mongodb-express-rest-api-example/"
    click AppDir "https://github.com/dpgalliance/dpg-resources/tree/main/docs/platform-independence/mongodb-express-rest-api-example/app/"
    click AppPkg "https://github.com/dpgalliance/dpg-resources/blob/main/docs/platform-independence/mongodb-express-rest-api-example/app/package.json"
    click AppSrc "https://github.com/dpgalliance/dpg-resources/tree/main/docs/platform-independence/mongodb-express-rest-api-example/app/src/"
    click AppPublic "https://github.com/dpgalliance/dpg-resources/tree/main/docs/platform-independence/mongodb-express-rest-api-example/app/public/"
    click ServerDir "https://github.com/dpgalliance/dpg-resources/tree/main/docs/platform-independence/mongodb-express-rest-api-example/server/"
    click ServerPkg "https://github.com/dpgalliance/dpg-resources/blob/main/docs/platform-independence/mongodb-express-rest-api-example/server/package.json"
    click Posts "https://github.com/dpgalliance/dpg-resources/blob/main/docs/platform-independence/mongodb-express-rest-api-example/server/routes/posts.mjs"
    click Conn "https://github.com/dpgalliance/dpg-resources/blob/main/docs/platform-independence/mongodb-express-rest-api-example/server/db/conn.mjs"
    click DockerCompose "https://github.com/dpgalliance/dpg-resources/blob/main/docs/platform-independence/mongodb-express-rest-api-example/docker-compose.yml"
    click DemoVideo "https://github.com/dpgalliance/dpg-resources/blob/main/docs/platform-independence/mongodb-express-rest-api-example/demo.mp4"

    %% Styles
    classDef devpipe fill:#D6EAF8,stroke:#1B4F72,color:#154360;
    classDef hosting fill:#D5F5E3,stroke:#196F3D,color:#145A32;
    classDef user fill:#FDEBD0,stroke:#D68910,color:#B9770E;
    classDef external fill:#E5E8E8,stroke:#616A6B,color:#2C3E50;
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