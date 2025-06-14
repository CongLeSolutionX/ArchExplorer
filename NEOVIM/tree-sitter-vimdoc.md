---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/neovim/tree-sitter-vimdoc
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




# tree-sitter-vimdoc repo project
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---

```mermaid
---
title: "tree-sitter-vimdoc repo project"
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
flowchart TD
    %% Grammar Definition Layer
    subgraph "Grammar Definition"
        direction TB
        GD1["grammar.js"]:::core
        GD2["src/grammar.json"]:::core
        GD3["src/node-types.json"]:::core
        GD4["tree-sitter.json"]:::core
    end

    %% Parser Generation & Core
    subgraph "Parser Generation & Core"
        direction TB
        PG["Parser Generation"]:::core
        CL["Shared Parser Library\n(.so/.dll/.dylib)"]:::core
        PC["src/parser.c"]:::core
        PH1["src/tree_sitter/parser.h"]:::core
        PH2["src/tree_sitter/alloc.h"]:::core
        PH3["src/tree_sitter/array.h"]:::core
    end

    %% Language Bindings
    subgraph "Language Bindings"
        direction TB
        subgraph "C Binding"
            direction TB
            C_H["tree-sitter-vimdoc.h"]:::binding
            C_PC["tree-sitter-vimdoc.pc.in"]:::binding
        end
        subgraph "Go Binding"
            direction TB
            GO1["binding.go"]:::binding
            GO2["binding_test.go"]:::binding
            GO3["go.mod"]:::binding
        end
        subgraph "Node.js Binding"
            direction TB
            N1["binding.cc"]:::binding
            N2["index.js"]:::binding
            N3["index.d.ts"]:::binding
        end
        subgraph "Python Binding"
            direction TB
            PY1["__init__.py"]:::binding
            PY2["binding.c"]:::binding
            PY3["__init__.pyi"]:::binding
            PY4["py.typed"]:::binding
        end
        subgraph "Rust Binding"
            direction TB
            R1["lib.rs"]:::binding
            R2["build.rs"]:::binding
        end
        subgraph "Swift Binding"
            direction TB
            S1["vimdoc.h"]:::binding
        end
    end

    %% Query Engine
    subgraph "Query Engine"
        direction TB
        Q1["highlights.scm"]:::queries
        Q2["injections.scm"]:::queries
    end

    %% Test Harness
    subgraph "Test Harness"
        direction TB
        TH["test/corpus/*.txt"]:::tests
    end

    %% Packaging & CI
    subgraph "Packaging & CI"
        direction TB
        BS["Build Scripts\n(Makefile, binding.gyp)"]:::infra
        PM["Package Manifests\n(Cargo.toml, package.json,\nsetup.py, pyproject.toml,\nPackage.swift)"]:::infra
        CI["CI Workflows\n(.github/workflows/*.yml)"]:::infra
    end

    %% Connections
    GD1 -->|defines grammar| PG
    GD2 -->|defines grammar| PG
    GD3 -->|defines grammar| PG
    GD4 -->|defines grammar| PG

    PG -->|generates| PC
    PG -->|generates| PH1
    PG -->|generates| PH2
    PG -->|generates| PH3
    PC -->|compiled into| CL
    PH1 -->|compiled into| CL
    PH2 -->|compiled into| CL
    PH3 -->|compiled into| CL

    CL -->|links against| C_H
    CL -->|links against| GO1
    CL -->|links against| N1
    CL -->|links against| PY2
    CL -->|links against| R1
    CL -->|links against| S1

    C_H -->|FFI| TH
    GO1 -->|FFI| TH
    N1 -->|FFI| TH
    PY2 -->|FFI| TH
    R1 -->|FFI| TH
    S1 -->|FFI| TH

    TH -->|JSON AST| Q1
    TH -->|JSON AST| Q2

    BS -->|builds| C_H
    BS -->|builds| GO1
    BS -->|builds| N1
    BS -->|builds| PY2
    BS -->|builds| R1
    BS -->|builds| S1

    PM -->|packages| C_H
    PM -->|packages| GO1
    PM -->|packages| N2
    PM -->|packages| PY1
    PM -->|packages| R1
    PM -->|packages| S1

    CI -->|runs| BS
    CI -->|runs| TH
    CI -->|publishes| PM

    %% Click Events
    click GD1 "https://github.com/neovim/tree-sitter-vimdoc/blob/master/grammar.js"
    click GD2 "https://github.com/neovim/tree-sitter-vimdoc/blob/master/src/grammar.json"
    click GD3 "https://github.com/neovim/tree-sitter-vimdoc/blob/master/src/node-types.json"
    click GD4 "https://github.com/neovim/tree-sitter-vimdoc/blob/master/tree-sitter.json"
    click PC "https://github.com/neovim/tree-sitter-vimdoc/blob/master/src/parser.c"
    click PH1 "https://github.com/neovim/tree-sitter-vimdoc/blob/master/src/tree_sitter/parser.h"
    click PH2 "https://github.com/neovim/tree-sitter-vimdoc/blob/master/src/tree_sitter/alloc.h"
    click PH3 "https://github.com/neovim/tree-sitter-vimdoc/blob/master/src/tree_sitter/array.h"
    click C_H "https://github.com/neovim/tree-sitter-vimdoc/blob/master/bindings/c/tree-sitter-vimdoc.h"
    click C_PC "https://github.com/neovim/tree-sitter-vimdoc/blob/master/bindings/c/tree-sitter-vimdoc.pc.in"
    click GO1 "https://github.com/neovim/tree-sitter-vimdoc/blob/master/bindings/go/binding.go"
    click GO2 "https://github.com/neovim/tree-sitter-vimdoc/blob/master/bindings/go/binding_test.go"
    click GO3 "https://github.com/neovim/tree-sitter-vimdoc/blob/master/bindings/go/go.mod"
    click N1 "https://github.com/neovim/tree-sitter-vimdoc/blob/master/bindings/node/binding.cc"
    click N2 "https://github.com/neovim/tree-sitter-vimdoc/blob/master/bindings/node/index.js"
    click N3 "https://github.com/neovim/tree-sitter-vimdoc/blob/master/bindings/node/index.d.ts"
    click PY1 "https://github.com/neovim/tree-sitter-vimdoc/blob/master/bindings/python/tree_sitter_vimdoc/__init__.py"
    click PY2 "https://github.com/neovim/tree-sitter-vimdoc/blob/master/bindings/python/tree_sitter_vimdoc/binding.c"
    click PY3 "https://github.com/neovim/tree-sitter-vimdoc/blob/master/bindings/python/tree_sitter_vimdoc/__init__.pyi"
    click PY4 "https://github.com/neovim/tree-sitter-vimdoc/blob/master/bindings/python/tree_sitter_vimdoc/py.typed"
    click R1 "https://github.com/neovim/tree-sitter-vimdoc/blob/master/bindings/rust/lib.rs"
    click R2 "https://github.com/neovim/tree-sitter-vimdoc/blob/master/bindings/rust/build.rs"
    click S1 "https://github.com/neovim/tree-sitter-vimdoc/blob/master/bindings/swift/TreeSitterVimdoc/vimdoc.h"
    click Q1 "https://github.com/neovim/tree-sitter-vimdoc/blob/master/queries/vimdoc/highlights.scm"
    click Q2 "https://github.com/neovim/tree-sitter-vimdoc/blob/master/queries/vimdoc/injections.scm"
    click TH "https://github.com/neovim/tree-sitter-vimdoc/blob/master/test/corpus/*.txt"
    click BS "https://github.com/neovim/tree-sitter-vimdoc/tree/master/Makefile"
    click BS "https://github.com/neovim/tree-sitter-vimdoc/blob/master/binding.gyp"
    click PM "https://github.com/neovim/tree-sitter-vimdoc/blob/master/Cargo.toml"
    click PM "https://github.com/neovim/tree-sitter-vimdoc/blob/master/package.json"
    click PM "https://github.com/neovim/tree-sitter-vimdoc/blob/master/package-lock.json"
    click PM "https://github.com/neovim/tree-sitter-vimdoc/blob/master/setup.py"
    click PM "https://github.com/neovim/tree-sitter-vimdoc/blob/master/pyproject.toml"
    click PM "https://github.com/neovim/tree-sitter-vimdoc/blob/master/Package.swift"
    click CI "https://github.com/neovim/tree-sitter-vimdoc/blob/master/.github/workflows/main.yml"
    click CI "https://github.com/neovim/tree-sitter-vimdoc/blob/master/.github/workflows/release.yml"

    %% Styles
    classDef core fill:#e0f7fa,stroke:#006064,color:#006064
    classDef binding fill:#e8f5e9,stroke:#2e7d32,color:#2e7d32
    classDef queries fill:#fff3e0,stroke:#ef6c00,color:#ef6c00
    classDef tests fill:#fff3e0,stroke:#ef6c00,color:#ef6c00
    classDef infra fill:#f5f5f5,stroke:#9e9e9e,color:#424242

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
    
  My_Meme ~~~ Closing_quote
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

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