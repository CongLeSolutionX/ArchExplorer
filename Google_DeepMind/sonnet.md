---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/sonnet
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




# sonnet repo project
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
title: "sonnet repo project"
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
    %% User Layer
    User["User Code (Notebooks & Scripts)"]:::user
    click User "https://github.com/google-deepmind/sonnet/tree/v2/examples/"

    %% Sonnet Library Layer
    subgraph "Sonnet Library" 
    direction TB
        subgraph "Core Library (Blue)" 
        direction TB
            CoreAbst["Core Abstraction<br/>(snt.Module)"]:::core
            click CoreAbst "https://github.com/google-deepmind/sonnet/blob/v2/sonnet/src/base.py"
            OnceUtil["Lazy Initialization Utility<br/>(once decorator)"]:::core
            click OnceUtil "https://github.com/google-deepmind/sonnet/blob/v2/sonnet/src/once.py"
            BuildSys["Parameter Creation & Build System"]:::core
            click BuildSys "https://github.com/google-deepmind/sonnet/blob/v2/sonnet/src/build.py"
        end

        subgraph "Extensions & Plugins (Green)"
        direction TB
            NetsAPI["Predefined Model Architectures<br/>(Public API)"]:::ext
            click NetsAPI "https://github.com/google-deepmind/sonnet/tree/v2/sonnet/nets/"
            NetsSrc["Predefined Model Architectures<br/>(Source & Tests)"]:::ext
            click NetsSrc "https://github.com/google-deepmind/sonnet/tree/v2/sonnet/src/nets/"
            OptAPI["Optimizer Wrappers<br/>(Public API)"]:::ext
            click OptAPI "https://github.com/google-deepmind/sonnet/blob/v2/sonnet/optimizers.py"
            OptSrc["Optimizer Implementations & Tests"]:::ext
            click OptSrc "https://github.com/google-deepmind/sonnet/tree/v2/sonnet/src/optimizers/"
            DistAPI["Distribution Strategy Adapter<br/>(Public API)"]:::ext
            click DistAPI "https://github.com/google-deepmind/sonnet/blob/v2/sonnet/distribute.py"
            DistSrc["Distribution Implementation & Tests"]:::ext
            click DistSrc "https://github.com/google-deepmind/sonnet/tree/v2/sonnet/src/distribute/"
            FuncAPI["Functional Wrappers<br/>(Public API)"]:::ext
            click FuncAPI "https://github.com/google-deepmind/sonnet/blob/v2/sonnet/functional.py"
            FuncSrc["Functional Implementation & Tests"]:::ext
            click FuncSrc "https://github.com/google-deepmind/sonnet/tree/v2/sonnet/src/functional/"
        end

        Conform["Conformance Suite & Golden Checkpoints"]:::test
        click Conform "https://github.com/google-deepmind/sonnet/tree/v2/sonnet/src/conformance/"
    end

    %% TensorFlow Backend
    TF["TensorFlow Backend<br/>(Eager & Graph)"]:::backend

    %% Storage
    Checkpt["Checkpoint Storage"]:::storage
    Saved["SavedModel Storage"]:::storage

    %% External Services
    Docs["Documentation Sources & Sphinx Extensions"]:::docs
    click Docs "https://github.com/google-deepmind/sonnet/tree/v2/docs/"
    CI["CI/CD Pipeline Configuration"]:::ci
    click CI "https://github.com/google-deepmind/sonnet/blob/v2/.github/workflows/ci.yml"
    Packaging["Packaging & Distribution"]:::ci
    click Packaging "https://github.com/google-deepmind/sonnet/blob/v2/setup.py"

    %% Connections
    User -->|"import snt & instantiate Module"| CoreAbst
    CoreAbst -->|"uses once decorator"| OnceUtil
    CoreAbst -->|"builds parameters via"| BuildSys
    CoreAbst -->|"manages submodules"| NetsAPI
    CoreAbst --> NetsSrc
    CoreAbst --> OptAPI
    CoreAbst --> OptSrc
    CoreAbst --> DistAPI
    CoreAbst --> DistSrc
    CoreAbst --> FuncAPI
    CoreAbst --> FuncSrc
    CoreAbst -->|"verified by"| Conform

    CoreAbst -->|"executes TF ops"| TF
    TF -->|"reads/writes tf.Variable"| BuildSys
    TF -->|"checkpoint ops"| Checkpt
    TF -->|"export model"| Saved

    CI -->|"runs tests on"| CoreAbst
    CI -->|"runs conformance suite"| Conform
    CI -->|"packages to"| Packaging
    %% Packaging -->|"publishes to PyPI"| 

    Docs -->|"generate docs from API"| CoreAbst
    Docs --> NetsAPI

    User -->|"consumes docs & examples"| Docs

    %% Styles
    classDef user fill:#f2f2f2,stroke:#333,stroke-width:1px;
    classDef core fill:#bbdefb,stroke:#1e88e5,stroke-width:1px;
    classDef ext fill:#c8e6c9,stroke:#43a047,stroke-width:1px;
    classDef backend fill:#ffe082,stroke:#fdd835,stroke-width:1px;
    classDef storage fill:#ffccbc,stroke:#e64a19,stroke-width:1px;
    classDef docs fill:#e1bee7,stroke:#8e24aa,stroke-width:1px;
    classDef ci fill:#ffecb3,stroke:#f9a825,stroke-width:1px;
    classDef test fill:#eeeeee,stroke:#757575,stroke-width:1px;

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