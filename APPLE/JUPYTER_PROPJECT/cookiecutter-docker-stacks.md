---
created: 2025-06-29 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/jupyter/cookiecutter-docker-stacks
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExdGo1YWl6bTM2MGtxYWluczdmanc2MXljZjdzZngwNTl1eW41MHR5YSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zkNWhK3dTiClXMDY2j/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# cookiecutter-docker-stacks repo project
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



---

```mermaid
---
title: "cookiecutter-docker-stacks repo project"
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
flowchart LR
    Dev["Developer"]:::external
    CLI["Cookiecutter CLI"]:::external

    subgraph Template_Repository_Artifacts["Template Repository Artifacts"]
        CC["cookiecutter.json"]:::template
        YC["configs/"]:::template
        PreC[".pre-commit-config.yaml"]:::template
        Flake8[".flake8"]:::template
        Mypy["mypy.ini"]:::template
        Pytest["pytest.ini"]:::template
        ReqT["requirements-test.txt"]:::template
        MDL[".markdownlint.yaml"]:::template
        HADL[".hadolint.yaml"]:::template
    end

    subgraph Root_CI_CD["Root CI/CD<br/>(Template Validation)"]
        RootTestsWF[".github/workflows/tests.yml"]:::ci
        PreCommitWF[".github/workflows/pre-commit.yml"]:::ci
    end

    Dev -->|"runs"| CLI
    CLI -->|"reads"| CC
    CLI -->|"reads"| YC
    CLI -->|"reads"| PreC
    CLI -->|"reads"| Flake8
    CLI -->|"reads"| Mypy
    CLI -->|"reads"| Pytest
    CLI -->|"reads"| ReqT
    CLI -->|"reads"| MDL
    CLI -->|"reads"| HADL

    CC --> RootTestsWF
    CC --> PreCommitWF
    YC --> RootTestsWF
    YC --> PreCommitWF

    CLI -->|"generates scaffold"| GenProj

    subgraph Generated_Project_Workspace["Generated Project Workspace"]
        TSDir["{{cookiecutter.stack_name}}/"]:::generated
        PerStackWF[".github/workflows/docker.yml"]:::ci
        Dependabot[".github/dependabot.yml"]:::generated
        GAttr[".gitattributes"]:::generated
        GIgn[".gitignore"]:::generated
        TRM["README.md"]:::generated
        DFile["image/Dockerfile"]:::generated
        RDev["requirements-dev.txt"]:::generated
        TSuite["tests/"]:::generated
    end

    GenProj --> TSDir
    TSDir --> PerStackWF
    TSDir --> Dependabot
    TSDir --> GAttr
    TSDir --> GIgn
    TSDir --> TRM
    TSDir --> DFile
    TSDir --> RDev
    TSDir --> TSuite

    subgraph Docker_and_Registry["Docker & Registry"]
        BuildService["Docker Build Service"]:::external
        Registry["Docker Registry"]:::external
    end

    TSDir -->|"local build"| BuildService
    PerStackWF -->|"CI build"| BuildService
    BuildService -->|"push image"| Registry

    classDef template fill:#cce5ff,stroke:#3399ff,color:#000000
    classDef generated fill:#d4edda,stroke:#28a745,color:#000000
    classDef ci fill:#ffe5b4,stroke:#ff8c00,color:#000000
    classDef external fill:#e2e3e5,stroke:#6c757d,color:#000000

    click CC "https://github.com/jupyter/cookiecutter-docker-stacks/blob/main/cookiecutter.json"
    click YC "https://github.com/jupyter/cookiecutter-docker-stacks/tree/main/configs/"
    click PreC "https://github.com/jupyter/cookiecutter-docker-stacks/blob/main/.pre-commit-config.yaml"
    click Flake8 "https://github.com/jupyter/cookiecutter-docker-stacks/blob/main/.flake8"
    click Mypy "https://github.com/jupyter/cookiecutter-docker-stacks/blob/main/mypy.ini"
    click Pytest "https://github.com/jupyter/cookiecutter-docker-stacks/blob/main/pytest.ini"
    click ReqT "https://github.com/jupyter/cookiecutter-docker-stacks/blob/main/requirements-test.txt"
    click MDL "https://github.com/jupyter/cookiecutter-docker-stacks/blob/main/.markdownlint.yaml"
    click HADL "https://github.com/jupyter/cookiecutter-docker-stacks/blob/main/.hadolint.yaml"
    click RootTestsWF "https://github.com/jupyter/cookiecutter-docker-stacks/blob/main/.github/workflows/tests.yml"
    click PreCommitWF "https://github.com/jupyter/cookiecutter-docker-stacks/blob/main/.github/workflows/pre-commit.yml"
    click TSDir "https://github.com/jupyter/cookiecutter-docker-stacks/tree/main/{{cookiecutter.stack_name}}/"
    click PerStackWF "https://github.com/jupyter/cookiecutter-docker-stacks/blob/main/{{cookiecutter.stack_name}}/.github/workflows/docker.yml"
    click Dependabot "https://github.com/jupyter/cookiecutter-docker-stacks/blob/main/{{cookiecutter.stack_name}}/.github/dependabot.yml"
    click GAttr "https://github.com/jupyter/cookiecutter-docker-stacks/blob/main/{{cookiecutter.stack_name}}/.gitattributes"
    click GIgn "https://github.com/jupyter/cookiecutter-docker-stacks/blob/main/{{cookiecutter.stack_name}}/.gitignore"
    click TRM "https://github.com/jupyter/cookiecutter-docker-stacks/blob/main/{{cookiecutter.stack_name}}/README.md"
    click DFile "https://github.com/jupyter/cookiecutter-docker-stacks/tree/main/{{cookiecutter.stack_name}}/image/Dockerfile"
    click RDev "https://github.com/jupyter/cookiecutter-docker-stacks/blob/main/{{cookiecutter.stack_name}}/requirements-dev.txt"
    click TSuite "https://github.com/jupyter/cookiecutter-docker-stacks/tree/main/{{cookiecutter.stack_name}}/tests/"


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
