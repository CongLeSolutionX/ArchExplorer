---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/filecoin-project/specs
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExMnF2dWN0czd0djAwaHhrMGFpbTB2cnFtdTgwaGNlZWJjY2I3aXhrYyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/b4R6VJ3y942mHySNta/giphy.gif)
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
    %% Developer & Repo
    Developer["Developer"]:::blue
    GitHub["GitHub Repo"]:::blue
    Developer -->|push code| GitHub

    %% CI/CD Pipeline
    subgraph "CI/CD Pipeline"
        direction TB
        Actions["GitHub Actions"]:::green
    end
    GitHub -->|trigger CI| Actions

    %% Build Steps
    subgraph "Build Steps"
        direction TB
        Hugo["Hugo Build"]:::green
        Webpack["Webpack Build"]:::green

        %% Hugo inputs
        content["Markdown Spec Pages (content/)"]:::code
        layouts["Hugo Templates & Partials (layouts/)"]:::code
        theme["Hugo Theme (themes/book/)"]:::code
        assets["CSS/SCSS & JS Assets (assets/)"]:::code
        staticGen["Generated SVG Diagrams (static/_gen/diagrams/)"]:::code
        toolsDir["Build-Time Tooling (tools/)"]:::green

        %% API inputs
        apiIndex["API Entry Point (api/index.js)"]:::code
        router["Router (api/src/router.js)"]:::code
        getJs["Handler (api/src/get.js)"]:::code
        webpackCfg["Webpack Config (api/src/webpack.config.js)"]:::code
        wranglerCfg["Wrangler Config (api/wrangler.toml)"]:::code
        apiPkg["API Package (api/package.json)"]:::code

        %% Build flows
        Actions --> Hugo
        Actions --> Webpack

        Hugo --> content
        Hugo --> layouts
        Hugo --> theme
        Hugo --> assets
        Hugo --> staticGen
        Hugo --> toolsDir

        Webpack --> apiIndex
        Webpack --> router
        Webpack --> getJs
        Webpack --> webpackCfg
        Webpack --> wranglerCfg
        Webpack --> apiPkg
    end

    %% Deployment
    subgraph "Deploy Targets"
        direction TB
        Fleek["Fleek/IPFS + CDN"]:::orange
        Worker["Cloudflare Workers"]:::orange
    end
    Hugo -->|deploy static| Fleek
    Webpack -->|deploy API| Worker

    %% Runtime
    subgraph "Runtime"
        direction TB
        User["End User Browser"]:::purple
        User -->|fetch static| Fleek
        User -->|call /api| Worker
    end

    %% Click Events for component mapping
    click content "https://github.com/filecoin-project/specs/tree/master/content/"
    click layouts "https://github.com/filecoin-project/specs/tree/master/layouts/"
    click theme "https://github.com/filecoin-project/specs/tree/master/themes/book/"
    click assets "https://github.com/filecoin-project/specs/tree/master/assets/"
    click staticGen "https://github.com/filecoin-project/specs/tree/master/static/_gen/diagrams/"
    click apiIndex "https://github.com/filecoin-project/specs/blob/master/api/index.js"
    click router "https://github.com/filecoin-project/specs/blob/master/api/src/router.js"
    click getJs "https://github.com/filecoin-project/specs/blob/master/api/src/get.js"
    click webpackCfg "https://github.com/filecoin-project/specs/blob/master/api/src/webpack.config.js"
    click wranglerCfg "https://github.com/filecoin-project/specs/blob/master/api/wrangler.toml"
    click apiPkg "https://github.com/filecoin-project/specs/blob/master/api/package.json"
    click toolsDir "https://github.com/filecoin-project/specs/blob/master/tools/diagrams.js"
    click toolsDir "https://github.com/filecoin-project/specs/blob/master/tools/toc.js"
    click toolsDir "https://github.com/filecoin-project/specs/blob/master/tools/readme.js"
    click toolsDir "https://github.com/filecoin-project/specs/blob/master/tools/watch.js"
    click toolsDir "https://github.com/filecoin-project/specs/blob/master/tools/toc/build-model.js"
    click GitHub "https://github.com/filecoin-project/specs/blob/master/.github/workflows/main.yml"
    click Fleek "https://github.com/filecoin-project/specs/blob/master/.fleek.json"

    %% Styles
    classDef blue fill:#D0E8FF,stroke:#0066CC,color:#000
    classDef green fill:#DFF8D8,stroke:#2E8B57,color:#000
    classDef orange fill:#FFE4B5,stroke:#CC8400,color:#000
    classDef purple fill:#E6D8FF,stroke:#800080,color:#000
    classDef code fill:#F0F0F0,stroke:#999,color:#000,stroke-dasharray: 2 2
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