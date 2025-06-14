---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/neovim/neovim-releases
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExMXVjejV3dnVjc2o5MXd3eXBvcDR1cHlzbHQ1Z2R6YjY0ZHpmdjJ6OCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/hL9q5k9dk9l0wGd4e0/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# neovim-releases repo project
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
title: "neovim-releases repo project"
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
    subgraph "Source"
        Repo["Unsupported-Nvim-Releases (GitHub Repo)"]:::github
        Readme["README.md"]:::github
        GitHubConfig[".github"]:::github
        Dependabot["Dependabot"]:::github
        Upstream["Upstream Neovim Source"]:::external
    end

    subgraph "Orchestration"
        WorkflowDir[".github/workflows"]:::github
        ReleaseYml["release.yml"]:::github
        NotesMd["notes.md"]:::github
        GitHub_Actions_Workflow["GitHub Actions Workflow"]:::github
    end

    subgraph "Execution"
        Runner["GitHub Hosted Runner\n(glibc2.17 Build Env)"]:::runner
        Build["Build & Package Steps\n(AppImage, tar.gz, deb)"]:::runner
    end

    subgraph "Storage"
        Releases["GitHub Releases"]:::storage
    end

    subgraph End_Unders["Users"]
        Users["End Users<br/>(Downloads Artifacts)"]:::user
    end

    Trigger["Tag Push / Manual Dispatch"]:::github

    Repo -->|hosts| Readme
    Repo -->|hosts| GitHubConfig
    GitHubConfig -->|contains| WorkflowDir
    Repo -->|triggers| Orchestration
    Dependabot -->|triggers| Orchestration
    Trigger -->|triggers| Orchestration

    WorkflowDir -->|defines| ReleaseYml
    WorkflowDir -->|documents| NotesMd
    ReleaseYml -->|executes| Orchestration
    NotesMd -->|guides| Orchestration
    Orchestration -->|runs on| Runner
    Runner -->|fetches| Upstream
    Runner -->|performs| Build
    Build -->|uploads artifacts| Releases
    Releases -->|serves| Users

    click Repo "https://github.com/neovim/neovim-releases/tree/master//"
    click Readme "https://github.com/neovim/neovim-releases/blob/master/README.md"
    click GitHubConfig "https://github.com/neovim/neovim-releases/blob/master/.github"
    click Dependabot "https://github.com/neovim/neovim-releases/blob/master/.github/dependabot.yml"
    click WorkflowDir "https://github.com/neovim/neovim-releases/tree/master/.github/workflows"
    click ReleaseYml "https://github.com/neovim/neovim-releases/blob/master/.github/workflows/release.yml"
    click NotesMd "https://github.com/neovim/neovim-releases/blob/master/.github/workflows/notes.md"

    classDef github fill:#cce5ff,stroke:#004085;
    classDef runner fill:#d4edda,stroke:#155724;
    classDef storage fill:#fff3cd,stroke:#856404;
    classDef external fill:#e2e3e5,stroke:#d6d8db;
    classDef user fill:#f8d7da,stroke:#721c24;

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