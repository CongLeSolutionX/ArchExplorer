---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/electron/website
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


# website repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes (<ins>sometimes, entertainment purposes</ins>), personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


----

```mermaid
---
title: "website repo project"
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
  subgraph "Content Sources"
    Blog["blog/"]:::content
    Docs["docs/"]:::content
    Templates["create-electron-documentation/templates"]:::content
  end

  subgraph "Pre-build & Transform Scripts"
    PreBuild["scripts/pre-build.ts"]:::process
    Tasks["scripts/tasks/"]:::process
    Utils["scripts/utils/"]:::process
    Transformers["src/transformers/"]:::process
  end

  subgraph "Docusaurus Build Engine"
    Config["docusaurus.config.ts"]:::build
    Sidebars["sidebars.js"]:::build
    Theme["src/theme/"]:::build
    Components["src/components/"]:::build
    Pages["src/pages/"]:::build
    Plugins["src/plugins/"]:::build
    StylesCSS["src/css/"]:::build
    StylesSCSS["src/theme/**/*.scss"]:::build
  end

  subgraph "Localization Pipeline"
    LocaleSrc["i18n/"]:::loc
    CrowdinCfg["crowdin.yml"]:::loc
    PrepI18n["scripts/prepare-i18n-content.ts"]:::loc
    Glossary["scripts/update-crowdin-glossary.ts"]:::loc
    L10nSrc["scripts/update-l10n-sources.ts"]:::loc
  end

  subgraph "CI/CD Infrastructure"
    Workflows[".github/workflows/"]:::ci
    Matchers[".github/problem-matchers/"]:::ci
  end

  subgraph "External Services"
    CrowdinServ["Crowdin"]:::external
    Algolia["Algolia DocSearch"]:::external
    CDN["CDN/Hosting"]:::external
  end

  Runtime["Build Output (build/)"]:::deployment

  %% Content to Pre-build
  Blog --> PreBuild
  Docs --> PreBuild
  Templates --> PreBuild

  %% Pre-build to transformers
  PreBuild --> Tasks
  PreBuild --> Utils
  PreBuild --> Transformers

  %% Transform to build engine
  Transformers --> Config

  %% Config to build internals
  Config --> Sidebars
  Config --> Theme
  Config --> Components
  Config --> Pages
  Config --> Plugins
  Config --> StylesCSS
  Config --> StylesSCSS

  %% Build to runtime
  StylesSCSS --> Runtime

  %% Localization flow
  PrepI18n --> CrowdinServ
  CrowdinServ --> LocaleSrc
  LocaleSrc --> Config
  Glossary --> CrowdinServ
  L10nSrc --> CrowdinServ

  %% CI/CD orchestration
  Workflows --> PreBuild
  Workflows --> PrepI18n
  Workflows --> Config
  Workflows --> Runtime

  %% External integrations
  Config --> Algolia
  Runtime --> CDN

  %% Click Events
  click Blog "https://github.com/electron/website/tree/main/blog/"
  click Docs "https://github.com/electron/website/tree/main/docs/"
  click Templates "https://github.com/electron/website/tree/main/create-electron-documentation/templates"
  click PreBuild "https://github.com/electron/website/blob/main/scripts/pre-build.ts"
  click Tasks "https://github.com/electron/website/tree/main/scripts/tasks/"
  click Utils "https://github.com/electron/website/tree/main/scripts/utils/"
  click Transformers "https://github.com/electron/website/tree/main/src/transformers/"
  click Config "https://github.com/electron/website/blob/main/docusaurus.config.ts"
  click Sidebars "https://github.com/electron/website/blob/main/sidebars.js"
  click Theme "https://github.com/electron/website/tree/main/src/theme/"
  click Components "https://github.com/electron/website/tree/main/src/components/"
  click Pages "https://github.com/electron/website/tree/main/src/pages/"
  click Plugins "https://github.com/electron/website/tree/main/src/plugins/"
  click StylesCSS "https://github.com/electron/website/tree/main/src/css/"
  click StylesSCSS "https://github.com/electron/website/blob/main/src/theme/**/*.scss"
  click LocaleSrc "https://github.com/electron/website/tree/main/i18n/"
  click CrowdinCfg "https://github.com/electron/website/blob/main/crowdin.yml"
  click PrepI18n "https://github.com/electron/website/blob/main/scripts/prepare-i18n-content.ts"
  click Glossary "https://github.com/electron/website/blob/main/scripts/update-crowdin-glossary.ts"
  click L10nSrc "https://github.com/electron/website/blob/main/scripts/update-l10n-sources.ts"
  click Workflows "https://github.com/electron/website/tree/main/.github/workflows/"
  click Matchers "https://github.com/electron/website/tree/main/.github/problem-matchers/"

  classDef content fill:#D0E6FF,stroke:#0366d6
  classDef process fill:#DFFFD0,stroke:#28a745
  classDef build fill:#E8F0FF,stroke:#6f42c1
  classDef loc fill:#FFF0D0,stroke:#D66300
  classDef ci fill:#FFEFEF,stroke:#D73A49
  classDef external fill:#F5F5F5,stroke:#888888
  classDef deployment fill:#E8FFEE,stroke:#22863A
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