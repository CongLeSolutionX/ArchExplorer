---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/JuliaLang/juliaup
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




# juliaup repo project
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
title: "juliaup repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#F5E3',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EEF5',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD'
    }
  }
}%%
flowchart TB
    %% User Layer
    User["User (Shell/Terminal)"]:::user

    %% Binaries Layer
    subgraph "User-facing Binaries"
        direction TB
        juliaup["juliaup CLI"]:::binary
        juliainstaller["juliainstaller"]:::binary
        julialauncher["julialauncher"]:::binary
    end

    User -->|"invokes"| juliaup
    User -->|"invokes"| juliainstaller
    User -->|"invokes"| julialauncher

    %% Core Library Layer
    subgraph "Core Library (src/lib.rs)" 
        direction TB
        corelib["Library Entry Point"]:::library
        cli["Command Parser & Dispatcher"]:::library
        cmds["Command Modules\n(src/command_*.rs)"]:::library
        config_file["Configuration File Handling"]:::library
        global_paths["Global Path Abstractions"]:::library
        jsondb["JSON Struct Definitions"]:::library
        versiondb_files["Static Version Manifests\n(versiondb/*.json)"]:::storage
        operations["Core Operations Logic"]:::library
        utils["Utility Functions"]:::library
        versions_file["Local Versions File Abstraction"]:::library
    end

    juliaup -->|"uses"| cli
    cli -->|"loads"| cmds
    cli -->|"calls"| operations
    cli -->|"reads/writes"| config_file
    config_file -->|"uses"| global_paths
    operations -->|"uses"| utils
    operations -->|"loads"| jsondb
    jsondb -->|"reads"| versiondb_files
    operations -->|"reads/writes"| versions_file
    corelib --> cli

    %% File System & External
    subgraph "Persistent Stores & External"
        direction TB
        filesystem["File System\n(JULIAUP_DEPOT_PATH, symlinks)"]:::external
        s3["External Juliaup Server\n(S3 HTTP)"]:::external
    end

    operations -->|"downloads"| s3
    operations -->|"stores artifacts"| filesystem
    cli -->|"reads config"| filesystem

    %% Packaging Subsystem
    subgraph "Packaging Subsystem" 
        direction TB
        msi["MSI Packaging\n(deploy/msi/**)"]:::packaging
        msix["MSIX/AppInstaller\n(deploy/msix/**)"]:::packaging
        shellscript["Shell Script Installer\n(deploy/shellscript/juliaup-init.sh)"]:::packaging
        powershell["PowerShell Helpers\n(deploy/winpkgidentityext/**)"]:::packaging
    end

    juliainstaller -->|"invokes"| shellscript
    juliainstaller -->|"uses"| msi
    juliainstaller -->|"uses"| msix
    juliainstaller -->|"uses"| powershell

    %% CI/CD Pipeline
    subgraph "CI/CD Pipeline (GitHub Actions)" 
        direction TB
        workflows["Workflows\n(.github/workflows/*.yml)"]:::ci
        release_meta["Release Metadata\n(release.toml)"]:::ci
        build_scripts["Build & Release Scripts\n(scripts/**)"]:::ci
    end

    workflows -->|"triggers build"| corelib
    workflows -->|"runs tests"| corelib
    workflows -->|"invokes packaging"| msi
    workflows -->|"invokes packaging"| msix
    workflows -->|"invokes"| build_scripts
    build_scripts -->|"update versiondb"| versiondb_files

    %% Click Events
    click juliaup "https://github.com/julialang/juliaup/blob/main/src/bin/juliaup.rs"
    click juliainstaller "https://github.com/julialang/juliaup/blob/main/src/bin/juliainstaller.rs"
    click julialauncher "https://github.com/julialang/juliaup/blob/main/src/bin/julialauncher.rs"
    click corelib "https://github.com/julialang/juliaup/blob/main/src/lib.rs"
    click cli "https://github.com/julialang/juliaup/blob/main/src/cli.rs"
    click config_file "https://github.com/julialang/juliaup/blob/main/src/config_file.rs"
    click global_paths "https://github.com/julialang/juliaup/blob/main/src/global_paths.rs"
    click jsondb "https://github.com/julialang/juliaup/blob/main/src/jsonstructs_versionsdb.rs"
    click versiondb_files "https://github.com/julialang/juliaup/tree/main/versiondb/"
    click operations "https://github.com/julialang/juliaup/blob/main/src/operations.rs"
    click utils "https://github.com/julialang/juliaup/blob/main/src/utils.rs"
    click versions_file "https://github.com/julialang/juliaup/blob/main/src/versions_file.rs"
    click msi "https://github.com/julialang/juliaup/tree/main/deploy/msi/"
    click msix "https://github.com/julialang/juliaup/tree/main/deploy/msix/"
    click shellscript "https://github.com/julialang/juliaup/blob/main/deploy/shellscript/juliaup-init.sh"
    click powershell "https://github.com/julialang/juliaup/tree/main/deploy/winpkgidentityext/"
    click workflows "https://github.com/julialang/juliaup/tree/main/.github/workflows/"
    click build_scripts "https://github.com/julialang/juliaup/tree/main/scripts/"

    %% Styles
    classDef user fill:#c8facc,stroke:#088f0d,color:#000
    classDef binary fill:#a5f3fc,stroke:#05606d,color:#000
    classDef library fill:#dbeafe,stroke:#1e40af,color:#000
    classDef storage fill:#fef9c3,stroke:#a16207,color:#000
    classDef external fill:#fed7aa,stroke:#c2410c,color:#000
    classDef packaging fill:#e0e7ff,stroke:#4338ca,color:#000
    classDef ci fill:#e5e7eb,stroke:#374151,color:#000
```

-----

<!-- 
```mermaid
%% Current Mermaid version
info
```  -->


```mermaid
---
title: "C<char>o&#770;</char>ngL<char>e&#770;</char>SolutionX"
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
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX/CongLeSolutionX' target='_blank'>Click here if you care about the profile of a tech guy seeking for job 🙏🏼</a>"}}

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