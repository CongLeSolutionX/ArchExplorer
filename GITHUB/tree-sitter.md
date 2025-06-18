---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/tree-sitter/tree-sitter
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


# tree-sitter repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


----

```mermaid
---
title: "tree-sitter repo project"
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
flowchart TB
    %% Styles
    classDef core fill:#d4edda,stroke:#28a745
    classDef binding fill:#cce5ff,stroke:#007bff
    classDef tool fill:#fff3cd,stroke:#ffc107
    classDef external fill:#f8f9fa,stroke:#6c757d
    
    subgraph Applications
        IDE["IDEs & Text Editors"]:::external
        DevTools["Development Tools"]:::external
    end

    subgraph BindingsLayer
        RustBinding["Rust Binding"]:::binding
        WebBinding["Web/WASM Binding"]:::binding
        OtherBindings["Other Language Bindings"]:::binding
    end

    subgraph CoreLibrary
        ParserGen["Parser Generator Engine"]:::core
        IncrParser["Incremental Parser"]:::core
        GrammarProc["Grammar Processor"]:::core
        SyntaxTree["Syntax Tree Manager"]:::core
    end

    subgraph BaseComponents
        Lexer["Lexer"]:::core
        Parser["Parser"]:::core
        TreeMgmt["Tree Management"]:::core
        QueryEngine["Query Engine"]:::core
    end

    subgraph Tools
        CLI["Command Line Interface"]:::tool
        SyntaxHighlight["Syntax Highlighting"]:::tool
        CodeNav["Code Navigation"]:::tool
        GrammarDef["Grammar Definition System"]:::tool
    end

    %% Relationships
    ParserGen --> GrammarDef
    GrammarDef --> ParserGen
    IncrParser --> SyntaxTree
    SyntaxTree --> TreeMgmt
    QueryEngine --> SyntaxTree
    
    RustBinding --> CoreLibrary
    WebBinding --> CoreLibrary
    OtherBindings --> CoreLibrary
    
    CoreLibrary --> BaseComponents
    
    IDE --> BindingsLayer
    DevTools --> BindingsLayer
    
    CLI --> ParserGen
    SyntaxHighlight --> QueryEngine
    CodeNav --> QueryEngine

    %% Click events
    click ParserGen "https://github.com/tree-sitter/tree-sitter/tree/master/cli/generate/"
    click IncrParser "https://github.com/tree-sitter/tree-sitter/tree/master/lib/src/"
    click RustBinding "https://github.com/tree-sitter/tree-sitter/tree/master/lib/binding_rust/"
    click WebBinding "https://github.com/tree-sitter/tree-sitter/tree/master/lib/binding_web/"
    click CLI "https://github.com/tree-sitter/tree-sitter/tree/master/cli/src/"
    click QueryEngine "https://github.com/tree-sitter/tree-sitter/blob/master/lib/src/query.c"
    click SyntaxHighlight "https://github.com/tree-sitter/tree-sitter/tree/master/highlight/"
    click GrammarDef "https://github.com/tree-sitter/tree-sitter/blob/master/cli/generate/src/grammar_files.rs"
    click CodeNav "https://github.com/tree-sitter/tree-sitter/tree/master/tags/"

    %% Legend
    subgraph Legend
        CoreComp["Core Component"]:::core
        BindingComp["Binding Component"]:::binding
        ToolComp["Tool Component"]:::tool
        ExtComp["External Component"]:::external
    end
```

----

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
 
  Closing_quote ~~~ My_Meme

  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

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