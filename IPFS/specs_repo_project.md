---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ipfs/specs
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExd3VwcHgzZWxnbTc3eWUwd2NpdnEwem9wdWVxemZ1eDE1aHpmZmlhdSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/N35rW3vRNeaDC/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# specs repo project
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
title: "specs repo project"
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
    'flowchart': { 'htmlLabels': true, 'curve': 'linear' },
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#222B2B',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#2221',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '20px'
    }
  }
}%%
flowchart TD
    subgraph "Content Layer"
        RootSpecs["Root Markdown Specs"]:::content
        IPIP["IPIP Proposals"]:::content
        HTTPG["HTTP Gateways Specs"]:::content
        IPNSs["IPNS Specs"]:::content
        RoutingSpecs["Routing Specs"]:::content
        Assets["Assets (img/ & src/img/)"]:::content
    end

    subgraph "Static Site Generator"
        Eleventy["Eleventy (Node.js)"]:::processing
        Templates["Templates:\ntemplate.html, template.md, src/_includes"]:::processing
        CSS["CSS:\nsrc/css/index.css, src/css/specs.css"]:::processing
        Config["Config:\npackage.json, Makefile"]:::processing
    end

    subgraph "Built Site"
        Site["Built Site\n(HTML, CSS, Assets)"]:::processing
    end

    subgraph "Build & Validation"
        Linter["Linter\n(.markdownlint.json)"]:::processing
        CI["CI Workflows"]:::infra
    end

    subgraph "Deployment"
        Deploy["GitHub Pages / CDN"]:::infra
    end

    subgraph "External Integrations"
        IPLD["IPLD.io, Multiformats, libp2p"]:::external
        Community["Community\n(Issues & PRs)"]:::external
    end

    %% Data Flows
    RootSpecs --> Eleventy
    IPIP --> Eleventy
    HTTPG --> Eleventy
    IPNSs --> Eleventy
    RoutingSpecs --> Eleventy
    Assets --> Eleventy

    Eleventy --> Site
    Templates --> Site
    CSS --> Site
    Config --> Eleventy

    Site --> Linter
    Linter --> CI
    CI --> Deploy

    CI <--> Community
    Community --> RootSpecs

    IPLD -.-> RootSpecs
    IPLD -.-> Eleventy

    %% Click Events
    click IPIP "https://github.com/ipfs/specs/blob/main/IPIP/*.md"
    click HTTPG "https://github.com/ipfs/specs/blob/main/http-gateways/*.md"
    click IPNSs "https://github.com/ipfs/specs/blob/main/ipns/*.md"
    click RoutingSpecs "https://github.com/ipfs/specs/blob/main/routing/*.md"
    click Assets "https://github.com/ipfs/specs/tree/main/img/"
    click Assets "https://github.com/ipfs/specs/tree/main/src/img/"
    click Templates "https://github.com/ipfs/specs/tree/main/src/_includes/"
    click Eleventy "https://github.com/ipfs/specs/blob/main/package.json"
    click Config "https://github.com/ipfs/specs/tree/main/Makefile"
    click CSS "https://github.com/ipfs/specs/blob/main/src/css/index.css"
    click CSS "https://github.com/ipfs/specs/blob/main/src/css/specs.css"
    click Linter "https://github.com/ipfs/specs/blob/main/.markdownlint.json"
    click CI "https://github.com/ipfs/specs/blob/main/.github/workflows/build.yml"
    click CI "https://github.com/ipfs/specs/blob/main/.github/workflows/linter.yml"
    click CI "https://github.com/ipfs/specs/blob/main/.github/workflows/stale.yml"
    click CI "https://github.com/ipfs/specs/blob/main/.github/workflows/generated-pr.yml"
    click Deploy "https://github.com/ipfs/specs/blob/main/.github/workflows/build.yml"
    click Community "https://github.com/ipfs/specs/tree/main/.github/CODEOWNERS"
    click Community "https://github.com/ipfs/specs/blob/main/.github/ISSUE_TEMPLATE/config.yml"
    click Community "https://github.com/ipfs/specs/blob/main/.github/ISSUE_TEMPLATE/open_an_issue.md"

    %% Styles
    classDef content fill:#cfe2f3,stroke:#0366d6,stroke-width:1px
    classDef processing fill:#d9ead3,stroke:#38761d,stroke-width:1px
    classDef infra fill:#f9cb9c,stroke:#b45f06,stroke-width:1px
    classDef external fill:#d9d2e9,stroke:#674ea7,stroke-width:1px
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
    
  My_Meme ~~~ Closing_quote
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

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