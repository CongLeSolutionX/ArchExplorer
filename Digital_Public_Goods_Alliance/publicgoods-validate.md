---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/DPGAlliance/publicgoods-validate
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




# publicgoods-validate repo project
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



---

```mermaid
---
title: "publicgoods-validate repo project"
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
  %% Root Repository
  subgraph "Root Repository"
    GitModules[".gitmodules"]:::repo
    GitModules --> WebappSubmodule["webapp submodule"]:::repo
  end

  %% Webapp Repository
  subgraph "Webapp Repository"
    PackageJSON["package.json"]:::repo
    PublicAssets["public/ (static assets & HTML)"]:::frontend
    SrcCode["src/ (SPA source code)"]:::frontend
    Functions["functions/ (serverless/API functions)"]:::api
    EnvConfig[".env"]:::repo
    Scripts["scripts/"]:::repo
    CIWorkflows[".github/workflows/ (CI/CD pipelines)"]:::repo
    HostingConfig["netlify.toml / vercel.json"]:::repo

    WebappSubmodule --> PackageJSON
    WebappSubmodule --> PublicAssets
    WebappSubmodule --> SrcCode
    WebappSubmodule --> Functions
    WebappSubmodule --> EnvConfig
    WebappSubmodule --> Scripts
    WebappSubmodule --> CIWorkflows
    WebappSubmodule --> HostingConfig
  end

  %% CI/CD Pipeline
  subgraph "CI/CD Pipeline"
    GitHubActions["GitHub Actions"]:::external
    NetlifyDeploy["Netlify/Vercel Build & Deploy"]:::external
  end

  %% Cloud Infrastructure
  subgraph "Cloud Infrastructure"
    CDN["CDN (Netlify/Vercel)"]:::external
    Browser["Browser (SPA)"]:::frontend
    ReviewAPI["Review Submission Function"]:::api
    Database["Database (Firestore/Airtable)"]:::data
    AuthService["GitHub OAuth"]:::external
    NotificationSvc["Email/Webhooks"]:::external
  end

  %% Relationships
  PackageJSON & SrcCode & PublicAssets -->|"source code"| GitHubActions
  CIWorkflows -->|triggers| GitHubActions
  GitHubActions -->|build & deploy| NetlifyDeploy
  HostingConfig -->|configures| NetlifyDeploy
  NetlifyDeploy -->|deploys SPA| CDN

  Browser -->|fetch SPA| CDN
  Browser -->|submit form| ReviewAPI
  ReviewAPI -->|uses code from| Functions
  ReviewAPI -->|read/write data| Database
  ReviewAPI -->|authenticate users| AuthService
  ReviewAPI -->|send notifications| NotificationSvc

  %% Click Events
  click GitModules "https://github.com/dpgalliance/publicgoods-validate/blob/main//.gitmodules"
  click PackageJSON "https://github.com/dpgalliance/publicgoods-validate/blob/main//webapp/package.json"
  click PublicAssets "https://github.com/dpgalliance/publicgoods-validate/tree/main//webapp/public/"
  click SrcCode "https://github.com/dpgalliance/publicgoods-validate/tree/main//webapp/src/"
  click Functions "https://github.com/dpgalliance/publicgoods-validate/tree/main//webapp/functions/"
  click EnvConfig "https://github.com/dpgalliance/publicgoods-validate/blob/main//webapp/.env"
  click Scripts "https://github.com/dpgalliance/publicgoods-validate/tree/main//webapp/scripts/"
  click CIWorkflows "https://github.com/dpgalliance/publicgoods-validate/tree/main//webapp/.github/workflows/"
  click HostingConfig "https://github.com/dpgalliance/publicgoods-validate/blob/main//webapp/netlify.toml"
  click HostingConfig "https://github.com/dpgalliance/publicgoods-validate/blob/main//webapp/vercel.json"

  %% Styles
  classDef frontend fill:#cce5ff,stroke:#3399ff,color:#000;
  classDef api fill:#fff3cd,stroke:#ffcc00,color:#000;
  classDef data fill:#d4edda,stroke:#28a745,color:#000;
  classDef external fill:#e2e3e5,stroke:#6c757d,color:#000;
  classDef repo fill:#f8d7da,stroke:#dc3545,color:#000;

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