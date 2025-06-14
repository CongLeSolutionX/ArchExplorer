---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/bluesky-social/atproto-website
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




# atproto-website repo project
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
title: "atproto-website repo project"
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
    %% Developer triggers
    Dev["Developer"]:::actor
    GitHub[(Git Repository)]:::datastore
    CI["CI/CD Pipeline"]:::process

    Dev -->|push code to| GitHub
    GitHub -->|triggers| CI

    %% Content Repository
    subgraph "Content Repository"
        direction TB
        MDX["MDX Content\n(src/app/[locale])"]:::content
        ReactComp["React Components\n(src/components)"]:::content
        Icons["Shared Icons Set\n(src/components/icons)"]:::content
        StylesSrc["Base Styles\n(src/styles/tailwind.css)"]:::content
        Assets["Static Assets\n(public)"]:::content
    end

    %% MDX Plugin Pipeline
    subgraph "MDX Plugin Pipeline"
        direction TB
        Recma["recma Plugin\n(src/mdx/recma.mjs)"]:::process
        Rehype["rehype Plugin\n(src/mdx/rehype.mjs)"]:::process
        Remark["remark Plugin\n(src/mdx/remark.mjs)"]:::process
        Search["search Plugin\n(src/mdx/search.mjs)"]:::process
    end

    %% Styling Pipeline
    subgraph "Styling Pipeline"
        direction TB
        TailwindCfg["Tailwind Config\n(tailwind.config.ts)"]:::process
        PostCSSCfg["PostCSS Config\n(postcss.config.js)"]:::process
        StylesProc["CSS Processor"]:::process
    end

    %% Build Pipeline
    subgraph "Build Pipeline"
        direction TB
        Build["Next.js Build"]:::build
    end

    CI --> Build
    MDX --> Build
    ReactComp --> Build
    Icons --> Build
    Assets --> Build
    Recma --> Build
    Rehype --> Build
    Remark --> Build
    Search --> Build
    TailwindCfg --> StylesProc --> Build
    PostCSSCfg --> StylesProc

    %% Next.js Runtime
    subgraph "Next.js Runtime" 
        direction TB
        Routing["App Router\n(src/app/[locale])"]:::runtime
        Layouts["Layouts & Providers\n(layout.tsx, providers.tsx)"]:::runtime
        NotFound["Fallback Pages\n(not-found.tsx)"]:::runtime
        Middleware["Locale Middleware\n(src/middleware.js)"]:::runtime
        SSGSSR["SSG/SSR Serverless"]:::runtime
    end

    Build --> Routing
    Middleware --> Routing
    Layouts --> Routing
    NotFound --> Routing
    Routing --> SSGSSR

    %% Deployment / CDN
    subgraph "Deployment & CDN"
        direction TB
        CDN["CDN / Edge Network"]:::infra
        Output[".next Output"]:::infra
    end

    Build --> Output --> CDN
    SSGSSR --> CDN

    %% Client
    Browser["Client Browser"]:::client
    Browser -->|request page| CDN
    CDN -->|serve HTML+JS| Browser

    %% Click Events
    click MDX "https://github.com/bluesky-social/atproto-website/tree/main/src/app/[locale]"
    click ReactComp "https://github.com/bluesky-social/atproto-website/tree/main/src/components"
    click Icons "https://github.com/bluesky-social/atproto-website/tree/main/src/components/icons"
    click Recma "https://github.com/bluesky-social/atproto-website/blob/main/src/mdx/recma.mjs"
    click Rehype "https://github.com/bluesky-social/atproto-website/blob/main/src/mdx/rehype.mjs"
    click Remark "https://github.com/bluesky-social/atproto-website/blob/main/src/mdx/remark.mjs"
    click Search "https://github.com/bluesky-social/atproto-website/blob/main/src/mdx/search.mjs"
    click TailwindCfg "https://github.com/bluesky-social/atproto-website/blob/main/tailwind.config.ts"
    click PostCSSCfg "https://github.com/bluesky-social/atproto-website/blob/main/postcss.config.js"
    click StylesSrc "https://github.com/bluesky-social/atproto-website/blob/main/src/styles/tailwind.css"
    click Assets "https://github.com/bluesky-social/atproto-website/tree/main/public"
    click Middleware "https://github.com/bluesky-social/atproto-website/blob/main/src/middleware.js"
    click Routing "https://github.com/bluesky-social/atproto-website/tree/main/src/app/[locale]"
    click Layouts "https://github.com/bluesky-social/atproto-website/blob/main/src/app/[locale]/layout.tsx"
    click Layouts "https://github.com/bluesky-social/atproto-website/blob/main/src/app/[locale]/providers.tsx"
    click NotFound "https://github.com/bluesky-social/atproto-website/blob/main/src/app/[locale]/not-found.tsx"
    click GitHub "https://github.com/bluesky-social/atproto-website/blob/main/README.md"
    click GitHub "https://github.com/bluesky-social/atproto-website/tree/main/Makefile"
    click GitHub "https://github.com/bluesky-social/atproto-website/blob/main/next-env.d.ts"
    click GitHub "https://github.com/bluesky-social/atproto-website/blob/main/types.d.ts"
    click GitHub "https://github.com/bluesky-social/atproto-website/blob/main/tsconfig.json"

    %% Styles
    classDef content fill:#e2f7e2,stroke:#1e9c1e,color:#1e9c1e
    classDef process fill:#e2ebf7,stroke:#1e40af,color:#1e40af
    classDef build fill:#dbeafe,stroke:#1e3a8a,color:#1e3a8a
    classDef runtime fill:#f0f9ff,stroke:#0284c7,color:#0284c7
    classDef infra fill:#fff7ed,stroke:#ea580c,color:#ea580c
    classDef actor fill:#f3f4f6,stroke:#6b7280,color:#374151
    classDef client fill:#f9fafb,stroke:#4b5563,color:#111827
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