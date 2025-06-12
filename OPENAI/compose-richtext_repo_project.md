---
created: 2025-06-012 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/halilozercan/compose-richtext
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExY2tvYWIyOGRpbWZodTQ2YTI2bjQ1eHpoaDY0YTZ3Mms2aWhneHNlYSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/fR6aYF0SUJAeoypyub/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# compose-richtext repo project
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
title: "compose-richtext repo project"
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
    %% Infrastructure
    subgraph "Infrastructure"
        direction TB
        BuildSrc["buildSrc/"]:::infra
        RootGradle["settings.gradle.kts, gradlew, gradlew.bat, gradle/wrapper/"]:::infra
        CI["GitHub Actions CI/CD"]:::infra
        Docs["docs/, mkdocs.yml"]:::infra
    end

    %% Parser Modules
    subgraph "Parser Modules"
        direction TB
        RC["richtext-commonmark: Kotlin MPP, CommonMark AST"]:::parser
        RM["richtext-markdown: Kotlin MPP, Markdown Parser"]:::parser
    end

    %% UI Modules
    subgraph "UI Modules"
    direction TB
        UI["richtext-ui: Kotlin MPP, Compose UI Base"]:::ui
        UIM["richtext-ui-material: Material Theme Extension"]:::ui
        UIM3["richtext-ui-material3: Material3 Theme Extension"]:::ui
    end

    %% Feature Modules
    subgraph "Feature Modules"
    direction TB
        PRINT["printing: Compose PDF/Print Adapter"]:::feature
        SLIDE["slideshow: Compose Slide Deck UI"]:::feature
    end

    %% Sample Apps
    subgraph "Sample Apps"
    direction TB
        AS["android-sample: Android Demo App"]:::sample
        DS["desktop-sample: Desktop Demo App"]:::sample
    end

    %% Dependencies
    RM -->|"uses CommonMark AST"| RC
    UI -->|"uses Markdown API"| RM
    UIM -->|"extends UI Base"| UI
    UIM3 -->|"extends UI Base"| UI
    PRINT -->|"depends on UI"| UI
    SLIDE -->|"depends on UI"| UI
    AS -->|"depends on CommonMark"| RC
    AS -->|"depends on Markdown"| RM
    AS -->|"depends on UI"| UI
    AS -->|"depends on Material UI"| UIM
    AS -->|"depends on Material3 UI"| UIM3
    AS -->|"depends on Printing"| PRINT
    AS -->|"depends on Slideshow"| SLIDE
    DS -->|"depends on CommonMark"| RC
    DS -->|"depends on Markdown"| RM
    DS -->|"depends on UI"| UI

    %% Build System feeds modules
    BuildSrc --> RC
    BuildSrc --> RM
    BuildSrc --> UI
    BuildSrc --> UIM
    BuildSrc --> UIM3
    BuildSrc --> PRINT
    BuildSrc --> SLIDE
    BuildSrc --> AS
    BuildSrc --> DS
    RootGradle --> BuildSrc
    RootGradle --> RC
    RootGradle --> RM
    RootGradle --> UI
    RootGradle --> UIM
    RootGradle --> UIM3
    RootGradle --> PRINT
    RootGradle --> SLIDE
    RootGradle --> AS
    RootGradle --> DS

    %% CI/CD triggers builds and docs and publish
    CI -->|"triggers build"| BuildSrc
    CI -->|"triggers docs deploy"| Docs
    CI -->|"triggers publish to Maven Central"| RM
    CI -->|"triggers publish to Maven Central"| RC
    CI -->|"triggers publish to Maven Central"| UI
    CI -->|"triggers publish to Maven Central"| UIM
    CI -->|"triggers publish to Maven Central"| UIM3
    CI -->|"triggers publish to Maven Central"| PRINT
    CI -->|"triggers publish to Maven Central"| SLIDE

    %% Documentation deployment
    Docs -->|"site deployed to"| halilibo["halilibo.com"]

    %% Click Events
    click RC "https://github.com/halilozercan/compose-richtext/tree/main/richtext-commonmark/"
    click RM "https://github.com/halilozercan/compose-richtext/tree/main/richtext-markdown/"
    click UI "https://github.com/halilozercan/compose-richtext/tree/main/richtext-ui/"
    click UIM "https://github.com/halilozercan/compose-richtext/tree/main/richtext-ui-material/"
    click UIM3 "https://github.com/halilozercan/compose-richtext/tree/main/richtext-ui-material3/"
    click PRINT "https://github.com/halilozercan/compose-richtext/tree/main/printing/"
    click SLIDE "https://github.com/halilozercan/compose-richtext/tree/main/slideshow/"
    click AS "https://github.com/halilozercan/compose-richtext/tree/main/android-sample/"
    click DS "https://github.com/halilozercan/compose-richtext/tree/main/desktop-sample/"
    click BuildSrc "https://github.com/halilozercan/compose-richtext/tree/main/buildSrc/"
    click RootGradle "https://github.com/halilozercan/compose-richtext/blob/main/settings.gradle.kts"
    click RootGradle "https://github.com/halilozercan/compose-richtext/tree/main/gradlew"
    click RootGradle "https://github.com/halilozercan/compose-richtext/blob/main/gradlew.bat"
    click RootGradle "https://github.com/halilozercan/compose-richtext/tree/main/gradle/wrapper/"
    click CI "https://github.com/halilozercan/compose-richtext/blob/main/.github/workflows/android.yml"
    click CI "https://github.com/halilozercan/compose-richtext/blob/main/.github/workflows/docs.yml"
    click CI "https://github.com/halilozercan/compose-richtext/blob/main/.github/workflows/publish.yml"
    click Docs "https://github.com/halilozercan/compose-richtext/tree/main/docs/"
    click Docs "https://github.com/halilozercan/compose-richtext/blob/main/mkdocs.yml"

    %% Styles
    classDef parser fill:#ADD8E6,stroke:#333,stroke-width:1px
    classDef ui fill:#90EE90,stroke:#333,stroke-width:1px
    classDef feature fill:#FFD580,stroke:#333,stroke-width:1px
    classDef sample fill:#D8BFD8,stroke:#333,stroke-width:1px
    classDef infra fill:#D3D3D3,stroke:#333,stroke-width:1px

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