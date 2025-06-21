---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/solc-bin
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExMWkyNnR3dGd0NzJ6bmtqNXd0bXl2M3cxbXE0YjFkem5xcmNnNTV5dSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/10ppffwhOftLy0/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# solc-bin repo project
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
title: "solc-bin repo project"
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
    %% Source Repository
    subgraph "GitHub Repo" 
        direction TB
        Gitignore[".gitignore"]:::source
        License["LICENSE"]:::source
        Readme["README.md"]:::source
        JekyllConfig["_config.yml"]:::source
        SoljsonJs["soljson.js"]:::source
        PackageJson["package.json"]:::source
    end

    %% CI Engines
    subgraph "CI Pipelines"
        direction TB
        CircleCI["CircleCI"]:::ci
        GHActions["GitHub Actions"]:::ci
    end

    %% CI Configuration Files
    subgraph "CI Config Files"
        direction TB
        CIConfig[".circleci/config.yml"]:::source
        NightlyYaml[".github/workflows/nightly-emscripten.yml"]:::source
        RandomMacYaml[".github/workflows/random-macosx-build.yml"]:::source
        S3MirrorYaml[".github/workflows/s3-mirror.yml"]:::source
        TBytecodeYaml[".github/workflows/t-bytecode-compare.yml"]:::source
    end

    %% Scripts for Indexing & Sync
    subgraph "Scripts" 
        direction TB
        UpdateMjs["update.mjs"]:::scripts
        SyncS3["sync-s3.sh"]:::scripts
        AddNightly["add-nightly-and-push.sh"]:::scripts
    end

    %% Bin Directory
    subgraph "bin/" 
        direction TB
        BinListJs["list.js"]:::source
        BinListJson["list.json"]:::source
        BinListTxt["list.txt"]:::source
        LatestJs["soljson-latest.js"]:::source
        NightlyJs["soljson-nightly.js"]:::source
        VersionedJs["soljson-v*.js"]:::source
    end

    %% Platform Directories
    subgraph "Platform Directories"
        direction TB
        ASMjs["emscripten-asmjs/"]:::source
        Wasm32["emscripten-wasm32/"]:::source
        PureWasm["wasm/"]:::source
        Linux["linux-amd64/"]:::source
        Macos["macosx-amd64/"]:::source
        Windows["windows-amd64/"]:::source
    end

    %% Static Hosting
    subgraph "Static Hosting"
        direction TB
        GHPages["GitHub Pages"]:::hosting
        S3Bucket["AWS S3 + CloudFront"]:::hosting
    end

    %% Client
    Client["Client (npm-solc, Truffle, Hardhat)"]:::client

    %% Relationships
    Gitignore -->|source| CircleCI
    License -->|source| GHActions
    Readme -->|docs| GHPages

    CircleCI -->|uses config| CIConfig
    GHActions -->|uses configs| NightlyYaml & RandomMacYaml & S3MirrorYaml & TBytecodeYaml

    CircleCI -->|runs| UpdateMjs
    CircleCI -->|runs| SyncS3
    CircleCI -->|runs| AddNightly
    GHActions -->|runs| UpdateMjs
    GHActions -->|runs| SyncS3
    GHActions -->|runs| AddNightly

    UpdateMjs -->|updates indexes| BinListJs & BinListJson & BinListTxt & ASMjs & Wasm32 & PureWasm & Linux & Macos & Windows
    AddNightly -->|adds builds| LatestJs & NightlyJs & VersionedJs
    SyncS3 -->|sync to| S3Bucket

    %% Publishing
    Gitignore -->|commit binaries| ASMjs & Wasm32 & PureWasm & Linux & Macos & Windows & LatestJs & NightlyJs & VersionedJs
    Gitignore -.->|serves| GHPages

    %% Distribution to Client
    Client -->|fetches from| GHPages
    Client -->|fetches from| S3Bucket

    %% Click Events
    click Gitignore "https://github.com/ethereum/solc-bin/blob/gh-pages/.gitignore"
    click License "https://github.com/ethereum/solc-bin/tree/gh-pages/LICENSE"
    click Readme "https://github.com/ethereum/solc-bin/blob/gh-pages/README.md"
    click JekyllConfig "https://github.com/ethereum/solc-bin/blob/gh-pages/_config.yml"
    click SoljsonJs "https://github.com/ethereum/solc-bin/blob/gh-pages/soljson.js"
    click PackageJson "https://github.com/ethereum/solc-bin/blob/gh-pages/package.json"
    click CIConfig "https://github.com/ethereum/solc-bin/blob/gh-pages/.circleci/config.yml"
    click NightlyYaml "https://github.com/ethereum/solc-bin/blob/gh-pages/.github/workflows/nightly-emscripten.yml"
    click RandomMacYaml "https://github.com/ethereum/solc-bin/blob/gh-pages/.github/workflows/random-macosx-build.yml"
    click S3MirrorYaml "https://github.com/ethereum/solc-bin/blob/gh-pages/.github/workflows/s3-mirror.yml"
    click TBytecodeYaml "https://github.com/ethereum/solc-bin/blob/gh-pages/.github/workflows/t-bytecode-compare.yml"
    click UpdateMjs "https://github.com/ethereum/solc-bin/blob/gh-pages/update.mjs"
    click SyncS3 "https://github.com/ethereum/solc-bin/blob/gh-pages/sync-s3.sh"
    click AddNightly "https://github.com/ethereum/solc-bin/blob/gh-pages/add-nightly-and-push.sh"
    click BinListJs "https://github.com/ethereum/solc-bin/blob/gh-pages/bin/list.js"
    click BinListJson "https://github.com/ethereum/solc-bin/blob/gh-pages/bin/list.json"
    click BinListTxt "https://github.com/ethereum/solc-bin/blob/gh-pages/bin/list.txt"
    click LatestJs "https://github.com/ethereum/solc-bin/blob/gh-pages/bin/soljson-latest.js"
    click NightlyJs "https://github.com/ethereum/solc-bin/blob/gh-pages/bin/soljson-nightly.js"
    click VersionedJs "https://github.com/ethereum/solc-bin/blob/gh-pages/bin/soljson-v*.js"
    click ASMjs "https://github.com/ethereum/solc-bin/tree/gh-pages/emscripten-asmjs/"
    click Wasm32 "https://github.com/ethereum/solc-bin/tree/gh-pages/emscripten-wasm32/"
    click PureWasm "https://github.com/ethereum/solc-bin/tree/gh-pages/wasm/"
    click Linux "https://github.com/ethereum/solc-bin/tree/gh-pages/linux-amd64/"
    click Macos "https://github.com/ethereum/solc-bin/tree/gh-pages/macosx-amd64/"
    click Windows "https://github.com/ethereum/solc-bin/tree/gh-pages/windows-amd64/"

    %% Styles
    classDef source fill:#d0e7ff,stroke:#004b8d,color:#004b8d
    classDef ci fill:#d0ffd6,stroke:#0b6623,color:#0b6623
    classDef scripts fill:#e0e0ff,stroke:#4b0082,color:#4b0082
    classDef hosting fill:#ffe5b4,stroke:#cc8400,color:#cc8400
    classDef client fill:#f3d6ff,stroke:#800080,color:#800080
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
