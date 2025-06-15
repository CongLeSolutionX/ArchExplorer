---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/yaasiinaxmed/meme-maker
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExb2U4aHJnYzZ4dHUyZ2g0a25ja21oM3UxNGo4b3AwNjFqd3VoM2Q3byZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/10zxDv7Hv5RF9C/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# meme-maker repo project
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
title: "meme-maker repo project"
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
    subgraph Build_and_Tooling["Build & Tooling"]
    direction TB
        vite["vite.config.ts"]:::build
        tsc1["tsconfig.json"]:::build
        tsc2["tsconfig.app.json"]:::build
        tsc3["tsconfig.node.json"]:::build
        postcss["postcss.config.js"]:::build
        tailwind["tailwind.config.js"]:::build
        eslint["eslint.config.js"]:::build
        pkg["package.json"]:::build
        lock["package-lock.json"]:::build
    end

    subgraph Hosting_and_Delivery["Hosting & Delivery"]
    direction TB
        CDN["Static Host/CDN<br/>(Vercel)"]:::hosting
        HTML["index.html"]:::hosting
    end

    subgraph Browser_Client["Browser / Client"]
    direction TB
        main["src/main.tsx"]:::spa
        App["src/App.tsx"]:::spa
        CSS["src/index.css"]:::spa

        subgraph React_App["React App"]
        direction TB
            subgraph "UI Layer"
            direction TB
                AnimalSel("AnimalSelector"):::spa
                GenerateBtn("GenerateButton"):::spa
                MemePrev("MemePreview"):::spa
            end
            GenSvc("Generator Service"):::spa
            State("State Management"):::spa
        end
    end

    %% External (Optional)
    subgraph External_Services["External Services"]
    direction TB
        ImgAPI["Image Hosting API"]:::external
    end

    %% Connections
    %% Build to Hosting
    vite -->|bundles| HTML
    tsc1 -->HTML
    tsc2 -->HTML
    tsc3 -->HTML
    postcss -->HTML
    tailwind -->HTML
    eslint -->HTML
    pkg -->HTML
    lock -->HTML
    HTML -->|"GET index.html"| CDN

    %% Hosting to Browser
    CDN -->|serves| HTML
    HTML -->|loads| main

    %% Browser flow
    main -->|"mounts App()"| App
    CSS -->|styles| App
    App -->|renders| AnimalSel
    App -->|renders| GenerateBtn
    App -->|renders| MemePrev
    GenerateBtn -->|"onClick generateRandom()"| GenSvc
    AnimalSel -->|"selectAnimal()"| State
    GenSvc -->|update mascot data| State
    State -->|provides props| App
    GenSvc -->|build image| MemePrev

    %% Optional external integration
    GenSvc -->|upload image| ImgAPI

    %% Click Events
    click HTML "https://github.com/yaasiinaxmed/meme-maker/blob/main/index.html"
    click main "https://github.com/yaasiinaxmed/meme-maker/blob/main/src/main.tsx"
    click App "https://github.com/yaasiinaxmed/meme-maker/blob/main/src/App.tsx"
    click CSS "https://github.com/yaasiinaxmed/meme-maker/blob/main/src/index.css"
    click vite "https://github.com/yaasiinaxmed/meme-maker/blob/main/vite.config.ts"
    click tsc1 "https://github.com/yaasiinaxmed/meme-maker/blob/main/tsconfig.json"
    click tsc2 "https://github.com/yaasiinaxmed/meme-maker/blob/main/tsconfig.app.json"
    click tsc3 "https://github.com/yaasiinaxmed/meme-maker/blob/main/tsconfig.node.json"
    click postcss "https://github.com/yaasiinaxmed/meme-maker/blob/main/postcss.config.js"
    click tailwind "https://github.com/yaasiinaxmed/meme-maker/blob/main/tailwind.config.js"
    click eslint "https://github.com/yaasiinaxmed/meme-maker/blob/main/eslint.config.js"
    click pkg "https://github.com/yaasiinaxmed/meme-maker/blob/main/package.json"
    click lock "https://github.com/yaasiinaxmed/meme-maker/blob/main/package-lock.json"

    %% Styles
    classDef build fill:#e0f2f1,stroke:#004d40,stroke-width:1px
    classDef hosting fill:#e3f2fd,stroke:#0d47a1,stroke-width:2px
    classDef spa fill:#fff3e0,stroke:#e65100,stroke-width:1px
    classDef external fill:#f5f5f5,stroke:#616161,stroke-width:1px,stroke-dasharray: 5 5

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