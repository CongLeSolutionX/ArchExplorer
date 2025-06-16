---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/L2-interop
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExanZydm52NDcyNWIwMWtneG9uOWk4aGpseXQ1bHR4b3c1N2x3MnB6bSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/m3XqQ8QhuIUuQau7n5/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# L2-interop repo project
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
title: "L2-interop repo project"
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
    subgraph "Foundational"
        Properties["Core Properties Module"]:::foundation
    end

    subgraph "Documentation Layer"
        DocsOverview["Overview"]:::docs
        DocsAddr["Addresses"]:::docs
        DocsAssets["Assets"]:::docs
        DocsIntents["Intents"]:::docs
        DocsMsg["Message-Passing"]:::docs
        DocsBridges["Shared Bridges"]:::docs
    end

    subgraph "Specification Layer"
        SpecsOverview(("Overview")):::specs
        SpecsAddr(("Addresses Specs")):::specs
        SpecsAssets(("Assets Specs")):::specs
        SpecsIntents(("Intents Specs")):::specs
        SpecsMsg(("Message-Passing Specs")):::specs
        SpecsBridges(("Shared Bridges Specs")):::specs
    end

    subgraph "Community Collaboration"
        Issues["Issue Templates"]:::community
        Guidelines["Contribution Guidelines"]:::community
        Nomenclature["Nomenclature"]:::community
    end

    Standards["Standards Bodies (EIP/ERC/etc)"]:::standards
    Impl["Implementations & Prototypes"]:::implement

    Properties -->|drives| DocsOverview
    Properties -->|drives| SpecsOverview

    DocsOverview -->|includes| DocsAddr
    DocsOverview -->|includes| DocsAssets
    DocsOverview -->|includes| DocsIntents
    DocsOverview -->|includes| DocsMsg
    DocsOverview -->|includes| DocsBridges

    SpecsOverview -->|comprises| SpecsAddr
    SpecsOverview -->|comprises| SpecsAssets
    SpecsOverview -->|comprises| SpecsIntents
    SpecsOverview -->|comprises| SpecsMsg
    SpecsOverview -->|comprises| SpecsBridges

    DocsOverview -->|onboarding guide| Issues
    DocsOverview -->|onboarding guide| Guidelines

    SpecsOverview -->|feeds formal proposals| Standards
    SpecsOverview -->|feeds prototypes| Impl

    Issues -->|feedback| DocsOverview
    Issues -->|feedback| SpecsOverview
    Guidelines -->|feedback| DocsOverview
    Guidelines -->|feedback| SpecsOverview
    Nomenclature -->|ensures consistency| DocsOverview
    Nomenclature -->|ensures consistency| SpecsOverview

    click Properties "https://github.com/ethereum/l2-interop/blob/main/PROPERTIES.md"
    click DocsOverview "https://github.com/ethereum/l2-interop/blob/main/docs/README.md"
    click DocsAddr "https://github.com/ethereum/l2-interop/tree/main/docs/addresses/"
    click DocsAssets "https://github.com/ethereum/l2-interop/tree/main/docs/assets/"
    click DocsIntents "https://github.com/ethereum/l2-interop/tree/main/docs/intents/"
    click DocsMsg "https://github.com/ethereum/l2-interop/tree/main/docs/message-passing/"
    click DocsBridges "https://github.com/ethereum/l2-interop/blob/main/docs/shared-bridges.md"
    click SpecsOverview "https://github.com/ethereum/l2-interop/blob/main/specs/README.md"
    click SpecsAddr "https://github.com/ethereum/l2-interop/tree/main/specs/addresses/"
    click Issues "https://github.com/ethereum/l2-interop/blob/main/.github/ISSUE_TEMPLATE/project-task.md"
    click Guidelines "https://github.com/ethereum/l2-interop/blob/main/CONTRIBUTING.md"
    click Nomenclature "https://github.com/ethereum/l2-interop/blob/main/NOMENCLATURE.md"

    classDef foundation fill:#cce5ff,stroke:#004085,color:#004085
    classDef docs fill:#d4edda,stroke:#155724,color:#155724
    classDef specs fill:#fff3cd,stroke:#856404,color:#856404
    classDef community fill:#e2e3e5,stroke:#6c757d,color:#6c757d
    classDef standards fill:#f5c6cb,stroke:#721c24,color:#721c24
    classDef implement fill:#d1ecf1,stroke:#0c5460,color:#0c5460

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