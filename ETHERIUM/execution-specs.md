---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/execution-specs
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExZzV4bHh6cTVnZmxsdHUxbTVjYzg4b3Rib3VjdG02NW5nMmliazdkYiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/QpVUMRUJGokfqXyfa1/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# execution-specs repo project
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
title: "execution-specs repo project"
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
    %% Actors
    Developer["Developer"]:::actor

    %% Core Spec Library
    subgraph "Core Spec Library" 
        ForkModules["Fork Modules"]:::blue
        Interpreter["Interpreter"]:::blue
        Instructions["Instructions"]:::blue
        Precompiles["Precompiled Contracts"]:::blue
        Crypto["Crypto Support"]:::blue
        Utils["Utilities"]:::blue
        Assets["Genesis & Network Assets"]:::blue
        Optimized["Optimized Implementations"]:::blue
        SpecTools["Spec Tooling"]:::blue
    end

    %% Documentation and Site
    subgraph "Documentation" 
        NetDocs["Network Upgrade Documents"]:::orange
        Lists["Lists & Metadata"]:::green
        SigLists["Signature Types"]:::green
        DocsGen["Documentation Generator"]:::orange
        Site["Static Site (GitHub Pages)"]:::orange
        Static["Static Styles"]:::orange
    end

    %% Tools and CI
    Scripts["CLI & Helper Scripts"]:::green
    Tests["Testing Suite"]:::purple
    CI["CI/CD Pipeline"]:::purple

    %% External Services
    Codecov["Codecov"]:::purple
    GitPOAP["GitPOAP"]:::purple
    PyPI["PyPI"]:::purple

    %% Relationships
    Developer --> CoreSpec
    Developer --> NetDocs
    Developer --> Lists
    Developer --> Scripts
    Developer --> CI

    CoreSpec --> Tests
    CoreSpec --> Scripts
    CoreSpec --> DocsGen

    NetDocs --> DocsGen
    Lists --> DocsGen
    SigLists --> DocsGen

    Scripts --> Tests
    Scripts --> DocsGen

    DocsGen --> Site
    Static --> Site

    CI --> Tests
    CI --> Site
    CI --> Codecov
    CI --> GitPOAP
    CI --> PyPI

    %% Click Events
    click ForkModules "https://github.com/ethereum/execution-specs/tree/master/src/ethereum/frontier"
    click Interpreter "https://github.com/ethereum/execution-specs/blob/master/src/ethereum/frontier/vm/interpreter.py"
    click Instructions "https://github.com/ethereum/execution-specs/tree/master/src/ethereum/frontier/vm/instructions/"
    click Precompiles "https://github.com/ethereum/execution-specs/tree/master/src/ethereum/frontier/vm/precompiled_contracts/"
    click Crypto "https://github.com/ethereum/execution-specs/tree/master/src/ethereum/crypto/"
    click Utils "https://github.com/ethereum/execution-specs/tree/master/src/ethereum/utils/"
    click Assets "https://github.com/ethereum/execution-specs/tree/master/src/ethereum/assets/"
    click Optimized "https://github.com/ethereum/execution-specs/tree/master/src/ethereum_optimized/"
    click SpecTools "https://github.com/ethereum/execution-specs/blob/master/src/ethereum_spec_tools/docc.py"
    click NetDocs "https://github.com/ethereum/execution-specs/tree/master/network-upgrades/mainnet-upgrades/"
    click Lists "https://github.com/ethereum/execution-specs/tree/master/lists/evm/"
    click SigLists "https://github.com/ethereum/execution-specs/tree/master/lists/signature-types/"
    click Scripts "https://github.com/ethereum/execution-specs/tree/master/scripts/"
    click Static "https://github.com/ethereum/execution-specs/blob/master/static/custom.css"
    click Tests "https://github.com/ethereum/execution-specs/tree/master/tests/"
    click CI "https://github.com/ethereum/execution-specs/blob/master/ .github/workflows/test.yaml"
    click Codecov "https://github.com/ethereum/execution-specs/blob/master/ .github/workflows/test.yaml"
    click GitPOAP "https://github.com/ethereum/execution-specs/blob/master/ .github/workflows/gh-pages.yaml"
    click PyPI "https://github.com/ethereum/execution-specs/blob/master/ .github/workflows/gh-pages.yaml"

    %% Styles
    classDef blue fill:#D0E8FF,stroke:#005B99,stroke-width:2px;
    classDef green fill:#DFFFE0,stroke:#2E8B57,stroke-width:2px;
    classDef orange fill:#FFE9B3,stroke:#CC8400,stroke-width:2px;
    classDef purple fill:#E8D0FF,stroke:#800080,stroke-width:2px;
    classDef actor fill:#FFFFFF,stroke:#000000,stroke-width:2px,stroke-dasharray: 5 5;

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
