---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/mujoco_menagerie
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




# mujoco_menagerie repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes (<ins>sometimes, entertainment purposes</ins>), personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


----

```mermaid
---
title: "mujoco_menagerie repo project"
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
flowchart LR
    %% Monorepo Root
    Repo["Monorepo Root"]:::internal

    subgraph "CI/Build Subsystem"
        CI["GitHub Actions CI"]:::ci
    end

    subgraph "Test Suite"
        MT["model_test.py"]:::internal
        MJXT["mjx_model_test.py"]:::internal
        TR["requirements.txt"]:::internal
    end

    subgraph "Gallery Generator"
        GG["generate_gallery.py"]:::scripts
    end

    subgraph "Repository Documentation"
        RD1["README.md"]:::internal
        RD2["CONTRIBUTING.md"]:::internal
        RD3["CHANGELOG.md"]:::internal
        RD4["LICENSE"]:::internal
    end

    subgraph "Static Assets"
        SA["assets/"]:::internal
    end

    subgraph "Issue & PR Templates"
        IT1["bug_report.md"]:::internal
        IT2["model_addition.md"]:::internal
        IT3["pull_request_template.md"]:::internal
    end

    subgraph "Model Module Template (×N)"
        M["<model_name>/"]:::internal
        subgraph "Module Contents"
            MA["assets/"]:::data
            MX["<model>.xml"]:::data
            SC["scene.xml"]:::data
            MJX["mjx_*.xml"]:::data
            MD["README.md"]:::internal
            MC["CHANGELOG.md"]:::internal
            ML["LICENSE"]:::internal
        end
    end

    subgraph "External Dependencies"
        MU["MuJoCo Engine"]:::external
        PB["Python bindings (mujoco)"]:::external
        RL["robot_descriptions loader"]:::external
    end

    subgraph "Consumers"
        CU1["Python API"]:::consumer
        CU2["CLI Viewer"]:::consumer
    end

    %% Relationships
    Repo -->|"triggers (on commit)"| CI
    CI -->|"validates & tests"| MT
    CI -->|"validates & tests"| MJXT
    CI -->|"uses"| TR
    CI -->|"generates gallery"| GG
    CI -->|"discovers modules"| M
    GG -->|"renders scenes"| SC

    Repo --> SA
    Repo --> RD1
    Repo --> RD2
    Repo --> RD3
    Repo --> RD4
    Repo --> IT1
    Repo --> IT2
    Repo --> IT3

    CU1 -->|"loads <model>.xml"| RL
    RL -->|"passes XML & assets"| MU
    CU2 -->|"calls mujoco.viewer"| MU
    MU -->|"runs simulation"| MU

    %% Discovery of modules by scripts & CI
    GG --> M
    MT --> M
    MJXT --> M

    %% Click Events
    click CI "https://github.com/google-deepmind/mujoco_menagerie/blob/main/.github/workflows/build.yml"
    click MT "https://github.com/google-deepmind/mujoco_menagerie/blob/main/test/model_test.py"
    click MJXT "https://github.com/google-deepmind/mujoco_menagerie/blob/main/test/mjx_model_test.py"
    click TR "https://github.com/google-deepmind/mujoco_menagerie/blob/main/test/requirements.txt"
    click GG "https://github.com/google-deepmind/mujoco_menagerie/blob/main/generate_gallery.py"
    click RD1 "https://github.com/google-deepmind/mujoco_menagerie/blob/main/README.md"
    click RD2 "https://github.com/google-deepmind/mujoco_menagerie/blob/main/CONTRIBUTING.md"
    click RD3 "https://github.com/google-deepmind/mujoco_menagerie/blob/main/CHANGELOG.md"
    click RD4 "https://github.com/google-deepmind/mujoco_menagerie/tree/main/LICENSE"
    click SA "https://github.com/google-deepmind/mujoco_menagerie/tree/main/assets/"
    click IT1 "https://github.com/google-deepmind/mujoco_menagerie/blob/main/.github/ISSUE_TEMPLATE/bug_report.md"
    click IT2 "https://github.com/google-deepmind/mujoco_menagerie/blob/main/.github/ISSUE_TEMPLATE/model_addition.md"
    click IT3 "https://github.com/google-deepmind/mujoco_menagerie/blob/main/.github/pull_request_template.md"
    click MA "https://github.com/google-deepmind/mujoco_menagerie/tree/main/franka_emika_panda/assets/"
    click MX "https://github.com/google-deepmind/mujoco_menagerie/blob/main/franka_emika_panda/panda.xml"
    click SC "https://github.com/google-deepmind/mujoco_menagerie/blob/main/franka_emika_panda/scene.xml"
    click MJX "https://github.com/google-deepmind/mujoco_menagerie/blob/main/franka_emika_panda/mjx_*.xml"
    click MD "https://github.com/google-deepmind/mujoco_menagerie/blob/main/franka_emika_panda/README.md"
    click MC "https://github.com/google-deepmind/mujoco_menagerie/blob/main/franka_emika_panda/CHANGELOG.md"
    click ML "https://github.com/google-deepmind/mujoco_menagerie/tree/main/franka_emika_panda/LICENSE"
    click M "https://github.com/google-deepmind/mujoco_menagerie/tree/main/unitree_go2/"
    classDef internal fill:#cce5ff,stroke:#333,stroke-width:1px
    classDef scripts fill:#ccffcc,stroke:#333,stroke-width:1px
    classDef ci fill:#ffebcc,stroke:#333,stroke-width:1px,stroke-dasharray: 5 5
    classDef external fill:#f8d7da,stroke:#333,stroke-width:1px
    classDef consumer fill:#e2e3e5,stroke:#333,stroke-width:1px
    classDef data fill:#d1ecf1,stroke:#333,stroke-width:1px

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