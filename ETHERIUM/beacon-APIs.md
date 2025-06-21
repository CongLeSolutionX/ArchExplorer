---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/beacon-APIs
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExZDM0MXNyaTMzc2g4dDJ1amhxd3hmM2hwdWFvbG14cnIzcWx5cGl4ayZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/2PL2ikbz6hGtzLIqtE/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# beacon-APIs repo project
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
title: "beacon-APIs repo project"
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
    %% Spec Source
    subgraph "Spec Source" 
        direction TB
        Apis["apis/"]:::code
        Types["types/"]:::code
        Params["params/index.yaml"]:::code
        TopAPI["beacon-node-oapi.yaml"]:::code
    end

    %% Bundler/Linter
    subgraph "Bundler/Linter" 
        direction TB
        RedoclyCLI["Redocly CLI"]:::tool
        RedoclyConfig[".redocly.yml"]:::code
        LocalDevServer["Local HTTP Server"]:::runtime
    end

    %% CI/CD Workflows
    subgraph "CI/CD Workflows" 
        direction TB
        MainWF["main.yml"]:::tool
        SpellcheckWF["spellcheck.yml"]:::tool
        PreReleaseWF["pre-release.yaml"]:::tool
        ReleaseWF["release.yaml"]:::tool
        DeployWF["deploy.yaml"]:::tool
    end

    %% Static Site Output
    subgraph "Static Site Output"
        direction TB
        Dist["dist/"]:::code
        Index["index.html"]:::code
    end

    %% Hosting & Consumption
    subgraph "Hosting & Consumption"
        direction TB
        GitHubPages["GitHub Pages"]:::hosting
        CustomServer["Custom HTTP Server"]:::hosting
        Browser["End-user Browser"]:::consumer
    end

    %% Flows
    Apis -->|"source fragments"| RedoclyCLI
    Types -->|"schemas"| RedoclyCLI
    Params -->|"parameters"| RedoclyCLI
    TopAPI -->|"entrypoint spec"| RedoclyCLI

    RedoclyCLI -->|"bundles spec"| Dist
    RedoclyCLI -->|"uses config"| RedoclyConfig
    LocalDevServer -->|"serves dist/ for dev"| Index

    MainWF -->|"on push/PR"| RedoclyCLI
    SpellcheckWF -->|"spellcheck"| MainWF
    MainWF -->|"runs lint & bundle"| RedoclyCLI
    PreReleaseWF -->|"on tag pre-release"| ReleaseWF
    ReleaseWF -->|"publish artifacts"| DeployWF
    DeployWF -->|"deploy dist/ to"| GitHubPages

    Dist -->|"served by"| GitHubPages
    Dist -->|"served by"| CustomServer
    Index -->|"loaded by"| Browser

    %% Click Events
    click Apis "https://github.com/ethereum/beacon-apis/tree/master/apis/"
    click Types "https://github.com/ethereum/beacon-apis/tree/master/types/"
    click Params "https://github.com/ethereum/beacon-apis/blob/master/params/index.yaml"
    click TopAPI "https://github.com/ethereum/beacon-apis/blob/master/beacon-node-oapi.yaml"
    click RedoclyConfig "https://github.com/ethereum/beacon-apis/blob/master/.redocly.yml"
    click MainWF "https://github.com/ethereum/beacon-apis/blob/master/.github/workflows/main.yml"
    click SpellcheckWF "https://github.com/ethereum/beacon-apis/blob/master/.github/workflows/spellcheck.yml"
    click PreReleaseWF "https://github.com/ethereum/beacon-apis/blob/master/.github/workflows/pre-release.yaml"
    click ReleaseWF "https://github.com/ethereum/beacon-apis/blob/master/.github/workflows/release.yaml"
    click DeployWF "https://github.com/ethereum/beacon-apis/blob/master/.github/workflows/deploy.yaml"
    click Dist "https://github.com/ethereum/beacon-apis/tree/master/dist/"
    click Index "https://github.com/ethereum/beacon-apis/blob/master/index.html"

    %% Styles
    classDef code fill:#D0E8FF,stroke:#1C7ED6,color:#1C7ED6
    classDef tool fill:#E6F4EA,stroke:#2F9E44,color:#2F9E44
    classDef hosting fill:#FFF4DB,stroke:#F08C00,color:#F08C00
    classDef runtime fill:#F0EBFF,stroke:#7048E8,color:#7048E8
    classDef consumer fill:#F8F9FA,stroke:#495057,color:#495057

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
