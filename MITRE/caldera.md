---
created: 2025-06-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/mitre/caldera
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




# caldera repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>

---


```mermaid
---
title: "caldera repo project"
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
    Client["Client Request"]:::external
    Client -->|"HTTP"| WebInterface

    subgraph "Backend Components"
        CoreEngine["Core Server Engine\n(asynchronous C2)"]:::backend
        RESTAPI["REST API Layer"]:::backend
        APIv2["API v2 (handlers,managers,schemas)"]:::backend
        Services["Service Layer"]:::backend
        Domain["Domain Objects & Logic"]:::backend
        Utility["Utility Libraries"]:::backend
    end

    subgraph "Frontend Components"
        WebInterface["Web Interface"]:::frontend
    end

    subgraph "Extension & Configuration"
        Plugins["Plugin System"]:::plugins
        DataConfig["Data Stores & Configuration"]:::config
    end

    External["External Dependencies\n(Docker,NodeJS,Go)"]:::external

    %% Connections between components
    Client -->|"HTTP"| WebInterface
    WebInterface -->|"APIRequest"| RESTAPI
    CoreEngine -->|"Orchestrates"| RESTAPI
    RESTAPI -->|"includes"| APIv2
    RESTAPI -->|"calls"| Services
    Services -->|"executes"| Domain
    Services -->|"utilizes"| Utility
    CoreEngine -->|"integrates"| Plugins
    DataConfig -->|"supplies"| CoreEngine
    External -->|"deploys"| CoreEngine

    %% Click Events for mapped components
    click CoreEngine "https://github.com/mitre/caldera/blob/master/server.py"
    click CoreEngine "https://github.com/mitre/caldera/blob/master/app/__init__.py"
    click RESTAPI "https://github.com/mitre/caldera/tree/master/app/api"
    click APIv2 "https://github.com/mitre/caldera/tree/master/app/api/v2"
    click WebInterface "https://github.com/mitre/caldera/tree/master/templates"
    click WebInterface "https://github.com/mitre/caldera/tree/master/static"
    click Services "https://github.com/mitre/caldera/tree/master/app/service"
    click Plugins "https://github.com/mitre/caldera/tree/master/plugins"
    click DataConfig "https://github.com/mitre/caldera/tree/master/data"
    click DataConfig "https://github.com/mitre/caldera/tree/master/conf"
    click Utility "https://github.com/mitre/caldera/tree/master/app/utility"
    click Domain "https://github.com/mitre/caldera/tree/master/app/objects"

    %% Styles
    classDef external fill:#ffcc00,stroke:#000,stroke-width:2px;
    classDef backend fill:#cce5ff,stroke:#003366,stroke-width:2px;
    classDef frontend fill:#d4edda,stroke:#155724,stroke-width:2px;
    classDef plugins fill:#f8d7da,stroke:#721c24,stroke-width:2px;
    classDef config fill:#fff3cd,stroke:#856404,stroke-width:2px;

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