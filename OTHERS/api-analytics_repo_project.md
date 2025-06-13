---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/tom-draper/api-analytics
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExd3Y4aWxkOGM5c3M1MmFsZGt3MHB4Y3didTJra3gyeHA0eXhnOXJ6ZCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/h8RDGogSns9wpOJFzR/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# api-analytics repo project
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
title: "api-analytics repo project"
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
    subgraph ClientLayer["Client Layer (Middleware)"]
        direction TB
        Python["Python Middleware"]:::python
        NodeJS["Node.js Middleware"]:::nodejs
        Go["Go Middleware"]:::go
        Rust["Rust Middleware"]:::rust
        Ruby["Ruby Middleware"]:::ruby
        CSharp["C# Middleware"]:::csharp
    end

    subgraph ServerCore["Core Server Components"]
        direction TB
        Logger["Logger Server"]:::server
        API["API Server"]:::server
        Monitor["Monitor Server"]:::server
        Email["Email Service"]:::service
    end

    subgraph Storage["Data Layer"]
        DB[(Database)]:::database
        Backup["Backup System"]:::utility
    end

    subgraph Dashboard["Dashboard Application"]
        Frontend["Frontend (Svelte)"]:::frontend
        Components["UI Components"]:::frontend
        Assets["Public Assets"]:::static
    end

    ClientLayer --> |"Analytics Data"| Logger
    Logger --> |"Store"| DB
    API --> |"Read"| DB
    Monitor --> |"Check"| DB
    Monitor --> |"Alerts"| Email
    DB --> |"Backup"| Backup
    API --> |"Serve Data"| Frontend
    Frontend --> Components
    Frontend --> Assets

    classDef python fill:#3776AB,color:#fff
    classDef nodejs fill:#68A063,color:#fff
    classDef go fill:#00ADD8,color:#fff
    classDef rust fill:#DEA584,color:#000
    classDef ruby fill:#CC342D,color:#fff
    classDef csharp fill:#178600,color:#fff
    classDef server fill:#2b2b2b,color:#fff
    classDef service fill:#FF6B6B,color:#fff
    classDef database fill:#F8B229,color:#000
    classDef frontend fill:#FF8427,color:#fff
    classDef static fill:#A4B494,color:#000
    classDef utility fill:#95A5A6,color:#fff

    click Python "https://github.com/tom-draper/api-analytics/tree/main/analytics/python/python/api_analytics"
    click NodeJS "https://github.com/tom-draper/api-analytics/tree/main/analytics/nodejs"
    click Go "https://github.com/tom-draper/api-analytics/tree/main/analytics/go"
    click Rust "https://github.com/tom-draper/api-analytics/tree/main/analytics/rust"
    click Ruby "https://github.com/tom-draper/api-analytics/tree/main/analytics/ruby/api_analytics"
    click CSharp "https://github.com/tom-draper/api-analytics/tree/main/analytics/csharp/analytics"
    click Logger "https://github.com/tom-draper/api-analytics/tree/main/server/logger"
    click API "https://github.com/tom-draper/api-analytics/tree/main/server/api"
    click Monitor "https://github.com/tom-draper/api-analytics/tree/main/server/monitor"
    click Email "https://github.com/tom-draper/api-analytics/tree/main/server/email"
    click DB "https://github.com/tom-draper/api-analytics/tree/main/server/database"
    click Frontend "https://github.com/tom-draper/api-analytics/tree/main/dashboard/src"
    click Components "https://github.com/tom-draper/api-analytics/tree/main/dashboard/src/components"
    click Assets "https://github.com/tom-draper/api-analytics/tree/main/dashboard/public"
    click Backup "https://github.com/tom-draper/api-analytics/tree/main/server/tools/archive/backup"
    
```

<!-- 
## TODO

Source: [GitHub - CongLeSolutionX/tom-draper\_api-analytics: Lightweight monitoring and analytics for API frameworks.](https://github.com/CongLeSolutionX/tom-draper_api-analytics) -->

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
