---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/electron/rfcs
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




# rfcs repo project
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
title: "rfcs repo project"
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
    %% Actors
    subgraph "Actors"
        Contributor("Contributor"):::actor
        Maintainers("Maintainers / API WG"):::actor
    end

    %% External Repo
    ElectronRepo["Electron/electron Repo"]:::repo

    %% RFC Repository
    subgraph "RFC Repository"
        GitHubConfig[".github/"]:::service
        subgraph ".github"
            Workflow["semantic.yml"]:::service
            CodeOwners["CODEOWNERS"]:::service
        end
        Template["0000-template.md"]:::repo
        TextDir["text/"]:::repo
        Example0004["0004-api-history-schema.md"]:::repo
        Example0008["0008-preload-realm.md"]:::repo
        Example0012["0012-corner-smoothing.md"]:::repo
        Example0015["0015-hyphenation-data-api.md"]:::repo
        ImagesDir["images/"]:::repo
        README["README.md"]:::repo
        LICENSE["LICENSE.md"]:::repo
    end

    %% Lifecycle States
    subgraph "RFC Lifecycle States"
        Proposed["Proposed"]:::state
        Pending["Pending Comment"]:::state
        Active["Active"]:::state
        Completed["Completed"]:::state
        Declined["Declined"]:::state
        Abandoned["Abandoned"]:::state
    end

    %% Flow
    Contributor -->|"forks repo"| GitHubConfig
    Contributor -->|"copy template\ncreate RFC"| Template
    Template -->|creates| TextDir
    TextDir -->|add new RFC file| Example0004
    TextDir --> Example0008
    TextDir --> Example0012
    TextDir --> Example0015
    Example0004 -->|"open PR"| GitHubConfig
    GitHubConfig -->|triggers| Workflow
    GitHubConfig -->|triggers| CodeOwners
    Workflow -->|"CI status"| Maintainers
    CodeOwners -->|"request review"| Maintainers
    Maintainers -->|"review & label"| Proposed
    Proposed -->|"2-week comment period"| Pending
    Pending -->|"consensus"| Active
    Proposed -->|"no response"| Abandoned
    Proposed -->|"rejected"| Declined
    Pending -->|"rejected"| Declined
    Active -->|"implementation PR"| ElectronRepo
    ElectronRepo -->|"merge impl PR"| Completed
    Active -->|"rejected"| Declined

    %% Assets & Docs
    ImagesDir -->|assets| TextDir
    README -->|docs process| Proposed
    LICENSE -->|repo license| GitHubConfig

    %% Click Events
    click Workflow "https://github.com/electron/rfcs/blob/main/.github/workflows/semantic.yml"
    click CodeOwners "https://github.com/electron/rfcs/tree/main/.github/CODEOWNERS"
    click Template "https://github.com/electron/rfcs/blob/main/0000-template.md"
    click TextDir "https://github.com/electron/rfcs/tree/main/text/"
    click Example0004 "https://github.com/electron/rfcs/blob/main/text/0004-api-history-schema.md"
    click Example0008 "https://github.com/electron/rfcs/blob/main/text/0008-preload-realm.md"
    click Example0012 "https://github.com/electron/rfcs/blob/main/text/0012-corner-smoothing.md"
    click Example0015 "https://github.com/electron/rfcs/blob/main/text/0015-hyphenation-data-api.md"
    click ImagesDir "https://github.com/electron/rfcs/tree/main/images/"
    click README "https://github.com/electron/rfcs/blob/main/README.md"
    click LICENSE "https://github.com/electron/rfcs/blob/main/LICENSE.md"
    click GitHubConfig "https://github.com/electron/rfcs/tree/main/.github/"

    %% Styles
    classDef actor fill:#f9f,stroke:#333,stroke-width:1px
    classDef service fill:#cff,stroke:#333,stroke-width:1px
    classDef repo fill:#ccf,stroke:#333,stroke-width:1px
    classDef state fill:#fcf,stroke:#333,stroke-width:1px

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