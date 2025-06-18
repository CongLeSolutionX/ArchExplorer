---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/hevm
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExMWRkMGMxZWx5bjVscGZtZjJlNjh5cDlyM2J5cnU2cHYybzh2NDhpeCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/sRFEa8lbeC7zbcIZZR/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# hevm repo project
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
title: "hevm repo project"
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
    %% CLI Layer
    CLI["hevm CLI"]:::cli
    click CLI "https://github.com/ethereum/hevm/blob/main/cli/cli.hs"

    %% Core Library Layer
    subgraph "EVM Core Library" 
        direction TB
        EVMEntry["Library Entry\n(src/EVM.hs)"]:::library
        click EVMEntry "https://github.com/ethereum/hevm/blob/main/src/EVM.hs"
        CoreModules["Core Modules\n(src/EVM/)"]:::library
        click CoreModules "https://github.com/ethereum/hevm/tree/main/src/EVM/"
        Assembler["Assembler\n(src/EVM/Assembler.hs)"]:::library
        click Assembler "https://github.com/ethereum/hevm/blob/main/src/EVM/Assembler.hs"
        SymExec["Symbolic Execution\n(src/EVM/SymExec.hs)"]:::library
        click SymExec "https://github.com/ethereum/hevm/blob/main/src/EVM/SymExec.hs"
        SMTInterface["SMT Interface\n(src/EVM/SMT.hs)"]:::library
        click SMTInterface "https://github.com/ethereum/hevm/blob/main/src/EVM/SMT.hs"
        Solvers["Solver Integration\n(src/EVM/Solvers.hs)"]:::library
        click Solvers "https://github.com/ethereum/hevm/blob/main/src/EVM/Solvers.hs"
    end

    %% Native FFI Layer
    NativeFFI["Ethjet FFI (C)"]:::native
    click NativeFFI "https://github.com/ethereum/hevm/tree/main/ethjet/"

    %% External Solvers
    ExternalSolvers["External SMT Solvers\n(Z3, CVC5, Bitwuzla)"]:::external

    %% Bench and Test Layers
    Bench["Benchmark Suite"]:::test
    click Bench "https://github.com/ethereum/hevm/blob/main/bench/bench.hs"
    TestSuite["Test Suite"]:::test
    click TestSuite "https://github.com/ethereum/hevm/tree/main/test/"

    %% Build Configuration
    subgraph "Build Config"
        direction TB
        Cabal["hevm.cabal"]:::external
        click Cabal "https://github.com/ethereum/hevm/blob/main/hevm.cabal"
        NixFlake["flake.nix\nflake.lock"]:::external
        click NixFlake "https://github.com/ethereum/hevm/blob/main/flake.nix"
        click NixFlake "https://github.com/ethereum/hevm/blob/main/flake.lock"
    end

    %% Connections
    CLI -->|"dispatches commands"| EVMEntry
    EVMEntry --> CoreModules
    CoreModules --> Assembler
    CoreModules --> SymExec
    CoreModules --> SMTInterface
    CoreModules --> Solvers
    CoreModules -->|"hash calls"| NativeFFI
    CoreModules <-->|"SMT protocol"| ExternalSolvers
    Bench -->|"drives API"| CoreModules
    TestSuite -->|"tests API"| CoreModules
    Cabal --> CLI
    Cabal --> CoreModules
    Cabal --> NativeFFI
    NixFlake --> Cabal

    %% Styles
    classDef cli fill:#D6EAF8,stroke:#2980B9,color:#154360
    classDef library fill:#D5F5E3,stroke:#27AE60,color:#145A32
    classDef native fill:#FAD7A0,stroke:#D35400,color:#7E5109
    classDef external fill:#D5D8DC,stroke:#7F8C8D,color:#2C3E50
    classDef test fill:#E8DAEF,stroke:#884EA0,color:#4A235A

```

-----

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
