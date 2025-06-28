---
created: 2025-06-25 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/Orange-Cyberdefense/arsenal
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExb2dnYTBqZHZjczg4c2xuaDF4NXVkNzMwa3J4N3F5OGNpMzFmZHQzYSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/My8Zr0fQ7yBY83g49m/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# arsenal repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for 👨‍🎓 <ins>educational purposes</ins> 👨‍🎓 (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), 📖 <ins> personal study </ins> 📖, and 🔖 <ins> reference </ins> 🔖.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


-----

```mermaid
---
title: "arsenal repo project"
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

    User@{ img: "https://raw.githubusercontent.com/CongLeSolutionX/CongLeSolutionX/refs/heads/main/assets/images/My-meme-questions-magnifying-glass-tangled-lines-bubble-thought-cyber-theme.png", label: "User", pos: "b", w: 200, h: 150, constraint: "on" }
    
    User:::external

    subgraph Core_Modules["Core Modules"]
    style Core_Modules fill:#F2F2,stroke:#333,stroke-width:1px, color: #FFFF
        CLI["CLI Parser"]:::core
        Config["Config Manager"]:::core
        Loader["Cheat Loader"]:::core
        Search["Search/UI Module"]:::core
        Builder["Command Builder"]:::core
        Injector["Injection Engine"]:::core
    end
    subgraph Data_Sources["Data Sources"]
    style Data_Sources fill:#F335,stroke:#333,stroke-width:1px, color: #FFFF
        FileSystem[(Cheats File System)]:::data
        MyCheats[(my_cheats)]:::data
    end
    subgraph External_Tools["External Tools"]
    style External_Tools fill:#F3B5,stroke:#333,stroke-width:1px, color: #FFFF
        FZF["fzf"]:::external
        Tmux["tmux"]:::external
    end
    Shell["Shell/Tmux"]:::external
    subgraph Entry_and_Packaging["Entry & Packaging"]
    style Entry_and_Packaging fill:#3BB5,stroke:#333,stroke-width:1px, color: #FFFF
        run("run"):::packaging
        setup("setup.py"):::packaging
        pyproject("pyproject.toml"):::packaging
        requirements("requirements.txt"):::packaging
        manifest("MANIFEST.in"):::packaging
        PKGBUILD("PKGBUILD"):::packaging
        CI(".github/workflows/lint_python.yml"):::packaging
    end

    User -->|"CLI Input"| CLI
    CLI -->|"load config"| Config
    Config -->|"paths & settings"| Loader
    Loader -->|"scan cheats"| FileSystem
    Loader -->|"scan user cheats"| MyCheats
    Loader -->|"cheat metadata"| Search
    Search -->|"fuzzy selection"| FZF
    Search -->|"selected cheat"| Builder
    Builder -->|"built command"| Injector
    Injector -->|"inject keystrokes"| Shell
    Injector -->|"inject via tmux"| Tmux
    Tmux -->|"pane communication"| Shell

    click CLI "https://github.com/orange-cyberdefense/arsenal/blob/master/arsenal/__main__.py"
    click CLI "https://github.com/orange-cyberdefense/arsenal/blob/master/arsenal/app.py"
    click Config "https://github.com/orange-cyberdefense/arsenal/blob/master/arsenal/modules/config.py"
    click Loader "https://github.com/orange-cyberdefense/arsenal/blob/master/arsenal/modules/cheat.py"
    click FileSystem "https://github.com/orange-cyberdefense/arsenal/tree/master/arsenal/data/cheats/"
    click Search "https://github.com/orange-cyberdefense/arsenal/blob/master/arsenal/modules/gui.py"
    click Builder "https://github.com/orange-cyberdefense/arsenal/blob/master/arsenal/modules/command.py"
    click Injector "https://github.com/orange-cyberdefense/arsenal/blob/master/arsenal/modules/check.py"
    click run "https://github.com/orange-cyberdefense/arsenal/tree/master/run"
    click setup "https://github.com/orange-cyberdefense/arsenal/blob/master/setup.py"
    click pyproject "https://github.com/orange-cyberdefense/arsenal/blob/master/pyproject.toml"
    click requirements "https://github.com/orange-cyberdefense/arsenal/blob/master/requirements.txt"
    click manifest "https://github.com/orange-cyberdefense/arsenal/blob/master/MANIFEST.in"
    click PKGBUILD "https://github.com/orange-cyberdefense/arsenal/tree/master/PKGBUILD"
    click CI "https://github.com/orange-cyberdefense/arsenal/blob/master/.github/workflows/lint_python.yml"

    classDef core fill:#A2E6,stroke:#000
    classDef external fill:#F28B,stroke:#000
    classDef data fill:#FA52,stroke:#000
    classDef packaging fill:#D3D8,stroke:#000

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
