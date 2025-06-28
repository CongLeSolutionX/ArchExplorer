---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/zket-core-program
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExY3Ayb3VlMDdjM3VuZ29pOGdydDRoYTMwNzRjbHg3bGhxNjllNzRncSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/ZNgxWr6PYCg8DVuZVh/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# zket-core-program repo project
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
title: "zket-core-program repo project"
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
    %% Users
    Contributor["Contributor"]:::user
    Student["Student/Reader Browser"]:::user

    %% Repository
    Repo["GitHub Repository"]:::system

    %% Content Layer
    subgraph "Content Layer"
        direction TB
        C2023["2023 Curriculum (Markdown)"]:::content
        A2023Ans["2023 Answers (Markdown)"]:::content
        C2024["2024 Curriculum (Markdown)"]:::content
        Assets2024["2024 Assets"]:::content
        ContribGuide["2024 Contributions Guide"]:::content
        Placeholder2025["2025 Curriculum Placeholder"]:::content
    end

    %% Collaboration & VCS
    subgraph "Collaboration & VCS"
        direction TB
        IssueTemp["Issue Templates"]:::collab
        PRTemp["Pull Request Template"]:::collab
        Gitignore[".gitignore"]:::collab
        Readme["README.md"]:::collab
    end

    %% CI/CD Pipeline
    subgraph "CI/CD Pipeline"
        direction TB
        Actions["GitHub Actions"]:::ci
        SSG["Static Site Generator"]:::ci
    end

    %% Hosting
    Pages["GitHub Pages (Hosting)"]:::hosting

    %% Relationships
    Contributor -->|fork/branch & commit| Repo
    Contributor -->|open PR| PRTemp
    Student -->|browse site| Pages
    Student -->|open issue| IssueTemp

    C2023 --> Repo
    A2023Ans --> Repo
    C2024 --> Repo
    Assets2024 --> Repo
    ContribGuide --> Repo
    Placeholder2025 --> Repo

    IssueTemp --> Repo
    PRTemp --> Repo
    Gitignore --> Repo
    Readme --> Repo

    Repo -->|on merge trigger CI| Actions
    Actions -->|run checks & build| SSG
    SSG -->|generate static site| Pages
    Pages -->|serve content| Student

    %% Click Events
    click C2023 "https://github.com/ethereum/zket-core-program/tree/main/2023/"
    click A2023Ans "https://github.com/ethereum/zket-core-program/tree/main/2023/answers/"
    click C2024 "https://github.com/ethereum/zket-core-program/tree/main/2024/"
    click Assets2024 "https://github.com/ethereum/zket-core-program/tree/main/2024/assets/"
    click ContribGuide "https://github.com/ethereum/zket-core-program/blob/main/2024/contributions/README.md"
    click Placeholder2025 "https://github.com/ethereum/zket-core-program/blob/main/2025/README.md"
    click IssueTemp "https://github.com/ethereum/zket-core-program/blob/main/.github/ISSUE_TEMPLATE/standard-issue-template-.md"
    click PRTemp "https://github.com/ethereum/zket-core-program/blob/main/.github/pull_request_template.md"
    click Gitignore "https://github.com/ethereum/zket-core-program/blob/main/.gitignore"
    click Readme "https://github.com/ethereum/zket-core-program/blob/main/README.md"

    %% Styles
    classDef content fill:#E0F7FA,stroke:#006064,color:#004D40
    classDef collab fill:#ECEFF1,stroke:#90A4AE,color:#37474F
    classDef ci fill:#E8F5E9,stroke:#388E3C,color:#1B5E20,stroke-dasharray: 5 5
    classDef hosting fill:#FFF8E1,stroke:#F9A825,color:#FF6F00
    classDef system fill:#BBDEFB,stroke:#1976D2,color:#0D47A1
    classDef user fill:#F3E5F5,stroke:#8E24AA,color:#4A148C,stroke-width:2px
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
