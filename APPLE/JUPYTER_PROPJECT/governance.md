---
created: 2025-06-29 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/jupyter/governance
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




# governance repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for 👨‍🎓 <ins>educational purposes</ins> 👨‍🎓 (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), 📖 <ins> personal study </ins> 📖, and 🔖 <ins> technical reference </ins> 🔖.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>



---

```mermaid
---
title: "governance repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright © 2025 Cong Le. All Rights Reserved."
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
flowchart LR
    %% Developer and Local Build
    Dev["Developer"]:::user
    LocalBuild["Local Build & Preview"]:::build
    Dev -->|"jupyter-book build ."| LocalBuild
    LocalBuild --> JBCLI

    %% Source Repository
    subgraph "GitHub Repository" 
        direction LR
        RepoContent["Markdown Content"]:::content
        RepoConfig["_config.yml & _toc.yml"]:::config
        RepoReq["requirements.txt"]:::config
        subgraph "CI/CD Workflows"
            direction TB
            BuildWF[".github/workflows/build.yml"]:::build
            DeployWF[".github/workflows/deploy.yml"]:::deploy
        end
        RepoMeta["README.md & LICENSE.md"]:::config
        RepoScripts["elections/process-votes.py"]:::config
        RepoPR[".github/PULL_REQUEST_TEMPLATE"]:::config
    end

    %% Expand Markdown Content
    subgraph "Markdown Content" 
        direction LR
        CHAR["charters/"]:::content
        COND["conduct/"]:::content
        ELEC["elections/"]:::content
        ARCH["archive/"]:::content
        BMEC["bootstrapping_executive_council.md"]:::content
        BMSSC["bootstrapping_subproject_councils.md"]:::content
        CBWG["communitybuildingworkinggroup.md"]:::content
        DM["decision_making.md"]:::content
        DC["distinguished_contributors.md"]:::content
        EC["executive_council.md"]:::content
        INTRO["intro.md"]:::content
        JF["jupyter_foundation.md"]:::content
        LP["linux-proposal.md"]:::content
        LSCAWG["list_of_standing_committees_and_working_groups.md"]:::content
        LOSP["list_of_subprojects.md"]:::content
        NEWSP["newsubprojects.md"]:::content
        OVW["overview.md"]:::content
        PAPERS["papers.md"]:::content
        PEOPLE["people.md"]:::content
        LICENSEMD["projectlicense.md"]:::content
        SSC["software_steering_council.md"]:::content
        SSWP["software_subprojects.md"]:::content
        SCWG["standing_committees_and_working_groups.md"]:::content
        TM["trademarks.md"]:::content
    end

    %% CI/CD and Build
    BuildWF -->|"on: push to main"| CI["CI Build Action"]:::build
    CI -->|"pip install & jupyter-book build"| JBCLI["Jupyter Book CLI"]:::build
    JBCLI -->|"generates HTML in _build/html"| HTML["Static HTML"]:::build
    HTML --> DeployWF
    DeployWF -->|"push to gh-pages"| Pages["GitHub Pages Hosting"]:::hosting
    Pages -->|"serves site"| User["End User Browser"]:::user

    %% Developer push to repo
    Dev -->|"push to main"| RepoContent
    Dev --> RepoConfig
    Dev --> RepoReq
    Dev --> RepoMeta
    Dev --> RepoScripts
    Dev --> RepoPR

    %% Local build flows into Jupyter Book CLI
    LocalBuild --> JBCLI

    %% Styles
    classDef content fill:#FFEFD5,stroke:#333,stroke-width:1px
    classDef config fill:#E6E6FA,stroke:#333,stroke-width:1px
    classDef build fill:#D3E4CD,stroke:#333,stroke-width:1px
    classDef deploy fill:#FADADD,stroke:#333,stroke-width:1px
    classDef hosting fill:#CFE0E8,stroke:#333,stroke-width:1px
    classDef user fill:#FFFACD,stroke:#333,stroke-width:1px

    %% Click Events for component mappings
    click CHAR "https://github.com/jupyter/governance/tree/main/charters/"
    click COND "https://github.com/jupyter/governance/tree/main/conduct/"
    click ELEC "https://github.com/jupyter/governance/tree/main/elections/"
    click ARCH "https://github.com/jupyter/governance/tree/main/archive/"
    click BMEC "https://github.com/jupyter/governance/blob/main/bootstrapping_executive_council.md"
    click BMSSC "https://github.com/jupyter/governance/blob/main/bootstrapping_subproject_councils.md"
    click CBWG "https://github.com/jupyter/governance/blob/main/communitybuildingworkinggroup.md"
    click DM "https://github.com/jupyter/governance/blob/main/decision_making.md"
    click DC "https://github.com/jupyter/governance/blob/main/distinguished_contributors.md"
    click EC "https://github.com/jupyter/governance/blob/main/executive_council.md"
    click INTRO "https://github.com/jupyter/governance/blob/main/intro.md"
    click JF "https://github.com/jupyter/governance/blob/main/jupyter_foundation.md"
    click LP "https://github.com/jupyter/governance/blob/main/linux-proposal.md"
    click LSCAWG "https://github.com/jupyter/governance/blob/main/list_of_standing_committees_and_working_groups.md"
    click LOSP "https://github.com/jupyter/governance/blob/main/list_of_subprojects.md"
    click NEWSP "https://github.com/jupyter/governance/blob/main/newsubprojects.md"
    click OVW "https://github.com/jupyter/governance/blob/main/overview.md"
    click PAPERS "https://github.com/jupyter/governance/blob/main/papers.md"
    click PEOPLE "https://github.com/jupyter/governance/blob/main/people.md"
    click LICENSEMD "https://github.com/jupyter/governance/blob/main/projectlicense.md"
    click SSC "https://github.com/jupyter/governance/blob/main/software_steering_council.md"
    click SSWP "https://github.com/jupyter/governance/blob/main/software_subprojects.md"
    click SCWG "https://github.com/jupyter/governance/blob/main/standing_committees_and_working_groups.md"
    click TM "https://github.com/jupyter/governance/blob/main/trademarks.md"
    click RepoConfig "https://github.com/jupyter/governance/blob/main/_config.yml"
    click RepoConfig "https://github.com/jupyter/governance/blob/main/_toc.yml"
    click RepoReq "https://github.com/jupyter/governance/blob/main/requirements.txt"
    click BuildWF "https://github.com/jupyter/governance/blob/main/.github/workflows/build.yml"
    click DeployWF "https://github.com/jupyter/governance/blob/main/.github/workflows/deploy.yml"
    click RepoMeta "https://github.com/jupyter/governance/blob/main/README.md"
    click RepoMeta "https://github.com/jupyter/governance/blob/main/LICENSE.md"
    click RepoScripts "https://github.com/jupyter/governance/blob/main/elections/process-votes.py"
    click RepoPR "https://github.com/jupyter/governance/blob/main/.github/PULL_REQUEST_TEMPLATE/pull_request_template.md"
    click RepoPR "https://github.com/jupyter/governance/blob/main/.github/PULL_REQUEST_TEMPLATE/standingcommittee.md"
    click RepoPR "https://github.com/jupyter/governance/blob/main/.github/PULL_REQUEST_TEMPLATE/workinggroup.md"

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
    

  Closing_quote ~~~ My_Meme
    
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