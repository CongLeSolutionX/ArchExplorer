---
created: 2025-06-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/carpentries-incubator/pymarc_basics
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExcXJraXYxbW5qbnFxZzUwcWppcmVrbm83eno0Znl0ZDBnbHpmMG8zaSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zioSZDwyCEbv9jZhUu/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# carpentries-incubator - pymarc_basics repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


----

```mermaid
---
title: "carpentries-incubator - pymarc_basics repo project"
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
  subgraph "Content Source"
    ML["Markdown Lessons"]:::content
    DE["Data & Examples"]:::content
    SA["Static Assets"]:::content
  end

  subgraph "Templating Engine & Config"
    JC["Jekyll Core"]:::templating
    LI["Layouts & Includes"]:::templating
    CF["Config Files"]:::templating
  end

  subgraph "Build & Utility Scripts"
    Lint["Lesson Linting Scripts"]:::build
    Gen["Episode Generation Script"]:::build
    Repo["Repository Checks"]:::build
    AST["Markdown AST Processing"]:::build
    Docker["Docker Serve Script"]:::build
    Make["Makefile"]:::build
  end

  subgraph "Static Site Output"
    SSO["_site Static Output"]:::output
  end

  subgraph "CI/CD Pipeline"
    Travis["Travis CI"]:::ci
    GHPages["GitHub Pages Host"]:::hosting
  end

  EndUser["Web Browser Clients"]:::external

  ML -->|"feeds Markdown + assets into Jekyll"| JC
  DE -->|" "| JC
  SA -->|" "| JC

  JC -->|"build hooks & scripts"| Lint
  JC -->|" "| Gen
  JC -->|" "| Repo
  JC -->|" "| AST
  JC -->|" "| Docker
  JC -->|" "| Make

  Make -->|"generates"| SSO
  Lint -->|" "| SSO
  Gen -->|" "| SSO
  Repo -->|" "| SSO
  AST -->|" "| SSO
  Docker -->|" "| SSO

  SSO -->|"artifact to test & deploy"| Travis
  Travis -->|"deploy"| GHPages
  GHPages -->|"HTTP requests"| EndUser

  %% Click Events for Content Source
  click ML "https://github.com/carpentries-incubator/pymarc_basics/blob/gh-pages/_episodes/*.md"
  click ML "https://github.com/carpentries-incubator/pymarc_basics/blob/gh-pages/index.md"
  click ML "https://github.com/carpentries-incubator/pymarc_basics/blob/gh-pages/reference.md"
  click ML "https://github.com/carpentries-incubator/pymarc_basics/blob/gh-pages/setup.md"
  click DE "https://github.com/carpentries-incubator/pymarc_basics/blob/gh-pages/setup/*.marc"
  click DE "https://github.com/carpentries-incubator/pymarc_basics/blob/gh-pages/setup/episode_*.py"
  click SA "https://github.com/carpentries-incubator/pymarc_basics/tree/gh-pages/assets/css/"
  click SA "https://github.com/carpentries-incubator/pymarc_basics/blob/gh-pages/assets/js/lesson.js"
  click SA "https://github.com/carpentries-incubator/pymarc_basics/tree/gh-pages/assets/fonts/"
  click SA "https://github.com/carpentries-incubator/pymarc_basics/tree/gh-pages/assets/img/"
  click SA "https://github.com/carpentries-incubator/pymarc_basics/tree/gh-pages/assets/favicons/"

  %% Click Events for Templating Engine & Config
  click LI "https://github.com/carpentries-incubator/pymarc_basics/tree/gh-pages/_layouts/"
  click LI "https://github.com/carpentries-incubator/pymarc_basics/tree/gh-pages/_includes/"
  click CF "https://github.com/carpentries-incubator/pymarc_basics/blob/gh-pages/_config.yml"
  click CF "https://github.com/carpentries-incubator/pymarc_basics/tree/gh-pages/Gemfile"

  %% Click Events for Build & Utility Scripts
  click Lint "https://github.com/carpentries-incubator/pymarc_basics/blob/gh-pages/bin/lesson_check.py"
  click Lint "https://github.com/carpentries-incubator/pymarc_basics/blob/gh-pages/bin/test_lesson_check.py"
  click Gen "https://github.com/carpentries-incubator/pymarc_basics/blob/gh-pages/bin/generate_md_episodes.R"
  click Repo "https://github.com/carpentries-incubator/pymarc_basics/blob/gh-pages/bin/repo_check.py"
  click Repo "https://github.com/carpentries-incubator/pymarc_basics/blob/gh-pages/bin/workshop_check.py"
  click AST "https://github.com/carpentries-incubator/pymarc_basics/blob/gh-pages/bin/markdown_ast.rb"
  click Docker "https://github.com/carpentries-incubator/pymarc_basics/blob/gh-pages/bin/run-make-docker-serve.sh"
  click Make "https://github.com/carpentries-incubator/pymarc_basics/tree/gh-pages/Makefile"

  %% Click Event for CI/CD
  click Travis "https://github.com/carpentries-incubator/pymarc_basics/blob/gh-pages/.travis.yml"

  %% Styles
  classDef content fill:#cfe2f3,stroke:#000,stroke-width:1px
  classDef templating fill:#d5f5e3,stroke:#000,stroke-width:1px
  classDef build fill:#fcf3cf,stroke:#000,stroke-width:1px
  classDef ci fill:#fadbd8,stroke:#000,stroke-width:1px
  classDef hosting fill:#ebdef0,stroke:#000,stroke-width:1px
  classDef output fill:#f2f3f4,stroke:#000,stroke-width:1px
  classDef external fill:#D3D3D3,stroke:#000,stroke-width:1px

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
