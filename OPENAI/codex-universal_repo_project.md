---
created: 2025-06-012 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/codex-universal
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


# codex-universal repo project
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
title: "codex-universal repo project"
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
    %% CI/CD Pipeline
    subgraph "CI/CD Pipeline"  
        direction TB
        DevCommit["Developer Commits"]:::external
        GHActions["GitHub Actions CI"]:::build
        DockerfileNode["Dockerfile"]:::build
        BuildImageYML["build-image.yml"]:::build
        Registry["Container Registry (ghcr.io)"]:::external
    end

    DevCommit -->|"triggers build"| GHActions
    GHActions -->|"uses"| BuildImageYML
    GHActions -->|"reads"| DockerfileNode
    GHActions -->|"push image"| Registry

    %% Runtime Flow
    subgraph "Developer Runtime"  
        direction TB
        DevMachine["Developer Machine"]:::external
        DockerEngine["Docker Engine"]:::build
        DockerImage["codex-universal Image"]:::build
        subgraph "Container Runtime"  
            direction TB
            Entrypoint["entrypoint.sh"]:::runtime
            SetupScript["setup_universal.sh"]:::runtime
            subgraph "Language Installers"  
                direction TB
                Pyenv["pyenv Installer"]:::runtime
                NvmRustGo["nvm/rustup/go/swift Installers"]:::runtime
            end
            subgraph "Pre-installed Tools"  
                direction TB
                RubyBunJava["ruby, bun, java, bazelisk"]:::runtime
            end
        end
        Workspace["Mounted User Workspace"]:::external
    end

    DevMachine -->|"docker pull"| Registry
    DevMachine -->|"docker run"| DockerEngine
    DockerEngine --> DockerImage
    DockerImage --> Entrypoint
    Entrypoint -->|"calls"| SetupScript
    SetupScript --> Pyenv
    SetupScript --> NvmRustGo
    Entrypoint --> RubyBunJava
    DockerEngine -.->|"mount"| Workspace
    DockerEngine -.->|"env vars CODEX_ENV_*"| SetupScript

    %% Documentation & Licensing
    subgraph "Project Files"  
        direction TB
        README["README.md"]:::docs
        Gitignore[".gitignore"]:::docs
        LicensesDir["LICENSES/"]:::docs
        SBOM1["codex-universal-image-sbom.spdx.json"]:::docs
        SBOM2["codex-universal-image-sbom.md"]:::docs
        LicenseFile["LICENSE"]:::docs
    end

    %% Click Events
    click BuildImageYML "https://github.com/openai/codex-universal/blob/main/.github/workflows/build-image.yml"
    click DockerfileNode "https://github.com/openai/codex-universal/tree/main/Dockerfile"
    click Entrypoint "https://github.com/openai/codex-universal/blob/main/entrypoint.sh"
    click SetupScript "https://github.com/openai/codex-universal/blob/main/setup_universal.sh"
    click README "https://github.com/openai/codex-universal/blob/main/README.md"
    click LicensesDir "https://github.com/openai/codex-universal/tree/main/LICENSES/"
    click SBOM1 "https://github.com/openai/codex-universal/blob/main/LICENSES/codex-universal-image-sbom.spdx.json"
    click SBOM2 "https://github.com/openai/codex-universal/blob/main/LICENSES/codex-universal-image-sbom.md"
    click LicenseFile "https://github.com/openai/codex-universal/tree/main/LICENSES/LICENSE"
    click Gitignore "https://github.com/openai/codex-universal/blob/main/.gitignore"

    %% Styles
    classDef build fill:#cfe2f3,stroke:#084298,stroke-width:1px
    classDef runtime fill:#d1e7dd,stroke:#0f5132,stroke-width:1px
    classDef docs fill:#fff3cd,stroke:#664d03,stroke-width:1px
    classDef external fill:#e2e3e5,stroke:#41464b,stroke-width:1px
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