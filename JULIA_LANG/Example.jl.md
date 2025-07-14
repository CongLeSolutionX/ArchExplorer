---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/JuliaLang/Example.jl
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




# Example.jl repo project
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
title: "Example.jl repo project"
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
    %% Code Artifacts
    subgraph "Code Artifacts"
        A1["Source Code Module"]:::code
        A2["Test Suite"]:::code
        A3["Documentation Site"]:::code
    end

    %% CI/CD Workflows
    subgraph "CI/CD Workflows"
        B1["CI Workflow"]:::ci
        B2["CompatHelper Workflow"]:::ci
        B3["TagBot Workflow"]:::ci
    end

    %% External Services
    subgraph "External Services"
        E1["Codecov"]:::external
        E2["GitHub Pages"]:::external
        E3["Nanosoldier Reports"]:::external
        E4["Julia Registry"]:::external
    end

    %% Events and Actors
    Dev((Developer)):::event
    Push["git push event"]:::event

    %% Flows
    Dev --> Push
    Push --> B1
    Push --> B2
    Push --> B3

    B1 -->|runs unit tests| A2
    B1 -->|uploads coverage| E1
    B1 -->|builds docs| A3
    A3 -->|deploy docs| E2

    E3 -->|periodic eval| B1
    E4 -->|dependency resolution| A1

    %% Click Events for Code Artifacts
    click A1 "https://github.com/julialang/example.jl/blob/master/src/Example.jl"
    click A1 "https://github.com/julialang/example.jl/tree/master/src/"
    click A2 "https://github.com/julialang/example.jl/blob/master/test/runtests.jl"
    click A2 "https://github.com/julialang/example.jl/tree/master/test/"
    click A3 "https://github.com/julialang/example.jl/blob/master/docs/make.jl"
    click A3 "https://github.com/julialang/example.jl/blob/master/docs/src/index.md"
    click A3 "https://github.com/julialang/example.jl/tree/master/docs/"
    click A3 "https://github.com/julialang/example.jl/blob/master/docs/Project.toml"

    %% Click Events for CI/CD Workflows
    click B1 "https://github.com/julialang/example.jl/blob/master/.github/workflows/ci.yml"
    click B2 "https://github.com/julialang/example.jl/blob/master/.github/workflows/CompatHelper.yml"
    click B3 "https://github.com/julialang/example.jl/blob/master/.github/workflows/TagBot.yml"

    %% Styles
    classDef code fill:#e0f7fa,stroke:#00796b;
    classDef ci fill:#fff3e0,stroke:#e65100;
    classDef external fill:#f3e5f5,stroke:#6a1b9a;
    classDef event fill:#eeeeee,stroke:#424242;
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