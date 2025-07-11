---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/ERCs
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExNDkxcjVkbjA1a3h6MmNodjdmeGpnNHpkOHl5MzV5ZTZzOXJqNTRzdSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/l0MYP5tAQKbLSGg7u/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# ERCs repo project
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
title: "ERCs repo project"
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
    %% Content Layer
    subgraph "Content Layer"
        ERCS_docs["ERC Documents"]:::content
        ERC_assets["ERC Assets"]:::content
    end
    Content_Source["Content Repository"]:::content
    ERCS_docs --> Content_Source
    ERC_assets --> Content_Source

    %% Presentation Layer
    subgraph "Presentation Layer"
        %% Jekyll Templating Components
        subgraph "Jekyll Templating Components"
            Layouts["Layouts"]:::presentation
            Includes["Includes"]:::presentation
            Data["Data"]:::presentation
            Config["Config"]:::presentation
        end
        JekyllEngine["Jekyll Templating Engine"]:::presentation
        Layouts --> JekyllEngine
        Includes --> JekyllEngine
        Data --> JekyllEngine
        Config --> JekyllEngine

        %% Static HTML & Styling
        subgraph "Static HTML & Styling"
            Index["index.html"]:::presentation
            NotFound["404.html"]:::presentation
            CNAME["CNAME"]:::presentation
            CSS["Styles (style.scss & override.css)"]:::presentation
        end
        JekyllEngine --> Index
        JekyllEngine --> NotFound
        JekyllEngine --> CNAME
        JekyllEngine --> CSS

        StaticSite["Static Site"]:::presentation
        Index --> StaticSite
        NotFound --> StaticSite
        CNAME --> StaticSite
        CSS --> StaticSite
    end
    Content_Source --> JekyllEngine

    %% Build & Deployment Infrastructure
    subgraph "Build & Deployment Infrastructure"
        %% CI/CD Workflows
        subgraph "CI/CD Workflows"
            Workflows["Workflows"]:::build
            IssueTemplates["Issue Templates"]:::build
            PRTemplate["PR Template"]:::build
        end
        %% Configuration & Dependency
        subgraph "Configuration & Dependency"
            Gemfile["Gemfile"]:::build
            GemfileLock["Gemfile.lock"]:::build
        end
        CICD["CI/CD Pipeline"]:::build
        BuildConfig["Build Config"]:::build

        Workflows --> CICD
        IssueTemplates --> CICD
        PRTemplate --> CICD

        Gemfile --> BuildConfig
        GemfileLock --> BuildConfig

        CICD --> StaticSite
        BuildConfig --> StaticSite

        Community["Community Contributions"]:::external
        Community --> CICD
    end

    %% External Deployment
    GitHubPages["GitHub Pages (Deployment)"]:::external
    StaticSite --> GitHubPages

    %% Click Events
    click ERCS_docs "https://github.com/ethereum/ercs/tree/master/ERCS/"
    click ERC_assets "https://github.com/ethereum/ercs/tree/master/assets/"
    click Layouts "https://github.com/ethereum/ercs/tree/master/_layouts/"
    click Includes "https://github.com/ethereum/ercs/tree/master/_includes/"
    click Data "https://github.com/ethereum/ercs/tree/master/_data/"
    click Config "https://github.com/ethereum/ercs/blob/master/_config.yml"
    click Index "https://github.com/ethereum/ercs/blob/master/index.html"
    click NotFound "https://github.com/ethereum/ercs/blob/master/404.html"
    click CNAME "https://github.com/ethereum/ercs/tree/master/CNAME"
    click CSS "https://github.com/ethereum/ercs/tree/master/assets/css/"
    click Workflows "https://github.com/ethereum/ercs/tree/master/.github/workflows/"
    click IssueTemplates "https://github.com/ethereum/ercs/tree/master/.github/ISSUE_TEMPLATE"
    click PRTemplate "https://github.com/ethereum/ercs/blob/master/PULL_REQUEST_TEMPLATE.md"
    click Gemfile "https://github.com/ethereum/ercs/tree/master/Gemfile"
    click GemfileLock "https://github.com/ethereum/ercs/blob/master/Gemfile.lock"

    %% Styles
    classDef content fill:#C3F7E0,stroke:#333,stroke-width:2px;
    classDef presentation fill:#F9E79F,stroke:#333,stroke-width:2px;
    classDef build fill:#AED6F1,stroke:#333,stroke-width:2px;
    classDef external fill:#F5B7B1,stroke:#333,stroke-width:2px;
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
