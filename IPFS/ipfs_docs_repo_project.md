---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ipfs/ipfs-docs
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExaHNwdmJteDFidGlyMnE4MHFiYnU3ZG05dnQ1eHY5NDQ4dnlzNmtzdCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/qc5fbrb4qpupRA9r4o/giphy.gif)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# ipfs-docs repo project
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
title: "ipfs-docs repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'linear' },
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#222B2B',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#2221',
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
        docs_md["Markdown Files\n(docs/**/*.md)"]:::content
        images_assets["Images\n(images/)"]:::content
    end
    click docs_md "https://github.com/ipfs/ipfs-docs/tree/main/docs/"
    click images_assets "https://github.com/ipfs/ipfs-docs/tree/main/images/"

    %% VuePress Static Site Generator
    subgraph "VuePress Static Site Generator" 
        direction TB
        vp_config["config.js"]:::build
        vp_head["head.js"]:::build
        vp_nav["nav/en.js"]:::build
        vp_plugin["vuepress-plugin-speedcurve"]:::build
        vp_theme["theme/"]:::build
    end
    click vp_config "https://github.com/ipfs/ipfs-docs/blob/main/docs/.vuepress/config.js"
    click vp_head "https://github.com/ipfs/ipfs-docs/blob/main/docs/.vuepress/head.js"
    click vp_nav "https://github.com/ipfs/ipfs-docs/blob/main/docs/.vuepress/nav/en.js"
    click vp_plugin "https://github.com/ipfs/ipfs-docs/tree/main/docs/.vuepress/plugins/vuepress-plugin-speedcurve/"
    click vp_theme "https://github.com/ipfs/ipfs-docs/tree/main/docs/.vuepress/theme/"

    %% Code-Generation Tool
    subgraph "Code-Generation Tool (HTTP API docs)" 
        direction TB
        cg_endpoints["endpoints.go"]:::build
        cg_makefile["Makefile"]:::build
        cg_main["main.go"]:::build
    end
    click cg_endpoints "https://github.com/ipfs/ipfs-docs/blob/main/tools/http-api-docs/endpoints.go"
    click cg_makefile "https://github.com/ipfs/ipfs-docs/tree/main/tools/http-api-docs/Makefile"
    click cg_main "https://github.com/ipfs/ipfs-docs/blob/main/tools/http-api-docs/http-api-docs/main.go"

    %% Local Development Server
    subgraph "Local Development Server"
        direction TB
        pkg_json["package.json"]:::build
        pkg_lock["package-lock.json"]:::build
        dev_server["npm start → Dev Server"]:::build
    end
    click pkg_json "https://github.com/ipfs/ipfs-docs/blob/main/package.json"
    click pkg_lock "https://github.com/ipfs/ipfs-docs/blob/main/package-lock.json"

    %% CI/CD Pipeline
    subgraph "CI/CD Pipeline" 
        direction TB
        subgraph "Lint Stage"
            direction TB
            lint_md[".markdownlint.jsonc"]:::ci
            lint_vale[".vale.ini"]:::ci
            lint_action["markdownlint & Vale"]:::ci
        end
        subgraph "Generate Stage"
            direction TB
            run_codegen["Run Code-Generation Tool"]:::ci
        end
        subgraph "Build Stage"
            direction TB
            vp_build["VuePress Build"]:::ci
        end
        subgraph "Test Stage"
            direction TB
            test_codegen["Unit Tests (Go)"]:::ci
            test_snapshot["Snapshot Tests"]:::ci
        end
        subgraph "Deploy Stage"
            direction TB
            deploy_fleek["Deploy to Fleek"]:::ci
        end
        workflows[".github/workflows/"]:::ci
        actions_latest["latest-kubo-tag Action"]:::ci
        actions_update["update-with-latest-versions Action"]:::ci
        dependabot_cfg[".github/dependabot.yml"]:::ci
    end
    click workflows "https://github.com/ipfs/ipfs-docs/tree/main/.github/workflows/"
    click actions_latest "https://github.com/ipfs/ipfs-docs/tree/main/.github/actions/latest-kubo-tag/"
    click actions_update "https://github.com/ipfs/ipfs-docs/tree/main/.github/actions/update-with-latest-versions/"
    click dependabot_cfg "https://github.com/ipfs/ipfs-docs/blob/main/.github/dependabot.yml"

    %% Deployment Target
    fleek["Fleek Hosting\n(static via IPFS/CDN)"]:::external

    %% External Services
    gh["GitHub (SCM, Issues, PRs)"]:::external
    npmreg["npm Registry"]:::external

    %% Relationships
    docs_md -->|feeds into| vp_config
    images_assets -->|assets for| vp_theme
    cg_main -->|generates API docs| vp_plugin
    cg_endpoints --> cg_main
    cg_makefile --> cg_main

    vp_config --> vp_build
    vp_head --> vp_build
    vp_nav --> vp_build
    vp_plugin --> vp_build
    vp_theme --> vp_build

    pkg_json --> dev_server
    pkg_lock --> dev_server
    dev_server --> vp_build

    gh --> workflows
    gh --> lint_action
    gh --> run_codegen
    gh --> vp_build
    gh --> test_codegen
    gh --> deploy_fleek

    lint_md --> lint_action
    lint_vale --> lint_action
    workflows --> lint_action
    lint_action --> run_codegen
    run_codegen --> vp_build
    vp_build --> test_snapshot
    test_codegen --> test_snapshot
    test_snapshot --> deploy_fleek
    deploy_fleek --> fleek

    gh --> dependabot_cfg
    gh --> actions_latest
    gh --> actions_update
    workflows --> actions_latest
    workflows --> actions_update

    npmreg --> pkg_json

    %% Styles
    classDef content fill:#e0f7e9,stroke:#27a745,stroke-width:2px
    classDef build fill:#e0f0ff,stroke:#2d6cdf,stroke-width:2px
    classDef ci fill:#fff4e5,stroke:#f5a623,stroke-width:2px
    classDef external fill:#f4e5ff,stroke:#9b59b6,stroke-width:2px
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
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

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