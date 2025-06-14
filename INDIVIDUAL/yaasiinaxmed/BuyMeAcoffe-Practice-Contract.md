---
created: 2025-06-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/yaasiinaxmed/BuyMeAcoffe-Practice-Contract
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


# BuyMeAcoffe-Practice-Contract repo project
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
title: "BuyMeAcoffe-Practice-Contract repo project"
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
    subgraph Local_Development_Environment["Local Development Environment"]
    direction TB
        IDE["Developer IDE & CLI"]:::local
        Contracts["contracts/ <br/>(Source Code)"]:::local
        PackageJSON["package.json<br/>(dependencies & scripts)"]:::local
        Gitignore[".gitignore<br/>(env exclusions)"]:::local
        README["README.md<br/>(project docs)"]:::local
        Lockfile["package-lock.json<br/>(dependency lock)"]:::local
        ThirdwebPkg["ThirdWeb Contracts Extension<br/>(@thirdweb-dev/contracts)"]:::local
    end

    subgraph Hardhat_Toolchain["Hardhat Toolchain"]
    direction TB
        HardhatConfig["hardhat.config.js<br/>(configuration)"]:::local
        
        subgraph Workflow["Workflow"]
        direction TB
            Compile["Hardhat Compile<br/>(solc compile)"]:::local
            Test["Hardhat Test<br/>(optional)"]:::local
            Deploy["Hardhat Deploy<br/>(deploy scripts)"]:::local
        end
    end

    %% External Services
    ThirdWebAPI["ThirdWeb Dashboard/API"]:::external
    RPCProvider["RPC Provider<br/>(Infura/Alchemy)"]:::external

    %% On-Chain Network
    EthereumNet["Ethereum Network<br/>(Goerli/Mainnet)"]:::chain

    %% Data Flows
    IDE -->|edit code| Contracts
    Contracts -->|invoke compile| Compile
    Compile -->|outputs ABI & bytecode| Deploy
    Test -->|runs tests| Deploy
    Deploy -->|eth_sendTransaction| RPCProvider
    Deploy -->|register metadata| ThirdWebAPI
    RPCProvider -->|eth_sendTransaction| EthereumNet
    ThirdWebAPI -->|API calls| EthereumNet

    %% Click Events
    click Contracts "https://github.com/yaasiinaxmed/buymeacoffe-practice-contract/tree/main/contracts/"
    click HardhatConfig "https://github.com/yaasiinaxmed/buymeacoffe-practice-contract/blob/main/hardhat.config.js"
    click PackageJSON "https://github.com/yaasiinaxmed/buymeacoffe-practice-contract/blob/main/package.json"
    click Gitignore "https://github.com/yaasiinaxmed/buymeacoffe-practice-contract/blob/main/.gitignore"
    click README "https://github.com/yaasiinaxmed/buymeacoffe-practice-contract/blob/main/README.md"
    click Lockfile "https://github.com/yaasiinaxmed/buymeacoffe-practice-contract/blob/main/package-lock.json"

    %% Styling
    classDef local fill:#d4f8d4,stroke:#2d7a2d,stroke-width:2px
    classDef external fill:#ffe0b3,stroke:#cc7a00,stroke-width:2px
    classDef chain fill:#c2e0ff,stroke:#00509e,stroke-width:2px

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