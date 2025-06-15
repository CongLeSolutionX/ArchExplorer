---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/internetarchive/bookreader
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExYXVqY2NjengxdXh4N3Jxb2N2aTYxcGV6ODR3Z2J5dHR0c210MGx4dSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/l0LHVgZQp79x2hZEA/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# bookreader repo project
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
title: "bookreader repo project"
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
  subgraph "User / Browser"
    DemoHTML["Demo HTML Pages"]:::demo
    ArchiveEmbed["Archive.org Embed"]:::demo
  end

  subgraph "BookReader Runtime"
    CoreDir["Core Engine (src/BookReader)"]:::core
    EntryPoint["Core Entry Point"]:::core
    JQuery["jQuery Wrapper"]:::core
    NavigatorDir["BookNavigator Components"]:::navigator
    PluginsDir["Plugin Layer"]:::plugin

    EntryPoint -->|imports| CoreDir
    EntryPoint -->|uses| JQuery
    EntryPoint -->|initializes| NavigatorDir
    EntryPoint -->|registers| PluginsDir
    CoreDir -->|emits events| NavigatorDir
    CoreDir -->|emits events| PluginsDir
    NavigatorDir -->|invokes| CoreDir
    PluginsDir -->|hooks/mixins| CoreDir
  end

  subgraph "Build & Packaging & Deployment"
    Babel["Babel"]:::build
    Webpack["Webpack"]:::build
    VersionScripts["Versioning Scripts"]:::build
    CI["GitHub Actions CI"]:::ci
    Dist["dist Bundle"]:::build
    Netlify["Netlify Deployment"]:::deploy
    NPM["NPM Publish"]:::deploy

    Babel -->|transpiles| Webpack
    VersionScripts -->|pre/post| Webpack
    CI -->|runs workflows| Webpack
    Webpack -->|bundles| Dist
    Dist -->|deployed| Netlify
    Dist -->|published| NPM
    CI -->|publishes| NPM
  end

  subgraph "Testing"
    Jest["Unit Tests (Jest)"]:::test
    TestCafe["E2E Tests (TestCafe)"]:::test

    Jest -->|tests| CoreDir
    Jest -->|tests| NavigatorDir
    Jest -->|tests| PluginsDir
    TestCafe -->|tests| DemoHTML
  end

  subgraph "External Dependencies"
    IIIF["IIIF Manifest Endpoints"]:::external
    IASearch["Internet Archive Search API"]:::external
    BrowserAPI["Browser APIs"]:::external

    DemoHTML -->|fetch manifest| IIIF
    DemoHTML -->|calls| IASearch
    PluginsDir -->|postMessage| BrowserAPI
  end

  click CoreDir "https://github.com/internetarchive/bookreader/tree/master/src/BookReader"
  click EntryPoint "https://github.com/internetarchive/bookreader/blob/master/src/BookReader.js"
  click JQuery "https://github.com/internetarchive/bookreader/blob/master/src/jquery-wrapper.js"
  click NavigatorDir "https://github.com/internetarchive/bookreader/tree/master/src/BookNavigator"
  click PluginsDir "https://github.com/internetarchive/bookreader/tree/master/src/plugins"
  click DemoHTML "https://github.com/internetarchive/bookreader/tree/master/BookReaderDemo"
  click Webpack "https://github.com/internetarchive/bookreader/blob/master/webpack.config.js"
  click Babel "https://github.com/internetarchive/bookreader/blob/master/babel.config.cjs"
  click Netlify "https://github.com/internetarchive/bookreader/blob/master/netlify.toml"
  click VersionScripts "https://github.com/internetarchive/bookreader/blob/master/scripts/preversion.js"
  click VersionScripts "https://github.com/internetarchive/bookreader/blob/master/scripts/postversion.js"
  click CI "https://github.com/internetarchive/bookreader/blob/master/.github/workflows/node.js.yml"
  click CI "https://github.com/internetarchive/bookreader/blob/master/.github/workflows/npm-publish.yml"
  click Jest "https://github.com/internetarchive/bookreader/tree/master/tests/jest"
  click TestCafe "https://github.com/internetarchive/bookreader/tree/master/tests/e2e"

  classDef core fill:#BBDEFB,stroke:#1E88E5;
  classDef navigator fill:#C8E6C9,stroke:#43A047;
  classDef plugin fill:#FFF9C4,stroke:#FBC02D;
  classDef build fill:#CFD8DC,stroke:#607D8B;
  classDef deploy fill:#CFD8DC,stroke:#455A64;
  classDef ci fill:#ECEFF1,stroke:#90A4AE;
  classDef test fill:#FFE0B2,stroke:#FB8C00;
  classDef demo fill:#E1BEE7,stroke:#8E24AA;
  classDef external fill:none,stroke-dasharray:5 5;
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
