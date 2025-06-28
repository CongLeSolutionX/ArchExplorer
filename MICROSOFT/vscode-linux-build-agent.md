---
created: 2025-03-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/microsoft/vscode-linux-build-agent
---



# vscode-linux-build-agent repo project
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
title: "vscode-linux-build-agent repo project"
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
    %% Top: CI Pipelines
    subgraph Azure_DevOps_Pipelines["Azure DevOps Pipelines"]
    style Azure_DevOps_Pipelines fill:#F2F2,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        Pipelines["Azure DevOps Pipelines"]:::ci
        Y1["azure-pipelines.yml"]:::ci
        Y2["build-containers.yml"]:::ci
        Y3["build-gnu-toolchain.yml"]:::ci
        Y4["build-musl-toolchain.yml"]:::ci
    end

    %% Sysroot Scripts
    Sysroot["Sysroot-scripts Service"]:::script

    %% Generated Data
    Packages["Generated Package Lists"]:::data
    P1["bullseye.amd64"]:::data
    P2["bullseye.arm64"]:::data
    P3["bullseye.armhf"]:::data

    %% Docker Engine
    Engine["Docker Engine"]:::engine

    %% Dockerfiles by distro/arch
    subgraph Dockerfiles_by_Distro_Arch["Dockerfiles by Distro/Arch"]
    style Dockerfiles_by_Distro_Arch fill:#BB22,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        subgraph Active_Targets["Active Targets"]
        style Active_Targets fill:#22BB,stroke:#333,stroke-width:1px, color: #FFFF
        direction TB
            DA1["alpine-arm64/Dockerfile"]:::dockerfile
            DA2["alpine-x64/Dockerfile"]:::dockerfile
        end
        subgraph Archived["Archived (Legacy)"]
        style Archived fill:#BEF2,stroke:#333,stroke-width:1px, color: #FFFF
        direction TB
            AR1["archived/arm64/Dockerfile_Unused"]:::dockerfile
            AR2["archived/armhf/Dockerfile_Unused"]:::dockerfile
            AR3["archived/bionic-arm32v7/Dockerfile_Unused"]:::dockerfile
            AR4["archived/bionic-arm64/Dockerfile_Unused"]:::dockerfile
            AR5["archived/bionic-armhf/Dockerfile_Unused"]:::dockerfile
            AR6["archived/bionic-x64-v0/Dockerfile_Unused"]:::dockerfile
            AR7["archived/bionic-x64-v0/xvfb-init.sh"]:::script
            AR8["archived/bionic-x64-v1/Dockerfile_Unused"]:::dockerfile
            AR9["archived/bionic-x64-v1/xvfb-init.sh"]:::script
        end
        subgraph Snapcraft_Packaging["Snapcraft Packaging"]
        style Snapcraft_Packaging fill:#E22,stroke:#333,stroke-width:1px, color: #FFFF
        direction TB
          SNAP["snapcraft-x64/Dockerfile"]:::dockerfile
        end
    end

    %% Registry and Consumers
    Registry["Container Registry"]:::registry
    Consumers["VS Code Build Consumers"]:::consumer

    %% External Repos
    External["External Package Repositories"]:::external

    %% Connections
    Pipelines --> Y1
    Pipelines --> Y2
    Pipelines --> Y3
    Pipelines --> Y4
    Pipelines -->|triggers| Sysroot
    External -->|provides packages| Sysroot
    Sysroot -->|generates| Packages
    Packages --> P1
    Packages --> P2
    Packages --> P3
    External -->|base layers| Engine
    Sysroot -->|feeds lists| Engine
    Engine -->|builds| DA1
    Engine -->|builds| DA2
    Engine -->|builds| AR1
    Engine -->|builds| AR2
    Engine -->|builds| AR3
    Engine -->|builds| AR4
    Engine -->|builds| AR5
    Engine -->|builds| AR6
    Engine -->|builds| AR7
    Engine -->|builds| AR8
    Engine -->|builds| AR9
    Engine -->|builds| SNAP
    DA1 -->|push| Registry
    DA2 -->|push| Registry
    SNAP -->|push| Registry
    Registry -->|pulled by| Consumers

    %% Click Events
    click Y1 "https://github.com/microsoft/vscode-linux-build-agent/blob/main/azure-pipelines.yml"
    click Y2 "https://github.com/microsoft/vscode-linux-build-agent/blob/main/build-containers.yml"
    click Y3 "https://github.com/microsoft/vscode-linux-build-agent/blob/main/build-gnu-toolchain.yml"
    click Y4 "https://github.com/microsoft/vscode-linux-build-agent/blob/main/build-musl-toolchain.yml"
    click Sysroot "https://github.com/microsoft/vscode-linux-build-agent/blob/main/sysroot-scripts/sysroot-creator.sh"
    click Sysroot "https://github.com/microsoft/vscode-linux-build-agent/blob/main/sysroot-scripts/merge-package-lists.py"
    click Sysroot "https://github.com/microsoft/vscode-linux-build-agent/blob/main/sysroot-scripts/keyring.gpg"
    click P1 "https://github.com/microsoft/vscode-linux-build-agent/blob/main/sysroot-scripts/generated_package_lists/bullseye.amd64"
    click P2 "https://github.com/microsoft/vscode-linux-build-agent/blob/main/sysroot-scripts/generated_package_lists/bullseye.arm64"
    click P3 "https://github.com/microsoft/vscode-linux-build-agent/blob/main/sysroot-scripts/generated_package_lists/bullseye.armhf"
    click DA1 "https://github.com/microsoft/vscode-linux-build-agent/tree/main/alpine-arm64/Dockerfile"
    click DA2 "https://github.com/microsoft/vscode-linux-build-agent/tree/main/alpine-x64/Dockerfile"
    click AR1 "https://github.com/microsoft/vscode-linux-build-agent/tree/main/archived/arm64/Dockerfile_Unused"
    click AR2 "https://github.com/microsoft/vscode-linux-build-agent/tree/main/archived/armhf/Dockerfile_Unused"
    click AR3 "https://github.com/microsoft/vscode-linux-build-agent/tree/main/archived/bionic-arm32v7/Dockerfile_Unused"
    click AR4 "https://github.com/microsoft/vscode-linux-build-agent/tree/main/archived/bionic-arm64/Dockerfile_Unused"
    click AR5 "https://github.com/microsoft/vscode-linux-build-agent/tree/main/archived/bionic-armhf/Dockerfile_Unused"
    click AR6 "https://github.com/microsoft/vscode-linux-build-agent/tree/main/archived/bionic-x64-v0/Dockerfile_Unused"
    click AR7 "https://github.com/microsoft/vscode-linux-build-agent/blob/main/archived/bionic-x64-v0/xvfb-init.sh"
    click AR8 "https://github.com/microsoft/vscode-linux-build-agent/tree/main/archived/bionic-x64-v1/Dockerfile_Unused"
    click AR9 "https://github.com/microsoft/vscode-linux-build-agent/blob/main/archived/bionic-x64-v1/xvfb-init.sh"
    click SNAP "https://github.com/microsoft/vscode-linux-build-agent/tree/main/snapcraft-x64/Dockerfile"

    %% Styles
    classDef ci fill:#EE22,stroke:#4D9FFF,color:#FFFF
    classDef script fill:#C2C,stroke:#FFAA33,color:#FFFF
    classDef data fill:#E6D5,stroke:#47B900,color:#FFFF
    classDef engine fill:#F0F0,stroke:#999999,color:#FFFF
    classDef dockerfile fill:#F2F2,stroke:#FF6666,color:#FFFF
    classDef external fill:#E0FA,stroke:#00ACC1,color:#FFFF,stroke-dasharray: 5 5
    classDef registry fill:#F3F5,stroke:#AB47BC,color:#FFFF
    classDef consumer fill:#ECF1,stroke:#78909C,color:#FFFF
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
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

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