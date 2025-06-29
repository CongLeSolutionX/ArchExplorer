---
created: 2025-06-29 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/jupyter/jupyter.github.io
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




# jupyter.github.io repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for 👨‍🎓 <ins>educational purposes</ins> 👨‍🎓 (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), 📖 <ins> personal study </ins> 📖, and 🔖 <ins> technical reference </ins> 🔖.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>



----

```mermaid
---
title: "jupyter.github.io repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright © 2025 Cong Le. All Rights Reserved."
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
    %% Local Development Layer
    subgraph "Local Development" 
        direction TB
        ContentTemplates["Content & Templates"]:::content
        JekyllLayouts["Jekyll Layouts (_layouts/)"]:::content
        JekyllIncludes["Jekyll Includes (_includes/)"]:::content
        SassPreprocessor["Sass Preprocessor (_sass/)"]:::devtools
        CSSEntrypoints["CSS Entrypoints (assets/css/)"]:::devtools
        JekyllConfig["Jekyll Config & Ruby Tools"]:::devtools
        RubyVersion["Ruby Version (.ruby-version)"]:::devtools
        GemfileNode["Gemfile"]:::devtools
        Nox["nox Build Orchestrator (noxfile.py)"]:::devtools
        JekyllEngine["Jekyll Engine (Rubygems & Bundler)"]:::devtools
        Browser["Browser (localhost:4000)"]:::devtools
    end

    %% CI/CD Layer
    subgraph "CI/CD Pipelines"
        direction TB
        GitHubActions["GitHub Actions\n(validate.yml & lighthouserc.json)"]:::ci
        Netlify["Netlify (PR Previews)"]:::ci
    end

    %% Hosting Layer
    subgraph "Hosting & Delivery"
        direction TB
        GitHubPages["GitHub Pages\n(jupyter.github.io)"]:::hosting
        DNS["DNS / CNAME Mapping"]:::hosting
    end

    %% README
    Readme["Project README (README.md)"]:::content

    %% Local Dev Flow
    ContentTemplates -->|includes layouts| JekyllLayouts
    ContentTemplates -->|includes snippets| JekyllIncludes
    ContentTemplates -->|source files| SassPreprocessor
    SassPreprocessor -->|compiles SCSS| CSSEntrypoints
    CSSEntrypoints -->|assets| JekyllEngine
    JekyllLayouts --> JekyllEngine
    JekyllIncludes --> JekyllEngine
    JekyllConfig --> JekyllEngine
    RubyVersion --> JekyllEngine
    GemfileNode --> JekyllEngine
    Nox -->|runs bundler + jekyll| JekyllEngine
    JekyllEngine -->|serves site| Browser

    %% CI Flow
    ContentTemplates -->|git push / PR| GitHubActions
    JekyllConfig --> GitHubActions
    Nox --> GitHubActions
    GitHubActions -->|reports| Readme
    ContentTemplates -->|on PR| Netlify
    JekyllEngine -->|build preview| Netlify

    %% Production Flow
    GitHubActions -->|merge main| GitHubPages
    Netlify ---|notifications| GitHubPages
    GitHubPages -->|served at| DNS
    DNS -->|resolves| GitHubPages

    %% Click Events
    click ContentTemplates "https://github.com/jupyter/jupyter.github.io/blob/main/."
    click JekyllLayouts "https://github.com/jupyter/jupyter.github.io/tree/main/_layouts/"
    click JekyllIncludes "https://github.com/jupyter/jupyter.github.io/tree/main/_includes/"
    click SassPreprocessor "https://github.com/jupyter/jupyter.github.io/tree/main/_sass/"
    click CSSEntrypoints "https://github.com/jupyter/jupyter.github.io/tree/main/assets/css/"
    click StaticAssets "https://github.com/jupyter/jupyter.github.io/tree/main/assets/"
    click JekyllConfig "https://github.com/jupyter/jupyter.github.io/blob/main/_config.yml"
    click RubyVersion "https://github.com/jupyter/jupyter.github.io/blob/main/.ruby-version"
    click GemfileNode "https://github.com/jupyter/jupyter.github.io/tree/main/Gemfile"
    click Nox "https://github.com/jupyter/jupyter.github.io/blob/main/noxfile.py"
    click Validate "https://github.com/jupyter/jupyter.github.io/blob/main/.github/workflows/validate.yml"
    click Lighthouse "https://github.com/jupyter/jupyter.github.io/blob/main/.github/workflows/lighthouserc.json"
    click Readme "https://github.com/jupyter/jupyter.github.io/blob/main/README.md"
    click DNS "https://github.com/jupyter/jupyter.github.io/tree/main/CNAME"

    %% Styles
    classDef content fill:#ffe6f2,stroke:#d6336c,color:#333
    classDef devtools fill:#e6f7ff,stroke:#339af0,color:#333
    classDef ci fill:#fff0b3,stroke:#fab005,color:#333
    classDef hosting fill:#e6ffe6,stroke:#2f9e44,color:#333

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
    

  Closing_quote ~~~ My_Meme
    
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