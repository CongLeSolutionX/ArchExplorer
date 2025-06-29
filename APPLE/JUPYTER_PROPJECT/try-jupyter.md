---
created: 2025-06-29 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/jupyter/try-jupyter
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




# try-jupyter repo project
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
title: "try-jupyter repo project"
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
    %% Static Host
    subgraph "Static Hosting" 
        direction TB
        GitHubPages["GitHub Pages\n(serves HTML, JS, CSS, content/)"]:::static
    end

    %% Runtime Environment in Browser
    subgraph "Client Runtime (Browser)" 
        direction TB
        Browser["Browser / Client"]:::runtime
        UI["JupyterLite UI\n(JupyterLab Front-end)"]:::runtime
        Kernels["WASM Kernels\n(Python, R)"]:::runtime
        FS["Virtual FS\n(Emscripten FS)"]:::persistence
        IndexedDB["IndexedDB\n(persistence)"]:::persistence
        subgraph "Static Content" 
            direction TB
            DataDir["content/data/"]:::data
            Museums["Museums_in_DC.geojson"]:::data
            BarVL["bar.vl.json"]:::data
            Fasta["fasta-example.fasta"]:::data
            Iris["iris.csv"]:::data
            NotebooksDir["content/notebooks/"]:::data
            IntroNB["Intro.ipynb"]:::data
            LorenzNB["Lorenz.ipynb"]:::data
            RNB["r.ipynb"]:::data
            SqliteNB["sqlite.ipynb"]:::data
        end
    end

    %% Build & Documentation
    subgraph "Build-Time & Docs" 
        direction TB
        CI["CI/CD (GitHub Actions)"]:::build
        DeployYML["deploy.yml"]:::config
        RTDPreview["rtd-preview.yml"]:::config
        Docs["ReadTheDocs"]:::build
        ConfPy["conf.py"]:::config
        RTDConfig[".readthedocs.yml"]:::config
        EnvBuild["Environment/Kernels Build Specs"]:::config
        EnvPy["environment-python.yml"]:::config
        EnvR["environment-r.yml"]:::config
        BuildEnv["build-environment.yml"]:::config
        Gitignore[".gitignore"]:::config
        Readme["README.md"]:::config
        JLiteCfg["jupyter-lite.json"]:::config
        LegacyCfg["jupyter_lite_config.json"]:::config
        REPLCfg["repl/jupyter-lite.json"]:::config
    end

    %% Relationships
    Browser -->|"HTTP GET assets"| GitHubPages
    GitHubPages -->|serves static content| UI
    UI -->|"loads kernels"| Kernels
    UI -->|"mounts FS"| FS
    FS -->|"persist/write"| IndexedDB
    Kernels -->|"executes code"| FS
    Browser -->|"user interacts"| UI

    CI -->|"runs workflows"| DeployYML
    CI -->|"runs workflows"| RTDPreview
    CI -->|"push to Pages"| GitHubPages
    Docs -->|"build docs from content"| ConfPy
    Docs -->|"uses config"| RTDConfig
    Docs -->|"source content"| NotebooksDir
    CI -->|"uses specs"| EnvPy
    CI -->|"uses specs"| EnvR
    CI -->|"uses specs"| BuildEnv
    CI -->|"checks ignore"| Gitignore
    CI -->|"references readme"| Readme
    CI -->|"reads front-end config"| JLiteCfg
    CI -->|"reads legacy config"| LegacyCfg
    CI -->|"reads repl config"| REPLCfg

    %% Click events
    click JLiteCfg "https://github.com/jupyter/try-jupyter/blob/main/jupyter-lite.json"
    click LegacyCfg "https://github.com/jupyter/try-jupyter/blob/main/jupyter_lite_config.json"
    click REPLCfg "https://github.com/jupyter/try-jupyter/blob/main/repl/jupyter-lite.json"
    click DataDir "https://github.com/jupyter/try-jupyter/tree/main/content/data/"
    click Museums "https://github.com/jupyter/try-jupyter/blob/main/content/data/Museums_in_DC.geojson"
    click BarVL "https://github.com/jupyter/try-jupyter/blob/main/content/data/bar.vl.json"
    click Fasta "https://github.com/jupyter/try-jupyter/blob/main/content/data/fasta-example.fasta"
    click Iris "https://github.com/jupyter/try-jupyter/blob/main/content/data/iris.csv"
    click NotebooksDir "https://github.com/jupyter/try-jupyter/tree/main/content/notebooks/"
    click IntroNB "https://github.com/jupyter/try-jupyter/blob/main/content/notebooks/Intro.ipynb"
    click LorenzNB "https://github.com/jupyter/try-jupyter/blob/main/content/notebooks/Lorenz.ipynb"
    click RNB "https://github.com/jupyter/try-jupyter/blob/main/content/notebooks/r.ipynb"
    click SqliteNB "https://github.com/jupyter/try-jupyter/blob/main/content/notebooks/sqlite.ipynb"
    click DeployYML "https://github.com/jupyter/try-jupyter/blob/main/.github/workflows/deploy.yml"
    click RTDPreview "https://github.com/jupyter/try-jupyter/blob/main/.github/workflows/rtd-preview.yml"
    click ConfPy "https://github.com/jupyter/try-jupyter/blob/main/conf.py"
    click RTDConfig "https://github.com/jupyter/try-jupyter/blob/main/.readthedocs.yml"
    click EnvPy "https://github.com/jupyter/try-jupyter/blob/main/environment-python.yml"
    click EnvR "https://github.com/jupyter/try-jupyter/blob/main/environment-r.yml"
    click BuildEnv "https://github.com/jupyter/try-jupyter/blob/main/build-environment.yml"
    click Gitignore "https://github.com/jupyter/try-jupyter/blob/main/.gitignore"
    click Readme "https://github.com/jupyter/try-jupyter/blob/main/README.md"

    %% Styles
    classDef runtime fill:#D0E8FF,stroke:#0366d6,color:#0366d6;
    classDef static fill:#FFE8B0,stroke:#D97706,color:#87460F;
    classDef data fill:#FFF4D6,stroke:#D4A017,color:#927C04;
    classDef persistence fill:#FFE0E0,stroke:#D62828,color:#b62a2a;
    classDef build fill:#E8FFE8,stroke:#228B22,color:#1B6E1B;
    classDef config fill:#E0E0FF,stroke:#4B0082,color:#4B0082;

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