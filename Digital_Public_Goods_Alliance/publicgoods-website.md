---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/DPGAlliance/publicgoods-website
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




# publicgoods-website repo project
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
title: "publicgoods-website repo project"
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
    %% Backend Layer
    subgraph "Backend Layer"
        direction TB
        WP_CMS["Offline WordPress CMS"]:::backend
        CandidatesRepo["Candidates JSON Repo"]:::repo
    end

    %% Processing Layer
    subgraph "Processing Layer"
        direction TB
        ScriptEngine["Script Engine (SSG)"]:::processing
    end

    %% Static Site Repo
    subgraph "Static Site Repo"
        direction TB
        StaticRepo["Static Website Repository"]:::repo
        subgraph "Micro-Frontends (React SPAs)"
            direction TB
            MapSPA["Map SPA"]:::spa
            RegistrySPA["Registry SPA"]:::spa
            EligibilitySPA["Eligibility SPA"]:::spa
            RoadmapSPA["Roadmap SPA"]:::spa
        end
    end

    %% CI/CD & Hosting
    subgraph "CI/CD & Hosting"
        direction TB
        GitHubActions["GitHub Actions"]:::hosting
        GitHubPagesCDN["GitHub Pages / CDN"]:::hosting
    end

    %% Client Layer
    Browser["End Users (Browser)"]:::client

    %% Flows
    WP_CMS -->|"Content Pull"| ScriptEngine
    CandidatesRepo -->|"JSON Pull"| ScriptEngine
    ScriptEngine -->|"Generates Static HTML"| StaticRepo
    StaticRepo -->|"CI Push"| GitHubActions
    GitHubActions -->|"Deploy"| GitHubPagesCDN
    Browser -->|"Request Pages"| GitHubPagesCDN
    GitHubPagesCDN -->|"Serve Assets"| Browser

    %% Click Events
    click WP_CMS "https://github.com/dpgalliance/publicgoods-website/tree/main/wp-content/"
    click MapSPA "https://github.com/dpgalliance/publicgoods-website/tree/main/map/static/js/"
    click RegistrySPA "https://github.com/dpgalliance/publicgoods-website/tree/main/registry/static/js/"
    click EligibilitySPA "https://github.com/dpgalliance/publicgoods-website/tree/main/eligibility/static/js/"
    click RoadmapSPA "https://github.com/dpgalliance/publicgoods-website/tree/main/roadmap/static/js/"

    %% Styles
    classDef backend fill:#ffdddd,stroke:#aa3333,stroke-width:2px
    classDef repo fill:#ddffdd,stroke:#33aa33,stroke-width:2px
    classDef processing fill:#ddddff,stroke:#3333aa,stroke-width:2px
    classDef hosting fill:#fff2cc,stroke:#aa7700,stroke-width:2px
    classDef client fill:#f0f0f0,stroke:#666666,stroke-width:2px
    classDef spa fill:#ddf0ff,stroke:#3399cc,stroke-width:2px
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