---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/eip-review-bot
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHp4MzVpN2dxb20ycWN4YWZ0cTJsaG94cDdwZmhqa3J5M2JncjBoZyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/p7k2JyaoiDtODAWseQ/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# eip-review-bot repo project
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
title: "eip-review-bot repo project"
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
    %% External Event Source
    GH["GitHub (pull_request event)"]:::external
    %% Runner Environment
    Runner["GitHub Actions Runner"]:::runner

    %% Action Code Subgraph
    subgraph "eip-review-bot Action Code"
        direction TB
        AY["action.yml"]:::internalModule
        Entry["action.ts"]:::internalModule
        Config["localConfig.ts"]:::internalModule
        Proc["process.ts"]:::internalModule
        Types["types.ts"]:::internalModule
        NamePR["namePr.ts"]:::internalModule
        Merge["merge.ts"]:::internalModule
        subgraph "Rules"
            direction TB
            RMDir["src/rules/"]:::internalModule
            Auth["authors.ts"]:::internalModule
            Editor["editorFile.ts"]:::internalModule
            NewRule["new.ts"]:::internalModule
            Stagnant["stagnant.ts"]:::internalModule
            StatusChange["statuschange.ts"]:::internalModule
            Terminal["terminal.ts"]:::internalModule
            Unknown["unknown.ts"]:::internalModule
        end
    end

    %% Octokit and API
    Octo["Octokit Client"]:::internalModule
    API["GitHub REST API"]:::externalService

    %% CI & Tests Side Panel
    subgraph "CI & Testing"
        direction TB
        BuildWF[".github/workflows/build.yml"]:::ci
        CIWF[".github/workflows/ci.yml"]:::ci
        CodeQL[".github/workflows/codeql-analysis.yml"]:::ci
        TestsCore["src/__tests__/"]:::ci
        TestsRules["src/rules/__tests__/"]:::ci
        MockOcto["generateMockOctokit.ts"]:::ci
        Docs["docs/exitcodes.md"]:::ci
        ConfigFiles["package.json, tsconfig.json"]:::ci
    end

    %% Main Flow
    GH -->|"JSON payload"| Runner
    Runner -->|"executes"| Entry
    Entry -->|"reads inputs"| Config
    Entry -->|"invokes"| Proc
    Proc -->|"uses types"| Types
    Proc -->|"calls"| NamePR
    Proc -->|"calls"| Merge
    Proc -->|"iterates rules"| Auth
    Proc --> Auth -->|"decision"| Octo
    Proc --> Editor -->|"decision"| Octo
    Proc --> NewRule -->|"decision"| Octo
    Proc --> Stagnant -->|"decision"| Octo
    Proc --> StatusChange -->|"decision"| Octo
    Proc --> Terminal -->|"decision"| Octo
    Proc --> Unknown -->|"decision"| Octo
    Octo -->|"POST reviewers"| API

    %% CI Flow (triggered on push/PR)
    GH -.->|"push/PR"| BuildWF
    BuildWF --> CIWF
    BuildWF --> CodeQL
    BuildWF --> TestsCore
    BuildWF --> TestsRules
    TestsCore --> MockOcto
    ConfigFiles --> BuildWF
    Docs --> BuildWF

    %% Click Events
    click AY "https://github.com/ethereum/eip-review-bot/blob/main/action.yml"
    click Entry "https://github.com/ethereum/eip-review-bot/blob/main/src/action.ts"
    click Config "https://github.com/ethereum/eip-review-bot/blob/main/src/localConfig.ts"
    click Proc "https://github.com/ethereum/eip-review-bot/blob/main/src/process.ts"
    click NamePR "https://github.com/ethereum/eip-review-bot/blob/main/src/namePr.ts"
    click Merge "https://github.com/ethereum/eip-review-bot/blob/main/src/merge.ts"
    click RMDir "https://github.com/ethereum/eip-review-bot/tree/main/src/rules/"
    click Auth "https://github.com/ethereum/eip-review-bot/blob/main/src/rules/authors.ts"
    click Editor "https://github.com/ethereum/eip-review-bot/blob/main/src/rules/editorFile.ts"
    click NewRule "https://github.com/ethereum/eip-review-bot/blob/main/src/rules/new.ts"
    click Stagnant "https://github.com/ethereum/eip-review-bot/blob/main/src/rules/stagnant.ts"
    click StatusChange "https://github.com/ethereum/eip-review-bot/blob/main/src/rules/statuschange.ts"
    click Terminal "https://github.com/ethereum/eip-review-bot/blob/main/src/rules/terminal.ts"
    click Unknown "https://github.com/ethereum/eip-review-bot/blob/main/src/rules/unknown.ts"
    click Types "https://github.com/ethereum/eip-review-bot/blob/main/src/types.ts"
    click TestsCore "https://github.com/ethereum/eip-review-bot/tree/main/src/__tests__/"
    click TestsRules "https://github.com/ethereum/eip-review-bot/tree/main/src/rules/__tests__/"
    click MockOcto "https://github.com/ethereum/eip-review-bot/blob/main/src/__tests__/generateMockOctokit.ts"
    click BuildWF "https://github.com/ethereum/eip-review-bot/blob/main/.github/workflows/build.yml"
    click CIWF "https://github.com/ethereum/eip-review-bot/blob/main/.github/workflows/ci.yml"
    click CodeQL "https://github.com/ethereum/eip-review-bot/blob/main/.github/workflows/codeql-analysis.yml"
    click Docs "https://github.com/ethereum/eip-review-bot/blob/main/docs/exitcodes.md"
    click ConfigFiles "https://github.com/ethereum/eip-review-bot/blob/main/package.json"
    click ConfigFiles "https://github.com/ethereum/eip-review-bot/blob/main/tsconfig.json"

    %% Styles
    classDef internalModule fill:#BBDEFB,stroke:#1976D2,stroke-width:1px
    classDef externalService fill:#C8E6C9,stroke:#388E3C,stroke-width:1px,shape:cylinder
    classDef runner fill:#FFE0B2,stroke:#F57C00,stroke-width:1px,shape:hexagon
    classDef ci fill:#E0E0E0,stroke:#757575,stroke-width:1px,shape:parallelogram
    classDef external fill:#E1BEE7,stroke:#8E24AA,stroke-width:1px

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
