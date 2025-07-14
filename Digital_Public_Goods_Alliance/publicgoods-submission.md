---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/DPGAlliance/publicgoods-submission
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




# publicgoods-submission repo project
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
title: "publicgoods-submission repo project"
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
    %% Client Tier
    subgraph "Client Tier"
        direction TB
        UserAgent["Browser / User Agent"]:::client
        SubmissionPage["Submission Form Page<br>(SSR/SSG)"]:::frontend
        StaticAssets["Static Assets<br>(JS, CSS, images)"]:::assets
    end

    %% Presentation & Application Tier
    subgraph "Presentation & Application Tier"
        direction TB
        NextJS["Next.js Frontend<br>(SSR/SSG & CSR)"]:::frontend
        FormRenderer["Data Driven Forms Renderer"]:::component
        APIRoute["pages/api/submit handler"]:::api
    end

    %% Data & Integration Tier
    subgraph "Data & Integration Tier"
        direction TB
        SchemaStore["JSON Schema Store"]:::data
        ExternalRegistry["External Registry Service / DB"]:::cloud
    end

    %% Infrastructure & DevOps
    subgraph "Infrastructure & DevOps"
        direction TB
        Vercel["Vercel Platform"]:::cloud
        GitModules["Git Submodule<br>(shared schema)"]:::data
        NextConfig["next.config.js"]:::config
        PackageJSON["package.json"]:::config
        TSConfig["tsconfig.json"]:::config
        Docs["Project Docs & Governance"]:::docs
    end

    %% Connections
    UserAgent -->|"GET /submission"| Vercel
    Vercel -->|"edge cache"| StaticAssets
    Vercel -->|"SSR/SSG request"| NextJS
    NextJS -->|"loads JSON schema"| SchemaStore
    NextJS -->|"renders page"| SubmissionPage
    SubmissionPage -->|"client hydration"| FormRenderer
    FormRenderer -->|"renders dynamic form"| UserAgent
    UserAgent -->|"POST JSON payload"| APIRoute
    APIRoute -->|"forwards nomination data"| ExternalRegistry
    ExternalRegistry -->|"response"| APIRoute
    APIRoute -->|"success/failure"| UserAgent

    Vercel --> NextJS
    Vercel --> APIRoute
    GitModules --- SchemaStore

    %% Click Events
    click NextJS "https://github.com/dpgalliance/publicgoods-submission/tree/main/webapp/pages"
    click SubmissionPage "https://github.com/dpgalliance/publicgoods-submission/blob/main/webapp/pages/submission.js"
    click FormRenderer "https://github.com/dpgalliance/publicgoods-submission/blob/main/webapp/components/FormRenderer.jsx"
    click SchemaStore "https://github.com/dpgalliance/publicgoods-submission/blob/main/webapp/schemas/schema.js"
    click APIRoute "https://github.com/dpgalliance/publicgoods-submission/blob/main/webapp/pages/api/submit.js"
    click StaticAssets "https://github.com/dpgalliance/publicgoods-submission/tree/main/webapp/public"
    click NextConfig "https://github.com/dpgalliance/publicgoods-submission/blob/main/webapp/next.config.js"
    click PackageJSON "https://github.com/dpgalliance/publicgoods-submission/blob/main/webapp/package.json"
    click TSConfig "https://github.com/dpgalliance/publicgoods-submission/blob/main/webapp/tsconfig.json"
    click GitModules "https://github.com/dpgalliance/publicgoods-submission/blob/main/.gitmodules"
    click Docs "https://github.com/dpgalliance/publicgoods-submission/blob/main/README.md"

    %% Styles
    classDef client fill:#a2d2ff,stroke:#0165a5,color:#000
    classDef frontend fill:#ffcad4,stroke:#ff0054,color:#000
    classDef component fill:#bde0fe,stroke:#0077b6,color:#000
    classDef api fill:#caf0f8,stroke:#0096c7,color:#000
    classDef data fill:#ffe5b4,stroke:#ff9900,color:#000
    classDef cloud fill:#e0e0e0,stroke:#717171,color:#000
    classDef assets fill:#d8f3dc,stroke:#2d6a4f,color:#000
    classDef config fill:#f0efeb,stroke:#a8a8a8,color:#000
    classDef docs fill:#f7d6bf,stroke:#d35400,color:#000

```

-----

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