---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/apple/containerization
---



# containerization repo project
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


----

```mermaid
---
title: "containerization repo project"
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
    %% Host Application Layer
    subgraph "Host Application Layer"
        direction TB
        cctl["cctl CLI"]:::host
        Containerization["Containerization Library"]:::host
    end

    cctl -->|uses APIs| Containerization

    %% Containerization sub-modules
    subgraph "Containerization Modules"
        direction TB
        OCIClient["OCI Client"]:::host
        OCIContent["OCI Content Store"]:::host
        EXT4Builder["EXT4 Rootfs Builder"]:::host
        Archive["Archive Support"]:::host
        Netlink["Netlink Networking"]:::host
        OSAbstractions["OS Abstractions"]:::host
        Extras["Extras"]:::host
        IOStreams["I/O Streams"]:::host
        VMManager["VM Manager"]:::host
        SandboxContext["SandboxContext (gRPC stubs)"]:::host
        CShim["CShim"]:::host
    end

    Containerization --> OCIClient
    Containerization --> OCIContent
    Containerization --> EXT4Builder
    Containerization --> Archive
    Containerization --> Netlink
    Containerization --> OSAbstractions
    Containerization --> Extras
    Containerization --> IOStreams
    Containerization --> VMManager
    Containerization --> SandboxContext
    Containerization --> CShim

    %% External Services
    OCIRegistry["OCI Registry (HTTPS)"]:::ext
    HostNet["Host Network Stack"]:::ext

    OCIClient -->|pull/push images| OCIRegistry
    Netlink -->|configures NAT| HostNet

    %% Virtualization.framework
    VZFW["Virtualization.framework"]:::virt

    Containerization -->|launch VM, vsock| VZFW

    %% VM Side
    subgraph "Lightweight VM" 
        direction TB
        LinuxKernel["Linux Kernel"]:::vmintern
        Rootfs["Rootfs ext4"]:::vmintern
        vminitd["vminitd (gRPC Server over vsock)"]:::vmintern
        Processes["Containerized Processes"]:::vmintern
    end

    VZFW --> LinuxKernel
    VZFW --> Rootfs
    VZFW --> vminitd
    vminitd --> Processes

    SandboxContext -->|gRPC over vsock| vminitd

    %% Kernel Build
    KernelBuild["Kernel Build Environment"]:::ext
    PrebuiltKernel["Pre-built Kernel Image"]:::ext

    KernelBuild --> PrebuiltKernel
    PrebuiltKernel --> LinuxKernel

    %% Build & CI
    subgraph "Build & Test Infrastructure"
        direction TB
        MakefileNode["Makefile"]:::ci
        GitHubActions[".github/workflows"]:::ci
        ProtoMake["Protobuf.Makefile"]:::ci
    end

    MakefileNode -->|triggers| cctl
    GitHubActions -->|runs| Containerization
    ProtoMake -->|generates stubs| SandboxContext

    %% Click Events
    click cctl "https://github.com/apple/containerization/tree/main/Sources/cctl/"
    click Containerization "https://github.com/apple/containerization/tree/main/Sources/Containerization/"
    click OCIClient "https://github.com/apple/containerization/tree/main/Sources/ContainerizationOCI/Client/"
    click OCIContent "https://github.com/apple/containerization/tree/main/Sources/ContainerizationOCI/Content/"
    click EXT4Builder "https://github.com/apple/containerization/tree/main/Sources/ContainerizationEXT4/"
    click Archive "https://github.com/apple/containerization/tree/main/Sources/ContainerizationArchive/"
    click Netlink "https://github.com/apple/containerization/tree/main/Sources/ContainerizationNetlink/"
    click OSAbstractions "https://github.com/apple/containerization/tree/main/Sources/ContainerizationOS/"
    click Extras "https://github.com/apple/containerization/tree/main/Sources/ContainerizationExtras/"
    click IOStreams "https://github.com/apple/containerization/tree/main/Sources/Containerization/IO/"
    click VMManager "https://github.com/apple/containerization/blob/main/Sources/Containerization/VZVirtualMachine+Helpers.swift"
    click VMManager "https://github.com/apple/containerization/blob/main/Sources/Containerization/VZVirtualMachineManager.swift"
    click VMManager "https://github.com/apple/containerization/blob/main/Sources/Containerization/VirtualMachineManager.swift"
    click SandboxContext "https://github.com/apple/containerization/tree/main/Sources/Containerization/SandboxContext/"
    click CShim "https://github.com/apple/containerization/tree/main/Sources/CShim/"
    click vminitd "https://github.com/apple/containerization/tree/main/vminitd/Sources/vminitd/"
    click LCShim "https://github.com/apple/containerization/tree/main/vminitd/Sources/LCShim/"
    click vmexec "https://github.com/apple/containerization/tree/main/vminitd/Sources/vmexec/"
    click KernelBuild "https://github.com/apple/containerization/tree/main/kernel/"
    click PrebuiltKernel "https://github.com/apple/containerization/tree/main/kernel/image/"
    click MakefileNode "https://github.com/apple/containerization/tree/main/Makefile"
    click GitHubActions "https://github.com/apple/containerization/tree/main/.github/workflows/"
    click ProtoMake "https://github.com/apple/containerization/blob/main/Protobuf.Makefile"

    %% Styles
    classDef host fill:#D0E8FF,stroke:#0000FF
    classDef virt fill:#EEEEEE,stroke:#888888
    classDef vmintern fill:#DDFFDD,stroke:#00AA00
    classDef ext fill:#FFE0B2,stroke:#FF8800
    classDef ci fill:#FFF3B0,stroke:#CC9900
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

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }

```

---
> **Licenses:**
>
> - **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
> - **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).
> 
---
