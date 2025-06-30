---
created: 2025-06-29 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/jupyter/docker-stacks
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExOXpsOHc2aHg3a2lzb251cWl6cXh6Z3A3enFyYmUyOXF4M2UzYmMyYyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/4NjjHHXoHbb6AmJHSu/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# docker-stacks repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for 👨‍🎓 <ins>educational purposes</ins> 👨‍🎓 (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), 📖 <ins> personal study </ins> 📖, and 🔖 <ins> technical reference </ins> 🔖.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>



-----

```mermaid
---
title: "docker-stacks repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright © 2025 Cong Le. All Rights Reserved."
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
    %% Source Code
    Repo["Code Repository (GitHub)"]:::source
    click Repo "https://github.com/jupyter/docker-stacks/tree/main//"

    %% CI/CD Orchestration
    CI["CI/CD Orchestration (GitHub Actions)"]:::cicd
    click CI "https://github.com/jupyter/docker-stacks/tree/main/.github/workflows/"
    click CI2 "https://github.com/jupyter/docker-stacks/tree/main/.github/actions/"

    %% Tagging Service
    Tagging["Tagging Service (Python CLI)"]:::service
    click Tagging "https://github.com/jupyter/docker-stacks/tree/main/tagging/"
    click TaggingApps "https://github.com/jupyter/docker-stacks/tree/main/tagging/apps/"
    click TaggingHierarchy "https://github.com/jupyter/docker-stacks/tree/main/tagging/hierarchy/"
    click TaggingManifests "https://github.com/jupyter/docker-stacks/tree/main/tagging/manifests/"
    click TaggingTaggers "https://github.com/jupyter/docker-stacks/tree/main/tagging/taggers/"
    click TaggingUtils "https://github.com/jupyter/docker-stacks/tree/main/tagging/utils/"

    %% Docker Build System
    DockerBuild["Docker Build System"]:::cicd
    click Images "https://github.com/jupyter/docker-stacks/tree/main/images/*-notebook/"
    click BinderDockerfile "https://github.com/jupyter/docker-stacks/tree/main/binder/Dockerfile"

    %% Test Harness
    TestHarness["Test Harness (pytest)"]:::service
    click TestsByImage "https://github.com/jupyter/docker-stacks/tree/main/tests/by_image/"
    click TestsShared "https://github.com/jupyter/docker-stacks/tree/main/tests/shared_checks/"
    click TestsUtils "https://github.com/jupyter/docker-stacks/tree/main/tests/utils/"
    click TestsConftest "https://github.com/jupyter/docker-stacks/blob/main/tests/conftest.py"
    click TestsRunner "https://github.com/jupyter/docker-stacks/blob/main/tests/run_tests.py"
    click PytestIni "https://github.com/jupyter/docker-stacks/blob/main/tests/pytest.ini"

    %% Publish to Registry
    Publish["Publish to Quay.io"]:::artifact
    click PublishWF1 "https://github.com/jupyter/docker-stacks/blob/main/.github/workflows/docker-tag-push.yml"
    click PublishWF2 "https://github.com/jupyter/docker-stacks/blob/main/.github/workflows/docker-build-test-upload.yml"

    Registry["Quay.io Registry"]:::external

    %% Documentation
    DocsBuilder["Documentation Site (Sphinx)"]:::docs
    click Docs "https://github.com/jupyter/docker-stacks/tree/main/docs/"
    click ConfPy "https://github.com/jupyter/docker-stacks/blob/main/docs/conf.py"
    click Static "https://github.com/jupyter/docker-stacks/tree/main/docs/_static/"
    click DocsSources "https://github.com/jupyter/docker-stacks/tree/main/docs/*"
    click ReadTheDocsConfig "https://github.com/jupyter/docker-stacks/blob/main/.readthedocs.yaml"

    RTD["ReadTheDocs"]:::external

    %% Wiki Updater
    WikiUpdater["Wiki Update Tool"]:::service
    click WikiUpd "https://github.com/jupyter/docker-stacks/blob/main/wiki/update_wiki.py"
    click WikiConfig "https://github.com/jupyter/docker-stacks/blob/main/wiki/config.py"
    click WikiTime "https://github.com/jupyter/docker-stacks/blob/main/wiki/manifest_time.py"
    click WikiHome "https://github.com/jupyter/docker-stacks/blob/main/wiki/Home.md"

    Wiki["GitHub Wiki"]:::external

    %% Examples & Binder
    Examples["Examples & Binder Service"]:::docs
    click Examples "https://github.com/jupyter/docker-stacks/tree/main/examples/"
    click BinderDir "https://github.com/jupyter/docker-stacks/tree/main/binder/"

    BinderHub["BinderHub"]:::external

    %% Build Orchestration & Linting
    BuildConfig["Build Orchestration & Linting Config"]:::service
    click Makefile "https://github.com/jupyter/docker-stacks/tree/main/Makefile"
    click Precommit "https://github.com/jupyter/docker-stacks/blob/main/.pre-commit-config.yaml"
    click Mypy "https://github.com/jupyter/docker-stacks/blob/main/mypy.ini"
    click Flake8 "https://github.com/jupyter/docker-stacks/blob/main/.flake8"
    click Hadolint "https://github.com/jupyter/docker-stacks/blob/main/.hadolint.yaml"

    %% Connections
    Repo -->|push commits| CI
    CI -->|runs| Tagging
    CI -->|builds images| DockerBuild
    DockerBuild -->|uses images/*-notebook| TestHarness
    DockerBuild -->|builds binder image| Examples
    CI -->|runs tests| TestHarness
    TestHarness -->|on success| Publish
    Publish -->|push images| Registry
    CI -->|build docs| DocsBuilder
    DocsBuilder -->|publish| RTD
    CI -->|update wiki| WikiUpdater
    WikiUpdater -->|push pages| Wiki
    CI -->|runs lint/mypy| BuildConfig
    Repo -.->|examples usage| Examples
    Examples -->|serves notebooks| BinderHub

    %% Styling
    classDef source fill:#ADD8E6,stroke:#333,stroke-width:1px;
    classDef cicd fill:#90EE90,stroke:#333,stroke-width:1px;
    classDef service fill:#FFFFE0,stroke:#333,stroke-width:1px;
    classDef artifact fill:#FFA500,stroke:#333,stroke-width:1px;
    classDef docs fill:#DDA0DD,stroke:#333,stroke-width:1px;
    classDef external fill:#D3D3D3,stroke:#333,stroke-width:1px;

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
    

  Closing_quote ~~~ My_Meme
    
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
