---
created: 2025-06-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/OWASP/CheatSheetSeries
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




# CheatSheetSeries repo project
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
title: "CheatSheetSeries repo project"
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
    %% Authoring Layer
    subgraph "Authoring (Content Layer)"
        direction TB
        CSrc["Markdown Sources\n(cheatsheets/, cheatsheets_draft/)"]:::source
        Assets["Assets\n(assets/)"]:::source
        Templates["Templates\n(New_CheatSheet.md)"]:::source
        Landing["Landing Pages\n(Index*.md)"]:::source
        GitHub["GitHub Repo"]:::external
        CSrc --> GitHub
        Assets --> GitHub
        Templates --> GitHub
        Landing --> GitHub
    end

    %% CI/CD Layer
    subgraph "CI/CD Pipeline"
        direction TB
        MDLint["md-lint\n(.github/workflows/md_lint_check.yml)"]:::build
        LinkCheck["link-check\n(.github/workflows/md-link-check.yml)"]:::build
        IdentifyIssues["identify old issues/PRs\n(.github/workflows/identify-old-issues-and-pr.yml)"]:::build
        BuildDeploy["build & deploy\n(.github/workflows/build-and-deploy-website.yml)"]:::build
        Publish["publishing check\n(.github/workflows/publishing-check.yml)"]:::build
        CI["CI Runner"]:::build
        GitHub --> MDLint
        GitHub --> LinkCheck
        GitHub --> IdentifyIssues
        GitHub --> BuildDeploy
        GitHub --> Publish
        MDLint --> CI
        LinkCheck --> CI
        IdentifyIssues --> CI
        BuildDeploy --> CI
        Publish --> CI
    end

    %% Build Layer
    subgraph "Build Layer"
        direction TB
        Makefile["Makefile"]:::build
        MkdocsConfig["mkdocs.yml"]:::build
        Reqs["requirements.txt"]:::build
        PackageJSON["package.json"]:::build
        ShellGenSite["Generate_Site.sh"]:::build
        ShellGenMk["Generate_Site_mkDocs.sh"]:::build
        LinkScript["Apply_Link_Check.sh"]:::build
        TOC["Generate CheatSheets TOC"]:::build
        RSS["Generate RSS Feed"]:::build
        TechJSON["Generate Technologies JSON"]:::build
        UpdateIdx["Update CheatSheets Index"]:::build
        IdentifyOld["Identify Old Issue And PR"]:::build
        Shell404["404 Page"]:::build
        MkDocsBuild["MkDocs Build Engine"]:::build
        CI --> Makefile
        CI --> MkdocsConfig
        CI --> Reqs
        CI --> PackageJSON
        CI --> ShellGenSite
        CI --> ShellGenMk
        CI --> LinkScript
        CI --> TOC
        CI --> RSS
        CI --> TechJSON
        CI --> UpdateIdx
        CI --> IdentifyOld
        CI --> Shell404
        Makefile --> MkDocsBuild
        MkdocsConfig --> MkDocsBuild
        Reqs --> MkDocsBuild
        PackageJSON --> MkDocsBuild
        ShellGenSite --> MkDocsBuild
        ShellGenMk --> MkDocsBuild
        LinkScript --> MkDocsBuild
        TOC --> MkDocsBuild
        RSS --> MkDocsBuild
        TechJSON --> MkDocsBuild
        UpdateIdx --> MkDocsBuild
        IdentifyOld --> MkDocsBuild
        Shell404 --> MkDocsBuild
    end

    %% Deployment Layer
    subgraph "Delivery & Deployment"
        direction TB
        StaticOut["Static Site Artifact\n(bundle.zip)"]:::deploy
        DockerImage["Docker Image"]:::deploy
        DockerReg["Docker Registry"]:::deploy
        ContainerRun["Container Runtime"]:::deploy
        StaticHost["Static Host\n(cheatsheetseries.owasp.org)"]:::deploy
        LocalVS["VSCode Config"]:::build
        LinkConfig["Link-Check Config\n(markdown-link-check-config.json)"]:::build
        LocalPreview["Local Preview\n(make serve / docker run)"]:::deploy
        MkDocsBuild --> StaticOut
        MkDocsBuild --> DockerImage
        DockerImage --> DockerReg
        DockerReg --> ContainerRun
        ContainerRun --> StaticHost
        StaticOut --> StaticHost
        Makefile --> LocalPreview
        DockerImage --> LocalPreview
        LocalVS --> LocalPreview
        LinkConfig --> MkDocsBuild
    end

    %% Consumption Layer
    subgraph "Consumption"
        direction TB
        EndUser["End User"]:::external
        StaticHost --> EndUser
    end

    %% External Services
    Slack["Slack & CC Badge"]:::external

    %% Click Events
    click CSrc "https://github.com/owasp/cheatsheetseries/tree/master//cheatsheets/"
    click Assets "https://github.com/owasp/cheatsheetseries/tree/master//assets/"
    click Templates "https://github.com/owasp/cheatsheetseries/blob/master//templates/New_CheatSheet.md"
    click Landing "https://github.com/owasp/cheatsheetseries/blob/master//Index.md"
    click GitHub "https://github.com/owasp/cheatsheetseries/tree/master//"
    click MDLint "https://github.com/owasp/cheatsheetseries/blob/master//.github/workflows/md_lint_check.yml"
    click LinkCheck "https://github.com/owasp/cheatsheetseries/blob/master//.github/workflows/md-link-check.yml"
    click IdentifyIssues "https://github.com/owasp/cheatsheetseries/blob/master//.github/workflows/identify-old-issues-and-pr.yml"
    click BuildDeploy "https://github.com/owasp/cheatsheetseries/blob/master//.github/workflows/build-and-deploy-website.yml"
    click Publish "https://github.com/owasp/cheatsheetseries/blob/master//.github/workflows/publishing-check.yml"
    click Makefile "https://github.com/owasp/cheatsheetseries/tree/master//Makefile"
    click MkdocsConfig "https://github.com/owasp/cheatsheetseries/blob/master//mkdocs.yml"
    click Reqs "https://github.com/owasp/cheatsheetseries/blob/master//requirements.txt"
    click PackageJSON "https://github.com/owasp/cheatsheetseries/blob/master//package.json"
    click ShellGenSite "https://github.com/owasp/cheatsheetseries/blob/master//scripts/Generate_Site.sh"
    click ShellGenMk "https://github.com/owasp/cheatsheetseries/blob/master//scripts/Generate_Site_mkDocs.sh"
    click LinkScript "https://github.com/owasp/cheatsheetseries/blob/master//scripts/Apply_Link_Check.sh"
    click TOC "https://github.com/owasp/cheatsheetseries/blob/master//scripts/Generate_CheatSheets_TOC.py"
    click RSS "https://github.com/owasp/cheatsheetseries/blob/master//scripts/Generate_RSS_Feed.py"
    click TechJSON "https://github.com/owasp/cheatsheetseries/blob/master//scripts/Generate_Technologies_JSON.py"
    click UpdateIdx "https://github.com/owasp/cheatsheetseries/blob/master//scripts/Update_CheatSheets_Index.py"
    click IdentifyOld "https://github.com/owasp/cheatsheetseries/blob/master//scripts/Identify_Old_Issue_And_PR.py"
    click Shell404 "https://github.com/owasp/cheatsheetseries/blob/master//scripts/404.html"
    click LinkConfig "https://github.com/owasp/cheatsheetseries/blob/master//markdown-link-check-config.json"
    click Dockerfile "https://github.com/owasp/cheatsheetseries/tree/master//Dockerfile"
    click LocalVS "https://github.com/owasp/cheatsheetseries/blob/master//Project.code-workspace"

    %% Styles
    classDef source fill:#BBDEFB,stroke:#1E88E5,stroke-width:1px
    classDef build fill:#C8E6C9,stroke:#43A047,stroke-width:1px
    classDef deploy fill:#FFE0B2,stroke:#FB8C00,stroke-width:1px
    classDef external fill:#E1BEE7,stroke:#8E24AA,stroke-width:1px

```

-----
xx
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