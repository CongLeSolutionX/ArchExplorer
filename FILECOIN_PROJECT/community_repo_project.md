---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/filecoin-project/community
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExMnF2dWN0czd0djAwaHhrMGFpbTB2cnFtdTgwaGNlZWJjY2I3aXhrYyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/b4R6VJ3y942mHySNta/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# community repo project
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
title: "community repo project"
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
    %% Contributors
    Contributors["Contributors"]:::external
    Contributors -->|"edit/add Markdown"| Repo

    %% Repository and Content
    subgraph "Markdown Content Repository" 
        direction TB
        CC["community-calls/"]:::repo
        PRJ["projects/"]:::repo
        POLL["polls/"]:::repo
        TPL["templates/"]:::repo
        IMG["images/"]:::repo
        SPBP["storage-provider-bounty-program/"]:::repo
        SPIC["storage-provider-incubation-center/"]:::repo
        SPWG["Storage Provider Working Group/"]:::repo
        FMM["filecoin-meetups.md"]:::repo
        MG["Meta Documentation & Governance"]:::repo
        MG --> READ["README.md"] 
        MG --> COC["CODE_OF_CONDUCT.md"]
        MG --> LIC1["LICENSE-APACHE"]
        MG --> LIC2["LICENSE-MIT"]
        MG --> SEC["SECURITY.md"]
        MG --> GIT[".gitignore"]
        MG --> CPY["COPYRIGHT"]
    end

    Repo["GitHub Repo"]:::repo
    Repo --> CC
    Repo --> PRJ
    Repo --> POLL
    Repo --> TPL
    Repo --> IMG
    Repo --> SPBP
    Repo --> SPIC
    Repo --> SPWG
    Repo --> FMM
    Repo --> MG

    %% CI/CD Pipeline
    subgraph "CI/CD Pipeline (GitHub Actions)" 
        direction TB
        Checkout["Checkout Code"]:::pipeline
        Build["Build Static Site"]:::pipeline
        Test["Test & Lint Markdown"]:::pipeline
        Deploy["Deploy to GitHub Pages"]:::pipeline
    end

    Repo -->|"push/PR triggers"| Checkout
    Checkout --> Build
    Build --> Test
    Test --> Deploy

    %% Hosting
    subgraph "Hosting & Delivery"
        direction TB
        Pages["GitHub Pages"]:::hosting
        CDN["CDN"]:::hosting
    end

    Deploy --> Pages
    Pages --> CDN
    CDN --> Browser

    %% Client
    Browser["Web Browser (User)"]:::client
    CDN --> Browser

    %% External Services
    subgraph "External Services" 
        direction TB
        Forum["Filecoin Community Forum"]:::external
        Slack["Slack"]:::external
        Disc["GitHub Discussions"]:::external
        Status["status.filecoin.io"]:::external
        Calendar["Google Calendar"]:::external
        YouTube["YouTube"]:::external
        Twitter["Twitter"]:::external
    end

    Browser -->|links/widgets| Forum
    Browser -->|links/widgets| Slack
    Browser -->|links/widgets| Disc
    Browser -->|links/widgets| Status
    Browser -->|calendar invites| Calendar
    Browser -->|embedded videos| YouTube
    Browser -->|social links| Twitter

    %% Click Events
    click CC "https://github.com/filecoin-project/community/tree/master/community-calls/"
    click PRJ "https://github.com/filecoin-project/community/tree/master/projects/"
    click POLL "https://github.com/filecoin-project/community/tree/master/polls/"
    click TPL "https://github.com/filecoin-project/community/tree/master/templates/"
    click IMG "https://github.com/filecoin-project/community/tree/master/images/"
    click SPBP "https://github.com/filecoin-project/community/blob/master/storage-provider-bounty-program/README.md"
    click SPIC "https://github.com/filecoin-project/community/blob/master/storage-provider-incubation-center/README.md"
    click SPWG "https://github.com/filecoin-project/community/blob/master/Storage Provider Working Group/README.md"
    click FMM "https://github.com/filecoin-project/community/blob/master/filecoin-meetups.md"
    click READ "https://github.com/filecoin-project/community/blob/master/README.md"
    click COC "https://github.com/filecoin-project/community/blob/master/CODE_OF_CONDUCT.md"
    click LIC1 "https://github.com/filecoin-project/community/tree/master/LICENSE-APACHE"
    click LIC2 "https://github.com/filecoin-project/community/tree/master/LICENSE-MIT"
    click SEC "https://github.com/filecoin-project/community/blob/master/SECURITY.md"
    click GIT "https://github.com/filecoin-project/community/blob/master/.gitignore"
    click CPY "https://github.com/filecoin-project/community/tree/master/COPYRIGHT"

    %% Styles
    classDef repo fill:#FFEBCC,stroke:#D26900;
    classDef pipeline fill:#CCE5FF,stroke:#004085;
    classDef hosting fill:#D4EDDA,stroke:#155724;
    classDef client fill:#E2E3E5,stroke:#6C757D;
    classDef external fill:#F8D7DA,stroke:#721C24;
```



---

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