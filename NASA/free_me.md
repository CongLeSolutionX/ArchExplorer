---
created: 2025-03-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExb3ptMWhnczg1dDQzeTR5a2d4c2J6dWxkdGRxNnBheHU1bGJrMXp4dyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/aEwLTJvYxwo1L09oyP/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----



# Free Me
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
title: "Free Me"
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
    'graph': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#2ff9',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph TD
    Environment["Environment Layer:<br>Command-Line/Documentation"]:::environment
    Config["Configuration Loader:<br>App Config"]:::config
    Input["Input Handler:<br>E-mail Ingestion"]:::input
    Mode["Mode Selector:<br>Real-time/Post-processing"]:::decision
    Engine["Filtering Engine:<br>Regex Matching"]:::engine
    Subscription["Subscription Management:<br>Admin Subscriptions"]:::config
    Direct["Direct Resend/Forwarding Module"]:::output
    Digest["Digest Generator:<br>Aggregates similar messages"]:::output
    Archive["Historical Archive:<br>Store & Query"]:::archive

    %% External influences
    Environment -->|"doc influence"| Config

    %% Configuration influence on components
    Config -->|"cfg"| Input
    Config -->|"cfg"| Engine
    Config -->|"cfg"| Subscription
    Config -->|"cfg"| Direct
    Config -->|"cfg"| Digest
    Config -->|"cfg"| Archive

    %% Processing pipeline flow
    Input -->|"choose mode"| Mode
    Mode -->|"process mode"| Engine
    Engine -->|"match subs"| Subscription
    Engine -->|"send direct"| Direct
    Engine -->|"generate digest"| Digest
    Engine <-->|"archive query"| Archive
    Direct -->|"store email"| Archive
    Digest -->|"store email"| Archive

    %% Styles
    classDef environment fill:#FFC3,stroke:#333,stroke-width:2px
    classDef config fill:#FFA5,stroke:#333,stroke-width:2px
    classDef input fill:#ADD4,stroke:#333,stroke-width:2px
    classDef engine fill:#EEC4,stroke:#333,stroke-width:2px
    classDef output fill:#FFC2,stroke:#333,stroke-width:2px
    classDef archive fill:#D3D3,stroke:#333,stroke-width:2px
    classDef decision fill:#EEE2,stroke:#333,stroke-width:2px,stroke-dasharray: 5 5

    %% Click Events
    click Input "https://github.com/pkolano/freeme/tree/master/freeme"
    click Engine "https://github.com/pkolano/freeme/tree/master/freeme"
    click Subscription "https://github.com/pkolano/freeme/tree/master/freemerc"
    click Direct "https://github.com/pkolano/freeme/blob/master/freeme_relay.sample"
    click Config "https://github.com/pkolano/freeme/tree/master/freemerc"
    click Environment "https://github.com/pkolano/freeme/blob/master/freeme.1"
    
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
