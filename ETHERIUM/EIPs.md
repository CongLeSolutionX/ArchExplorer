---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/EIPs
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExanZydm52NDcyNWIwMWtneG9uOWk4aGpseXQ1bHR4b3c1N2x3MnB6bSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/m3XqQ8QhuIUuQau7n5/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# EIPs repo project
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
title: "EIPs repo project"
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
    subgraph Contributors
        Contributor["Contributor"]:::external
    end

    subgraph "GitHub Repository"
        Repo["GitHub Repo"]:::external

        subgraph "Content Store"
            EIPFiles["EIP Markdown Files"]:::content
            StatusData["_data/statuses.yaml"]:::content
            Assets["Per-EIP Assets"]:::content
        end

        subgraph "Static Site Generator"
            Jekyll["Jekyll Engine"]:::processing
            ConfigYml["_config.yml"]:::processing
            Layouts["_layouts/"]:::processing
            Includes["_includes/"]:::processing
            RubyDeps["Gemfile & Gemfile.lock"]:::processing
            EipwCfg["config/eipw.toml"]:::processing
            MarkdownLint["config/.markdownlint.yaml"]:::processing
            Codespell["config/.codespell-whitelist"]:::processing
        end

        subgraph "CI Validation & Automation"
            Actions["GitHub Actions Workflows"]:::automation
            Renovate["Renovate Bot Config"]:::automation
            ReviewBot["Auto-Review Bots"]:::automation
        end
    end

    subgraph "Deployment Platform"
        Pages["GitHub Pages (CNAME)"]:::hosting
    end

    subgraph "End Users"
        Browser["Browser"]:::external
    end

    Contributor -->|pull_request / push| Repo
    Repo --> EIPFiles
    Repo --> StatusData
    Repo --> Assets
    Repo -->|trigger pull_request| Actions
    Renovate -->|dependency PRs| Repo
    Actions -->|label / merge approved| ReviewBot
    ReviewBot -->|auto-merge| Repo
    Repo -->|merge to main| Jekyll
    Jekyll -->|reads templates & content| ConfigYml
    Jekyll -->|reads templates & content| Layouts
    Jekyll -->|reads templates & content| Includes
    Jekyll -->|reads templates & content| RubyDeps
    Jekyll -->|applies rules| EipwCfg
    Jekyll -->|applies rules| MarkdownLint
    Jekyll -->|applies rules| Codespell
    Jekyll -->|processes content| EIPFiles
    Jekyll -->|processes data| StatusData
    Jekyll -->|processes assets| Assets
    Jekyll -->|builds _site| Pages
    Pages -->|serves site| Browser

    click EIPFiles "https://github.com/ethereum/eips/tree/master/EIPS/"
    click StatusData "https://github.com/ethereum/eips/blob/master/_data/statuses.yaml"
    click Assets "https://github.com/ethereum/eips/tree/master/assets/"
    click ConfigYml "https://github.com/ethereum/eips/blob/master/_config.yml"
    click Layouts "https://github.com/ethereum/eips/tree/master/_layouts/"
    click Includes "https://github.com/ethereum/eips/tree/master/_includes/"
    click RubyDeps "https://github.com/ethereum/eips/blob/master/Gemfile & Gemfile.lock"
    click EipwCfg "https://github.com/ethereum/eips/blob/master/config/eipw.toml"
    click MarkdownLint "https://github.com/ethereum/eips/blob/master/config/.markdownlint.yaml"
    click Codespell "https://github.com/ethereum/eips/blob/master/config/.codespell-whitelist"
    click Actions "https://github.com/ethereum/eips/blob/master/.github/workflows/ci.yml"
    click Renovate "https://github.com/ethereum/eips/blob/master/.github/renovate.json"
    click Pages "https://github.com/ethereum/eips/tree/master/CNAME"

    classDef content fill:#aadaff,stroke:#333,stroke-width:1px
    classDef processing fill:#aaffaa,stroke:#333,stroke-width:1px
    classDef automation fill:#ffcc99,stroke:#333,stroke-width:1px
    classDef hosting fill:#e0b0ff,stroke:#333,stroke-width:1px
    classDef external fill:#dddddd,stroke:#333,stroke-width:1px

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