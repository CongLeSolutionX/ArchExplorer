---
created: 2025-03-23 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExdXp3dTJrNjExdTd5c3JwdzlsZmo0ZmJqbjJhanN1d2JnMnBmNWN3ayZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/52qtwCtj9OLTi/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----



# JAWA
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---



```mermaid
---
title: "JamF - JAWA"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: default
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'lineColor': '#F8B229'
    }
  }
}%%
flowchart TD
    subgraph "External Integration"
        JF["Jamf Pro"]:::external
        OK["Okta"]:::external
        NP["Nginx Reverse Proxy"]:::external
    end

    subgraph "Backend Components"
        WS["Web Server (app.py)"]:::backend
        CV["Controller/Views Layer"]:::controller
        WR["Webhook Receiver (jawa_receiver.py)"]:::backend
        DC["Data & Configuration (data)"]:::data
        UT["Utility/Installer Scripts (bin)"]:::utility
    end

    subgraph "Frontend Components"
        UI["UI Templates (templates)"]:::frontend
        ST["Static Assets (static)"]:::frontend
    end

    DEP["Containerization/Deployment Support (Dockerfile.build)"]:::deployment

    JF -->|"HTTPS_request"| WS
    OK -->|"HTTPS_request"| WS
    NP -->|"SSL_termination"| WS

    WS -->|"routes_to"| CV
    CV -->|"accesses"| DC
    CV -->|"calls_utilities"| UT
    WS -->|"delegates_webhook"| WR

    CV -->|"renders_using"| UI
    CV -->|"serves"| ST
    DC -->|"informs_scheduling"| CV
    DEP -->|"builds_deploys"| WS

    click WS "https://github.com/jamf/jawa/blob/main/app.py"
    click CV "https://github.com/jamf/jawa/tree/main/views/"
    click UI "https://github.com/jamf/jawa/tree/main/templates/"
    click ST "https://github.com/jamf/jawa/tree/main/static/"
    click DC "https://github.com/jamf/jawa/tree/main/data/"
    click UT "https://github.com/jamf/jawa/tree/main/bin/"
    click WR "https://github.com/jamf/jawa/blob/main/webhook/jawa_receiver.py"
    click DEP "https://github.com/jamf/jawa/blob/main/Dockerfile.build"

    classDef external fill:#f88,stroke:#800,stroke-width:2px;
    classDef backend fill:#afa,stroke:#080,stroke-width:2px;
    classDef controller fill:#bbf,stroke:#225,stroke-width:2px;
    classDef data fill:#ffd,stroke:#aa0,stroke-width:2px;
    classDef utility fill:#fea,stroke:#c60,stroke-width:2px;
    classDef frontend fill:#cdf,stroke:#369,stroke-width:2px;
    classDef deployment fill:#efd,stroke:#5a5,stroke-width:2px;


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
