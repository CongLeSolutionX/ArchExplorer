---
created: 2025-06-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/torproject/support
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


# support repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes (<ins>sometimes, entertainment purposes</ins>), personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


----

```mermaid
---
title: "support repo project"
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
    %% Top Layer: Development & Source
    subgraph "Developer & Source"
        Dev[/"Developer Workstation"/]:::process
        Repo["Source Repository"]:::code
    end

    %% External Services
    subgraph "External Services"
        Weblate((Weblate)):::external
        Issues((GitLab Issues)):::external
    end

    %% CI/CD Pipeline
    CI["GitLab CI/CD"]:::process

    %% Build Pipeline
    subgraph "Build Pipeline"
        subgraph "Asset Pipeline"
            SCSS("Compile SCSS"):::process
            Babel("Transpile JS"):::process
            StaticAssets["Assets/static/ CSS, JS, fonts, images"]:::code
        end
        Lektor["Lektor Build Engine"]:::process
    end

    %% Content & Templates
    subgraph "Content & Templates"
        Content(("content/")):::content
        Databags(("databags/")):::content
        Models(("models/")):::content
        Templates(("templates/")):::code
        I18n(("i18n/")):::content
    end

    %% Output Artifacts
    Artifacts["Generated Static Site"]:::code

    %% Deployment Targets
    subgraph "Deployment Targets"
        PublicServer["Public Web Server"]:::deployment
        OnionServer["Tor Onion Service"]:::deployment
    end

    %% End Users
    subgraph "End Users"
        Browser[(Browser)]:::client
        TorBrowser[(Tor Browser)]:::client
    end

    %% Flows
    Dev -->|push code| Repo
    Dev -->|develop & test| Lektor
    Repo -->|triggers build| CI
    CI -->|compile SCSS| SCSS
    CI -->|transpile JS| Babel
    CI -->|invoke build| Lektor
    SCSS --> StaticAssets
    Babel --> StaticAssets
    Content --> Lektor
    Databags --> Lektor
    Models --> Lektor
    Templates --> Lektor
    I18n --> Lektor
    Weblate -->|update translations| I18n
    CI -->|package| Artifacts
    Artifacts -->|deploy artifacts| PublicServer
    Artifacts -->|deploy artifacts| OnionServer
    Issues -.-> CI
    Browser -->|HTTP GET| PublicServer
    TorBrowser -->|HTTP GET| OnionServer

    %% Click Events
    click Repo "https://github.com/torproject/support/tree/main//"
    %% click ".gitlab-ci.yml" ".gitlab-ci.yml"
    click requirements.txt "https://github.com/torproject/support/blob/main/requirements.txt"
    click support.lektorproject "https://github.com/torproject/support/blob/main/support.lektorproject"
    click configs/scss.ini "https://github.com/torproject/support/blob/main/configs/scss.ini"
    click babel.cfg "https://github.com/torproject/support/blob/main/babel.cfg"
    click configs/i18n.ini "https://github.com/torproject/support/blob/main/configs/i18n.ini"
    click content "https://github.com/torproject/support/tree/main/content/"
    click databags "https://github.com/torproject/support/tree/main/databags/"
    click models "https://github.com/torproject/support/tree/main/models/"
    click templates "https://github.com/torproject/support/tree/main/templates/"

    %% Styles
    classDef code fill:#ADD8E6,stroke:#333,stroke-width:1px
    classDef content fill:#98FB98,stroke:#333,stroke-width:1px
    classDef process fill:#FFA500,stroke:#333,stroke-width:1px
    classDef external fill:#D8BFD8,stroke:#333,stroke-width:1px
    classDef deployment fill:#D3D3D3,stroke:#333,stroke-width:1px
    classDef client fill:#FFFF99,stroke:#333,stroke-width:1px
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