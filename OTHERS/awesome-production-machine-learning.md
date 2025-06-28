---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/EthicalML/awesome-production-machine-learning
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExZmdoYWhxb3c2NmR6OGZoMzN5NWxqNjJmbmVxd3U0NDFobjc4ZHdvNyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/xUA7bjPYcgAvwq5CKc/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# EthicalML - awesome-production-machine-learning repo project
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
title: "awesome-production-machine-learning repo project"
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
    subgraph "Developer Environment"
        Dev["Developer Local Env"]:::user
    end

    subgraph "GitHub Repository (Code + Docs)"
        RepoRoot["/"]:::code
        README["README.md"]:::code
        Config["_config.yml"]:::build
        Workflows[".github/workflows/"]:::code
        ImagesDir["images/"]:::build
        Contrib["CONTRIBUTING.md"]:::code
        Citation["CITATION.cff"]:::code
        License["LICENSE"]:::code
    end

    subgraph "CI/CD Pipeline"
        CI["GitHub Actions CI"]:::code
    end

    subgraph "Build Step"
        Jekyll["Jekyll SSG"]:::build
    end

    subgraph "Hosting"
        Pages["GitHub Pages Hosting"]:::build
    end

    Browser["User Browser"]:::user

    shields["shields.io"]:::external
    ghapi["GitHub API"]:::external
    RepoImages["Repo/images/"]:::build
    hf["Hugging Face Space"]:::external

    Dev -->|"git push"| RepoRoot
    RepoRoot --> CI
    Workflows --> CI
    README --> CI
    Config --> CI
    CI -->|"run Jekyll build"| Jekyll
    Jekyll -->|"deploy static files"| Pages
    Pages -->|"serves static site"| Browser
    Browser -->|"fetch badges"| shields
    Browser -->|"fetch star count"| ghapi
    Browser -->|"fetch images"| RepoImages
    Browser -->|"external search link"| hf

    click RepoRoot "https://github.com/ethicalml/awesome-production-machine-learning/tree/master//"
    click Workflows "https://github.com/ethicalml/awesome-production-machine-learning/tree/master/.github/workflows/"
    click README "https://github.com/ethicalml/awesome-production-machine-learning/blob/master/README.md"
    click Config "https://github.com/ethicalml/awesome-production-machine-learning/blob/master/_config.yml"
    click ImagesDir "https://github.com/ethicalml/awesome-production-machine-learning/tree/master/images/"
    click Contrib "https://github.com/ethicalml/awesome-production-machine-learning/blob/master/CONTRIBUTING.md"
    click Citation "https://github.com/ethicalml/awesome-production-machine-learning/blob/master/CITATION.cff"
    click License "https://github.com/ethicalml/awesome-production-machine-learning/tree/master/LICENSE"

    classDef code fill:#add8e6,stroke:#000,stroke-width:1px
    classDef build fill:#90ee90,stroke:#000,stroke-width:1px
    classDef external fill:#ffcc99,stroke:#000,stroke-width:1px
    classDef user fill:#d3d3f8,stroke:#000,stroke-width:1px

```

----


```mermaid
---
title: "❓...CongLeSolutionX....❓"
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
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }

```

---
><b>Licenses</b>:
>
>- <b>MIT License</b>:  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
>- <b>Creative Commons Attribution-ShareAlike 4.0 International</b>: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) [![CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/88x31.png)](https://creativecommons.org/licenses/by-sa/4.0/) - Legal details in [LICENSE-CC-BY-SA-4.0](THE_PAST/LICENSE-CC-BY-SA-4.0) and at [Creative Commons official site](https://creativecommons.org/licenses/by-sa/4.0/).
>
---
