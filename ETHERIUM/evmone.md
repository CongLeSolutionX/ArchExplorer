---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/evmone
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExcmp3emoyMWhzenZqODZydnUzdHV5eDFjc282bTk4M3oxdmRtenM0aSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/pOEbLRT4SwD35IELiQ/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# evmone repo project
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
title: "evmone repo project"
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
    ExternalClient["Ethereum Client"]:::external
    subgraph "EVMC Plugin Boundary"
        EVMCInterface["EVMC Interface Layer"]:::interface
    end
    subgraph "EVMone Core"
        EVMCore["EVM Core (Dispatcher)"]:::core
        subgraph "Interpreters"
            Baseline["Baseline Interpreter"]:::module
            Advanced["Advanced Interpreter"]:::module
        end
        Precompiles["Precompiles Module"]:::module
        EVMMAX["EVMMAX (GMP-backed precompiles)"]:::module
        EOFParser["EOF Parser & Validator"]:::parser
    end
    subgraph "External Dependencies"
        Intx["intx Library"]:::deps
        Ethash["ethash Library"]:::deps
        GMP["GMP (optional)"]:::deps
    end
    Build["CMake/Hunter Modules"]:::deps

    ExternalClient -->|"evmc_execute"| EVMCInterface
    EVMCInterface -->|"dispatch()"| EVMCore
    EVMCore -->|"baseline strategy"| Baseline
    EVMCore -->|"advanced strategy"| Advanced
    EVMCore -->|"invoke precompile"| Precompiles
    EVMCore -->|"invoke evmmax"| EVMMAX
    EVMCInterface -->|"validate_eof"| EOFParser

    Precompiles --> Intx
    Precompiles --> Ethash
    Precompiles --> GMP
    EVMCore --> Ethash

    Intx --> Build
    Ethash --> Build
    GMP --> Build

    click EVMCInterface "https://github.com/ethereum/evmone/blob/master/include/evmone/evmone.h"
    click EVMCore "https://github.com/ethereum/evmone/blob/master/lib/evmone/vm.cpp"
    click Baseline "https://github.com/ethereum/evmone/blob/master/lib/evmone/baseline_execution.cpp"
    click Advanced "https://github.com/ethereum/evmone/blob/master/lib/evmone/advanced_execution.cpp"
    click Precompiles "https://github.com/ethereum/evmone/tree/master/lib/evmone_precompiles/"
    click EVMMAX "https://github.com/ethereum/evmone/blob/master/include/evmmax/evmmax.hpp"
    click EOFParser "https://github.com/ethereum/evmone/blob/master/lib/evmone/eof.cpp"
    click Build "https://github.com/ethereum/evmone/tree/master/cmake/"

    classDef external fill:#f9f,stroke:#333,stroke-width:1px
    classDef interface fill:#bbf,stroke:#333,stroke-width:1px
    classDef core fill:#bfb,stroke:#333,stroke-width:1px
    classDef module fill:#ffb,stroke:#333,stroke-width:1px
    classDef parser fill:#fbf,stroke:#333,stroke-width:1px
    classDef deps fill:#eef,stroke:#333,stroke-width:1px
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
