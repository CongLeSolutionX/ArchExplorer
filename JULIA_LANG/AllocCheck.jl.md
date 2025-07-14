---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/JuliaLang/AllocCheck.jl
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




# AllocCheck.jl repo project
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
title: "AllocCheck.jl repo project"
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
flowchart TD
    %% User invocation
    User["User Code"]:::external
    User -->|"@check_allocs macro"| Entry

    %% Main entry file
    Entry["AllocCheck.jl"]:::core
    click Entry "https://github.com/julialang/alloccheck.jl/blob/main/src/AllocCheck.jl"
    Entry -->|"expand macro"| Macro

    subgraph "src/ modules"
        direction TB
        Macro["@check_allocs (macro.jl)"]:::macro
        click Macro "https://github.com/julialang/alloccheck.jl/blob/main/src/macro.jl"

        subgraph "Compiler Front-End" 
            direction TB
            CompilerFE["compiler.jl"]:::compiler
            click CompilerFE "https://github.com/julialang/alloccheck.jl/blob/main/src/compiler.jl"
            CompilerUtils["compiler_utils.jl"]:::compiler
            click CompilerUtils "https://github.com/julialang/alloccheck.jl/blob/main/src/compiler_utils.jl"
        end

        Classify["Classification Engine (classify.jl)"]:::classify
        click Classify "https://github.com/julialang/alloccheck.jl/blob/main/src/classify.jl"

        ABI["ABI Handler (abi_call.jl)"]:::classify
        click ABI "https://github.com/julialang/alloccheck.jl/blob/main/src/abi_call.jl"

        BT["Backtrace Builder (static_backtrace.jl)"]:::report
        click BT "https://github.com/julialang/alloccheck.jl/blob/main/src/static_backtrace.jl"

        Types["Type Definitions (types.jl)"]:::support
        click Types "https://github.com/julialang/alloccheck.jl/blob/main/src/types.jl"

        Utils["Utilities (utils.jl)"]:::support
        click Utils "https://github.com/julialang/alloccheck.jl/blob/main/src/utils.jl"
    end

    %% External dependencies
    GPUCompiler["GPUCompiler.jl / LLVM.jl"]:::external

    %% Sidecar subsystems
    subgraph Documentation
        direction TB
        Make["docs/make.jl"]:::docs
        click Make "https://github.com/julialang/alloccheck.jl/blob/main/docs/make.jl"
        DocsSrc["docs/src/"]:::docs
        click DocsSrc "https://github.com/julialang/alloccheck.jl/tree/main/docs/src/"
    end

    subgraph "Test Suite"
        direction TB
        Test["runtests.jl"]:::test
        click Test "https://github.com/julialang/alloccheck.jl/blob/main/test/runtests.jl"
    end

    subgraph "CI Workflows"
        direction TB
        CI1["CI.yml"]:::ci
        click CI1 "https://github.com/julialang/alloccheck.jl/blob/main/.github/workflows/CI.yml"
        CI2["CompatHelper.yml"]:::ci
        click CI2 "https://github.com/julialang/alloccheck.jl/blob/main/.github/workflows/CompatHelper.yml"
        CI3["TagBot.yml"]:::ci
        click CI3 "https://github.com/julialang/alloccheck.jl/blob/main/.github/workflows/TagBot.yml"
        CI4["docs.yml"]:::ci
        click CI4 "https://github.com/julialang/alloccheck.jl/blob/main/.github/workflows/docs.yml"
    end

    %% Core pipeline
    Macro -->|"call compiler"| CompilerFE
    CompilerFE -->|"request IR"| GPUCompiler
    GPUCompiler -->|"LLVM IR"| CompilerFE
    CompilerFE -->|"full IR"| ABI
    CompilerFE -->|"full IR"| Classify
    ABI -->|"resolved calls"| Classify
    Classify -->|"AllocationReport"| BT
    BT -->|"AllocCheckFailure / Result"| Entry
    Entry -->|"return result or throw"| User

    %% Support usage
    Types -.-> Macro
    Types -.-> CompilerFE
    Types -.-> Classify
    Types -.-> BT
    Utils -.-> CompilerFE
    Utils -.-> Classify
    Utils -.-> BT

    %% Side arrows
    Test -.-> Macro
    Test -.-> Entry
    Documentation -.-> Entry
    CI1 -.-> Test
    CI1 -.-> Documentation

    %% Styles
    classDef macro fill:#cce5ff,stroke:#333
    classDef compiler fill:#d4edda,stroke:#333
    classDef classify fill:#fff3cd,stroke:#333
    classDef report fill:#f8d7da,stroke:#333
    classDef support fill:#e2e3e5,stroke:#333
    classDef core fill:#cfe2ff,stroke:#333
    classDef external fill:#f5c6cb,stroke:#333,stroke-dasharray: 5 5
    classDef docs fill:#d1ecf1,stroke:#333
    classDef test fill:#d6d8db,stroke:#333
    classDef ci fill:#d1d3e0,stroke:#333

```


---

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