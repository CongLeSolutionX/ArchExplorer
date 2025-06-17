---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/github/training-kit
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


# training-kit repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


---

```mermaid
---
title: "training-kit repo project"
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
    %% Local Development Environment
    subgraph "Local Development"
        direction TB
        Dev["Developer"]:::tools
        BS["script/bootstrap"]:::tools
        NU["script/server"]:::tools
        RB["Ruby/Bundler"]:::tools
        NP["Node/npm"]:::tools
        JE["Jekyll Engine"]:::tools
        LS["Local Preview Server"]:::hosting
        Dev -->|"runs"| BS
        Dev -->|"runs"| NU
        BS -->|"installs gems"| RB
        BS -->|"installs npm deps"| NP
        NU -->|"starts"| LS
        RB -->|"provides Jekyll"| JE
        NP -->|"compiles SCSS"| JE
    end

    %% CI/CD Pipeline
    subgraph "CI/CD Pipeline" 
        direction TB
        Repo["GitHub Repo"]:::cicd
        WF[".github/workflows"]:::cicd
        QL["CodeQL Analysis"]:::cicd
        DR["Dependency Review"]:::cicd
        JB["Jekyll Build"]:::cicd
        Repo -->|"pushes"| WF
        WF --> QL
        WF --> DR
        WF --> JB
    end

    %% Build Pipeline
    subgraph "Automated Build"
        direction TB
        RB2["Ruby/Bundler"]:::tools
        NP2["Node/npm"]:::tools
        BS2["script/build"]:::tools
        PK["script/package"]:::tools
        JE2["Jekyll Engine"]:::tools
        RB2 --> JE2
        NP2 --> JE2
        BS2 --> JE2
        JE2 --> PK
    end

    %% Content Sources
    subgraph "Content (Markdown)" 
        direction TB
        DL["downloads/**"]:::content
        GG["git-guides/*.md"]:::content
        PG["_pages/404.md"]:::content
    end

    %% Templates & Includes
    subgraph "Templates & Includes"
        direction TB
        LO1["_layouts/cheat-sheet.html"]:::templates
        LO2["_layouts/default.html"]:::templates
        IN["_includes/*.html"]:::templates
    end

    %% Static Assets
    subgraph "Static Assets"
        direction TB
        SCSS["assets/_scss/*.scss"]:::templates
        CSS["assets/css/*.scss"]:::templates
        FN["assets/fonts/*"]:::templates
    end

    %% Jekyll Generation
    subgraph "Site Generation"
        direction TB
        JE3["Jekyll Engine"]:::tools
        OUT["_site Output"]:::hosting
        JE3 --> OUT
    end

    %% Hosting
    subgraph "Hosting"
        direction TB
        GP["GitHub Pages"]:::hosting
        HS["Static HTTP Server"]:::hosting
        OUT --> GP
        OUT --> HS
        CNAME["CNAME"]:::hosting
    end

    %% Flows into Jekyll
    RB2 --> JE3
    NP2 --> JE3
    LO1 --> JE3
    LO2 --> JE3
    IN --> JE3
    DL --> JE3
    GG --> JE3
    PG --> JE3
    SCSS --> JE3
    CSS --> JE3
    FN --> JE3

    %% Version Config & Metadata
    subgraph "Configuration & Metadata"
        direction TB
        GI[".gitignore"]:::cicd
        CFG["_config.yml"]:::templates
        GMB["Gemfile"]:::tools
        GML["Gemfile.lock"]:::tools
        PKJ["package.json"]:::tools
        PKL["package-lock.json"]:::tools
        GI
        CFG
        GMB
        GML
        PKJ
        PKL
    end

    %% Developer push to repo
    Dev -->|"git push"| Repo

    click WF "https://github.com/github/training-kit/tree/main/.github/workflows"
    click QL "https://github.com/github/training-kit/blob/main/.github/workflows/codeql.yml"
    click DR "https://github.com/github/training-kit/blob/main/.github/workflows/dependency-review.yml"
    click JB "https://github.com/github/training-kit/blob/main/.github/workflows/jekyll.yml"
    click GI "https://github.com/github/training-kit/blob/main/.gitignore"
    click CFG "https://github.com/github/training-kit/blob/main/_config.yml"
    click GMB "https://github.com/github/training-kit/tree/main/Gemfile"
    click GML "https://github.com/github/training-kit/blob/main/Gemfile.lock"
    click PKJ "https://github.com/github/training-kit/blob/main/package.json"
    click PKL "https://github.com/github/training-kit/blob/main/package-lock.json"
    click BS "https://github.com/github/training-kit/tree/main/script/bootstrap"
    click BS2 "https://github.com/github/training-kit/tree/main/script/build"
    click NU "https://github.com/github/training-kit/tree/main/script/server"
    click PK "https://github.com/github/training-kit/tree/main/script/package"
    click LO1 "https://github.com/github/training-kit/blob/main/_layouts/cheat-sheet.html"
    click LO2 "https://github.com/github/training-kit/blob/main/_layouts/default.html"
    click IN "https://github.com/github/training-kit/tree/main/_includes/"
    click PG "https://github.com/github/training-kit/blob/main/_pages/404.md"
    click DL "https://github.com/github/training-kit/tree/main/downloads/"
    click GG "https://github.com/github/training-kit/tree/main/git-guides/"
    click SCSS "https://github.com/github/training-kit/tree/main/assets/_scss/"
    click CSS "https://github.com/github/training-kit/tree/main/assets/css/"
    click FN "https://github.com/github/training-kit/tree/main/assets/fonts/"
    click CNAME "https://github.com/github/training-kit/tree/main/CNAME"

    classDef tools fill:#ADD8E6,stroke:#000
    classDef content fill:#90EE90,stroke:#000
    classDef templates fill:#FFA500,stroke:#000
    classDef cicd fill:#DDA0DD,stroke:#000
    classDef hosting fill:#D8BFD8,stroke:#000

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
 
  Closing_quote ~~~ My_Meme

  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

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