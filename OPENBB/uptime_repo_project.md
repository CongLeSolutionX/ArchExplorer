---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/OpenBB-finance/uptime
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExMXVjejV3dnVjc2o5MXd3eXBvcDR1cHlzbHQ1Z2R6YjY0ZHpmdjJ6OCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/hL9q5k9dk9l0wGd4e0/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# uptime repo project
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
title: "uptime repo project"
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
    Scheduler["Scheduler (Cron Trigger)"]:::scheduler

    subgraph "GitHub Actions Workflows"
        UP["Uptime CI Workflow"]:::workflow
        RT["Response Time CI Workflow"]:::workflow
        GR["Graphs CI Workflow"]:::workflow
        SU["Summary CI Workflow"]:::workflow
        STA["Static Site CI Workflow"]:::workflow
    end

    subgraph "External Services"
        OPENBB["openbb.co"]:::external
        DOCS["docs.openbb.co"]:::external
        BOTPLAT["Bot Platform"]:::external
        BOTAPI["Bot API"]:::external
        PRO["OpenBB Pro"]:::external
        PROBE["Pro Backend"]:::external
        AIBACK["AI Backend"]:::external
    end

    API_DATA["api/ (JSON Endpoints)"]:::datastore
    HISTORY["history/ (YAML History)"]:::datastore
    GRAPHS["graphs/ (PNG Graphs)"]:::datastore

    GH_PAGES["GitHub Pages (Status Site)"]:::hosting
    ISSUES["GitHub Issues (Incident Logging)"]:::user
    USERS["End Users"]:::user

    Scheduler --> UP
    Scheduler --> RT

    UP --> OPENBB
    UP --> DOCS
    UP --> BOTPLAT
    UP --> BOTAPI
    UP --> PRO
    UP --> PROBE
    UP --> AIBACK

    RT --> OPENBB
    RT --> DOCS
    RT --> BOTPLAT
    RT --> BOTAPI
    RT --> PRO
    RT --> PROBE
    RT --> AIBACK

    UP --> API_DATA
    RT --> API_DATA

    UP --> HISTORY
    RT --> HISTORY

    HISTORY --> GR
    HISTORY --> SU
    API_DATA --> SU

    GR --> GRAPHS
    GRAPHS --> STA
    SU --> STA

    STA --> GH_PAGES
    GH_PAGES --> USERS

    UP -.->|on failure| ISSUES
    RT -.->|on failure| ISSUES

    click UP "https://github.com/openbb-finance/uptime/blob/master/.github/workflows/uptime.yml"
    click RT "https://github.com/openbb-finance/uptime/blob/master/.github/workflows/response-time.yml"
    click GR "https://github.com/openbb-finance/uptime/blob/master/.github/workflows/graphs.yml"
    click SU "https://github.com/openbb-finance/uptime/blob/master/.github/workflows/summary.yml"
    click STA "https://github.com/openbb-finance/uptime/blob/master/.github/workflows/site.yml"
    click API_DATA "https://github.com/openbb-finance/uptime/tree/master/api/"
    click HISTORY "https://github.com/openbb-finance/uptime/tree/master/history/"
    click GRAPHS "https://github.com/openbb-finance/uptime/tree/master/graphs/"

    classDef workflow fill:#f9d5b3,stroke:#f08a5d,stroke-width:1px
    classDef datastore fill:#d0e6f6,stroke:#004e89,stroke-width:1px
    classDef external fill:#c3f584,stroke:#6a994e,stroke-width:1px
    classDef hosting fill:#e0bbf0,stroke:#5e548e,stroke-width:1px
    classDef scheduler fill:#ffe8d6,stroke:#ff4500,stroke-width:1px
    classDef user fill:#f0f0f0,stroke:#888,stroke-width:1px
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