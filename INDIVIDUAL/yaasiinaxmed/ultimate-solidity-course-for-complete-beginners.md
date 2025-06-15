---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/yaasiinaxmed/ultimate-solidity-course-for-complete-beginners
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExb2U4aHJnYzZ4dHUyZ2g0a25ja21oM3UxNGo4b3AwNjFqd3VoM2Q3byZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/10zxDv7Hv5RF9C/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# ultimate-solidity-course-for-complete-beginners repo project
> <ins>📢 **Disclaimer** 🚨</ins>
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
title: "ultimate-solidity-course-for-complete-beginners repo project"
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
    subgraph "Developer Environment"
        Dev["Developer Workstation <br/>(IDE)"]:::developer
    end

    subgraph Code_Repository["Code Repository"]
        Repo["Git Repository"]:::repo
        Exercises["Exercises/"]:::code
        Solutions["Solutions/"]:::code
        OZ[".deps/npm/@openzeppelin/contracts/"]:::code
        OZAccess["access/"]:::code
        OZUtils["utils/"]:::code
        RemixTests[".deps/remix-tests/"]:::code
        Readme["readme.md"]:::doc
        Gitignore[".gitignore"]:::doc
    end

    subgraph Build_and_Test_Pipeline["Build & Test Pipeline"]
        Compiler["Solidity Compiler<br/>(solc/Remix)"]:::build
        TestRunner["Remix-Tests"]:::build
    end

    subgraph Blockchain_Network["Blockchain Network"]
        Sepolia["Ethereum Sepolia Testnet"]:::chain
    end

    subgraph Wallet_Provider["Wallet Provider"]
        MetaMask["MetaMask"]:::wallet
    end

    subgraph DApp_Front_End["DApp Front-End"]
        ReactUI["React DApp<br/>(CodeSandbox)"]:::frontend
    end

    Dev -->|edits| Exercises
    Dev -->|edits| Solutions
    Dev -->|adds docs| Readme
    Dev -->|configures| Gitignore

    Exercises -->|imports| OZ
    Solutions -->|imports| OZ
    OZ --> OZAccess
    OZ --> OZUtils

    Exercises -->|compiles| Compiler
    Solutions -->|compiles| Compiler
    Compiler -->|runs tests| TestRunner
    TestRunner -->|uses| RemixTests

    TestRunner -->|on success deploys via| MetaMask
    MetaMask -->|sends deploy tx| Sepolia
    ReactUI -->|RPC calls / events| Sepolia
    ReactUI -->|uses Web3 provider| MetaMask

    Repo --> Exercises
    Repo --> Solutions
    Repo --> OZ
    Repo --> RemixTests
    Repo --> Readme
    Repo --> Gitignore

    classDef code fill:#D0E7FF,stroke:#036,stroke-width:1px
    classDef repo fill:#E0F7FA,stroke:#00796B,stroke-width:1px
    classDef build fill:#E8F5E9,stroke:#388E3C,stroke-width:1px
    classDef chain fill:#FFF3E0,stroke:#F57C00,stroke-width:1px
    classDef wallet fill:#FFE0B2,stroke:#FB8C00,stroke-width:1px
    classDef frontend fill:#F3E5F5,stroke:#8E24AA,stroke-width:1px
    classDef developer fill:#ECEFF1,stroke:#455A64,stroke-width:1px
    classDef doc fill:#FFF9C4,stroke:#FBC02D,stroke-width:1px

    click Exercises "https://github.com/yaasiinaxmed/ultimate-solidity-course-for-complete-beginners/tree/main/Exercises/"
    click Solutions "https://github.com/yaasiinaxmed/ultimate-solidity-course-for-complete-beginners/tree/main/Solutions/"
    click OZ "https://github.com/yaasiinaxmed/ultimate-solidity-course-for-complete-beginners/tree/main/.deps/npm/@openzeppelin/contracts/"
    click OZAccess "https://github.com/yaasiinaxmed/ultimate-solidity-course-for-complete-beginners/tree/main/.deps/npm/@openzeppelin/contracts/access/"
    click OZUtils "https://github.com/yaasiinaxmed/ultimate-solidity-course-for-complete-beginners/tree/main/.deps/npm/@openzeppelin/contracts/utils/"
    click RemixTests "https://github.com/yaasiinaxmed/ultimate-solidity-course-for-complete-beginners/tree/main/.deps/remix-tests/"
    click Readme "https://github.com/yaasiinaxmed/ultimate-solidity-course-for-complete-beginners/blob/main/readme.md"
    click Gitignore "https://github.com/yaasiinaxmed/ultimate-solidity-course-for-complete-beginners/blob/main/.gitignore"

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