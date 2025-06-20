---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/VSCodium/vscodium
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExa2J2a3FheWVnYzAyaW9kZGx3dTB5YWttYTE3NHFubTNqdTZsbG00dyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/A06UFEx8jxEwU/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# VSCodium repo project
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


---

```mermaid
---
title: "vscodium repo project"
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
    subgraph "Source & Upstream Integration"
        A1["Upstream VS Code Source"]:::source
        A2["src/insider"]:::source
        A3["src/stable"]:::source
        A4["product.json"]:::source
    end

    subgraph "Patch & Customization Layer"
        B1["patches Directory"]:::patch
        B2["dev/patch.sh"]:::patch
        B3["announcements-builtin.json"]:::patch
        B4["announcements-extra.json"]:::patch
    end

    subgraph "Build & Packaging System"
        C1["build Directory"]:::build
        C2["dev/build.sh, dev/build.ps1, dev/build_docker.sh"]:::build
        C3["build/linux/appimage/recipe.yml"]:::build
        C4["build/windows/msi/build.sh"]:::build
    end

    subgraph "CI/CD & Automation"
        D1["GitHub Actions Workflows (.github/workflows)"]:::cicd
    end

    subgraph "Distribution & Store Integrations"
        E3["release.sh & update_version.sh"]:::dist
        E1["stores/snapcraft"]:::dist
        E2["stores/winget"]:::dist
    end

    subgraph "Documentation"
        F1["docs Directory"]:::docs
    end

    %% Flow Connections
    %% CI/CD triggers build system
    D1 -->|"triggers_build"| C1
    D1 -->|"invokes_build_scripts"| C2

    %% Upstream source is cloned and then customized
    A1 -->|"clone"| B1
    A2 --- A1
    A3 --- A1
    A4 --- A1

    %% Patch & customization layer applies modifications
    B1 -->|"apply_customizations"| C1
    B2 --- B1
    B3 --- B1
    B4 --- B1

    %% Build process: build directory runs scripts to package binaries
    C1 -->|"runs_build_scripts"| C2
    C2 -->|"packages_Linux_binary"| C3
    C2 -->|"packages_Windows_binary"| C4
    C2 -->|"produces_final_binaries"| E3

    %% Distribution channels receive final binaries
    E3 -->|"distributes_to"| E1
    E3 -->|"distributes_to"| E2

    %% Documentation supports build and troubleshooting
    F1 ---|"guides"| C1

    %% Style Definitions
    classDef source fill:#ADD8E6,stroke:#000,stroke-width:1px;
    classDef patch fill:#C1E1C1,stroke:#333,stroke-width:1px;
    classDef build fill:#FFFACD,stroke:#333,stroke-width:1px;
    classDef cicd fill:#FFB6C1,stroke:#333,stroke-width:1px;
    classDef dist fill:#F4A460,stroke:#333,stroke-width:1px;
    classDef docs fill:#D3D3D3,stroke:#333,stroke-width:1px;

    %% Click Events
    click A1 "https://github.com/vscodium/vscodium/tree/master/upstream"
    click A2 "https://github.com/vscodium/vscodium/tree/master/src/insider"
    click A3 "https://github.com/vscodium/vscodium/tree/master/src/stable"
    click A4 "https://github.com/vscodium/vscodium/blob/master/product.json"

    click B1 "https://github.com/vscodium/vscodium/tree/master/patches"
    click B2 "https://github.com/vscodium/vscodium/blob/master/dev/patch.sh"
    click B3 "https://github.com/vscodium/vscodium/blob/master/announcements-builtin.json"
    click B4 "https://github.com/vscodium/vscodium/blob/master/announcements-extra.json"

    click C1 "https://github.com/vscodium/vscodium/tree/master/build"
    click C2 "https://github.com/vscodium/vscodium/blob/master/dev/build.sh"
    click C3 "https://github.com/vscodium/vscodium/blob/master/build/linux/appimage/recipe.yml"
    click C4 "https://github.com/vscodium/vscodium/blob/master/build/windows/msi/build.sh"

    click D1 "https://github.com/vscodium/vscodium/tree/master/.github/workflows"

    click E1 "https://github.com/vscodium/vscodium/tree/master/stores/snapcraft"
    click E2 "https://github.com/vscodium/vscodium/tree/master/stores/winget"
    click E3 "https://github.com/vscodium/vscodium/blob/master/release.sh"

    click F1 "https://github.com/vscodium/vscodium/tree/master/docs"
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
