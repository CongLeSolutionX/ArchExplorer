---
created: 2025-06-04 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/rust-lang/rfcs
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExb3p0eTVtY3BoNXdvY2psamtpaGx0MHZiNzZ4MGt1cjZ0cnhnYXZ0eiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/l0He4fJxPCbfqv7Xi/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----

# rfcs repo project
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
    %% Authoring
    Contributor["Contributor (Local Git)"]:::person

    %% Source Repository
    subgraph "Source Repository"
        Repo["GitHub Repository"]:::source
        Content["RFC Markdown (text/)"]:::source
        Config["Book Config (book.toml)"]:::source
        Workflow["CI Workflow (.github/workflows/deploy.yml)"]:::ci
        RenovateBotConf["Renovate Config (.github/renovate.json5)"]:::bot
        TriagebotConf["Triagebot Config (triagebot.toml)"]:::bot
        README["README.md & LICENSEs"]:::docs
    end

    %% CI/CD Pipeline
    subgraph "CI/CD Pipeline"
        CI["GitHub Actions CI"]:::ci
        GenerateScript["generate-book.py"]:::tool
        MdBook["mdBook"]:::tool
    end

    %% Deployment
    Artifacts["Static Site Artifacts"]:::artifact
    Pages["GitHub Pages Hosting"]:::host

    %% Relationships
    Contributor -->|"push/PR"| Repo
    RenovateBot(("Renovate Bot")):::bot -->|"scans repo"| Repo
    Repo -->|"triggers build"| CI
    Repo -->|"PR events"| Triagebot(("Triagebot")):::bot
    CI -->|"runs script"| GenerateScript
    GenerateScript -->|"orchestrates"| MdBook
    Config --> MdBook
    Content --> MdBook
    MdBook -->|"produces"| Artifacts
    CI -->|"deploy site"| Pages

    %% Click Events
    click Repo "https://github.com/rust-lang/rfcs/blob/master/."
    click Content "https://github.com/rust-lang/rfcs/tree/master/text/"
    click Config "https://github.com/rust-lang/rfcs/blob/master/book.toml"
    click Workflow "https://github.com/rust-lang/rfcs/blob/master/.github/workflows/deploy.yml"
    click GenerateScript "https://github.com/rust-lang/rfcs/blob/master/generate-book.py"
    click RenovateBotConf "https://github.com/rust-lang/rfcs/blob/master/.github/renovate.json5"
    click TriagebotConf "https://github.com/rust-lang/rfcs/blob/master/triagebot.toml"
    click README "https://github.com/rust-lang/rfcs/blob/master/README.md"

    %% Styles
    classDef person fill:#D6E9F8,stroke:#4A90E2,color:#1A1A1A;
    classDef source fill:#E8F1F8,stroke:#3C8DAD,color:#1A1A1A;
    classDef ci fill:#FFF4E5,stroke:#FFA726,color:#1A1A1A;
    classDef tool fill:#E8F8E8,stroke:#4CAF50,color:#1A1A1A;
    classDef artifact fill:#F3E5F5,stroke:#9C27B0,color:#1A1A1A;
    classDef host fill:#F3E5F5,stroke:#7B1FA2,color:#1A1A1A;
    classDef bot fill:#FFF9C4,stroke:#FBC02D,color:#1A1A1A;
    classDef docs fill:#ECEFF1,stroke:#607D8B,color:#1A1A1A;
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