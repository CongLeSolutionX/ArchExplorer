---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/streamlit/streamlit
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExZmdoYWhxb3c2NmR6OGZoMzN5NWxqNjJmbmVxd3U0NDFobjc4ZHdvNyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/xUA7bjPYcgAvwq5CKc/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# streamlit repo project
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
title: "streamlit repo project"
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
    subgraph "Frontend Layer"
        Browser["Client Browser"]
        FrontendApp["Frontend Application"]:::frontend
        ComponentLib["Component Library"]:::frontend
        UIElements["UI Elements"]:::frontend
        Widgets["Widget System"]:::frontend
    end

    subgraph "Backend Layer"
        WebServer["Web Server"]:::backend
        WebSocket["WebSocket Handler"]:::backend
        ScriptRunner["Script Runner"]:::backend
        StateManager["State Management"]:::backend
        SessionMgr["Session Manager"]:::backend
        MediaMgr["Media File Manager"]:::backend
        CompRegistry["Component Registry"]:::backend
    end

    subgraph "Data Layer"
        Cache["Cache Storage"]:::storage
        ProtoDefs["Protocol Definitions"]:::proto
    end

    Browser <--> FrontendApp
    FrontendApp --> ComponentLib
    ComponentLib --> UIElements
    ComponentLib --> Widgets
    FrontendApp <-->|WebSocket| WebSocket
    WebSocket --> WebServer
    WebServer --> ScriptRunner
    ScriptRunner --> StateManager
    StateManager --> Cache
    ScriptRunner --> MediaMgr
    StateManager --> SessionMgr
    ScriptRunner --> CompRegistry
    WebSocket -.->|Uses| ProtoDefs

    classDef frontend fill:#2374ab
    classDef backend fill:#57a773
    classDef storage fill:#ffc857
    classDef proto fill:#ef6461

    click FrontendApp "https://github.com/streamlit/streamlit/tree/develop/frontend/app/src"
    click ComponentLib "https://github.com/streamlit/streamlit/tree/develop/frontend/lib/src/components"
    click WebSocket "https://github.com/streamlit/streamlit/blob/develop/lib/streamlit/web/server/browser_websocket_handler.py"
    click ScriptRunner "https://github.com/streamlit/streamlit/blob/develop/lib/streamlit/runtime/scriptrunner/script_runner.py"
    click StateManager "https://github.com/streamlit/streamlit/tree/develop/lib/streamlit/runtime/state"
    click Cache "https://github.com/streamlit/streamlit/tree/develop/lib/streamlit/runtime/caching/storage"
    click SessionMgr "https://github.com/streamlit/streamlit/blob/develop/lib/streamlit/runtime/session_manager.py"
    click CompRegistry "https://github.com/streamlit/streamlit/blob/develop/lib/streamlit/components/v1/component_registry.py"
    click MediaMgr "https://github.com/streamlit/streamlit/blob/develop/lib/streamlit/runtime/media_file_manager.py"
    click ProtoDefs "https://github.com/streamlit/streamlit/tree/develop/proto/streamlit/proto"
    click WebServer "https://github.com/streamlit/streamlit/blob/develop/lib/streamlit/web/server/server.py"
    click UIElements "https://github.com/streamlit/streamlit/tree/develop/frontend/lib/src/components/elements"
    click Widgets "https://github.com/streamlit/streamlit/tree/develop/frontend/lib/src/components/widgets"
    
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
