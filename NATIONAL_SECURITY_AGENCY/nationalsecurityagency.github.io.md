---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExb2ZlaTdrbzJobzd2eTF5dzFwOW5rcjhvN3RyeWhnbmhyaXQ3b2E1ayZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/kyd2BtRpfv4q8O5oq0/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# NationalSecurityAgency.github.io
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## A Diagrammatic Guide



```mermaid
---
title: "NATIONAL SECURITY AGENCY - NationalSecurityAgency.github.io"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "flowchart": {"htmlLabels": true, 'curve': 'natural'},
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#f231',
      'primaryTextColor': '#239',
      'primaryBorderColor': '#7c2',
      'textColor': '#F8B229',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TD
    %% Content & Data Layer
    subgraph Content_and_Data["Content & Data"]
        Pages["Pages (Markdown)"]
        Data["Data Configuration (_data)"]
    end

    %% Build Engine Layer
    subgraph Build_Engine["Build Engine"]
        Jekyll["Jekyll Build Process"]
    end

    %% Template & Theme Layer
    subgraph Template_and_Theme["Template & Theme"]
        Layouts["Layouts"]
        Includes["Includes"]
        Styles["Styles"]
    end

    %% CI/CD Pipeline Layer
    subgraph CI_CD_Pipeline["CI/CD Pipeline"]
        CI["GitHub Actions Pipeline"]
    end

    %% External Dependencies Layer
    subgraph External_Dependencies["External Dependencies"]
        USWDS["USWDS Theme"]
    end

    %% Output Layer
    subgraph Output["Output"]
        StaticSite["Final Static Site Output"]
    end

    %% Flow Connections
    Pages -->|"feeds"| Jekyll
    Data  -->|"feeds"| Jekyll
    CI    -->|"triggers"| Jekyll
    Jekyll -->|"generates"| Layouts
    Jekyll -->|"generates"| Includes
    Jekyll -->|"generates"| Styles
    USWDS -->|"influences"| Styles
    Jekyll -->|"builds"| StaticSite

    %% Click Events for Component Mapping
    click Jekyll "https://github.com/nationalsecurityagency/nationalsecurityagency.github.io/blob/main/_config.yml"
    click Jekyll "https://github.com/nationalsecurityagency/nationalsecurityagency.github.io/tree/main/Gemfile"
    click Jekyll "https://github.com/nationalsecurityagency/nationalsecurityagency.github.io/blob/main/Gemfile.lock"
    click Layouts "https://github.com/nationalsecurityagency/nationalsecurityagency.github.io/tree/main/_layouts"
    click Includes "https://github.com/nationalsecurityagency/nationalsecurityagency.github.io/tree/main/_includes"
    click Styles "https://github.com/nationalsecurityagency/nationalsecurityagency.github.io/tree/main/_sass"
    click Styles "https://github.com/nationalsecurityagency/nationalsecurityagency.github.io/blob/main/css/nsa.scss"
    click Data "https://github.com/nationalsecurityagency/nationalsecurityagency.github.io/tree/main/_data"
    click Pages "https://github.com/nationalsecurityagency/nationalsecurityagency.github.io/tree/main/pages"
    click CI "https://github.com/nationalsecurityagency/nationalsecurityagency.github.io/tree/main/.github/workflows"

    %% Styles and Classes
    classDef content fill:#FDA5,stroke:#333,stroke-width:2px
    classDef build fill:#AE65,stroke:#333,stroke-width:2px
    classDef template fill:#AFB4,stroke:#333,stroke-width:2px
    classDef ci fill:#F5B7,stroke:#333,stroke-width:2px
    classDef external fill:#D7E2,stroke:#333,stroke-width:2px
    classDef output fill:#F9E7,stroke:#333,stroke-width:2px

    class Pages,Data content
    class Jekyll build
    class Layouts,Includes,Styles template
    class CI ci
    class USWDS external
    class StaticSite output
    
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
