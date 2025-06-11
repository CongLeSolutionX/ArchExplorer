---
created: 2025-03-23 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExdDl3cXMwNWE1aXBzbXhsNndkcW9saTBjazFxeHVzeWk3cTBkd240MyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/0U7bWQK9s75PjRKcHz/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----



# Aftermath
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---



```mermaid
---
title: "JamF - Aftermath"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'graph': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A["Main Application Core"]:::core

    subgraph "Collection Modules"
        B["Artifacts Module"]:::module
        C["Filesystem Module"]:::module
        D["Network Module"]:::module
        E["Persistence Module"]:::module
        F["Processes Module"]:::module
        G["Endpoint Security Module"]:::module
        H["System Recon Module"]:::module
        I["Unified Logs Module"]:::module
    end

    J["Output/Artifact Repository"]:::output
    K["Analysis Module"]:::analysis
    L["Parsed Results (Timeline,Narrative)"]:::analysis

    subgraph "Support Components"
        M["Extension Utilities"]:::support
        N["Helper Components"]:::support
        O["Library Integrations"]:::support
    end

    subgraph "External Dependencies"
        P["macOS APIs"]:::external
        Q["TrueTree"]:::external
        R["Shell Utilities"]:::external
    end

    %% Main Core invokes Collection Modules
    A -->|"invokes"| B
    A -->|"invokes"| C
    A -->|"invokes"| D
    A -->|"invokes"| E
    A -->|"invokes"| F
    A -->|"invokes"| G
    A -->|"invokes"| H
    A -->|"invokes"| I

    %% Collection Modules output to central repository
    B -->|"outputs"| J
    C -->|"outputs"| J
    D -->|"outputs"| J
    E -->|"outputs"| J
    F -->|"outputs"| J
    G -->|"outputs"| J
    H -->|"outputs"| J
    I -->|"outputs"| J

    %% Analysis Phase consumes the output repository
    J -->|"analyzed_by"| K
    K -->|"produces"| L

    %% Optional analysis via CLI flag
    A -->|"--analyze"| K

    %% Support Dependencies (dashed connections)
    B -.-> M
    C -.-> M
    D -.-> M
    E -.-> M
    F -.-> O
    G -.-> O
    H -.-> N
    I -.-> M

    %% External Dependencies Connections
    C -.-> P
    D -.-> P
    G -.-> P
    F -.-> Q
    G -.-> Q
    D -.-> R
    F -.-> R

    %% Click Events
    click A "https://github.com/jamf/aftermath/blob/main/aftermath/main.swift"
    click K "https://github.com/jamf/aftermath/blob/main/analysis/AnalysisModule.swift"
    click B "https://github.com/jamf/aftermath/blob/main/artifacts/ArtifactsModule.swift"
    click C "https://github.com/jamf/aftermath/blob/main/filesystem/FileSystemModule.swift"
    click D "https://github.com/jamf/aftermath/blob/main/network/NetworkModule.swift"
    click E "https://github.com/jamf/aftermath/blob/main/persistence/PersistenceModule.swift"
    click F "https://github.com/jamf/aftermath/blob/main/processes/ProcessModule.swift"
    click G "https://github.com/jamf/aftermath/blob/main/endpointSecurity/ESModule.swift"
    click H "https://github.com/jamf/aftermath/blob/main/systemRecon/SystemReconModule.swift"
    click I "https://github.com/jamf/aftermath/blob/main/unifiedlogs/UnifiedLogModule.swift"
    click M "https://github.com/jamf/aftermath/tree/main/extensions"
    click N "https://github.com/jamf/aftermath/blob/main/helpers/CHelpers.swift"
    click O "https://github.com/jamf/aftermath/tree/main/libs"

    %% Style Definitions
    classDef core fill:#fcc43,stroke:#ff0000,stroke-width:2px
    classDef module fill:#cfc33,stroke:#008000,stroke-width:2px
    classDef output fill:#ccf23,stroke:#0000ff,stroke-width:2px
    classDef analysis fill:#e0cff,stroke:#6600cc,stroke-width:2px
    classDef support fill:#fcc33,stroke:#999900,stroke-width:2px
    classDef external fill:#fec32,stroke:#cc6600,stroke-width:2px

    class A core
    class B,C,D,E,F,G,H,I module
    class J output
    class K,L analysis
    class M,N,O support
    class P,Q,R external
    
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
