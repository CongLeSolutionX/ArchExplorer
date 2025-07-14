---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/JuliaLang/PackageCompilerX.jl
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




# PackageCompilerX.jl repo project
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
title: "PackageCompilerX.jl repo project"
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
    %% User Layer
    subgraph "User Layer"
        CLI["Julia REPL / CLI"]:::user
    end

    %% Core Library Layer
    subgraph "Core Library Layer"
        API["Core API"]:::julia
        Config["Config Resolver"]:::julia
        CWrap["C Embedding Layer"]:::c
    end

    %% Build / Artifacts Layer
    subgraph "Build / Artifacts Layer"
        ProjectToml["Project.toml"]:::spec
        ArtifactsToml["Artifacts.toml"]:::spec
        FSIO["Filesystem I/O & Bundling"]:::julia
        SysImageOut["sysimage (.so/.dll)"]:::spec
        AppBundle["app/ folder"]:::spec
    end

    %% Infrastructure Layer
    subgraph "Infrastructure Layer"
        Examples["Examples"]:::example
        Tests["Tests"]:::test
        subgraph "CI Workflows"
            GHWF["documenter-workflow.yml"]:::infra
            CH["CompatHelper.yml"]:::infra
            Travis[".travis.yml"]:::infra
        end
        DocsGen["Docs Generator"]:::docs
    end

    %% Connections
    CLI -->|"calls"| API
    API -->|"queries"| Config
    API -->|"reads specs"| ProjectToml
    API -->|"reads specs"| ArtifactsToml
    API -->|"invokes"| CWrap
    API -->|"write sysimage"| FSIO
    API -->|"bundle app"| FSIO
    FSIO -->|"outputs"| SysImageOut
    FSIO -->|"outputs"| AppBundle
    Examples -->|"demo usage"| API
    Tests -->|"exercise"| API
    GHWF -->|"runs"| Tests
    GHWF -->|"builds"| DocsGen
    CH -->|"runs"| Tests
    Travis -->|"runs"| Tests

    %% Click Events
    click API "https://github.com/julialang/packagecompilerx.jl/blob/master/src/PackageCompilerX.jl"
    click Config "https://github.com/julialang/packagecompilerx.jl/blob/master/src/juliaconfig.jl"
    click CWrap "https://github.com/julialang/packagecompilerx.jl/blob/master/src/embedding_wrapper.c"
    click ProjectToml "https://github.com/julialang/packagecompilerx.jl/blob/master/Project.toml"
    click ArtifactsToml "https://github.com/julialang/packagecompilerx.jl/blob/master/Artifacts.toml"
    click Examples "https://github.com/julialang/packagecompilerx.jl/tree/master/examples/MyApp/"
    click Tests "https://github.com/julialang/packagecompilerx.jl/tree/master/test/"
    click GHWF "https://github.com/julialang/packagecompilerx.jl/blob/master/.github/workflows/documenter-workflow.yml"
    click CH "https://github.com/julialang/packagecompilerx.jl/blob/master/.github/workflows/CompatHelper.yml"
    click Travis "https://github.com/julialang/packagecompilerx.jl/blob/master/.travis.yml"
    click DocsGen "https://github.com/julialang/packagecompilerx.jl/blob/master/docs/make.jl"

    %% Styles
    classDef user fill:#D6EAF8,stroke:#2980B9;
    classDef julia fill:#AED6F1,stroke:#1F618D;
    classDef c fill:#A9DFBF,stroke:#27AE60;
    classDef spec fill:#FCF3CF,stroke:#B7950B;
    classDef example fill:#F9E79F,stroke:#B9770E;
    classDef test fill:#F5B7B1,stroke:#C0392B;
    classDef docs fill:#FAD7A0,stroke:#D35400;
    classDef infra fill:#EDBB99,stroke:#BA4A00;
```

-----


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