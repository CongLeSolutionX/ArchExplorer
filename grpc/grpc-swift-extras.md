---
created: 2025-06-27 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/grpc/grpc-swift-extras
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExbTc1ZWN5Z2Nka3hldWh6aHpjMGU2cWNuZHp3dXp4bTIybjM2cHBpcCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/hCAndh3LRpdH5CqHHh/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# grpc-swift-extras repo project
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



----

```mermaid
---
title: "grpc-swift-extras repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'linear'},
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#22BB',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EEF2',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '15px'
    }
  }
}%%
flowchart TD
    subgraph "Consumer"
        EUA["End User App"]:::consumer
    end

    EUA -->|"uses Extras Modules"| HGS
    EUA --> RFS
    EUA --> OTEL
    EUA --> SLC

    ExternalCore["Core gRPC Swift"]:::external
    HGS -->|"depends on"| ExternalCore
    IOT --> ExternalCore
    OTEL --> ExternalCore
    RFS --> ExternalCore
    SLC --> ExternalCore

    subgraph "Extras Modules"
        HGS["GRPCHealthService"]:::library
        IOT["GRPCInteropTests"]:::library
        OTEL["GRPCOTelTracingInterceptors"]:::library
        RFS["GRPCReflectionService"]:::library
        SLC["GRPCServiceLifecycle"]:::library
    end

    subgraph "Protobuf Codegen Pipeline" 
        Fetch["fetch.sh"]:::script
        Gen["generate.sh"]:::script
        ProtoDefs["dev/protos/"]:::generated
    end

    Fetch --> Gen
    Gen -->|"generates code into modules"| HGS
    Gen --> IOT
    Gen --> OTEL
    Gen --> RFS
    Gen --> SLC
    Gen --> ProtoDefs

    subgraph "Tests"
        HST["GRPCHealthServiceTests"]:::test
        OTTest["GRPCOTelTracingInterceptorsTests"]:::test
        RFST["GRPCReflectionServiceTests"]:::test
        SLT["GRPCServiceLifecycleTests"]:::test
        IPIT["InProcessInteropTests"]:::test
    end

    HST --> HGS
    OTTest --> OTEL
    RFST --> RFS
    SLT --> SLC
    IPIT -->|"tests Core + Extras"| ExternalCore

    subgraph "CI/CD Workflows"
        CI1["main.yml"]:::ci
        CI2["pull_request.yml"]:::ci
        CI3["pull_request_label.yml"]:::ci
        CI4["soundness.yml"]:::ci
    end

    CI1 --> Fetch
    CI1 --> Gen
    CI1 -->|"build & test"| HST
    CI2 --> HST
    CI3 --> HST
    CI4 -->|"soundness checks"| SLC

    subgraph "Developer Scripts"
        devFormat["format.sh"]:::script
        devCheck["check-generated-code.sh"]:::script
        devLicense["license-check.sh"]:::script
        devSound["soundness.sh"]:::script
    end

    devFormat -->|"runs formatting"| Gen
    devCheck -->|"verifies generated code"| Gen
    devLicense -->|"checks licenses"| HGS
    devSound -->|"soundness analysis"| SLC

    classDef library fill:#add8e6,stroke:#000,stroke-width:1px
    classDef generated fill:#d3d3d3,stroke:#000,stroke-width:1px
    classDef script fill:#98fb98,stroke:#000,stroke-width:1px
    classDef test fill:#90ee90,stroke:#000,stroke-width:1px
    classDef ci fill:#90ee90,stroke:#000,stroke-width:1px
    classDef external fill:#f5f5f5,stroke:#000,stroke-width:1px
    classDef consumer fill:#ffcc99,stroke:#000,stroke-width:1px

    click HGS "https://github.com/grpc/grpc-swift-extras/tree/main/Sources/GRPCHealthService"
    click IOT "https://github.com/grpc/grpc-swift-extras/tree/main/Sources/GRPCInteropTests"
    click OTEL "https://github.com/grpc/grpc-swift-extras/tree/main/Sources/GRPCOTelTracingInterceptors"
    click RFS "https://github.com/grpc/grpc-swift-extras/tree/main/Sources/GRPCReflectionService"
    click SLC "https://github.com/grpc/grpc-swift-extras/tree/main/Sources/GRPCServiceLifecycle"
    click Fetch "https://github.com/grpc/grpc-swift-extras/blob/main/dev/protos/fetch.sh"
    click Gen "https://github.com/grpc/grpc-swift-extras/blob/main/dev/protos/generate.sh"
    click ProtoDefs "https://github.com/grpc/grpc-swift-extras/tree/main/dev/protos/"
    click HST "https://github.com/grpc/grpc-swift-extras/tree/main/Tests/GRPCHealthServiceTests"
    click OTTest "https://github.com/grpc/grpc-swift-extras/tree/main/Tests/GRPCOTelTracingInterceptorsTests"
    click RFST "https://github.com/grpc/grpc-swift-extras/tree/main/Tests/GRPCReflectionServiceTests"
    click SLT "https://github.com/grpc/grpc-swift-extras/tree/main/Tests/GRPCServiceLifecycleTests"
    click IPIT "https://github.com/grpc/grpc-swift-extras/tree/main/Tests/InProcessInteropTests"
    click CI1 "https://github.com/grpc/grpc-swift-extras/blob/main/.github/workflows/main.yml"
    click CI2 "https://github.com/grpc/grpc-swift-extras/blob/main/.github/workflows/pull_request.yml"
    click CI3 "https://github.com/grpc/grpc-swift-extras/blob/main/.github/workflows/pull_request_label.yml"
    click CI4 "https://github.com/grpc/grpc-swift-extras/blob/main/.github/workflows/soundness.yml"
    click devFormat "https://github.com/grpc/grpc-swift-extras/blob/main/dev/format.sh"
    click devCheck "https://github.com/grpc/grpc-swift-extras/blob/main/dev/check-generated-code.sh"
    click devLicense "https://github.com/grpc/grpc-swift-extras/blob/main/dev/license-check.sh"
    click devSound "https://github.com/grpc/grpc-swift-extras/blob/main/dev/soundness.sh"

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
