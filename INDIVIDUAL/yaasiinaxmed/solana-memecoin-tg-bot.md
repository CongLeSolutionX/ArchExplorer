---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/yaasiinaxmed/solana-memecoin-tg-bot
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExNTdwNjc2NDlvYWw4ZWVnZzR3cXVsYjVqdzhtbHozMWk2Ym9lanJlciZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/5NoLXTfMR1xAfsYcgF/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# solana-memecoin-tg-bot repo project
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
title: "solana-memecoin-tg-bot repo project"
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
    subgraph User_Side["User Side"]
        User["Telegram Client"]:::external
    end

    subgraph Telegram_Infrastructure["Telegram Infrastructure"]
        TelegramAPI["Telegram Bot API"]:::external
    end

    subgraph Bot_Application["Bot Application"]
    direction TB
        BotEntry["Entry Point<br/>(bot/main.py)<br/>– Command Router<br/>– Response Formatter"]:::code
        UtilsPkg["Utils Package<br/>(utils/__init__.py)"]:::code
        SolUtils["Solana Utils Module<br/>(utils/solana_utils.py)"]:::code
        Config["Configuration<br/>(.env)"]:::config
    end

    subgraph Solana_Network["Solana Network"]
        SolRPC["Solana RPC Endpoint<br/>(Devnet/Mainnet)"]:::external
    end

    User -->|"sendCommand"| TelegramAPI
    TelegramAPI -->|"receiveUpdate"| BotEntry
    BotEntry -->|"loadConfig"| Config
    BotEntry -->|"invokeUtils"| SolUtils
    SolUtils -->|"callRPC"| SolRPC
    SolRPC -->|"returnData"| SolUtils
    SolUtils -->|"returnResult"| BotEntry
    BotEntry -->|"formatReply"| TelegramAPI
    TelegramAPI -->|"deliverMessage"| User

    click BotEntry "https://github.com/yaasiinaxmed/solana-memecoin-tg-bot/blob/main/bot/main.py"
    click SolUtils "https://github.com/yaasiinaxmed/solana-memecoin-tg-bot/blob/main/utils/solana_utils.py"
    click Config "https://github.com/yaasiinaxmed/solana-memecoin-tg-bot/blob/main/.env"
    click README "https://github.com/yaasiinaxmed/solana-memecoin-tg-bot/blob/main/README.md"
    click UtilsPkg "https://github.com/yaasiinaxmed/solana-memecoin-tg-bot/blob/main/utils/__init__.py"

    classDef external fill:#b7eeb7,stroke:#333,stroke-width:1px
    classDef code fill:#b1c1f0,stroke:#333,stroke-width:1px
    classDef config fill:#f0d8b0,stroke:#333,stroke-width:1px

    class User,TelegramAPI,SolRPC external
    class BotEntry,SolUtils,UtilsPkg code
    class Config config

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
