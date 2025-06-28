---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is an ongoing document collecting notes for personal educational purposes and references. 
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExeHJ4YXdtYjJpMDl0MzEwYmU4ZzBobG0waGNiN3MzNzR0d2R2NnMwNSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/26gssNOlBJKjEM3yo/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----

# mermaid-bot
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## A Diagrammatic Guide 


```mermaid
---
title: "MERMAID-JS - mermaid-bot"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "flowchart": { "htmlLabels": true, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TD
    GH["GitHub"]:::external
    PS["Probot Server"]:::container
    IDX["Initialization (index.ts)"]:::core
    ELG["Eligibility Check (eligibleUsers.ts)"]:::core
    NTF["Notification Handler (notify.ts)"]:::core
    DF["Dockerfile"]:::deploy
    AY["app.yml"]:::deploy
    PK["package.json"]:::deploy
    USR["eligibleUsers.json"]:::config
    ENV[".env.example"]:::config
    TS["Testing Suite"]:::test

    GH -->|"webhook_event"| PS
    PS -->|"initializes"| IDX
    IDX -->|"calls"| ELG
    ELG -->|"triggers"| NTF
    DF -->|"configures"| PS
    AY -->|"configures"| PS
    PK -->|"configures"| PS
    ENV -->|"provides_env"| IDX
    USR -->|"configures"| ELG
    TS -->|"validates"| PS

    click DF "https://github.com/mermaid-js/mermaid-bot/tree/main/Dockerfile"
    click AY "https://github.com/mermaid-js/mermaid-bot/blob/main/app.yml"
    click PK "https://github.com/mermaid-js/mermaid-bot/blob/main/package.json"
    click IDX "https://github.com/mermaid-js/mermaid-bot/blob/main/src/index.ts"
    click ELG "https://github.com/mermaid-js/mermaid-bot/blob/main/src/eligibleUsers.ts"
    click NTF "https://github.com/mermaid-js/mermaid-bot/blob/main/src/notify.ts"
    click USR "https://github.com/mermaid-js/mermaid-bot/blob/main/eligibleUsers.json"
    click ENV "https://github.com/mermaid-js/mermaid-bot/blob/main/.env.example"
    click TS "https://github.com/mermaid-js/mermaid-bot/tree/main/test"

    classDef external fill:#fc44,stroke:#333,stroke-width:2px
    classDef container fill:#cef3,stroke:#333,stroke-width:2px
    classDef core fill:#dda3,stroke:#333,stroke-width:2px
    classDef deploy fill:#9cf3,stroke:#333,stroke-width:2px
    classDef config fill:#f6c3,stroke:#333,stroke-width:2px
    classDef test fill:#fcc3,stroke:#333,stroke-width:2px
    
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

  Closing_quote ~~~ My_Meme
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }

```

---
> **Licenses:**
>
> - **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
> - **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).
> 
---

