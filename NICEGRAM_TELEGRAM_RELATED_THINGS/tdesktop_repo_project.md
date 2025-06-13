---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/telegramdesktop/tdesktop
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

# tdesktop repo project
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
title: "tdesktop repo project"
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
    %% Platform & System Layer
    subgraph Platform
        Platform_Integration["Platform Integration"]
        ThirdParty["Third-Party Libraries"]
        SystemServices["System Services"]
    end

    %% Data Access Layer
    subgraph DataLayer
        Storage["File Management"]:::data
        Database["Local Database"]:::data
    end

    %% Network Layer
    subgraph NetworkLayer
        MTProto["MTProto Protocol"]:::network
        API["API Communication"]:::network
    end

    %% Business Logic Layer
    subgraph CoreLayer
        Core["Core Application"]:::core
        Session["Session Management"]:::core
        ChatLogic["Chat Processing"]:::core
        MediaProcessor["Media Processing"]:::media
    end

    %% Presentation Layer
    subgraph UILayer
        MainWindow["Main Window"]:::ui
        ChatInterface["Chat Interface"]:::ui
        MediaViewer["Media Viewer"]:::ui
        Settings["Settings Panel"]:::ui
        Auth["Authentication UI"]:::auth
    end

    %% Relationships
    MainWindow --> Core
    ChatInterface --> ChatLogic
    MediaViewer --> MediaProcessor
    Settings --> Core
    Auth --> Session

    Core --> MTProto
    Core --> Storage
    Session --> API
    ChatLogic --> Storage
    MediaProcessor --> Storage

    MTProto --> API
    API --> SystemServices
    Storage --> Database
    Core --> Platform

    %% Click Events
    click UILayer "https://github.com/telegramdesktop/tdesktop/tree/dev/Telegram/SourceFiles/ui/"
    click DataLayer "https://github.com/telegramdesktop/tdesktop/tree/dev/Telegram/SourceFiles/data/"
    click NetworkLayer "https://github.com/telegramdesktop/tdesktop/tree/dev/Telegram/SourceFiles/mtproto/"
    click ChatLogic "https://github.com/telegramdesktop/tdesktop/tree/dev/Telegram/SourceFiles/history/"
    click MediaProcessor "https://github.com/telegramdesktop/tdesktop/tree/dev/Telegram/SourceFiles/media/"
    click Auth "https://github.com/telegramdesktop/tdesktop/tree/dev/Telegram/SourceFiles/intro/"
    click Settings "https://github.com/telegramdesktop/tdesktop/tree/dev/Telegram/SourceFiles/settings/"
    click MainWindow "https://github.com/telegramdesktop/tdesktop/blob/dev/Telegram/SourceFiles/window/main_window.cpp"
    click MediaViewer "https://github.com/telegramdesktop/tdesktop/tree/dev/Telegram/SourceFiles/media/view/"
    click MTProto "https://github.com/telegramdesktop/tdesktop/tree/dev/Telegram/SourceFiles/mtproto/"
    click Storage "https://github.com/telegramdesktop/tdesktop/tree/dev/Telegram/SourceFiles/storage/"
    click Session "https://github.com/telegramdesktop/tdesktop/tree/dev/Telegram/SourceFiles/main/session/"
    click API "https://github.com/telegramdesktop/tdesktop/tree/dev/Telegram/SourceFiles/api/"
    click Core "https://github.com/telegramdesktop/tdesktop/tree/dev/Telegram/SourceFiles/core/"

    %% Legend
    subgraph Legend
        UI["UI Component"]:::ui
        CoreComp["Core Component"]:::core
        DataComp["Data Component"]:::data
        NetworkComp["Network Component"]:::network
        MediaComp["Media Component"]:::media
        AuthComp["Auth Component"]:::auth
        PlatformComp["Platform Component"]:::platform
    end
 %% Styles
    classDef ui fill:#e1f5fe,stroke:#01579b
    classDef core fill:#f3e5f5,stroke:#4a148c
    classDef data fill:#e8f5e9,stroke:#1b5e20
    classDef network fill:#fff3e0,stroke:#e65100
    classDef media fill:#fce4ec,stroke:#880e4f
    classDef platform fill:#eceff1,stroke:#263238
    classDef auth fill:#f1f8e9,stroke:#33691e



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