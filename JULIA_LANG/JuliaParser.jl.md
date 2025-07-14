---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/JuliaLang/JuliaParser.jl
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




# JuliaParser.jl repo project
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
title: "JuliaParser.jl repo project"
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
    %% Input Layer
    source(["Julia Source (string/file)"]):::io

    %% Core Pipeline
    subgraph "Core Pipeline"
        lexer["Lexer"]:::core
        token["Token Definitions"]:::core
        tokenStream[(TokenStream)]:::data
        parser["Parser"]:::core
        exprAST[(Expr AST)]:::data
    end

    %% Support Services
    diagnostics["Diagnostics"]:::support
    linenum["LineNumbers"]:::support

    %% Tooling Layers
    interactive["Interactive / REPL Utilities"]:::tooling
    precompile["Precompile Hooks"]:::tooling

    %% CLI Integration
    replCLI[/REPL Script/]:::cli
    testCLI[/Test Shell Script/]:::cli

    %% Testing
    tests[/Automated Test Suite/]:::tests

    %% Data Flows
    source -->|"raw source"| lexer
    lexer -->|"TokenStream"| tokenStream
    tokenStream --> parser
    parser -->|"Expr AST"| exprAST

    %% Diagnostics & Line Numbers
    lexer --> diagnostics
    parser --> diagnostics
    diagnostics --> linenum

    %% Post-Pipeline Usage
    exprAST --> interactive
    exprAST --> precompile

    %% CLI usage
    replCLI --> lexer
    replCLI --> parser
    testCLI --> lexer
    testCLI --> parser

    %% Tests
    tests --> lexer
    tests --> parser
    tests --> diagnostics
    tests --> linenum

    %% Click Events
    click source "https://github.com/julialang/juliaparser.jl/blob/master/src/JuliaParser.jl"
    click lexer "https://github.com/julialang/juliaparser.jl/blob/master/src/lexer.jl"
    click token "https://github.com/julialang/juliaparser.jl/blob/master/src/token.jl"
    click parser "https://github.com/julialang/juliaparser.jl/blob/master/src/parser.jl"
    click diagnostics "https://github.com/julialang/juliaparser.jl/blob/master/src/diagnostics.jl"
    click linenum "https://github.com/julialang/juliaparser.jl/blob/master/src/LineNumbers.jl"
    click interactive "https://github.com/julialang/juliaparser.jl/blob/master/src/interactiveutil.jl"
    click precompile "https://github.com/julialang/juliaparser.jl/blob/master/src/precompile.jl"
    click replCLI "https://github.com/julialang/juliaparser.jl/blob/master/bin/repl.jl"
    click testCLI "https://github.com/julialang/juliaparser.jl/blob/master/bin/testshell.jl"
    click tests "https://github.com/julialang/juliaparser.jl/tree/master/test/"

    %% Styles
    classDef core fill:#D0E9FF,stroke:#0366D6,color:#0366D6,stroke-width:1px;
    classDef support fill:#E6F5D0,stroke:#228B22,color:#228B22,stroke-width:1px;
    classDef tooling fill:#DFF0D8,stroke:#3C763D,color:#3C763D,stroke-width:1px;
    classDef cli fill:#FCF8E3,stroke:#8A6D3B,color:#8A6D3B,stroke-width:1px,shape:parallelogram;
    classDef tests fill:#F2DEDE,stroke:#A94442,color:#A94442,stroke-width:1px,shape:parallelogram;
    classDef data fill:#FFF5E6,stroke:#FF8C00,color:#FF8C00,stroke-width:1px;
    classDef io fill:#F5F5F5,stroke:#999999,color:#333333,stroke-width:1px,shape:parallelogram;
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