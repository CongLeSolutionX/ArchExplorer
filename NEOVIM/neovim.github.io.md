---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/neovim/neovim.github.io
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


# neovim.github.io repo project
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
title: "neovim.github.io repo project"
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
    subgraph "Source Code Repository"
        GitHub["GitHub Repo"]:::code
    end

    subgraph "Continuous Integration"
        TravisCI["Travis CI"]:::code
    end

    subgraph "Build Environment"
        Jekyll["Jekyll Engine"]:::code
        Config["_config.yml"]:::code
        Gemfile["Gemfile & Gemfile.lock"]:::code

        subgraph "Layouts"
            DefaultLayout["default.html"]:::code
            PostLayout["post.html"]:::code
            NewsletterLayout["newsletter.html"]:::code
        end

        subgraph "Includes"
            Nav["nav.html"]:::code
            Footer["footer.html"]:::code
            NewsSidebar["news_sidebar.html"]:::code
            PostSidebar["post_sidebar.html"]:::code
            WhatIsNvim["whatisnvim.html"]:::code
        end

        Posts["_posts/*.md"]:::code
        SiteData["nav.yml"]:::code

        subgraph "Static Pages & Assets"
            About["about.html"]:::code
            Roadmap["roadmap.html"]:::code
            Community["community.html"]:::code
            CSS["css/"]:::code
            JS["js/"]:::code
            Images["images/"]:::code
            Doc2["doc2/"]:::code
        end

        BuildOutput["_site/"]:::runtime
    end

    subgraph "Hosting/CDN"
        CDN["Static File Host"]:::runtime
        CNAME["CNAME"]:::runtime
        WellKnown[".well-known/"]:::runtime
    end

    Browser["Browser (User)"]:::runtime
    Algolia["Algolia DocSearch"]:::ext
    Developer["Developer"]:::runtime

    Developer -->|"git push"| GitHub
    GitHub -->|"triggers build"| TravisCI
    TravisCI -->|"runs build"| Jekyll
    Jekyll -->|"generates"_site| BuildOutput
    TravisCI -->|"deploys static files"| CDN
    CDN -->|"serves files"| Browser
    Browser -->|"HTTP GET"| CDN
    Browser -->|"Search API calls"| Algolia

    click GitHub "https://github.com/neovim/neovim.github.io/tree/master//"
    click TravisCI "https://github.com/neovim/neovim.github.io/blob/master//.travis.yml"
    click Config "https://github.com/neovim/neovim.github.io/blob/master//_config.yml"
    click Gemfile "https://github.com/neovim/neovim.github.io/tree/master//Gemfile"
    click DefaultLayout "https://github.com/neovim/neovim.github.io/blob/master//_layouts/default.html"
    click PostLayout "https://github.com/neovim/neovim.github.io/blob/master//_layouts/post.html"
    click NewsletterLayout "https://github.com/neovim/neovim.github.io/blob/master//_layouts/newsletter.html"
    click Nav "https://github.com/neovim/neovim.github.io/blob/master//_includes/nav.html"
    click Footer "https://github.com/neovim/neovim.github.io/blob/master//_includes/footer.html"
    click NewsSidebar "https://github.com/neovim/neovim.github.io/blob/master//_includes/news_sidebar.html"
    click PostSidebar "https://github.com/neovim/neovim.github.io/blob/master//_includes/post_sidebar.html"
    click WhatIsNvim "https://github.com/neovim/neovim.github.io/blob/master//_includes/whatisnvim.html"
    click Posts "https://github.com/neovim/neovim.github.io/tree/master//_posts"
    click SiteData "https://github.com/neovim/neovim.github.io/blob/master//_data/nav.yml"
    click About "https://github.com/neovim/neovim.github.io/blob/master//about.html"
    click Roadmap "https://github.com/neovim/neovim.github.io/blob/master//roadmap.html"
    click Community "https://github.com/neovim/neovim.github.io/blob/master//community.html"
    click CSS "https://github.com/neovim/neovim.github.io/tree/master//css/"
    click JS "https://github.com/neovim/neovim.github.io/tree/master//js/"
    click Images "https://github.com/neovim/neovim.github.io/tree/master//images/"
    click Doc2 "https://github.com/neovim/neovim.github.io/tree/master//doc2/"
    click CNAME "https://github.com/neovim/neovim.github.io/tree/master//CNAME"
    click WellKnown "https://github.com/neovim/neovim.github.io/tree/master//.well-known/"

    classDef code fill:#B0E0E6,stroke:#333,stroke-width:1px
    classDef runtime fill:#C6E2C6,stroke:#333,stroke-width:1px
    classDef ext fill:#FFD580,stroke:#333,stroke-width:1px
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