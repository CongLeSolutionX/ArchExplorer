---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/JuliaLang/JuliaSyntax.jl
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




# JuliaSyntax.jl repo project
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
title: "JuliaSyntax.jl repo project"
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
    %% I/O & Lexical Analysis
    subgraph "I/O & Lexical Analysis"
        direction TB
        Source[("Source Files")]:::io
        click Source "https://github.com/julialang/juliasyntax.jl/blob/main/src/core/source_files.jl"
        ParseStream["Parse Stream\n(stream + buffer)"]:::io
        click ParseStream "https://github.com/julialang/juliasyntax.jl/blob/main/src/core/parse_stream.jl"
        JuliaLex["Julia Parse Stream"]:::io
        click JuliaLex "https://github.com/julialang/juliasyntax.jl/blob/main/src/julia/julia_parse_stream.jl"
        Tokenizer["Tokenizer"]:::io
        click Tokenizer "https://github.com/julialang/juliasyntax.jl/blob/main/src/julia/tokenize.jl"
        Classify["Token Classification"]:::io
        click Classify "https://github.com/julialang/juliasyntax.jl/blob/main/src/julia/kinds.jl"
        click Classify "https://github.com/julialang/juliasyntax.jl/blob/main/src/julia/literal_parsing.jl"
    end

    %% Parsing & Tree Construction
    subgraph "Parsing & Tree Construction"
        direction TB
        Parser["Parser\n(recursive descent)"]:::parse
        click Parser "https://github.com/julialang/juliasyntax.jl/blob/main/src/julia/parser.jl"
        GreenNode["Green Tree Nodes"]:::parse
        click GreenNode "https://github.com/julialang/juliasyntax.jl/blob/main/src/porcelain/green_node.jl"
        SyntaxTree["Syntax Tree Wrapper"]:::parse
        click SyntaxTree "https://github.com/julialang/juliasyntax.jl/blob/main/src/porcelain/syntax_tree.jl"
    end

    %% Diagnostics & Recovery
    subgraph "Diagnostics & Recovery"
        direction TB
        Diagnostics["Diagnostics"]:::diag
        click Diagnostics "https://github.com/julialang/juliasyntax.jl/blob/main/src/core/diagnostics.jl"
        Cursors["Tree Cursors"]:::diag
        click Cursors "https://github.com/julialang/juliasyntax.jl/blob/main/src/core/tree_cursors.jl"
    end

    %% Public API & Integration
    subgraph "Public API & Integration"
        direction TB
        API["Parser API"]:::api
        click API "https://github.com/julialang/juliasyntax.jl/blob/main/src/julia/parser_api.jl"
        ExprConv["Expr Conversion"]:::api
        click ExprConv "https://github.com/julialang/juliasyntax.jl/blob/main/src/integration/expr.jl"
        Hooks["Integration Hooks"]:::api
        click Hooks "https://github.com/julialang/juliasyntax.jl/blob/main/src/integration/hooks.jl"
    end

    %% Precompilation & Tools
    subgraph "Precompilation & Tools"
        direction TB
        PrecompileScript["Precompile Script"]:::tools
        click PrecompileScript "https://github.com/julialang/juliasyntax.jl/blob/main/src/precompile.jl"
        SysCompile["Sysimage Build Script"]:::tools
        click SysCompile "https://github.com/julialang/juliasyntax.jl/blob/main/sysimage/compile.jl"
        SysPreHelp["Sysimage Helpers"]:::tools
        click SysPreHelp "https://github.com/julialang/juliasyntax.jl/blob/main/sysimage/precompile.jl"
        click SysPreHelp "https://github.com/julialang/juliasyntax.jl/blob/main/sysimage/precompile_exec.jl"
        SysCore["Sysimage Core Package"]:::tools
        click SysCore "https://github.com/julialang/juliasyntax.jl/blob/main/sysimage/JuliaSyntaxCore/src/JuliaSyntaxCore.jl"
        click SysCore "https://github.com/julialang/juliasyntax.jl/blob/main/sysimage/JuliaSyntaxCore/Project.toml"
        ToolsAux["Auxiliary Tools"]:::tools
        click ToolsAux "https://github.com/julialang/juliasyntax.jl/tree/main/tools/"
    end

    %% Testing, Documentation & Prototypes
    Test["Testing Suite"]:::tools
    click Test "https://github.com/julialang/juliasyntax.jl/tree/main/test/"
    Docs["Documentation"]:::tools
    click Docs "https://github.com/julialang/juliasyntax.jl/blob/main/docs/src/design.md"
    click Docs "https://github.com/julialang/juliasyntax.jl/blob/main/docs/src/howto.md"
    Proto["Prototypes & Experiments"]:::tools
    click Proto "https://github.com/julialang/juliasyntax.jl/blob/main/prototypes/simple_parser.jl"
    click Proto "https://github.com/julialang/juliasyntax.jl/blob/main/prototypes/syntax_interpolation.jl"

    %% Data Flow
    Source --> ParseStream --> JuliaLex --> Tokenizer --> Classify --> Parser --> GreenNode --> SyntaxTree --> API --> ExprConv
    Parser -->|error events| Diagnostics
    Diagnostics -->|recovery info| Parser
    SyntaxTree --> Hooks
    ExprConv --> Hooks
    Hooks --> SysCompile
    GreenNode --> SysCompile
    SyntaxTree --> SysCompile

    %% Peripheral Flows
    Test -.-> Parser
    Test -.-> Diagnostics
    Test -.-> ExprConv
    Docs -.-> API
    Docs -.-> Hooks
    Proto -.-> Parser

    %% Styles
    classDef io fill:#E0F7FA,stroke:#006064,color:#006064
    classDef parse fill:#E8F5E9,stroke:#2E7D32,color:#2E7D32
    classDef diag fill:#FFF3E0,stroke:#EF6C00,color:#EF6C00
    classDef api fill:#F3E5F5,stroke:#6A1B9A,color:#6A1B9A
    classDef tools fill:#ECEFF1,stroke:#37474F,color:#37474F

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