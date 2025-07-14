---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/JuliaLang/www.julialang.org
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




# www.julialang.org repo project
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
title: "www.julialang.org repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#F5E3',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EEF5',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD'
    }
  }
}%%
flowchart LR
  %% Source Layer
  subgraph "Source Layer"
    subgraph "Site Content"
      blog["blog/"]:::source
      community["community/"]:::source
      contribute["contribute/"]:::source
      jsoc["jsoc/"]:::source
      learning["learning/"]:::source
      research["research/"]:::source
    end
    subgraph "Static Assets"
      assets["assets/"]:::source
      archived_assets["_assets/"]:::source
    end
    subgraph "CSS Stylesheets"
      css_app["app.css"]:::source
      css_fonts["fonts.css"]:::source
      css_franklin["franklin.css"]:::source
    end
    subgraph "Templates"
      layout["_layout/"]:::source
    end
    subgraph "Client Libraries"
      libs["_libs/"]:::source
    end
    subgraph "Config & Metadata"
      project_toml["Project.toml"]:::source
      manifest["Manifest.toml"]:::source
      config_md["config.md"]:::source
      readme["README.md"]:::source
    end
    subgraph "Downloads"
      downloads_proj["downloads/Project.toml"]:::source
      downloads_manifest["downloads/Manifest.toml"]:::source
    end
    subgraph "Deployment Metadata"
      cname["CNAME"]:::source
      nojekyll[".nojekyll"]:::source
      error404["404.md"]:::source
    end
  end

  %% Build Layer
  subgraph "Build Layer"
    Franklin["Franklin.jl Build Engine"]:::build
    LiveServer["Local LiveServer (localhost:8000)"]:::build
  end

  %% CI/CD Layer
  subgraph "CI/CD Layer"
    subgraph "GitHub Actions Workflows"
      check_orgs["check_orgs.yml"]:::ci
      typos["typos.yml"]:::ci
      pr_comment["pr_comment.yml"]:::ci
      deploy_wf["deploy.yml"]:::ci
    end
    subgraph "CI Utilities"
      check_tool["check_orgs.jl"]:::ci
      utils["utils.jl"]:::ci
    end
    netlify["Netlify (PR Previews)"]:::service
    ghpages_workflow["GitHub Pages Deploy"]:::service
  end

  %% Hosting Layer
  subgraph "Hosting Layer"
    ghpages_host["GitHub Pages CDN"]:::hosting
    netlify_host["Netlify Hosting"]:::hosting
  end

  %% Data Flow
  blog -->|source| Franklin
  community --> Franklin
  contribute --> Franklin
  jsoc --> Franklin
  learning --> Franklin
  research --> Franklin

  assets --> Franklin
  archived_assets --> Franklin
  css_app --> Franklin
  css_fonts --> Franklin
  css_franklin --> Franklin
  layout --> Franklin
  libs --> Franklin
  project_toml --> Franklin
  manifest --> Franklin
  config_md --> Franklin
  readme --> Franklin
  downloads_proj --> Franklin
  downloads_manifest --> Franklin
  cname --> Franklin
  nojekyll --> Franklin
  error404 --> Franklin

  Franklin -->|serves| LiveServer
  Franklin -->|builds| check_orgs
  Franklin -->|builds| typos
  Franklin -->|builds| pr_comment
  Franklin -->|builds| deploy_wf

  check_orgs --> check_tool
  check_orgs --> utils
  typos --> utils
  pr_comment --> netlify
  deploy_wf --> ghpages_workflow

  ghpages_workflow --> ghpages_host
  netlify --> netlify_host

  LiveServer -.->|preview| ghpages_host
  LiveServer -.->|optional preview| netlify_host

  %% Click Events
  click blog "https://github.com/julialang/www.julialang.org/tree/main//blog/"
  click community "https://github.com/julialang/www.julialang.org/tree/main//community/"
  click contribute "https://github.com/julialang/www.julialang.org/tree/main//contribute/"
  click jsoc "https://github.com/julialang/www.julialang.org/tree/main//jsoc/"
  click learning "https://github.com/julialang/www.julialang.org/tree/main//learning/"
  click research "https://github.com/julialang/www.julialang.org/tree/main//research/"
  click assets "https://github.com/julialang/www.julialang.org/tree/main//assets/"
  click archived_assets "https://github.com/julialang/www.julialang.org/tree/main//_assets/"
  click css_app "https://github.com/julialang/www.julialang.org/blob/main//_css/app.css"
  click css_fonts "https://github.com/julialang/www.julialang.org/blob/main//_css/fonts.css"
  click css_franklin "https://github.com/julialang/www.julialang.org/blob/main//_css/franklin.css"
  click layout "https://github.com/julialang/www.julialang.org/tree/main//_layout/"
  click libs "https://github.com/julialang/www.julialang.org/tree/main//_libs/"
  click project_toml "https://github.com/julialang/www.julialang.org/blob/main//Project.toml"
  click manifest "https://github.com/julialang/www.julialang.org/blob/main//Manifest.toml"
  click config_md "https://github.com/julialang/www.julialang.org/blob/main//config.md"
  click readme "https://github.com/julialang/www.julialang.org/blob/main//README.md"
  click downloads_proj "https://github.com/julialang/www.julialang.org/blob/main//downloads/Project.toml"
  click downloads_manifest "https://github.com/julialang/www.julialang.org/blob/main//downloads/Manifest.toml"
  click cname "https://github.com/julialang/www.julialang.org/tree/main//CNAME"
  click nojekyll "https://github.com/julialang/www.julialang.org/blob/main//.nojekyll"
  click error404 "https://github.com/julialang/www.julialang.org/blob/main//404.md"
  click check_orgs "https://github.com/julialang/www.julialang.org/blob/main//.github/workflows/check_orgs.yml"
  click typos "https://github.com/julialang/www.julialang.org/blob/main//.github/workflows/typos.yml"
  click pr_comment "https://github.com/julialang/www.julialang.org/blob/main//.github/workflows/pr_comment.yml"
  click deploy_wf "https://github.com/julialang/www.julialang.org/blob/main//.github/workflows/deploy.yml"
  click check_tool "https://github.com/julialang/www.julialang.org/blob/main//tools/check_orgs/check_orgs.jl"
  click utils "https://github.com/julialang/www.julialang.org/blob/main//utils.jl"

  %% Styles
  classDef source fill:#f9f,stroke:#333,stroke-width:1px
  classDef build fill:#9cf,stroke:#333,stroke-width:1px
  classDef ci fill:#fc9,stroke:#333,stroke-width:1px
  classDef service fill:#cfc,stroke:#333,stroke-width:1px
  classDef hosting fill:#ccf,stroke:#333,stroke-width:1px

```

-----

<!-- 
```mermaid
%% Current Mermaid version
info
```  -->


```mermaid
---
title: "C<char>o&#770;</char>ngL<char>e&#770;</char>SolutionX"
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
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX/CongLeSolutionX' target='_blank'>Click here if you care about the profile of a tech guy seeking for job 🙏🏼</a>"}}

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