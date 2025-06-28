---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/github/opensource.guide
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


# opensource.guide repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>

---


```mermaid
---
title: "opensource.guide repo project"
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
    %% User and Repo
    Developer["Developer Workstation"]:::user
    GitHubRepo["GitHub Repository"]:::source

    %% Source Zone
    subgraph "Source Zone"
        direction TB
        Articles["_articles/ (Markdown Articles)"]:::source
        Locales["_data/locales/ (Localization YAML Data)"]:::source
        Layouts["_layouts/ (Layouts)"]:::source
        Includes["_includes/ (Includes/Partials)"]:::source
        CSS["assets/css/ (SCSS → CSS)"]:::source
        JS["assets/js/ (JS Bundling & Search Worker)"]:::source
        ConfigYAML["_config.yml"]:::source
        Gemfile["Gemfile"]:::source
        GemfileLock["Gemfile.lock"]:::source
        PackageJSON["package.json"]:::source
        PackageLock["package-lock.json"]:::source
        NodeVersion[".node-version"]:::source
        subgraph "Project Docs & Style Guides"
            direction TB
            Doc1["docs/content-model.md"]:::source
            Doc2["docs/personas.md"]:::source
            Doc3["docs/styleguide.md"]:::source
            Doc4["docs/translations.md"]:::source
        end
        IndexHTML["index.html"]:::source
    end

    %% CI/CD
    subgraph "CI/CD Pipeline"
        direction TB
        CI_JEKYLL[".github/workflows/jekyll.yml"]:::processing
        CI_TESTS[".github/workflows/tests.yml"]:::processing
        CI_PREVIEW[".github/workflows/jekyll-preview.yml"]:::processing
        CI_STALE[".github/workflows/stale.yml"]:::processing
    end

    %% Build Zone
    subgraph "Build Zone"
        direction TB
        Bootstrap["script/bootstrap"]:::processing
        BuildScript["script/build"]:::processing
        ServerScript["script/server"]:::processing
        TestScript["script/test"]:::processing
        HTMLProofer["script/html-proofer"]:::processing
        JekyllEngine["Jekyll Build Engine"]:::processing
        Generated["Built Static Site"]:::processing
    end

    %% Deployment Zone
    subgraph "Deployment Zone"
        direction TB
        Hosting["GitHub Pages / CDN"]:::deployment
        Browser["End-User Browser"]:::user
    end

    %% Relationships
    Developer -->|"push code"| GitHubRepo
    GitHubRepo --> CI_JEKYLL
    GitHubRepo --> CI_TESTS
    GitHubRepo --> CI_PREVIEW
    GitHubRepo --> CI_STALE

    CI_TESTS --> TestScript
    CI_TESTS --> HTMLProofer

    CI_JEKYLL --> Bootstrap
    CI_JEKYLL --> BuildScript

    Bootstrap --> JekyllEngine
    BuildScript --> JekyllEngine
    BuildScript --> CSS
    BuildScript --> JS

    TestScript --> HTMLProofer

    %% Source to Build
    Articles --> JekyllEngine
    Locales --> JekyllEngine
    Layouts --> JekyllEngine
    Includes --> JekyllEngine
    ConfigYAML --> JekyllEngine
    Gemfile --> JekyllEngine
    GemfileLock --> JekyllEngine
    PackageJSON --> JekyllEngine
    PackageLock --> JekyllEngine
    NodeVersion --> JekyllEngine
    Doc1 --> JekyllEngine
    Doc2 --> JekyllEngine
    Doc3 --> JekyllEngine
    Doc4 --> JekyllEngine
    IndexHTML --> JekyllEngine

    JekyllEngine --> Generated
    HTMLProofer --> Generated

    Generated --> Hosting
    Hosting --> Browser

    %% Click Events
    click Articles "https://github.com/github/opensource.guide/tree/main/_articles/"
    click Locales "https://github.com/github/opensource.guide/tree/main/_data/locales/"
    click Layouts "https://github.com/github/opensource.guide/tree/main/_layouts/"
    click Includes "https://github.com/github/opensource.guide/tree/main/_includes/"
    click CSS "https://github.com/github/opensource.guide/tree/main/assets/css/"
    click JS "https://github.com/github/opensource.guide/tree/main/assets/js/"
    click Bootstrap "https://github.com/github/opensource.guide/tree/main/script/bootstrap"
    click BuildScript "https://github.com/github/opensource.guide/tree/main/script/build"
    click ServerScript "https://github.com/github/opensource.guide/tree/main/script/server"
    click TestScript "https://github.com/github/opensource.guide/tree/main/script/test"
    click HTMLProofer "https://github.com/github/opensource.guide/tree/main/script/html-proofer"
    click CI_JEKYLL "https://github.com/github/opensource.guide/blob/main/.github/workflows/jekyll.yml"
    click CI_TESTS "https://github.com/github/opensource.guide/blob/main/.github/workflows/tests.yml"
    click CI_PREVIEW "https://github.com/github/opensource.guide/blob/main/.github/workflows/jekyll-preview.yml"
    click CI_STALE "https://github.com/github/opensource.guide/blob/main/.github/workflows/stale.yml"
    click ConfigYAML "https://github.com/github/opensource.guide/blob/main/_config.yml"
    click Gemfile "https://github.com/github/opensource.guide/tree/main/Gemfile"
    click GemfileLock "https://github.com/github/opensource.guide/blob/main/Gemfile.lock"
    click PackageJSON "https://github.com/github/opensource.guide/blob/main/package.json"
    click PackageLock "https://github.com/github/opensource.guide/blob/main/package-lock.json"
    click NodeVersion "https://github.com/github/opensource.guide/blob/main/.node-version"
    click Doc1 "https://github.com/github/opensource.guide/blob/main/docs/content-model.md"
    click Doc2 "https://github.com/github/opensource.guide/blob/main/docs/personas.md"
    click Doc3 "https://github.com/github/opensource.guide/blob/main/docs/styleguide.md"
    click Doc4 "https://github.com/github/opensource.guide/blob/main/docs/translations.md"
    click IndexHTML "https://github.com/github/opensource.guide/blob/main/index.html"
    click Hosting "https://github.com/github/opensource.guide/tree/main/CNAME"

    %% Styles
    classDef source fill:#f9f,stroke:#333,stroke-width:1px
    classDef processing fill:#ff9,stroke:#333,stroke-width:1px
    classDef deployment fill:#9ff,stroke:#333,stroke-width:1px
    classDef user fill:#cfc,stroke:#333,stroke-width:1px
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

  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

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