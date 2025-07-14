---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/JuliaLang/PrecompileTools.jl
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




# PrecompileTools.jl repo project
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
title: "PrecompileTools.jl repo project"
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
flowchart TD
    subgraph "Core Library Module"
        Core["PrecompileTools.jl"]:::core
        Invalidations["invalidations.jl"]:::core
        Workloads["workloads.jl"]:::core
    end

    subgraph "External Systems"
        Preferences["Preferences.jl"]:::external
        JuliaEngine["Julia Precompilation Engine"]:::external
    end

    subgraph "Documentation Pipeline"
        DocsSrc["docs/src"]:::external
        MakeDocs["make.jl"]:::external
        DocsProj["Project.toml"]:::external
        DocsMan["Manifest.toml"]:::external
        Documenter["Documenter.jl"]:::external
        DocsSrc --> MakeDocs
        DocsProj --> MakeDocs
        DocsMan --> MakeDocs
        MakeDocs --> Documenter
    end

    subgraph "Test Harness"
        Tests["test/runtests.jl"]:::test
        WithoutCov["test/without_coverage.jl"]:::test
    end

    subgraph "CI/CD Services"
        CI["CI.yml"]:::ci
        Compat["CompatHelper.yml"]:::ci
        TagBot["TagBot.yml"]:::ci
    end

    subgraph "Configuration Files"
        Project["Project.toml"]:::config
        Manifest["Manifest.toml"]:::config
        Gitignore[".gitignore"]:::config
        License["LICENSE"]:::config
    end

    Core -->|"reads Preferences"| Preferences
    Core -->|"calls Invalidations"| Invalidations
    Invalidations -->|"marks changes"| Workloads
    Workloads -->|"sends code for compilation"| JuliaEngine
    JuliaEngine -->|"writes cache to disk"| Core

    Tests -->|"invoke API"| Core
    Tests -->|"validate invalidations"| Invalidations
    Tests -->|"validate workloads"| Workloads
    WithoutCov -->|"invoke API"| Core

    CI -->|"runs tests"| Tests
    CI -->|"builds docs"| MakeDocs
    CI -->|"checks compatibility"| Compat
    CI -->|"publishes releases"| TagBot

    classDef core fill:#D0E8FF,stroke:#333,stroke-width:1px
    classDef external fill:#DFFFE0,stroke:#333,stroke-width:1px,stroke-dasharray: 5 5
    classDef test fill:#FFEDD0,stroke:#333,stroke-width:1px
    classDef ci fill:#E8D0FF,stroke:#333,stroke-width:1px
    classDef config fill:#EFEFEF,stroke:#333,stroke-width:1px

    click Core "https://github.com/julialang/precompiletools.jl/blob/main/src/PrecompileTools.jl"
    click Invalidations "https://github.com/julialang/precompiletools.jl/blob/main/src/invalidations.jl"
    click Workloads "https://github.com/julialang/precompiletools.jl/blob/main/src/workloads.jl"
    click DocsSrc "https://github.com/julialang/precompiletools.jl/tree/main/docs/src"
    click MakeDocs "https://github.com/julialang/precompiletools.jl/blob/main/docs/make.jl"
    click DocsProj "https://github.com/julialang/precompiletools.jl/blob/main/docs/Project.toml"
    click DocsMan "https://github.com/julialang/precompiletools.jl/blob/main/docs/Manifest.toml"
    click CI "https://github.com/julialang/precompiletools.jl/blob/main/.github/workflows/CI.yml"
    click Compat "https://github.com/julialang/precompiletools.jl/blob/main/.github/workflows/CompatHelper.yml"
    click TagBot "https://github.com/julialang/precompiletools.jl/blob/main/.github/workflows/TagBot.yml"
    click Tests "https://github.com/julialang/precompiletools.jl/blob/main/test/runtests.jl"
    click WithoutCov "https://github.com/julialang/precompiletools.jl/blob/main/test/without_coverage.jl"
    click Project "https://github.com/julialang/precompiletools.jl/blob/main/Project.toml"
    click Manifest "https://github.com/julialang/precompiletools.jl/blob/main/Manifest.toml"
    click Gitignore "https://github.com/julialang/precompiletools.jl/blob/main/.gitignore"
    click License "https://github.com/julialang/precompiletools.jl/tree/main/LICENSE"
```

------

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