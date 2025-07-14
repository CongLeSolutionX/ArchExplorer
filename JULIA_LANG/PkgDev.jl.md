---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/JuliaLang/PkgDev.jl
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




# PkgDev.jl repo project
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
title: "PkgDev.jl repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#F5E3',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EEF5',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD'
    }
  }
}%%
flowchart TB
    %% User Layer
    User["User REPL/CLI"]:::external
    
    %% Core Library Modules
    subgraph "PkgDev.jl Library"
        direction TB
        PkgDev["PkgDev.jl\n(root module)"]:::module
        TagModule["TagModule\n(tag.jl)"]:::module
        ButlerModule["ButlerModule\n(pkgbutler.jl)"]:::module
        FormatModule["FormatModule\n(format.jl)"]:::module
    end

    %% Local Repository
    GitRepo["Local Git Repository"]:::data

    %% External Services
    subgraph "External Services"
        direction TB
        GitHubAPI["GitHub API"]:::external
        RegistryAPI["Registry API"]:::external
        Registrator["Registrator"]:::external
        TagBot["TagBot"]:::external
    end

    %% CI Workflows & Configs
    subgraph "CI & Workflows"
        direction TB
        GitHubWorkflows["GitHub Actions Workflows"]:::workflow
        TravisCI["Travis CI\n(.travis.yml)"]:::workflow
    end

    %% Project Files & Tests
    ProjectToml["Project.toml"]:::data
    Readme["README.md"]:::data
    Tests["Automated Tests\n(test/runtests.jl)"]:::data

    %% Interactions
    User -->|invokes| PkgDev
    PkgDev -->|calls| TagModule
    PkgDev -->|calls| ButlerModule
    PkgDev -->|calls| FormatModule

    TagModule -->|creates branches & commits| GitRepo
    TagModule -->|creates PRs| GitHubAPI
    TagModule -->|submits registry PRs| RegistryAPI
    GitHubAPI -->|triggers actions| TagBot
    GitHubAPI -->|notifies| Registrator

    ButlerModule -->|configures repo files| GitRepo
    ButlerModule -->|sets secrets & keys| GitHubAPI
    ButlerModule -->|injects workflows| GitHubWorkflows
    GitHubWorkflows -->|periodic CI runs| ButlerModule

    FormatModule -->|formats code| GitRepo

    GitRepo -->|push & sync| GitHubAPI
    Tests -->|validate| PkgDev

    PkgDev -->|reads| ProjectToml
    PkgDev -->|reads| Readme

    %% Click Events
    click PkgDev "https://github.com/julialang/pkgdev.jl/blob/master/src/PkgDev.jl"
    click TagModule "https://github.com/julialang/pkgdev.jl/blob/master/src/tag.jl"
    click ButlerModule "https://github.com/julialang/pkgdev.jl/blob/master/src/pkgbutler.jl"
    click FormatModule "https://github.com/julialang/pkgdev.jl/blob/master/src/format.jl"
    click GitHubWorkflows "https://github.com/julialang/pkgdev.jl/tree/master/.github/workflows/"
    click TravisCI "https://github.com/julialang/pkgdev.jl/blob/master/.travis.yml"
    click ProjectToml "https://github.com/julialang/pkgdev.jl/blob/master/Project.toml"
    click Readme "https://github.com/julialang/pkgdev.jl/blob/master/README.md"
    click Tests "https://github.com/julialang/pkgdev.jl/blob/master/test/runtests.jl"

    %% Styles
    classDef module fill:#ADD8E6,stroke:#000,stroke-width:1px
    classDef external fill:#90EE90,stroke:#000,stroke-width:1px
    classDef data fill:#FFD700,stroke:#000,stroke-width:1px
    classDef workflow fill:#DDA0DD,stroke:#000,stroke-width:1px
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