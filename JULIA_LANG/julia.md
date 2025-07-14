---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/JuliaLang/julia
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




# julia repo project
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
title: "julia repo project"
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
    subgraph "Frontend Layer"
        CLI["CLI/REPL"]:::frontend
    end

    subgraph "Standard Library Layer"
        StdLib["Standard Library (stdlib)"]:::stdlib
    end

    subgraph "Compiler Layer"
        compilerCore["Compiler"]:::compiler
        IRGen["IR Generation"]:::compiler
        Opt["Optimization (ssair)"]:::compiler
        CodeGen["Code Generation"]:::compiler
        compilerCore --> IRGen
        compilerCore --> Opt
        compilerCore --> CodeGen
    end

    subgraph "Runtime Layer"
        Base["Base"]:::runtime
        Src["Src"]:::runtime
    end

    subgraph "Build & Deployment"
        Deps["Deps"]:::build
        BuildScripts["Build Scripts"]:::build
        CICD["CI/CD Configs"]:::build
    end

    subgraph "Documentation & Testing"
        Docs["Documentation"]:::doc
        Tests["Tests"]:::doc
    end

    %% Relationships between layers
    CLI -->|"sendsCode"| compilerCore
    compilerCore -->|"executesOn"| Src
    compilerCore -->|"executesOn"| Base
    Base -->|"supports"| StdLib
    StdLib -->|"feeds"| CLI

    Deps -->|"builds"| compilerCore
    BuildScripts -->|"builds"| compilerCore
    BuildScripts -->|"builds"| Src
    CICD -->|"triggers"| Tests
    CICD -->|"triggers"| Docs

    %% Click Events
    click CLI "https://github.com/julialang/julia/tree/master/cli/"
    click StdLib "https://github.com/julialang/julia/tree/master/stdlib/"
    click compilerCore "https://github.com/julialang/julia/tree/master/Compiler/"
    click IRGen "https://github.com/julialang/julia/tree/master/Compiler/src"
    click Opt "https://github.com/julialang/julia/tree/master/Compiler/src/ssair"
    click Base "https://github.com/julialang/julia/tree/master/base/"
    click Src "https://github.com/julialang/julia/tree/master/src/"
    click Deps "https://github.com/julialang/julia/tree/master/deps/"
    click BuildScripts "https://github.com/julialang/julia/tree/master/Makefile"
    click CICD "https://github.com/julialang/julia/tree/master/.github/"
    click Docs "https://github.com/julialang/julia/tree/master/doc/"
    click Tests "https://github.com/julialang/julia/tree/master/test/"

    %% Styles
    classDef frontend fill:#F9E79F,stroke:#D4AC0D,stroke-width:2px;
    classDef stdlib fill:#FAD7A0,stroke:#E67E22,stroke-width:2px;
    classDef compiler fill:#AED6F1,stroke:#2471A3,stroke-width:2px;
    classDef runtime fill:#A9DFBF,stroke:#1E8449,stroke-width:2px;
    classDef build fill:#D2B4DE,stroke:#8E44AD,stroke-width:2px;
    classDef doc fill:#F5B7B1,stroke:#CB4335,stroke-width:2px;
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