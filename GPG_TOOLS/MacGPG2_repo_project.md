---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/GPGTools/MacGPG2
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExeWRyejBiMWgzb200eDUwdmh3OW1seHdpY3BnbG9jYXQweXMzYzU3diZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/d3MLdIYIHup9Q2xG/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# MacGPG2 repo project
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
title: "MacGPG2 repo project"
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
    %% Layer 1: Upstream Sources
    subgraph "Layer 1: Upstream Sources"
        style Up_GnuPG fill:#D0E8FF,stroke:#004080
        Up_GnuPG["GnuPG Upstream"]:::upstream
        style Up_GnuTLS fill:#D0E8FF,stroke:#004080
        Up_GnuTLS["GnuTLS Upstream"]:::upstream
        style Up_Nettle fill:#D0E8FF,stroke:#004080
        Up_Nettle["Nettle Upstream"]:::upstream
    end

    %% Layer 2: Patch Manager
    subgraph "Layer 2: Patch Manager"
        style Patches_GnuPG fill:#FFF4C2,stroke:#8A6508
        Patches_GnuPG["patches/gnupg"]:::patch
        style Patches_GnuTLS fill:#FFF4C2,stroke:#8A6508
        Patches_GnuTLS["patches/gnutls"]:::patch
        style Patches_Nettle fill:#FFF4C2,stroke:#8A6508
        Patches_Nettle["patches/nettle"]:::patch
    end

    %% Layer 3: Build Orchestrator
    subgraph "Layer 3: Build Orchestrator"
        style MakefileNode fill:#D2F8D2,stroke:#1A7F1A
        MakefileNode["Makefile"]:::build
        style Script_Version fill:#D2F8D2,stroke:#1A7F1A
        Script_Version["add_version_plist.sh"]:::build
        style Script_CreateGPG fill:#D2F8D2,stroke:#1A7F1A
        Script_CreateGPG["create_gpg.sh"]:::build
        style Script_CheckSH fill:#D2F8D2,stroke:#1A7F1A
        Script_CheckSH["check_for_new_versions (FTP).sh"]:::build
        style Script_CheckPY fill:#D2F8D2,stroke:#1A7F1A
        Script_CheckPY["check_for_new_versions.py"]:::build
        style Config_Version fill:#D2F8D2,stroke:#1A7F1A
        Config_Version["Version.config"]:::build
        style Config_Libs fill:#D2F8D2,stroke:#1A7F1A
        Config_Libs["libs.json"]:::build

        %% External dependencies
        style ExtDeps fill:#E0E0E0,stroke:#606060
        ExtDeps["gcc/clang, lzip, patch, autotools"]:::external
    end

    %% Layer 4: Packaging Module
    subgraph "Layer 4: Packaging Module"
        style Payload_Bin fill:#FFE0B2,stroke:#B35900
        Payload_Bin["payload/bin"]:::payload
        style Payload_Libexec fill:#FFE0B2,stroke:#B35900
        Payload_Libexec["payload/libexec"]:::payload
        style Payload_Skel fill:#FFE0B2,stroke:#B35900
        Payload_Skel["payload/etc/skel/.gnupg"]:::payload
        style Skel_dirmngr fill:#FFE0B2,stroke:#B35900
        Skel_dirmngr["dirmngr.conf"]:::payload
        style Skel_agent fill:#FFE0B2,stroke:#B35900
        Skel_agent["gpg-agent.conf"]:::payload
        style Skel_gpg fill:#FFE0B2,stroke:#B35900
        Skel_gpg["gpg.conf"]:::payload
    end

    %% Layer 5: Installation Target
    subgraph "Layer 5: Installation Target"
        style Install_Target fill:#FFFFFF,stroke:#000000
        Install_Target["build/MacGPG2 → /usr/local/MacGPG2"]:::target
    end

    %% Relationships & Data Flow
    Up_GnuPG -->|"fetch"| Patches_GnuPG
    Up_GnuTLS -->|"fetch"| Patches_GnuTLS
    Up_Nettle -->|"fetch"| Patches_Nettle

    Patches_GnuPG -->|"apply patches"| MakefileNode
    Patches_GnuTLS -->|"apply patches"| MakefileNode
    Patches_Nettle -->|"apply patches"| MakefileNode

    MakefileNode -->|"invoke scripts"| Script_Version
    MakefileNode -->|"invoke scripts"| Script_CreateGPG
    MakefileNode -->|"invoke scripts"| Script_CheckSH
    MakefileNode -->|"invoke scripts"| Script_CheckPY
    MakefileNode -->|"use configs"| Config_Version
    MakefileNode -->|"use configs"| Config_Libs

    ExtDeps -->|"tools for build"| MakefileNode

    MakefileNode -->|"compile & link"| Payload_Bin
    MakefileNode -->|"generate helpers"| Payload_Libexec
    MakefileNode -->|"populate configs"| Payload_Skel

    Payload_Skel --> Skel_dirmngr
    Payload_Skel --> Skel_agent
    Payload_Skel --> Skel_gpg

    Payload_Bin -->|"assemble payload"| Install_Target
    Payload_Libexec -->|"assemble payload"| Install_Target
    Payload_Skel -->|"assemble payload"| Install_Target

    %% Click Events
    click Patches_GnuPG "https://github.com/gpgtools/macgpg2/tree/dev/patches/gnupg"
    click Patches_GnuTLS "https://github.com/gpgtools/macgpg2/tree/dev/patches/gnutls"
    click Patches_Nettle "https://github.com/gpgtools/macgpg2/tree/dev/patches/nettle"
    click MakefileNode "https://github.com/gpgtools/macgpg2/tree/dev/Makefile"
    click Script_Version "https://github.com/gpgtools/macgpg2/blob/dev/add_version_plist.sh"
    click Script_CreateGPG "https://github.com/gpgtools/macgpg2/blob/dev/create_gpg.sh"
    click Script_CheckSH "https://github.com/gpgtools/macgpg2/blob/dev/check_for_new_versions (FTP).sh"
    click Script_CheckPY "https://github.com/gpgtools/macgpg2/blob/dev/check_for_new_versions.py"
    click Config_Version "https://github.com/gpgtools/macgpg2/blob/dev/Version.config"
    click Config_Libs "https://github.com/gpgtools/macgpg2/blob/dev/libs.json"
    click Payload_Bin "https://github.com/gpgtools/macgpg2/tree/dev/payload/bin"
    click Payload_Libexec "https://github.com/gpgtools/macgpg2/tree/dev/payload/libexec"
    click Payload_Skel "https://github.com/gpgtools/macgpg2/blob/dev/payload/etc/skel/.gnupg"
    click Skel_dirmngr "https://github.com/gpgtools/macgpg2/blob/dev/payload/etc/skel/.gnupg/dirmngr.conf"
    click Skel_agent "https://github.com/gpgtools/macgpg2/blob/dev/payload/etc/skel/.gnupg/gpg-agent.conf"
    click Skel_gpg "https://github.com/gpgtools/macgpg2/blob/dev/payload/etc/skel/.gnupg/gpg.conf"

    %% Styles
    classDef upstream fill:#D0E8FF,stroke:#004080,stroke-width:1px
    classDef patch fill:#FFF4C2,stroke:#8A6508,stroke-width:1px
    classDef build fill:#D2F8D2,stroke:#1A7F1A,stroke-width:1px
    classDef payload fill:#FFE0B2,stroke:#B35900,stroke-width:1px
    classDef external fill:#E0E0E0,stroke:#606060,stroke-width:1px
    classDef target fill:#FFFFFF,stroke:#000000,stroke-width:1px,stroke-dasharray: 5 5
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
