---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/nxbn-website
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExZDN3OTJmZmxqbmg3NmF5cmtzb20wZ2ozaXh0M2s4emg2ajBuZnBkcSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/lnfzT3k8g7wpG/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# nxbn-website repo project
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
title: "nxbn-website repo project"
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
    %% Infrastructure / CI & Hosting
    subgraph "Infrastructure / CI & Hosting"
        GH["GitHub Repo"]:::infra
        CI["CI (GitHub Actions)"]:::infra
        Vercel["Vercel (Build & CDN)"]:::infra
    end
    GH -->|"push code"| CI
    CI -->|"build & deploy"| Vercel

    %% CDN Layer
    subgraph "CDN Layer"
        StaticAssets["Static Assets & HTML"]:::frontend
        SSR["Serverless SSR Endpoints"]:::service
    end
    Vercel --> StaticAssets
    Vercel --> SSR

    %% Client
    Browser["User Browser"]:::frontend
    Browser -->|"request pages"| StaticAssets
    Browser -->|"request SSR"| SSR
    StaticAssets -->|"serve static pages"| Browser
    SSR -->|"serve dynamic pages"| Browser

    %% Next.js Application Core
    subgraph "Next.js Application Core"
        NC1["next.config.js"]:::service
        NC2["_app.tsx"]:::frontend
        NC3["_document.tsx"]:::frontend
        NC4["[...slug].tsx"]:::service
    end
    NC1 --> NextBuild
    NC2 --> NextBuild
    NC3 --> NextBuild
    NC4 --> NextBuild

    %% Build-Time Data Layer
    subgraph "Build-Time Data Layer"
        Markdown["Markdown Content"]:::data
        JSONData["JSON Data"]:::data
    end
    Markdown --> NextBuild
    JSONData --> NextBuild

    NextBuild["Next.js Build (SSG)"]:::service
    NextBuild --> StaticAssets
    NextBuild -.-> SSR

    %% Runtime Data Fetch
    SSR -->|"getStaticProps / getStaticPaths\nor SSR"| NextRun["Next.js Runtime"]:::service
    NextRun -->|"optional dynamic fetch"| Notion["Notion API"]:::external

    %% Opportunities Service Abstraction
    subgraph "Opportunities Service" 
        O1["index.ts"]:::service
        O2["json-provider.ts"]:::service
        O3["mock-provider.ts"]:::service
        O4["notion-provider.ts"]:::service
        O5["types.ts"]:::service
    end
    JSONData --> O2
    O2 --> O1
    Markdown --> O3
    Notion --> O4
    O3 --> O1
    O4 --> O1
    O1 --> NextBuild
    O1 --> NextRun

    %% UI Component Library
    subgraph "UI Component Library (Chakra UI)"
        UITheme["src/@chakra-ui"]:::frontend
        Buttons["src/components/Buttons"]:::frontend
        Board["src/components/OpportunityBoard"]:::frontend
        MapComp["src/components/Map"]:::frontend
        Heroes["src/components/Heroes"]:::frontend
        Nav["src/components/Nav"]:::frontend
        Icons["src/components/icons"]:::frontend
    end
    UITheme --> NC2
    Buttons --> NC2
    Board --> NC2
    MapComp --> NC2
    Heroes --> NC2
    Nav --> NC2
    Icons --> NC2

    %% Route-Level Layouts
    subgraph "Route-Level Layouts"
        L1["FellowLayout.tsx"]:::frontend
        L2["InternshipsOpen.tsx"]:::frontend
        L3["InternshipsClosed.tsx"]:::frontend
        L4["ScholarsOpen.tsx"]:::frontend
        L5["ScholarsClosed.tsx"]:::frontend
        L6["CookieLayout.tsx"]:::frontend
        L7["RootLayout.tsx"]:::frontend
    end
    L1 --> NC4
    L2 --> NC4
    L3 --> NC4
    L4 --> NC4
    L5 --> NC4
    L6 --> NC4
    L7 --> NC4

    %% Utility Libraries
    subgraph "Utility Libraries"
        U1["fonts.ts"]:::service
        U2["rehypeHeadingIds.ts"]:::service
        U3["rehypeImg.ts"]:::service
        U4["remarkInferToc.ts"]:::service
        U5["url.ts"]:::service
    end
    U1 --> NC2
    U2 --> NextBuild
    U3 --> NextBuild
    U4 --> NextBuild
    U5 --> NextBuild

    %% CI/CD & Repository Configuration
    subgraph "Repo Config & CI/CD"
        G1["ISSUE_TEMPLATE/*.md"]:::infra
        G2["PULL_REQUEST_TEMPLATE.md"]:::infra
        G3["next-sitemap.config.js"]:::infra
        G4["package.json"]:::infra
        G5["tsconfig.json"]:::infra
        G6[".eslintrc.json"]:::infra
        G7[".prettierrc"]:::infra
    end
    G1 --> GH
    G2 --> GH
    G3 --> CI
    G4 --> CI
    G5 --> CI
    G6 --> CI
    G7 --> CI

    %% Click Events
    click NC1 "https://github.com/ethereum/nxbn-website/blob/master/next.config.js"
    click NC2 "https://github.com/ethereum/nxbn-website/blob/master/src/pages/_app.tsx"
    click NC3 "https://github.com/ethereum/nxbn-website/blob/master/src/pages/_document.tsx"
    click NC4 "https://github.com/ethereum/nxbn-website/blob/master/src/pages/[...slug].tsx"
    click Markdown "https://github.com/ethereum/nxbn-website/tree/master/public/content/fellowship/"
    click JSONData "https://github.com/ethereum/nxbn-website/blob/master/public/data/internships-2025.json"
    click JSONData "https://github.com/ethereum/nxbn-website/blob/master/src/data/internships-2025.json"
    click JSONData "https://github.com/ethereum/nxbn-website/blob/master/src/data/mock-opportunities.json"
    click O1 "https://github.com/ethereum/nxbn-website/blob/master/src/services/opportunities/index.ts"
    click O2 "https://github.com/ethereum/nxbn-website/blob/master/src/services/opportunities/json-provider.ts"
    click O3 "https://github.com/ethereum/nxbn-website/blob/master/src/services/opportunities/mock-provider.ts"
    click O4 "https://github.com/ethereum/nxbn-website/blob/master/src/services/opportunities/notion-provider.ts"
    click O5 "https://github.com/ethereum/nxbn-website/blob/master/src/services/opportunities/types.ts"
    click UITheme "https://github.com/ethereum/nxbn-website/tree/master/src/@chakra-ui/"
    click Buttons "https://github.com/ethereum/nxbn-website/tree/master/src/components/Buttons"
    click Board "https://github.com/ethereum/nxbn-website/tree/master/src/components/OpportunityBoard"
    click MapComp "https://github.com/ethereum/nxbn-website/tree/master/src/components/Map"
    click Heroes "https://github.com/ethereum/nxbn-website/tree/master/src/components/Heroes"
    click Nav "https://github.com/ethereum/nxbn-website/tree/master/src/components/Nav"
    click Icons "https://github.com/ethereum/nxbn-website/tree/master/src/components/icons"
    click L1 "https://github.com/ethereum/nxbn-website/blob/master/src/layouts/FellowLayout.tsx"
    click L2 "https://github.com/ethereum/nxbn-website/blob/master/src/layouts/InternshipsOpen.tsx"
    click L3 "https://github.com/ethereum/nxbn-website/blob/master/src/layouts/InternshipsClosed.tsx"
    click L4 "https://github.com/ethereum/nxbn-website/blob/master/src/layouts/ScholarsOpen.tsx"
    click L5 "https://github.com/ethereum/nxbn-website/blob/master/src/layouts/ScholarsClosed.tsx"
    click L6 "https://github.com/ethereum/nxbn-website/blob/master/src/layouts/CookieLayout.tsx"
    click L7 "https://github.com/ethereum/nxbn-website/blob/master/src/layouts/RootLayout.tsx"
    click U1 "https://github.com/ethereum/nxbn-website/blob/master/src/lib/fonts.ts"
    click U2 "https://github.com/ethereum/nxbn-website/blob/master/src/utils/rehypeHeadingIds.ts"
    click U3 "https://github.com/ethereum/nxbn-website/blob/master/src/utils/rehypeImg.ts"
    click U4 "https://github.com/ethereum/nxbn-website/blob/master/src/utils/remarkInferToc.ts"
    click U5 "https://github.com/ethereum/nxbn-website/blob/master/src/utils/url.ts"

    %% Styles
    classDef frontend fill:#cce5ff,stroke:#004085
    classDef data fill:#d4edda,stroke:#155724
    classDef external fill:#fff3cd,stroke:#856404
    classDef infra fill:#e2e3e5,stroke:#6c757d
    classDef service fill:#e2e6ff,stroke:#004085

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
