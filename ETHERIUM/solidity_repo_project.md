---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/solidity
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExOW14N2tybW9mamw2MzB6ZXJ2MjNuejV2NzAwbGhuaXhyNjB0anBtNCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/IJDx6i7F9DFlwSXw4F/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----

# solidity repo project
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
title: "solidity repo project"
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
    %% Front-End Layer
    subgraph "Front-End"
        direction TB
        CLI(("solc CLI")):::frontend
        Scanner["Scanner"]:::frontend
        Parser["Parser"]:::frontend
        AST["AST"]:::frontend
    end

    %% Mid-End Layer
    subgraph "Mid-End"
        direction TB
        Analysis["Semantic Analysis"]:::mid
        IRGen["IR Generator"]:::mid
        Optimiser["Optimiser Passes"]:::mid
    end

    %% Back-End Layer
    subgraph "Back-End"
        direction TB
        Codegen["Yul→EVM Codegen"]:::backend
        Assembler["Assembly & Bytecode Emitter"]:::backend
        Linker["Linker"]:::backend
        Bytecode["Bytecode Output"]:::backend
    end

    %% Formal Verification
    subgraph "Formal Verification"
        direction TB
        FormalEngine["Model Checker"]:::formal
        SMTUtil["SMT Adapter"]:::formal
        Z3(("Z3")):::external
        CVC5(("CVC5")):::external
    end

    %% Language Server
    LSP(("LSP Server")):::frontend

    %% Build & CI Orchestration
    BuildCI(("Build & CI")):::infra

    %% Data Flow
    CLI --> Scanner --> Parser --> AST --> Analysis --> IRGen --> Optimiser --> Codegen --> Assembler --> Linker --> Bytecode

    %% LSP interactions
    LSP --> Parser
    LSP --> Analysis

    %% Formal interactions
    FormalEngine --> Analysis
    FormalEngine --> SMTUtil --> Z3
    SMTUtil --> CVC5

    %% Build & CI orchestration
    BuildCI --> CLI
    BuildCI --> LSP
    BuildCI --> Analysis
    BuildCI --> IRGen
    BuildCI --> Codegen
    BuildCI --> FormalEngine
    BuildCI --> TestSuite[(Tests & Examples)]:::infra

    %% Click Events
    click CLI "https://github.com/ethereum/solidity/blob/develop/solc/main.cpp"
    click CLI "https://github.com/ethereum/solidity/blob/develop/solc/CommandLineInterface.cpp"
    click CLI "https://github.com/ethereum/solidity/blob/develop/solc/CommandLineParser.cpp"
    click Scanner "https://github.com/ethereum/solidity/blob/develop/liblangutil/Scanner.cpp"
    click Parser "https://github.com/ethereum/solidity/blob/develop/liblangutil/ParserBase.cpp"
    click Parser "https://github.com/ethereum/solidity/blob/develop/libsolidity/parsing/Parser.cpp"
    click AST "https://github.com/ethereum/solidity/blob/develop/libsolidity/ast/AST.cpp"
    click Analysis "https://github.com/ethereum/solidity/blob/develop/libsolidity/analysis/NameAndTypeResolver.cpp"
    click IRGen "https://github.com/ethereum/solidity/blob/develop/libsolidity/codegen/ir/IRGenerator.cpp"
    click Optimiser "https://github.com/ethereum/solidity/blob/develop/libyul/optimiser/ASTWalker.cpp"
    click Codegen "https://github.com/ethereum/solidity/blob/develop/libyul/backends/evm/AsmCodeGen.cpp"
    click Assembler "https://github.com/ethereum/solidity/blob/develop/libevmasm/Assembly.cpp"
    click Linker "https://github.com/ethereum/solidity/blob/develop/libevmasm/LinkerObject.cpp"
    click FormalEngine "https://github.com/ethereum/solidity/blob/develop/libsolidity/formal/ModelChecker.cpp"
    click SMTUtil "https://github.com/ethereum/solidity/blob/develop/libsmtutil/SMTLib2Interface.cpp"
    click LSP "https://github.com/ethereum/solidity/blob/develop/libsolidity/lsp/LanguageServer.cpp"
    click BuildCI "https://github.com/ethereum/solidity/blob/develop/CMakeLists.txt"

    %% Styles
    classDef frontend fill:#D0E8FF,stroke:#0366d6,color:#0366d6;
    classDef mid fill:#E6F4EA,stroke:#22863a,color:#22863a;
    classDef backend fill:#FFF5E5,stroke:#d9941c,color:#d9941c;
    classDef formal fill:#F3E8FF,stroke:#6f42c1,color:#6f42c1;
    classDef infra fill:#F0F0F0,stroke:#6a737d,color:#6a737d;
    classDef external fill:#FFFFFF,stroke:#444444,stroke-dasharray: 2 2,color:#444444;
```


---

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
