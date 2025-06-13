---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/bluesky-social/social-app
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




# social-app repo project
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
title: "social-app repo project"
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
    subgraph Client["Client Applications"]
        MobileApp["Mobile App Core"]:::client
        SharedComp["Shared Components"]:::client
    end

    subgraph Server["Server Components"]
        Bskyweb["Bskyweb Service"]:::server
        Embedr["Embedr Service"]:::server
        LinkService["Link Service"]:::server
        OGCard["OG Card Service"]:::server
    end

    subgraph PresentationLayer["Presentation Layer"]
        Views["Views"]:::ui
        Components["Components"]:::ui
        Screens["Screens"]:::ui
        Shell["Shell/Navigation"]:::ui
    end

    subgraph StateManagement["State Management"]
        Session["Session Management"]:::state
        Queries["Queries"]:::state
        Preferences["Preferences"]:::state
        Cache["Cache Management"]:::state
    end

    subgraph BusinessLogic["Business Logic"]
        API["API Integration"]:::logic
        Auth["Authentication"]:::logic
        Feed["Feed Management"]:::logic
        Moderation["Content Moderation"]:::logic
    end

    subgraph CoreServices["Core Services"]
        Localization["Localization"]:::service
        Storage["Storage"]:::service
        Logging["Logging"]:::service
        Analytics["Analytics"]:::service
    end

    subgraph CustomModules["Custom Modules"]
        BottomSheet["Bottom Sheet"]:::module
        BGNotification["Background Notification Handler"]:::module
        GIFView["GIF View"]:::module
        SwissArmy["Swiss Army Utilities"]:::module
    end

    MobileApp --> PresentationLayer
    SharedComp --> PresentationLayer
    
    PresentationLayer --> StateManagement
    StateManagement --> BusinessLogic
    BusinessLogic --> CoreServices
    BusinessLogic --> Server
    
    CustomModules --> PresentationLayer
    CustomModules --> BusinessLogic

    classDef client fill:#3498db,stroke:#2980b9,color:#fff
    classDef server fill:#e74c3c,stroke:#c0392b,color:#fff
    classDef ui fill:#2ecc71,stroke:#27ae60,color:#fff
    classDef state fill:#9b59b6,stroke:#8e44ad,color:#fff
    classDef logic fill:#f1c40f,stroke:#f39c12,color:#000
    classDef service fill:#95a5a6,stroke:#7f8c8d,color:#fff
    classDef module fill:#e67e22,stroke:#d35400,color:#fff

    click MobileApp "https://github.com/bluesky-social/social-app/blob/main/src/App.native.tsx"
    click SharedComp "https://github.com/bluesky-social/social-app/tree/main/src/components"
    click Bskyweb "https://github.com/bluesky-social/social-app/tree/main/bskyweb"
    click Embedr "https://github.com/bluesky-social/social-app/tree/main/bskyweb/cmd/embedr"
    click LinkService "https://github.com/bluesky-social/social-app/tree/main/bskylink"
    click OGCard "https://github.com/bluesky-social/social-app/tree/main/bskyogcard"
    click Views "https://github.com/bluesky-social/social-app/tree/main/src/view"
    click Components "https://github.com/bluesky-social/social-app/tree/main/src/components"
    click Screens "https://github.com/bluesky-social/social-app/tree/main/src/screens"
    click Shell "https://github.com/bluesky-social/social-app/tree/main/src/view/shell"
    click Session "https://github.com/bluesky-social/social-app/tree/main/src/state/session"
    click Queries "https://github.com/bluesky-social/social-app/tree/main/src/state/queries"
    click Preferences "https://github.com/bluesky-social/social-app/tree/main/src/state/preferences"
    click Cache "https://github.com/bluesky-social/social-app/tree/main/src/state/cache"
    click API "https://github.com/bluesky-social/social-app/tree/main/src/lib/api"
    click Feed "https://github.com/bluesky-social/social-app/tree/main/src/lib/api/feed"
    click Moderation "https://github.com/bluesky-social/social-app/tree/main/src/lib/moderation"
    click Localization "https://github.com/bluesky-social/social-app/tree/main/src/locale"
    click Storage "https://github.com/bluesky-social/social-app/tree/main/src/storage"
    click Logging "https://github.com/bluesky-social/social-app/tree/main/src/logger"
    click BottomSheet "https://github.com/bluesky-social/social-app/tree/main/modules/bottom-sheet"
    click BGNotification "https://github.com/bluesky-social/social-app/tree/main/modules/expo-background-notification-handler"
    click GIFView "https://github.com/bluesky-social/social-app/tree/main/modules/expo-bluesky-gif-view"
    click SwissArmy "https://github.com/bluesky-social/social-app/tree/main/modules/expo-bluesky-swiss-army"
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