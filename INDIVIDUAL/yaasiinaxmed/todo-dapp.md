---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/yaasiinaxmed/todo-dapp
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExMjdzMjVieWtrMHMwNXp2bzV5eGZxeWd1cTN2ajBqM2twMXR0MHFxZCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/xT9DPIlGnuHpr2yObu/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# todo-dapp repo project
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
title: "todo-dapp repo project"
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
    subgraph Developer_Environment["Developer Environment"]
    direction TB
        VITE["Vite Build Configuration"]:::dev
        POSTCSS["PostCSS Configuration"]:::dev
        TAILWINDCFG["Tailwind CSS Configuration"]:::dev
        ESLINT["ESLint Configuration"]:::dev
        PKG["Package Dependencies & Scripts"]:::dev
    end

    subgraph Static_Asset_Server["Static Asset Server"]
    direction TB
        PUBLIC["public/"]:::server
    end

    subgraph Frontend_UI_Layer["Frontend UI Layer"]
    direction TB
        BROWSER["User’s Web Browser<br/>(Client)"]:::ui
        INDEX["index.html"]:::ui
        MAIN["React SPA Entry Point"]:::ui
        APP["Main React Application Component"]:::ui
        STYLES["Global Styles (Tailwind CSS)"]:::ui
        ASSETS["Static Assets (Images, Icons, etc.)"]:::ui
    end

    subgraph Web3_Integration_Layer["Web3 Integration Layer"]
    direction TB
        THIRDWEB["Thirdweb SDK"]:::web3
        ABI["Smart Contract ABI"]:::web3
        WALLET["Ethereum Wallet"]:::web3
    end

    subgraph Blockchain_Network_Layer["Blockchain Network Layer"]
    direction TB
        NODE["Ethereum Node (Sepolia RPC)"]:::blockchain
        CONTRACT["Smart Contract State"]:::blockchain
    end

    %% Connections
    BROWSER -->|"GET index.html, JS, CSS"| PUBLIC
    PUBLIC -->|"serves assets"| BROWSER

    BROWSER -->|"loads"| INDEX
    INDEX -->|"boots app"| MAIN
    MAIN -->|"renders"| APP
    APP -->|"imports styles"| STYLES
    APP -->|"imports assets"| ASSETS

    APP -->|"init ThirdwebProvider"| THIRDWEB
    THIRDWEB -->|"uses ABI"| ABI

    APP -->|"prompt connect"| WALLET
    WALLET -->|"sign transactions"| APP

    THIRDWEB -->|"eth_call / eth_sendTransaction"| NODE
    NODE -->|"invoke addTask()/getTasks()"| CONTRACT
    CONTRACT -->|"emit events"| NODE
    NODE -->|"return data & events"| THIRDWEB

    %% Click Events
    click INDEX "https://github.com/yaasiinaxmed/todo-dapp/blob/main/index.html"
    click MAIN "https://github.com/yaasiinaxmed/todo-dapp/blob/main/src/main.jsx"
    click APP "https://github.com/yaasiinaxmed/todo-dapp/blob/main/src/App.jsx"
    click STYLES "https://github.com/yaasiinaxmed/todo-dapp/blob/main/src/index.css"
    click ASSETS "https://github.com/yaasiinaxmed/todo-dapp/tree/main/src/assets/"
    click ABI "https://github.com/yaasiinaxmed/todo-dapp/blob/main/src/abi.json"
    click PUBLIC "https://github.com/yaasiinaxmed/todo-dapp/tree/main/public/"
    click VITE "https://github.com/yaasiinaxmed/todo-dapp/blob/main/vite.config.js"
    click POSTCSS "https://github.com/yaasiinaxmed/todo-dapp/blob/main/postcss.config.js"
    click TAILWINDCFG "https://github.com/yaasiinaxmed/todo-dapp/blob/main/tailwind.config.js"
    click ESLINT "https://github.com/yaasiinaxmed/todo-dapp/blob/main/eslint.config.js"
    click PKG "https://github.com/yaasiinaxmed/todo-dapp/blob/main/package.json"

    %% Styles
    classDef ui fill:#D6EFFF,stroke:#000,stroke-width:1px;
    classDef web3 fill:#E6D5FF,stroke:#000,stroke-width:1px;
    classDef blockchain fill:#FFE6CC,stroke:#000,stroke-width:1px;
    classDef dev fill:#F0F0F0,stroke:#000,stroke-width:1px;
    classDef server fill:#E0FFE0,stroke:#000,stroke-width:1px;
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
