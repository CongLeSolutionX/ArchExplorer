---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/consensus-specs
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExdDVubDV2MTI4cDlyNmo1ZDZ3NnpicWR3djB2dWc3ajBkNXgyY2tiYyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/U7srgXY5l8ftJsX5Rb/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----

# consensus-specs repo project
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
title: "consensus-specs repo project"
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
    Developer["Developer"]:::actor
    ExternalServices["Discord / External Spec Repos"]:::external

    subgraph "GitHub Repo"
    %% :::repo
        direction TB
        DocsWF(("Docs Pipeline")):::ci
        GenVecWF(("Vector Pipeline")):::ci
        RunTestsWF(("Run Tests Pipeline")):::ci
        NightTestsWF(("Nightly Tests Pipeline")):::ci

        SpecLib["Spec-Building Python Library"]:::code
        SpecBuilders["Spec Builders"]:::code

        Presets[(YAML Presets)]:::data
        Configs[(YAML Configs)]:::data

        Specs[(Markdown Specs)]:::docs
        SSZ[(SSZ Documentation)]:::docs

        MkDocsConfig["mkdocs.yml"]:::code
        DocsDir["docs/"]:::docs

        StaticSite["Static Site Generator"]:::code
        PublishedSite[/Published Site/]:::output

        TestGen["Test-Vector Generators"]:::code
        JSONVec[(JSON Test Vectors)]:::data

        PySpec["Reference PySpec Tests"]:::code
        Solidity["Solidity Deposit Contract"]:::code
    end

    Developer -->|commits changes| DocsWF
    Developer -->|commits changes| GenVecWF
    Developer -->|commits changes| RunTestsWF
    Developer -->|commits changes| NightTestsWF

    DocsWF -->|runs| SpecLib
    DocsWF -->|runs| MkDocsConfig
    SpecLib -->|reads| Presets
    SpecLib -->|reads| Configs
    SpecLib -->|emits| Specs
    DocsWF -->|runs| StaticSite

    MkDocsConfig -->|configures| StaticSite
    DocsDir -->|inputs| StaticSite
    Specs -->|inputs| StaticSite
    SSZ -->|inputs| StaticSite
    StaticSite -->|publishes| PublishedSite

    GenVecWF -->|runs| TestGen
    TestGen -->|reads| SpecLib
    TestGen -->|emits| JSONVec

    RunTestsWF -->|runs| PySpec
    RunTestsWF -->|runs| Solidity
    NightTestsWF -->|runs| PySpec
    NightTestsWF -->|runs| Solidity

    Developer -->|views| PublishedSite
    Developer -->|interacts| ExternalServices

    classDef actor fill:#FFD580,stroke:#E69500
    classDef repo fill:#E0E0E0,stroke:#A0A0A0
    classDef ci fill:#FFCCCC,stroke:#CC0000,stroke-width:2px
    classDef code fill:#CCCCFF,stroke:#0000CC
    classDef data fill:#CCFFCC,stroke:#009900,stroke-width:2px
    classDef docs fill:#FFFFCC,stroke:#999900
    classDef output fill:#D9D9D9,stroke:#666666
    classDef external fill:#CCFFFF,stroke:#009999

    click DocsWF "https://github.com/ethereum/consensus-specs/blob/dev/.github/workflows/docs.yml"
    click GenVecWF "https://github.com/ethereum/consensus-specs/blob/dev/.github/workflows/generate_vectors.yml"
    click RunTestsWF "https://github.com/ethereum/consensus-specs/blob/dev/.github/workflows/run-tests.yml"
    click NightTestsWF "https://github.com/ethereum/consensus-specs/blob/dev/.github/workflows/nightly-tests.yml"
    click SpecLib "https://github.com/ethereum/consensus-specs/tree/dev/pysetup/"
    click SpecBuilders "https://github.com/ethereum/consensus-specs/tree/dev/pysetup/spec_builders/"
    click Presets "https://github.com/ethereum/consensus-specs/tree/dev/presets/"
    click Configs "https://github.com/ethereum/consensus-specs/tree/dev/configs/"
    click Specs "https://github.com/ethereum/consensus-specs/tree/dev/specs/"
    click SSZ "https://github.com/ethereum/consensus-specs/tree/dev/ssz/"
    click MkDocsConfig "https://github.com/ethereum/consensus-specs/blob/dev/mkdocs.yml"
    click DocsDir "https://github.com/ethereum/consensus-specs/tree/dev/docs/"
    click TestGen "https://github.com/ethereum/consensus-specs/tree/dev/tests/generators/"
    click JSONVec "https://github.com/ethereum/consensus-specs/tree/dev/tests/formats/"
    click PySpec "https://github.com/ethereum/consensus-specs/tree/dev/tests/core/pyspec/eth2spec/"
    click Solidity "https://github.com/ethereum/consensus-specs/tree/dev/solidity_deposit_contract/"

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
