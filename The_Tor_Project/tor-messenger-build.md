---
created: 2025-06-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/TheTorProject/tor-messenger-build
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExbXFtdDhnZG1kcjlnMDhkYzZ0cWcyNDdtMDNzMnlzd3lrcjU0a2hubyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/l0Iy3uCVSzlSmtQbe/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# tor-messenger-build repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>

---

```mermaid
---
title: "tor-messenger-build repo project"
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
    %% Host Infrastructure
    subgraph "Host Infrastructure"
        style HostEnv fill:#cccccc
        HostEnv["Host Build Environment"]:::infra
    end

    %% Provisioner
    Ansible["Ansible Provisioner"]:::orchestrator
    click Ansible "https://github.com/thetorproject/tor-messenger-build/tree/master//tools/ansible"

    %% Orchestrator & Config
    subgraph "Configuration & Orchestrator"
        style Makefile fill:#e0ffe0
        Makefile["Makefile Orchestrator\n(rbm, rbm.conf)"]:::orchestrator
    end
    click Makefile "https://github.com/thetorproject/tor-messenger-build/tree/master//Makefile"
    click Makefile "https://github.com/thetorproject/tor-messenger-build/tree/master//rbm"
    click Makefile "https://github.com/thetorproject/tor-messenger-build/blob/master//rbm.conf"

    %% External Dependencies
    subgraph "External Dependencies"
        style Fetchers fill:#ffe0b3
        Fetchers["Source Fetchers\n(git, hg)"]:::external
        style Keyring fill:#ffe0b3
        Keyring["GPG Keyring"]:::external
    end
    click Fetchers "https://github.com/thetorproject/tor-messenger-build/tree/master//tools/version-control-tools"
    click Keyring "https://github.com/thetorproject/tor-messenger-build/tree/master//keyring"

    %% Project Modules
    subgraph "Project Modules" 
        style Projects fill:#e0f0ff
        Projects["Common Build Helpers"]:::build
        TorMessenger["Tor Messenger"]:::build
        TorBrowser["Tor Browser"]:::build
        Thunderbird["Thunderbird"]:::build
        Libgcrypt["libgcrypt"]:::build
        Libotr["libotr"]:::build
        MozillaCore["Mozilla Core"]:::build
        Instantbird["Instantbird"]:::build
        ContainerTemplate["Container Image Template"]:::build
        PatchConfig["Patch & Config Layer"]:::build
    end
    click Projects "https://github.com/thetorproject/tor-messenger-build/tree/master//projects/common"
    click TorMessenger "https://github.com/thetorproject/tor-messenger-build/tree/master//projects/tor-messenger"
    click TorBrowser "https://github.com/thetorproject/tor-messenger-build/tree/master//projects/tor-browser"
    click Thunderbird "https://github.com/thetorproject/tor-messenger-build/tree/master//projects/thunderbird"
    click Libgcrypt "https://github.com/thetorproject/tor-messenger-build/tree/master//projects/libgcrypt"
    click Libotr "https://github.com/thetorproject/tor-messenger-build/tree/master//projects/libotr"
    click MozillaCore "https://github.com/thetorproject/tor-messenger-build/tree/master//projects/mozilla"
    click Instantbird "https://github.com/thetorproject/tor-messenger-build/tree/master//projects/instantbird"
    click ContainerTemplate "https://github.com/thetorproject/tor-messenger-build/tree/master//projects/container-image"
    click PatchConfig "https://github.com/thetorproject/tor-messenger-build/tree/master//projects/*/config"

    %% Build Containers
    subgraph "Build Containers (OCI via runc)"
        style BuildContainers fill:#e0f0ff
        BuildContainers["Ephemeral Build Container"]:::build
    end
    click BuildContainers "https://github.com/thetorproject/tor-messenger-build/tree/master//projects/container-image"

    %% Packaging Tools
    subgraph "Packaging Tools"
        style Packaging fill:#e0f0ff
        DMG2MAR["dmg2mar"]:::build
        UpdateResponses["update-responses"]:::build
        NSIS["NSIS Scripts"]:::build
    end
    click DMG2MAR "https://github.com/thetorproject/tor-messenger-build/tree/master//tools/dmg2mar"
    click UpdateResponses "https://github.com/thetorproject/tor-messenger-build/tree/master//tools/update-responses"
    click NSIS "https://github.com/thetorproject/tor-messenger-build/blob/master//projects/tor-messenger/tor-messenger.nsi"

    %% Output Repositories
    subgraph "Output Repositories"
        style Output fill:#cccccc
        OutDir["out/"]:::infra
        ReleaseDir["release/"]:::infra
    end

    %% Flows
    HostEnv -->|provisions via| Ansible
    HostEnv -->|runs| Makefile
    Makefile -->|uses| Fetchers
    Makefile -->|verifies via| Keyring
    Fetchers -->|populate| Projects
    Makefile -->|launches| BuildContainers
    Projects -->|mounts into| BuildContainers
    PatchConfig -->|applies in| BuildContainers
    BuildContainers -->|produces artifacts| Packaging
    Packaging -->|outputs installers| OutDir
    Packaging -->|publishes| ReleaseDir

    %% Styles
    classDef orchestrator fill:#e0ffe0,stroke:#333,stroke-width:1px
    classDef build fill:#e0f0ff,stroke:#333,stroke-width:1px
    classDef external fill:#ffe0b3,stroke:#333,stroke-width:1px
    classDef infra fill:#cccccc,stroke:#333,stroke-width:1px
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
