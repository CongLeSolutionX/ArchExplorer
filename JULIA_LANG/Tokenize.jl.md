---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/JuliaLang/Tokenize.jl
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




# Tokenize.jl repo project
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
title: "Tokenize.jl repo project"
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
    %% Runtime Path (Green)
    Input["Client Code / User"]:::runtime
    API["Tokenize.tokenize\n(src/Tokenize.jl)"]:::runtime
    Lexer["Lexer Engine\n(src/lexer.jl)"]:::runtime
    Output["Output Iterator"]:::runtime

    %% Helper Modules (Blue)
    Factory["Token Factory\n(src/token.jl, src/token_kinds.jl)"]:::helper
    Utilities["Utilities\n(src/utilities.jl)"]:::helper

    %% Compile-Time Hooks (Gray)
    Precompile["Precompile Hooks\n(src/_precompile.jl)"]:::compile

    %% Non-Runtime Activities (Dashed)
    subgraph Testing_and_Benchmarking["Testing & Benchmarking"]
        style Testing_and_Benchmarking stroke-dasharray: 5 5
        Tests["Tests Suite"]:::nonruntime
        Benchmarks["Benchmarks Suite"]:::nonruntime
        CI["CI Workflows"]:::nonruntime
    end

    %% Data Flow
    Input -->|"calls"| API
    API -->|"invokes"| Lexer
    Lexer -->|"emits raw tokens"| Factory
    Factory -->|"yields tokens"| Output
    Output -->|"returns iterator"| Input

    %% Helper Interaction
    Utilities -->|"supports"| Factory

    %% Compile-Time
    Precompile -->|"hooks into"| API

    %% Click Events
    click API "https://github.com/julialang/tokenize.jl/blob/master/src/Tokenize.jl"
    click Lexer "https://github.com/julialang/tokenize.jl/blob/master/src/lexer.jl"
    click Factory "https://github.com/julialang/tokenize.jl/blob/master/src/token.jl"
    click Factory "https://github.com/julialang/tokenize.jl/blob/master/src/token_kinds.jl"
    click Utilities "https://github.com/julialang/tokenize.jl/blob/master/src/utilities.jl"
    click Precompile "https://github.com/julialang/tokenize.jl/blob/master/src/_precompile.jl"
    click Tests "https://github.com/julialang/tokenize.jl/tree/master/test/"
    click Benchmarks "https://github.com/julialang/tokenize.jl/tree/master/benchmark/"
    click CI "https://github.com/julialang/tokenize.jl/tree/master/.github/workflows/"

    %% Legend
    subgraph "Legend"
        direction TB
        R["Runtime Path"]:::runtime
        H["Helper Modules"]:::helper
        C["Compile-Time Hooks"]:::compile
        N["Non-Runtime Activities"]:::nonruntime
    end

    classDef runtime fill:#ccffcc,stroke:#333,stroke-width:1px
    classDef helper fill:#ccccff,stroke:#333,stroke-width:1px
    classDef compile fill:#eeeeee,stroke:#333,stroke-width:1px
    classDef nonruntime stroke:#333,stroke-dasharray: 5 5,fill:none
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