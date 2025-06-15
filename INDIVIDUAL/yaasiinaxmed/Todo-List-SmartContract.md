---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/yaasiinaxmed/Todo-List-SmartContract
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExdTRxOGhzZHh0MHc0dGhjcHd5eDQ0bDNtczV6bmU4Zm8yZHNmYzNvNSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/qoHbWYjhZqSPOyU9Z7/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# Todo-List-SmartContract repo project
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
title: "Todo-List-SmartContract repo project"
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
    subgraph Developer_Tools["Developer Tools"]
    direction TB
        IDE["Remix IDE"]:::dev
        ContractSrc["TodoList.sol"]:::dev
        RemixTests["Remix Tests"]:::dev
        Prettier[".prettierrc.json"]:::dev
        Readme["README.md"]:::dev
    end

    subgraph Build_and_Deployment["Build & Deployment"]
    direction TB
        Compiler["Solidity Compiler"]:::dev
        Artifact["TodoList.json (ABI+Bytecode)"]:::dev
        Metadata["TodoList_metadata.json"]:::dev
        BuildInfo["9ddfb7a4bb5d9f537d67c8c966a5b65e.json"]:::dev
        Scenario["scenario.json"]:::dev
        Deployer["Deployment Script"]:::dev
    end

    subgraph Blockchain_Network["Blockchain Network"]
    direction TB
        Sepolia["Sepolia Testnet"]:::chain
        DeployedContract["TodoList Contract"]:::chain
    end

    subgraph Frontend["Frontend"]
    direction TB
        ReactUI["React/Next.js UI"]:::ui
        Vercel["Vercel Hosting"]:::ui
        Wallet["MetaMask"]:::ui
        EthersJS["Ethers.js"]:::ui
    end

    subgraph External_Services["External Services"]
    direction TB
        RPC["RPC Provider<br/>(Infura/Alchemy)"]:::ext
        Etherscan["Etherscan Explorer"]:::ext
    end

    %% Connections
    ContractSrc -->|"compiled by"| Compiler
    RemixTests -->|"run tests on"| ContractSrc
    Prettier -->|"formats"| ContractSrc
    Readme -->|"describes project"| ContractSrc

    Compiler -->|"outputs"| Artifact
    Compiler -->|"outputs"| Metadata
    Compiler -->|"outputs"| BuildInfo
    Scenario -->|"configures"| Deployer
    Artifact -->|"used by"| Deployer
    Metadata -->|"used by"| Deployer
    BuildInfo -->|"used by"| Deployer

    Deployer -->|"deploys via RPC"| Sepolia
    Sepolia -->|"hosts"| DeployedContract

    ReactUI -->|"connects via"| EthersJS
    EthersJS -->|"through"| Wallet
    Wallet -->|"sends tx to"| RPC
    RPC -->|"forwards tx to"| Sepolia
    ReactUI -->|"fetches ABI from"| Artifact

    Sepolia -->|"verifies tx on"| Etherscan
    DeployedContract -->|"state stored on"| Sepolia

    ReactUI -->|"hosted on"| Vercel

    %% Click Events
    click RemixTests "https://github.com/yaasiinaxmed/todo-list-smartcontract/tree/main/.deps/remix-tests"
    click Prettier "https://github.com/yaasiinaxmed/todo-list-smartcontract/blob/main/.prettierrc.json"
    click Readme "https://github.com/yaasiinaxmed/todo-list-smartcontract/blob/main/README.md"
    click Artifact "https://github.com/yaasiinaxmed/todo-list-smartcontract/blob/main/artifacts/TodoList.json"
    click Metadata "https://github.com/yaasiinaxmed/todo-list-smartcontract/blob/main/artifacts/TodoList_metadata.json"
    click BuildInfo "https://github.com/yaasiinaxmed/todo-list-smartcontract/blob/main/artifacts/build-info/9ddfb7a4bb5d9f537d67c8c966a5b65e.json"
    click Scenario "https://github.com/yaasiinaxmed/todo-list-smartcontract/blob/main/scenario.json"

    %% Styles
    classDef dev fill:#D0E1FF,stroke:#0366d6,color:#0366d6,stroke-width:1.5px;
    classDef chain fill:#CFF5D2,stroke:#22863a,color:#22863a,stroke-width:1.5px;
    classDef ui fill:#FFE0B2,stroke:#d2691e,color:#d2691e,stroke-width:1.5px;
    classDef ext fill:#E0E0E0,stroke:#586069,color:#586069,stroke-width:1.5px;

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
