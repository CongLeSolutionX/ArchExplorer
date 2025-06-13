---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/monkeytypegame/monkeytype
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExcm8waTZlc3NoeHA5aGM3eTQ3M2Ruanc3ajdtZGFodTJyajRqcDRodyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/1229mlttgo8aR2/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# monkeytype repo project
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
title: "monkeytype repo project"
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
    subgraph Legend
        style Legend fill:#f5f5f5,stroke:#333
        A[Frontend Component]:::frontend
        B[Backend Service]:::backend
        C[(Database)]:::database
        D{{External Service}}:::external
    end

    %% Frontend Layer
    subgraph Frontend["Frontend Layer"]
        Client["Client Application"]:::frontend
        click Client "https://github.com/monkeytypegame/monkeytype/tree/master/frontend/src/"
        UI["UI Components"]:::frontend
        click UI "https://github.com/monkeytypegame/monkeytype/tree/master/frontend/src/ts/elements/"
        State["State Management"]:::frontend
        click State "https://github.com/monkeytypegame/monkeytype/tree/master/frontend/src/ts/states/"
        Theme["Theme System"]:::frontend
        click Theme "https://github.com/monkeytypegame/monkeytype/tree/master/frontend/static/themes/"
        
        subgraph TestSystem["Test System"]
            WordsGen["Words Generator"]:::frontend
            click WordsGen "https://github.com/monkeytypegame/monkeytype/blob/master/frontend/src/ts/test/words-generator.ts"
            TestLogic["Test Logic"]:::frontend
            click TestLogic "https://github.com/monkeytypegame/monkeytype/blob/master/frontend/src/ts/test/test-logic.ts"
            TestUI["Test UI"]:::frontend
            click TestUI "https://github.com/monkeytypegame/monkeytype/blob/master/frontend/src/ts/test/test-ui.ts"
            ResultProc["Results Processor"]:::frontend
            click ResultProc "https://github.com/monkeytypegame/monkeytype/blob/master/frontend/src/ts/test/result.ts"
        end

        subgraph Config["Configuration System"]
            ThemeCtrl["Theme Controller"]:::frontend
            click ThemeCtrl "https://github.com/monkeytypegame/monkeytype/blob/master/frontend/src/ts/controllers/theme-controller.ts"
            TestConfig["Test Configuration"]:::frontend
            click TestConfig "https://github.com/monkeytypegame/monkeytype/blob/master/frontend/src/ts/test/test-config.ts"
            SoundCtrl["Sound Controller"]:::frontend
            click SoundCtrl "https://github.com/monkeytypegame/monkeytype/blob/master/frontend/src/ts/controllers/sound-controller.ts"
        end
    end

    %% Backend Layer
    subgraph Backend["Backend Layer"]
        API["API Server"]:::backend
        click API "https://github.com/monkeytypegame/monkeytype/tree/master/backend/src/api/"
        Auth["Authentication System"]:::backend
        click Auth "https://github.com/monkeytypegame/monkeytype/blob/master/backend/src/init/firebase-admin.ts"
        DAL["Data Access Layer"]:::backend
        click DAL "https://github.com/monkeytypegame/monkeytype/tree/master/backend/src/dal/"
        
        subgraph Queues["Queue System"]
            EmailQ["Email Queue"]:::backend
            click EmailQ "https://github.com/monkeytypegame/monkeytype/blob/master/backend/src/queues/email-queue.ts"
            GeorgeQ["George Queue"]:::backend
            click GeorgeQ "https://github.com/monkeytypegame/monkeytype/blob/master/backend/src/queues/george-queue.ts"
            LaterQ["Later Queue"]:::backend
            click LaterQ "https://github.com/monkeytypegame/monkeytype/blob/master/backend/src/queues/later-queue.ts"
            MonkeyQ["Monkey Queue"]:::backend
            click MonkeyQ "https://github.com/monkeytypegame/monkeytype/blob/master/backend/src/queues/monkey-queue.ts"
        end

        subgraph Routes["API Routes"]
            Users["User Management"]:::backend
            click Users "https://github.com/monkeytypegame/monkeytype/blob/master/backend/src/api/routes/users.ts"
            Results["Test Results"]:::backend
            click Results "https://github.com/monkeytypegame/monkeytype/blob/master/backend/src/api/routes/results.ts"
            Leaderboards["Leaderboards"]:::backend
            click Leaderboards "https://github.com/monkeytypegame/monkeytype/blob/master/backend/src/api/routes/leaderboards.ts"
            ConfigAPI["Configuration"]:::backend
            click ConfigAPI "https://github.com/monkeytypegame/monkeytype/blob/master/backend/src/api/routes/configuration.ts"
            Quotes["Quotes"]:::backend
            click Quotes "https://github.com/monkeytypegame/monkeytype/blob/master/backend/src/api/routes/quotes.ts"
        end
    end

    %% Data Storage
    subgraph Storage["Data Storage"]
        MongoDB[(MongoDB)]:::database
        click MongoDB "https://github.com/monkeytypegame/monkeytype/blob/master/backend/src/init/db.ts"
        Redis[(Redis)]:::database
        click Redis "https://github.com/monkeytypegame/monkeytype/blob/master/backend/src/init/redis.ts"
        RedisScripts["Redis Scripts"]:::database
        click RedisScripts "https://github.com/monkeytypegame/monkeytype/tree/master/backend/redis-scripts/"
        Firebase{{Firebase Auth}}:::external
    end

    %% External Services
    Discord{{Discord}}:::external
    Email{{Email Service}}:::external
    Captcha{{Captcha System}}:::external

    %% Relationships
    Client --> API
    Client --> Firebase
    API --> Auth
    Auth --> Firebase
    API --> DAL
    DAL --> MongoDB
    DAL --> Redis
    API --> Queues
    Queues --> Email
    API --> Discord
    API --> Captcha

    %% Styles
    classDef frontend fill:#2196F3,stroke:#1565C0,color:#fff
    classDef backend fill:#4CAF50,stroke:#2E7D32,color:#fff
    classDef database fill:#FF9800,stroke:#EF6C00,color:#fff
    classDef external fill:#9E9E9E,stroke:#616161,color:#fff
    
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
