---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/OpenBB-finance/openbb-docs
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExamtjaHQxam1la2x4MTU1NmVoYTRsM3Fka3FsMXFwNHdtNjhpMnRvcyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3kuSo744UIPJjcJUEn/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# openbb-docs repo project
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
title: "openbb-docs repo project"
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
    %% Content Authoring Layer
    subgraph "Content Authoring Layer"
        direction TB
        MC["Markdown Content"]:::content
        subgraph "Python Preprocessing Scripts"
            direction TB
            GP1["generate_excel_markdown.py"]:::python
            GP2["generate_platform_markdown.py"]:::python
            GP3["generate_widgets_library.py"]:::python
        end
    end

    %% Presentation & Build Layer
    subgraph "Presentation & Build"
        direction TB
        subgraph "Docusaurus Configuration"
            direction TB
            DC1["docusaurus.config.ts"]:::config
            DC2["sidebars.js"]:::config
            DC3["tailwind.config.ts"]:::config
            DC4["babel.config.cjs"]:::config
            VS1["version-v3-sidebars.json"]:::config
            VS2["versions.json"]:::config
        end
        subgraph "Custom UI Components & Styles"
            direction TB
            CRC["src/components/"]:::react
            TO["src/theme/"]:::react
            GS["src/css/custom.css"]:::css
            CP["src/pages/"]:::pages
            SA["static/"]:::static
        end
        DSSG["Docusaurus SSG (Node.js)"]:::build
        TC["TailwindCSS Engine"]:::build
    end

    %% External Integration
    subgraph "External Integration"
        direction TB
        AC["initialAlgoliaCrawler.js"]:::external
        Algolia["Algolia Search API"]:::external
    end

    %% CI/CD Pipeline
    subgraph "Build & Deployment Pipeline"
        direction TB
        CI["deploy-gh-pages.yml"]:::ci
        Tests["test_platform_docs.py"]:::tests
    end

    %% Hosting & Delivery
    GH["GitHub Pages (CDN)"]:::hosting
    User["End User Browser"]:::user

    %% Relationships
    GP1 -->|generates| MC
    GP2 -->|generates| MC
    GP3 -->|generates| MC
    MC -->|"content + config"| DSSG
    CRC -->|"components + theme"| DSSG
    TO -->|"theme overrides"| DSSG
    GS -->|"styles"| DSSG
    CP -->|"custom pages"| DSSG
    SA -->|"assets"| DSSG
    DC1 -->|"configures"| DSSG
    DC2 -->|"sidebar info"| DSSG
    DC3 -->|"Tailwind setup"| TC
    TC -->|"styles injection"| DSSG
    VS1 -->|"versioned sidebar"| DSSG
    VS2 -->|"versions metadata"| DSSG

    DSSG -->|"npm run build"| BuildOutput["build/"]:::build
    BuildOutput -->|"publish"| GH
    CI -->|"on push build & deploy"| DSSG
    Tests -->|"validate docs"| DSSG

    User -->|visits site| GH
    User -->|search queries| Algolia
    AC -->|"update search index"| Algolia

    %% Click Events
    click MC "https://github.com/openbb-finance/openbb-docs/tree/main/content/"
    click GP1 "https://github.com/openbb-finance/openbb-docs/blob/main/scripts/generate_excel_markdown.py"
    click GP2 "https://github.com/openbb-finance/openbb-docs/blob/main/scripts/generate_platform_markdown.py"
    click GP3 "https://github.com/openbb-finance/openbb-docs/blob/main/scripts/generate_widgets_library.py"
    click DC1 "https://github.com/openbb-finance/openbb-docs/blob/main/docusaurus.config.ts"
    click DC2 "https://github.com/openbb-finance/openbb-docs/blob/main/sidebars.js"
    click DC3 "https://github.com/openbb-finance/openbb-docs/blob/main/tailwind.config.ts"
    click DC4 "https://github.com/openbb-finance/openbb-docs/blob/main/babel.config.cjs"
    click VS1 "https://github.com/openbb-finance/openbb-docs/blob/main/versioned_sidebars/version-v3-sidebars.json"
    click VS2 "https://github.com/openbb-finance/openbb-docs/blob/main/versions.json"
    click CRC "https://github.com/openbb-finance/openbb-docs/tree/main/src/components/"
    click TO "https://github.com/openbb-finance/openbb-docs/tree/main/src/theme/"
    click GS "https://github.com/openbb-finance/openbb-docs/blob/main/src/css/custom.css"
    click CP "https://github.com/openbb-finance/openbb-docs/tree/main/src/pages/"
    click SA "https://github.com/openbb-finance/openbb-docs/tree/main/static/"
    click CI "https://github.com/openbb-finance/openbb-docs/blob/main/.github/workflows/deploy-gh-pages.yml"
    click AC "https://github.com/openbb-finance/openbb-docs/blob/main/utils/initialAlgoliaCrawler.js"
    click Tests "https://github.com/openbb-finance/openbb-docs/blob/main/tests/test_platform_docs.py"

    %% Styles
    classDef content fill:#E0F7FA,stroke:#006064
    classDef python fill:#FFF3E0,stroke:#E65100
    classDef config fill:#E8F5E9,stroke:#1B5E20
    classDef react fill:#E3F2FD,stroke:#0D47A1
    classDef css fill:#F3E5F5,stroke:#4A148C
    classDef static fill:#ECEFF1,stroke:#263238
    classDef pages fill:#F1F8E9,stroke:#33691E
    classDef build fill:#FFFDE7,stroke:#F57F17
    classDef ci fill:#F9FBE7,stroke:#827717
    classDef tests fill:#FFEBEE,stroke:#B71C1C
    classDef external fill:#FFF8E1,stroke:#FF6F00
    classDef hosting fill:#E8EAF6,stroke:#1A237E
    classDef user fill:#FFEBEE,stroke:#B71C1C
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
