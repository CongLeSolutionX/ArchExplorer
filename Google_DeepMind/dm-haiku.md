---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/dm-haiku
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




# dm-haiku repo project
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
title: "dm-haiku repo project"
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
    User["User Code"]:::user
    Docs["Documentation & Notebooks"]:::infra

    subgraph "Haiku Public API"
        API_init["__init__.py"]:::library
        API_config["config.py"]:::library
        API_ds["data_structures.py"]:::library
        API_initl["initializers.py"]:::library
        API_mp["mixed_precision.py"]:::library
        API_nets["nets.py"]:::library
        API_pad["pad.py"]:::library
        API_test["testing.py"]:::library
        API_typing["typing.py"]:::library
    end

    subgraph "Haiku Core Library"
        subgraph "Private Source (haiku/_src)"
            Private["haiku/_src"]:::library
            Module["Module Abstraction"]:::library
            Networks["Standard Networks"]:::library
            Transform["Transform Engine"]:::library
            State["Parameter & State Store"]:::storage
            RNG["RNG Management"]:::library
        end
    end

    subgraph "JAX Core"
        JAX["JAX Core<br/>(jit, grad, pmap)"]:::external
        XLA["XLA Compiler & Runtime<br/>(CPU/GPU/TPU)"]:::external
    end

    InfraCI["CI/CD Pipelines"]:::infra
    Build["Build & Deployment Scripts"]:::infra
    TestsInt["Integration Tests & Checkpoints"]:::user
    TestsUnit["Unit Tests"]:::user
    DocsConf["Documentation Build Config"]:::infra

    User -->|"uses API"| API_init
    User --> API_config
    User --> API_ds
    User --> API_initl
    User --> API_mp
    User --> API_nets
    User --> API_pad
    User --> API_test
    User --> API_typing

    User -->|"defines networks"| Module
    Module -->|"collected by init"| State
    User -->|"applies transform"| Transform
    Transform -->|"init"| State
    Transform -->|"apply"| Module
    Transform -->|"uses RNG"| RNG
    Transform -->|"passes to"| JAX
    JAX -->|"compiles with"| XLA

    Private --> Module
    Private --> Networks
    Private --> Transform
    Private --> State
    Private --> RNG

    TestsInt <--> Private
    TestsUnit <--> Private

    Docs <--> DocsConf
    DocsConf --> API_ds
    DocsConf --> API_initl

    InfraCI --> Private
    InfraCI --> Docs
    Build --> Private

    classDef user fill:#f96,stroke:#333,stroke-width:1px
    classDef library fill:#bbf,stroke:#333,stroke-width:1px
    classDef external fill:#bfb,stroke:#333,stroke-width:1px
    classDef infra fill:#ccc,stroke:#333,stroke-width:1px
    classDef storage fill:#fcf,stroke:#333,stroke-width:1px

    click User "https://github.com/google-deepmind/dm-haiku/tree/main/examples/"
    click Docs "https://github.com/google-deepmind/dm-haiku/tree/main/docs/"
    click API_init "https://github.com/google-deepmind/dm-haiku/blob/main/haiku/__init__.py"
    click API_config "https://github.com/google-deepmind/dm-haiku/blob/main/haiku/config.py"
    click API_ds "https://github.com/google-deepmind/dm-haiku/blob/main/haiku/data_structures.py"
    click API_initl "https://github.com/google-deepmind/dm-haiku/blob/main/haiku/initializers.py"
    click API_mp "https://github.com/google-deepmind/dm-haiku/blob/main/haiku/mixed_precision.py"
    click API_nets "https://github.com/google-deepmind/dm-haiku/blob/main/haiku/nets.py"
    click API_pad "https://github.com/google-deepmind/dm-haiku/blob/main/haiku/pad.py"
    click API_test "https://github.com/google-deepmind/dm-haiku/blob/main/haiku/testing.py"
    click API_typing "https://github.com/google-deepmind/dm-haiku/blob/main/haiku/typing.py"
    click Private "https://github.com/google-deepmind/dm-haiku/tree/main/haiku/_src/"
    click Module "https://github.com/google-deepmind/dm-haiku/blob/main/haiku/_src/module.py"
    click Module "https://github.com/google-deepmind/dm-haiku/blob/main/haiku/_src/base.py"
    click Module "https://github.com/google-deepmind/dm-haiku/blob/main/haiku/_src/data_structures.py"
    click Networks "https://github.com/google-deepmind/dm-haiku/tree/main/haiku/_src/nets/"
    click Transform "https://github.com/google-deepmind/dm-haiku/blob/main/haiku/_src/transform.py"
    click Transform "https://github.com/google-deepmind/dm-haiku/blob/main/haiku/_src/multi_transform.py"
    click State "https://github.com/google-deepmind/dm-haiku/blob/main/haiku/_src/stateful.py"
    click State "https://github.com/google-deepmind/dm-haiku/blob/main/haiku/_src/deferred.py"
    click State "https://github.com/google-deepmind/dm-haiku/blob/main/haiku/_src/config.py"
    click RNG "https://github.com/google-deepmind/dm-haiku/blob/main/haiku/_src/random.py"
    click TestsInt "https://github.com/google-deepmind/dm-haiku/tree/main/haiku/_src/integration/"
    click TestsInt "https://github.com/google-deepmind/dm-haiku/tree/main/haiku/_src/integration/checkpoints/"
    click TestsUnit "https://github.com/google-deepmind/dm-haiku/blob/main/haiku/_src/module_test.py"
    click TestsUnit "https://github.com/google-deepmind/dm-haiku/blob/main/haiku/_src/transform_test.py"
    click TestsUnit "https://github.com/google-deepmind/dm-haiku/blob/main/haiku/_src/random_test.py"
    click InfraCI "https://github.com/google-deepmind/dm-haiku/blob/main/.github/workflows/ci.yml"
    click InfraCI "https://github.com/google-deepmind/dm-haiku/blob/main/.github/workflows/docs.yml"
    click InfraCI "https://github.com/google-deepmind/dm-haiku/blob/main/.github/workflows/integration.yml"
    click InfraCI "https://github.com/google-deepmind/dm-haiku/blob/main/.github/workflows/pypi-publish.yml"
    click DocsConf "https://github.com/google-deepmind/dm-haiku/blob/main/docs/conf.py"
    click DocsConf "https://github.com/google-deepmind/dm-haiku/blob/main/docs/api.rst"
    click DocsConf "https://github.com/google-deepmind/dm-haiku/tree/main/docs/notebooks/"
    click Build "https://github.com/google-deepmind/dm-haiku/blob/main/setup.py"
    click Build "https://github.com/google-deepmind/dm-haiku/blob/main/MANIFEST.in"
    click Build "https://github.com/google-deepmind/dm-haiku/tree/main/WORKSPACE"
    click Build "https://github.com/google-deepmind/dm-haiku/blob/main/test.sh"
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