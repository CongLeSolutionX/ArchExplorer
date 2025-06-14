---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/filecoin-project/FIPs
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




# FIPs repo project
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
title: "FIPs repo project"
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
    Authors["Authors"]:::actor
    Reviewers["Reviewers & Stewards"]:::actor

    %% Subgraph: Content Authoring
    subgraph "Content Authoring"
        direction TB
        FIPS["FIPS Directory"]:::content
        FRCs["FRCs Directory"]:::content
        Templates["Proposal Template"]:::content
        Calls["Community Call Notes"]:::content
        Resources["Supplementary Resources"]:::content
        PRTemplate["Pull Request Template"]:::process
        README["README.md"]:::content
        Mission["mission.md"]:::content
        Proposing["proposing.md"]:::content
        Funding["FUNDING.json"]:::content
        Codeowners["CODEOWNERS"]:::content
        Gitignore[".gitignore"]:::content
    end

    %% Subgraph: CI/CD Pipeline
    subgraph "CI/CD Pipeline"
        direction TB
        MainWF["Main Workflow (main.yml)"]:::process
        TestWF["Test Workflow (test.yml)"]:::process
        LabelerScript["GitHub Labeler Script"]:::process
        LabelerTests["Labeler Test Suite"]:::process
        Requirements["Python Dependencies (.txt)"]:::process
    end

    %% Subgraph: Governance Review
    subgraph "Governance Review"
        direction TB
        ReviewPR["Review & Merge PR"]:::process
    end

    %% Subgraph: External Integration
    subgraph "External Integration"
        direction TB
        GitHubHost["GitHub Hosting"]:::external
        ActionsRunner["Actions Runner"]:::external
        SpecsRepo["External Specs Repo"]:::external
    end

    %% Connections
    Authors -->|"submit PR"| FIPS
    Authors --> Templates
    FIPS & FRCs & Templates -->|"include PR Template"| PRTemplate
    PRTemplate -->|"PR created in Repo"| GitHubHost
    GitHubHost -->|"trigger workflows"| ActionsRunner
    ActionsRunner --> MainWF
    ActionsRunner --> TestWF
    MainWF -->|"invoke labeler"| LabelerScript
    TestWF -->|"run tests"| LabelerTests
    LabelerScript --> Requirements
    ActionsRunner -->|"report status"| GitHubHost
    GitHubHost --> Reviewers
    Reviewers -->|"merge PR"| GitHubHost
    GitHubHost -->|"sync on merge"| SpecsRepo
    Reviewers --> Calls
    Calls --> Resources

    %% Click Events
    click FIPS "https://github.com/filecoin-project/fips/tree/master/FIPS/"
    click FRCs "https://github.com/filecoin-project/fips/tree/master/FRCs/"
    click Templates "https://github.com/filecoin-project/fips/blob/master/templates/template.md"
    click Calls "https://github.com/filecoin-project/fips/tree/master/Community Governance Calls/"
    click Resources "https://github.com/filecoin-project/fips/tree/master/resources/"
    click MainWF "https://github.com/filecoin-project/fips/blob/master/.github/workflows/main.yml"
    click TestWF "https://github.com/filecoin-project/fips/blob/master/.github/workflows/test.yml"
    click LabelerScript "https://github.com/filecoin-project/fips/blob/master/.github/workflows/githublabeler.py"
    click LabelerTests "https://github.com/filecoin-project/fips/blob/master/.github/workflows/test_githublabeler.py"
    click Requirements "https://github.com/filecoin-project/fips/blob/master/.github/workflows/requirements.txt"
    click PRTemplate "https://github.com/filecoin-project/fips/blob/master/.github/pull_request_template.md"
    click README "https://github.com/filecoin-project/fips/blob/master/README.md"
    click Mission "https://github.com/filecoin-project/fips/blob/master/mission.md"
    click Proposing "https://github.com/filecoin-project/fips/blob/master/proposing.md"
    click Funding "https://github.com/filecoin-project/fips/blob/master/FUNDING.json"
    click Codeowners "https://github.com/filecoin-project/fips/tree/master/CODEOWNERS"
    click Gitignore "https://github.com/filecoin-project/fips/blob/master/.gitignore"

    %% Styles
    classDef content fill:#D0E8FF,stroke:#009,stroke-width:1px
    classDef process fill:#DFFFE0,stroke:#080,stroke-width:1px
    classDef actor fill:#FFD8A8,stroke:#E67A00,stroke-width:1px
    classDef external fill:#EEEEEE,stroke:#666,stroke-width:1px
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