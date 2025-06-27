---
created: 2025-06-27 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/grpc/grpc-swift-protobuf
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




# grpc-swift-protobuf repo project
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



---

```mermaid
---
title: "grpc-swift-protobuf repo project"
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
    %% Code Generation Pipeline
    subgraph "Code Generation Pipeline"
        direction TB
        ProtoFiles[".proto files"]:::codegen
        Protoc["protoc"]:::codegen
        PluginEntry["protoc-gen-grpc-swift-2"]:::codegen
        CoreLib["GRPCProtobufCodeGen"]:::codegen
        Parser["ProtobufCodeGenParser"]:::codegen
        Generator["ProtobufCodeGenerator"]:::codegen
        GeneratedFiles["Generated Swift Stubs"]:::codegen
    end

    %% Runtime Libraries
    subgraph "Runtime Libraries"
        direction TB
        CRuntime["CGRPCProtobuf (C Library)"]:::runtime
        SwiftRuntime["GRPCProtobuf (Swift Runtime)"]:::runtime
    end

    %% SPM and CLI Plugins
    subgraph "SPM Plugins & CLI"
        direction TB
        SPMPlugin["GRPCProtobufGenerator\n(Build Plugin)"]:::plugin
        CLIPlugin["GRPCProtobufGeneratorCommand\n(CLI Wrapper)"]:::plugin
        SharedUtils["PluginsShared"]:::plugin
    end

    %% Tests
    subgraph "Tests"
        direction TB
        UnitCodeGen["CodeGen Unit Tests"]:::tests
        UnitRuntime["Runtime Unit Tests"]:::tests
        Integration["IntegrationTests"]:::tests
    end

    %% Consumer
    App["Consumer App / Tests"]:::other

    %% Connections
    ProtoFiles --> Protoc
    Protoc -->|"--plugin=protoc-gen-grpc-swift-2"| PluginEntry
    PluginEntry -->|"uses"| CoreLib
    CoreLib --> Parser
    Parser --> Generator
    Generator --> GeneratedFiles
    GeneratedFiles -->|"compile & link"| SwiftRuntime
    SwiftRuntime --> CRuntime

    SPMPlugin -->|"invokes protoc"| Protoc
    CLIPlugin -->|"invokes protoc"| Protoc
    SPMPlugin --> SharedUtils
    CLIPlugin --> SharedUtils

    App --> GeneratedFiles
    App --> SwiftRuntime
    Integration --> SPMPlugin
    Integration --> GeneratedFiles
    UnitCodeGen --> CoreLib
    UnitRuntime --> SwiftRuntime

    %% Click Events
    click CRuntime "https://github.com/grpc/grpc-swift-protobuf/tree/main/Sources/CGRPCProtobuf"
    click SwiftRuntime "https://github.com/grpc/grpc-swift-protobuf/tree/main/Sources/GRPCProtobuf"
    click CoreLib "https://github.com/grpc/grpc-swift-protobuf/tree/main/Sources/GRPCProtobufCodeGen"
    click PluginEntry "https://github.com/grpc/grpc-swift-protobuf/tree/main/Sources/protoc-gen-grpc-swift-2"
    click SPMPlugin "https://github.com/grpc/grpc-swift-protobuf/tree/main/Plugins/GRPCProtobufGenerator"
    click CLIPlugin "https://github.com/grpc/grpc-swift-protobuf/tree/main/Plugins/GRPCProtobufGeneratorCommand"
    click SharedUtils "https://github.com/grpc/grpc-swift-protobuf/tree/main/Plugins/PluginsShared"
    click UnitCodeGen "https://github.com/grpc/grpc-swift-protobuf/tree/main/Tests/GRPCProtobufCodeGenTests"
    click UnitRuntime "https://github.com/grpc/grpc-swift-protobuf/tree/main/Tests/GRPCProtobufTests"
    click Integration "https://github.com/grpc/grpc-swift-protobuf/tree/main/IntegrationTests/PluginTests"

    %% Styles
    classDef codegen fill:#D0E8FF,stroke:#0066CC,color:#003366
    classDef runtime fill:#D0FFD8,stroke:#339933,color:#003300
    classDef plugin fill:#FFE8D0,stroke:#CC6600,color:#663300
    classDef tests fill:#F0F0F0,stroke:#999999,color:#333333
    classDef other fill:#FFD8D8,stroke:#CC3333,color:#660000

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