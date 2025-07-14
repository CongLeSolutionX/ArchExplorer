---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/JuliaLang/FunctionWrappers.jl
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




# FunctionWrappers.jl repo project
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
title: "FunctionWrappers.jl repo project"
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
    %% Nodes
    User["User Code / Consumer"]:::external
    SourceModule["FunctionWrappers.jl\n(src/FunctionWrappers.jl)"]:::source
    Runtime["Julia Runtime & C API\n(jlcall wrapper)"]:::runtime
    TestSuite["Test Suite\n(test/runtests.jl)"]:::source
    CIPipeline["CI/CD Pipeline\n(GitHub Actions)"]:::ci
    TagBot["TagBot Workflow\n(.github/workflows/TagBot.yml)"]:::ci
    Registry["Julia Package Registry"]:::external
    Metadata["Project.toml"]:::source
    README["README.md"]:::source
    License["LICENSE.md"]:::source
    Gitignore[".gitignore"]:::source

    %% Layout
    User -->|"using FunctionWrappers; call wrapper"| SourceModule
    SourceModule -->|"invoke type-stable call"| Runtime
    TestSuite -->|"unit tests"| SourceModule
    CIPipeline -->|"run tests & coverage"| TestSuite
    CIPipeline -->|"report status"| README
    CIPipeline -->|"reads metadata"| Metadata
    Metadata -->|"dependency constraints"| SourceModule
    Metadata -->|"dependency constraints"| Registry
    TagBot -->|"publish new version"| Registry

    %% Click Events
    click SourceModule "https://github.com/julialang/functionwrappers.jl/blob/master/src/FunctionWrappers.jl"
    click TestSuite "https://github.com/julialang/functionwrappers.jl/blob/master/test/runtests.jl"
    click CIPipeline "https://github.com/julialang/functionwrappers.jl/blob/master/.github/workflows/ci.yml"
    click TagBot "https://github.com/julialang/functionwrappers.jl/blob/master/.github/workflows/TagBot.yml"
    click Metadata "https://github.com/julialang/functionwrappers.jl/blob/master/Project.toml"
    click README "https://github.com/julialang/functionwrappers.jl/blob/master/README.md"
    click License "https://github.com/julialang/functionwrappers.jl/blob/master/LICENSE.md"
    click Gitignore "https://github.com/julialang/functionwrappers.jl/blob/master/.gitignore"

    %% Styling
    classDef source fill:#D0E7FF,stroke:#024B80,stroke-width:1px;
    classDef runtime fill:#E0FFE0,stroke:#0A6A0A,stroke-width:1px;
    classDef external fill:#E0FFE0,stroke:#0A6A0A,stroke-width:1px;
    classDef ci fill:#FFE0B3,stroke:#A05A00,stroke-width:1px;

    class User,Registry external
    class SourceModule,TestSuite,Metadata,README,License,Gitignore source
    class Runtime runtime
    class CIPipeline,TagBot ci
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