---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/remix-live-alpha
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExa3Z6cjBrbXI5dHplNXpyYWM5bmgwZXpkMDc4NnQ3dmN2MXQweGh2NyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/i4jKn7itdV2Tvjzj6Y/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# remix-live-alpha repo project
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
title: "remix-live-alpha repo project"
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
    %% Browser
    Browser["Browser"]:::external
    Browser --> Index

    subgraph "Core Shell"
        Index["index.html"]:::core
        Runtime["runtime.0.66.0-dev.1749882005979.js"]:::core
        Polyfills["polyfills.0.66.0-dev.1749882005979.js"]:::core
        Common["common.0.66.0-dev.1749882005979.js"]:::core
        Main["main.0.66.0-dev.1749882005979.js"]:::core
        Loader["Plugin Manager & Registry (loader.js)"]:::core
    end

    Browser --> Runtime
    Browser --> Polyfills
    Runtime --> Common
    Runtime --> Main
    Main --> Loader

    subgraph "Monaco Editor & Workers"
        Monaco["Monaco Editor"]:::monaco
        WorkerEditor["Editor Worker"]:::monaco
        WorkerLang["Language Worker"]:::monaco
    end

    Loader --> Monaco
    Monaco --> WorkerEditor
    Monaco --> WorkerLang

    subgraph "Parser & Language Service"
        ANTLR["antlr.js"]:::parser
        Tokens["Solidity-EZVQ6AE4.tokens"]:::parser
    end

    Loader --> ANTLR
    ANTLR --> Tokens
    WorkerLang --> ANTLR

    subgraph "Solidity Compiler Engine"
        SolJSON["soljson.js + versioned"]:::wasm
    end

    Loader --> SolJSON

    subgraph "Shared Services"
        FS["File System"]:::service
        WS["Virtual Workspace"]:::service
        NP["Network Provider"]:::service
    end

    Loader --> FS
    Loader --> WS
    Loader --> NP

    subgraph "Plugin Containers"
        subgraph "Circuit Compiler Plugin" 
            CC_HTML["index.html"]:::plugin
            CC_WASM["*.module.wasm"]:::wasm
        end
        subgraph "Contract Verification Plugin"
            CV_HTML["index.html"]:::plugin
        end
        subgraph "Doc-Gen Plugin"
            DG_HTML["index.html"]:::plugin
        end
        subgraph "LearnEth Plugin"
            LE_HTML["index.html"]:::plugin
        end
        subgraph "Noir Compiler Plugin"
            NC_HTML["index.html"]:::plugin
        end
        subgraph "Quick-DApp Plugin"
            QD_HTML["index.html"]:::plugin
        end
        subgraph "Remix-DApp Plugin"
            RD_HTML["index.html"]:::plugin
        end
        subgraph "Solhint Plugin"
            SH_HTML["index.html"]:::plugin
        end
        subgraph "Vyper Plugin"
            VY_HTML["index.html"]:::plugin
        end
    end

    Loader --> CC_HTML
    Loader --> CV_HTML
    Loader --> DG_HTML
    Loader --> LE_HTML
    Loader --> NC_HTML
    Loader --> QD_HTML
    Loader --> RD_HTML
    Loader --> SH_HTML
    Loader --> VY_HTML

    CC_HTML --> CC_WASM
    CV_HTML --> SolJSON
    NC_HTML --> SolJSON
    SH_HTML --> SolJSON
    VY_HTML --> SolJSON

    CC_HTML -->|"RPC/Etherscan"| External["External Ethereum Network/Etherscan"]:::external

    subgraph "Static Assets"
        Themes["CSS Themes"]:::assets
        Fonts["Fonts & FontAwesome"]:::assets
        Images["Images"]:::assets
        Audio["Audio"]:::assets
        Config["list.json & version.json"]:::assets
    end

    Index --> Themes
    Index --> Fonts
    Index --> Images
    Index --> Audio
    Index --> Config

    subgraph "CI/CD Pipeline"
        GH["GitHub Actions Workflow"]:::ci
        Build["Auto Build & Deploy"]:::ci
    end

    GH --> Build
    Build --> Production["Production ZIP"]:::external

    %% Click events
    click Index "https://github.com/ethereum/remix-live-alpha/blob/gh-pages/index.html"
    click Runtime "https://github.com/ethereum/remix-live-alpha/blob/gh-pages/runtime.0.66.0-dev.1749882005979.js"
    click Polyfills "https://github.com/ethereum/remix-live-alpha/blob/gh-pages/polyfills.0.66.0-dev.1749882005979.js"
    click Common "https://github.com/ethereum/remix-live-alpha/blob/gh-pages/common.0.66.0-dev.1749882005979.js"
    click Main "https://github.com/ethereum/remix-live-alpha/blob/gh-pages/main.0.66.0-dev.1749882005979.js"
    click Loader "https://github.com/ethereum/remix-live-alpha/blob/gh-pages/assets/js/loader.js"
    click CC_HTML "https://github.com/ethereum/remix-live-alpha/blob/gh-pages/plugins/circuit-compiler/index.html"
    click CC_WASM "https://github.com/ethereum/remix-live-alpha/tree/gh-pages/plugins/circuit-compiler/"
    click CV_HTML "https://github.com/ethereum/remix-live-alpha/blob/gh-pages/plugins/contract-verification/index.html"
    click DG_HTML "https://github.com/ethereum/remix-live-alpha/blob/gh-pages/plugins/doc-gen/index.html"
    click LE_HTML "https://github.com/ethereum/remix-live-alpha/blob/gh-pages/plugins/learneth/index.html"
    click NC_HTML "https://github.com/ethereum/remix-live-alpha/blob/gh-pages/plugins/noir-compiler/index.html"
    click QD_HTML "https://github.com/ethereum/remix-live-alpha/blob/gh-pages/plugins/quick-dapp/index.html"
    click RD_HTML "https://github.com/ethereum/remix-live-alpha/blob/gh-pages/plugins/remix-dapp/index.html"
    click SH_HTML "https://github.com/ethereum/remix-live-alpha/blob/gh-pages/plugins/solhint/index.html"
    click VY_HTML "https://github.com/ethereum/remix-live-alpha/blob/gh-pages/plugins/vyper/index.html"
    click GH "https://github.com/ethereum/remix-live-alpha/blob/gh-pages/.github/workflows/gh-actions-deploy.yml"

    %% Styles
    classDef core fill:#cce5ff,stroke:#004085,color:#004085
    classDef plugin fill:#d4edda,stroke:#155724,color:#155724
    classDef wasm fill:#ffe5b4,stroke:#cc8400,color:#cc8400
    classDef external fill:#e2e3e5,stroke:#6c757d,color:#6c757d
    classDef service fill:#f2f2f2,stroke:#888,color:#555
    classDef monaco fill:#fff3cd,stroke:#856404,color:#856404
    classDef parser fill:#f8d7da,stroke:#721c24,color:#721c24
    classDef assets fill:#d1ecf1,stroke:#0c5460,color:#0c5460
    classDef ci fill:#f5c6cb,stroke:#a71d2a,color:#a71d2a

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
