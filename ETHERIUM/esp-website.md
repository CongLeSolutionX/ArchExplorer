---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/esp-website
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExcjcwdXl5NWRnOW11M3F1MzN4Njh2NThtbmZoemU3MHczY3p6bzM2NiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/IcZhFmufozDCij3p22/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# esp-website repo project
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
title: "esp-website repo project"
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
    %% Frontend Layer
    subgraph "Frontend (Browser & Next.js)" 
        direction TB
        Browser["Browser"]:::external
        StaticAssets["Static Assets<br/>(public)"]:::frontend
        NextPages["Next.js Pages<br/>(TSX, Chakra UI, SSG/SSR)"]:::frontend
        UIComponents["UI Components<br/>(Chakra UI, Framer Motion)"]:::frontend
        FormComponents["Form Components<br/>(react-hook-form)"]:::frontend
        LayoutComponents["Layout Components"]:::frontend
        CustomHooks["Custom Hooks"]:::frontend
        Theme["Theme Customizations"]:::frontend
        Utils["Utility Functions"]:::frontend
    end

    %% API Layer
    subgraph "API Layer (Serverless Functions)" 
        direction TB
        APIRoutes["Next.js API Routes<br/>(Node, JSforce)"]:::backend
        MMParse["Middleware: multipartyParse"]:::backend
        MMSanitize["Middleware: sanitizeFields"]:::backend
        MMCaptcha["Middleware: verifyCaptcha"]:::backend
    end

    %% External Services
    subgraph "External Services" 
        direction TB
        Salesforce["Salesforce REST API"]:::external
        hCaptcha["hCaptcha API"]:::external
        GoogleSheets["Google Sheets CSV"]:::external
        Netlify["Netlify CI/CD & Hosting"]:::external
    end

    %% Build Process
    subgraph "Build & Data-fetching"
        direction TB
        NetlifyBuild["Netlify Build"]:::external
        GSFetch["Fetch CSV via getStaticProps"]:::frontend
    end

    %% Connections
    Browser -->|"requests pages"| NextPages
    Browser -->|"fetches assets"| StaticAssets
    NextPages -->|"uses"| UIComponents
    NextPages -->|"uses"| FormComponents
    NextPages -->|"wraps with"| LayoutComponents
    NextPages -->|"calls hooks"| CustomHooks
    NextPages -->|"applies theme"| Theme
    NextPages -->|"calls utils"| Utils

    NextPages -->|"API calls"| APIRoutes
    APIRoutes -->|"uses"| MMParse
    APIRoutes -->|"uses"| MMSanitize
    APIRoutes -->|"uses"| MMCaptcha
    MMCaptcha -->|"verifies captcha"| hCaptcha
    APIRoutes -->|"JSforce calls"| Salesforce

    NetlifyBuild -->|"build-time"| GSFetch
    GSFetch -->|"reads CSV"| GoogleSheets
    GSFetch -->|"generates static pages"| NextPages

    NetlifyBuild -->|"deploy functions"| APIRoutes
    NetlifyBuild -->|"deploy static assets"| StaticAssets

    %% Click Events
    click StaticAssets "https://github.com/ethereum/esp-website/tree/master/public/"
    click NextPages "https://github.com/ethereum/esp-website/blob/master/src/pages/**/*.tsx"
    click UIComponents "https://github.com/ethereum/esp-website/tree/master/src/components/UI/"
    click FormComponents "https://github.com/ethereum/esp-website/tree/master/src/components/forms/"
    click LayoutComponents "https://github.com/ethereum/esp-website/tree/master/src/components/layout/"
    click CustomHooks "https://github.com/ethereum/esp-website/tree/master/src/hooks/"
    click Theme "https://github.com/ethereum/esp-website/tree/master/src/theme/"
    click Utils "https://github.com/ethereum/esp-website/tree/master/src/utils/"
    click APIRoutes "https://github.com/ethereum/esp-website/blob/master/src/pages/api/*.ts"
    click MMParse "https://github.com/ethereum/esp-website/blob/master/src/middlewares/multipartyParse.ts"
    click MMSanitize "https://github.com/ethereum/esp-website/blob/master/src/middlewares/sanitizeFields.ts"
    click MMCaptcha "https://github.com/ethereum/esp-website/blob/master/src/middlewares/verifyCaptcha.ts"
    click Salesforce "https://github.com/ethereum/esp-website/blob/master/src/pages/api/project-grants.ts"
    click GSFetch "https://github.com/ethereum/esp-website/tree/master/src/utils/"

    %% Styles
    classDef frontend fill:#D0E8FF,stroke:#027BFF,color:#000
    classDef backend fill:#DFF5D0,stroke:#2E7D32,color:#000
    classDef external fill:#FFE5B4,stroke:#FF8C00,color:#000

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
