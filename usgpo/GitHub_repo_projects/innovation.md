---
created: 2025-06-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/usgpo/innovation
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExc3lodDZzaXl2ZzVscG14ZjQ5MWdzOWI5eWIxaXNhYWFvdm1pMHBuYiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/y2pJDVHLeZtlu/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# innovation repo project
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
title: "innovation repo project"
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
    %% Developer Workstation (Source Files)
    subgraph "Developer Workstation" 
        direction TB
        DEV["Developer Workstation"]:::source
        DF1["Gemfile & Gemfile.lock"]:::source
        DF2["README.md, LICENSE.md, CONTRIBUTING.md"]:::source
        DF3["_pages, _events, resources/reports content"]:::source
        DF4["assets/css/main.scss"]:::source
        DF5["assets/img/*"]:::source
    end

    %% Version Control & CI
    subgraph "GitHub Repository" 
        direction TB
        GIT["GitHub Repo"]:::source
        GR1[".gitignore"]:::source
        GR2["CODEOWNERS"]:::source
        GR3["CONTRIBUTING.md"]:::source
    end

    %% Jekyll Build Engine
    subgraph "Jekyll Build Engine" 
        direction TB
        BEEngine["Build Engine (Jekyll)"]:::build
        BE1["_config.yml"]:::build
        BE2["_data/"]:::build
        BE3["_includes/"]:::build
        BE4["_layouts/"]:::build
        BE5["_pages/"]:::build
        BE6["_events/"]:::build
        BE7["assets/css/main.scss"]:::build
        BE8["assets/img/"]:::build
        BE9["index.md"]:::build
    end

    %% Hosting Layer
    HC["GitHub Pages + CDN"]:::hosting

    %% End Users
    BR["End User Browser"]:::client

    %% Connections
    DEV -->|git push| GIT
    GIT -->|trigger build| BEEngine
    BEEngine -->|deploy site| HC
    BR -->|HTTP GET| HC
    HC -->|serves static site| BR

    %% Click Events
    click DF1 "https://github.com/usgpo/innovation/tree/master//Gemfile"
    click DF2 "https://github.com/usgpo/innovation/blob/master//README.md"
    click DF3 "https://github.com/usgpo/innovation/tree/master//_pages"
    click DF4 "https://github.com/usgpo/innovation/blob/master//assets/css/main.scss"
    click DF5 "https://github.com/usgpo/innovation/tree/master//assets/img"
    click GR1 "https://github.com/usgpo/innovation/blob/master//.gitignore"
    click GR2 "https://github.com/usgpo/innovation/tree/master//CODEOWNERS"
    click GR3 "https://github.com/usgpo/innovation/blob/master//CONTRIBUTING.md"
    click BE1 "https://github.com/usgpo/innovation/blob/master//_config.yml"
    click BE2 "https://github.com/usgpo/innovation/tree/master//_data"
    click BE3 "https://github.com/usgpo/innovation/tree/master//_includes"
    click BE4 "https://github.com/usgpo/innovation/tree/master//_layouts"
    click BE5 "https://github.com/usgpo/innovation/tree/master//_pages"
    click BE6 "https://github.com/usgpo/innovation/tree/master//_events"
    click BE7 "https://github.com/usgpo/innovation/blob/master//assets/css/main.scss"
    click BE8 "https://github.com/usgpo/innovation/tree/master//assets/img"
    click BE9 "https://github.com/usgpo/innovation/blob/master//index.md"

    %% Styles
    classDef source fill:#D0E6FF,stroke:#0366D6,color:#0366D6;
    classDef build fill:#FFE5B4,stroke:#FF8C00,color:#FF8C00;
    classDef hosting fill:#D4F1BE,stroke:#2E8B57,color:#2E8B57;
    classDef client fill:#E5D0FF,stroke:#6A5ACD,color:#6A5ACD;

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
