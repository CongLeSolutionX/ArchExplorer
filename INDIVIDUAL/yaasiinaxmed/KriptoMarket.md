---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/yaasiinaxmed/KriptoMarket
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExNHJtY2dxbmRxNGVpM2VmMjJiYWJjc3h5dnFxazZqNnVtZ3JwNjdtNyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/8dDrjuofiDKqJqHTpF/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# KriptoMarket repo project
> <ins>📢 **Disclaimer** 🚨</ins>
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
title: "KriptoMarket repo project"
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
    %% Layers
    Browser["Browser/Client"]:::userFacing
    CDN["Static Hosting<br/>(Vercel/CDN)"]:::build
    subgraph React_SPA["React SPA"]
    direction TB
        subgraph "Application Bootstrap"
            direction TB
            Main["main.jsx"]:::userFacing
            App["App.jsx"]:::userFacing
        end
        subgraph Routing_Pages_Layer["Routing /<br/> Pages Layer"]
        direction TB
            IndexPg["Index.jsx"]:::userFacing
            AssetDetailPg["AssetDetail.jsx"]:::userFacing
            DEXPg["DEXScreener.jsx"]:::userFacing
        end
        Nav["nav-items.jsx"]:::userFacing
        subgraph Domain_Components["Domain Components"]
        direction TB
            AssetDesc["AssetDescription.jsx"]:::userFacing
            AssetInfo["AssetInfo.jsx"]:::userFacing
            AssetLinks["AssetLinks.jsx"]:::userFacing
            CategoryFilter["CategoryFilter.jsx"]:::userFacing
            CoinListItem["CoinListItem.jsx"]:::userFacing
            ContractAddr["ContractAddress.jsx"]:::userFacing
            LangSwitch["LanguageSwitcher.jsx"]:::userFacing
            PriceChart["PriceChart.jsx"]:::userFacing
        end
        UIPrims["UI Primitives<br/>(accordion, dialog, button, etc.)"]:::internal
        subgraph Utilities["Utilities"]
        direction TB
            FetchUtil["utils.js"]:::internal
            Translate["translate.js"]:::internal
        end
        subgraph Styling_Entry["Styling Entry"]
            IndexCSS["index.css"]:::internal
        end
        subgraph Build_and_Tooling_Configs["Build & Tooling Configs"]
        direction TB
            Pkg["package.json"]:::build
            ViteCfg["vite.config.js"]:::build
            TailwindCfg["tailwind.config.js"]:::build
            PostcssCfg["postcss.config.js"]:::build
            BunLock["bun.lockb"]:::build
        end
    end
    ExternalAPI["External Crypto API"]:::external

    %% Connections
    Browser -->|"Request index.html"| CDN
    CDN -->|"Serve static assets"| Browser
    Browser -->|"Load SPA bundle"| Main
    Main -->|"Render App"| App
    App -->|"Route change"| IndexPg
    App -->|"Route change"| AssetDetailPg
    App -->|"Route change"| DEXPg
    App -->|"Load nav config"| Nav
    IndexPg -->|"Use domain comps"| AssetDesc
    AssetDetailPg -->|"Use domain comps"| AssetInfo
    DEXPg -->|"Use domain comps"| CoinListItem
    CategoryFilter -->|"Filter events"| AssetListItem[(CoinListItem)]
    AssetDetailPg -->|"Use PriceChart"| PriceChart
    LangSwitch -->|"locale switch"| Translate
    FetchUtil -->|"GET /cryptodata"| ExternalAPI
    IndexPg -->|"Fetch data"| FetchUtil
    AssetDetailPg -->|"Fetch data"| FetchUtil
    DEXPg -->|"Fetch data"| FetchUtil
    UIPrims -->|"Provide UI primitives"| DomainComponents[Domain Components]
    BuildCfgs[Build & Tooling Configs] -->|"CI → Vite build"| CDN

    %% Click Events
    click Browser "https://github.com/yaasiinaxmed/kriptomarket/blob/main/index.html"
    click CDN "https://github.com/yaasiinaxmed/kriptomarket/blob/main/vercel.json"
    click Main "https://github.com/yaasiinaxmed/kriptomarket/blob/main/src/main.jsx"
    click App "https://github.com/yaasiinaxmed/kriptomarket/blob/main/src/App.jsx"
    click IndexPg "https://github.com/yaasiinaxmed/kriptomarket/blob/main/src/pages/Index.jsx"
    click AssetDetailPg "https://github.com/yaasiinaxmed/kriptomarket/blob/main/src/pages/AssetDetail.jsx"
    click DEXPg "https://github.com/yaasiinaxmed/kriptomarket/blob/main/src/pages/DEXScreener.jsx"
    click Nav "https://github.com/yaasiinaxmed/kriptomarket/blob/main/src/nav-items.jsx"
    click AssetDesc "https://github.com/yaasiinaxmed/kriptomarket/blob/main/src/components/AssetDescription.jsx"
    click AssetInfo "https://github.com/yaasiinaxmed/kriptomarket/blob/main/src/components/AssetInfo.jsx"
    click AssetLinks "https://github.com/yaasiinaxmed/kriptomarket/blob/main/src/components/AssetLinks.jsx"
    click CategoryFilter "https://github.com/yaasiinaxmed/kriptomarket/blob/main/src/components/CategoryFilter.jsx"
    click CoinListItem "https://github.com/yaasiinaxmed/kriptomarket/blob/main/src/components/CoinListItem.jsx"
    click ContractAddr "https://github.com/yaasiinaxmed/kriptomarket/blob/main/src/components/ContractAddress.jsx"
    click LangSwitch "https://github.com/yaasiinaxmed/kriptomarket/blob/main/src/components/LanguageSwitcher.jsx"
    click PriceChart "https://github.com/yaasiinaxmed/kriptomarket/blob/main/src/components/PriceChart.jsx"
    click UIPrims "https://github.com/yaasiinaxmed/kriptomarket/tree/main/src/components/ui/"
    click FetchUtil "https://github.com/yaasiinaxmed/kriptomarket/blob/main/src/lib/utils.js"
    click Translate "https://github.com/yaasiinaxmed/kriptomarket/blob/main/src/utils/translate.js"
    click Pkg "https://github.com/yaasiinaxmed/kriptomarket/blob/main/package.json"
    click ViteCfg "https://github.com/yaasiinaxmed/kriptomarket/blob/main/vite.config.js"
    click TailwindCfg "https://github.com/yaasiinaxmed/kriptomarket/blob/main/tailwind.config.js"
    click PostcssCfg "https://github.com/yaasiinaxmed/kriptomarket/blob/main/postcss.config.js"
    click BunLock "https://github.com/yaasiinaxmed/kriptomarket/blob/main/bun.lockb"
    click IndexCSS "https://github.com/yaasiinaxmed/kriptomarket/blob/main/src/index.css"

    %% Styles
    classDef userFacing fill:#cef2,stroke:#333,stroke-width:1px
    classDef build fill:#d4a2,stroke:#333,stroke-width:1px
    classDef external fill:#f3d2,stroke:#333,stroke-width:1px
    classDef internal fill:#eef5,stroke:#333,stroke-width:1px
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
