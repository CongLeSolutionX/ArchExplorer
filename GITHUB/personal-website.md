---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/github/personal-website
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


# personal-website repo project
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
title: "personal-website repo project"
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
    subgraph Developer_and_Source["Developer & Source"]
    direction TB
        Gemfile["Gemfile"]:::dev
        ConfigYml["_config.yml"]:::dev
        Readme["README.md"]:::dev
        Index["index.html"]:::dev
        Gitignore[".gitignore"]:::dev
        Gitattributes[".gitattributes"]:::dev
        License["LICENSE.txt"]:::dev
        PostMD["_posts/2019-01-29-hello-world.md"]:::dev
        DefaultLayout["_layouts/default.html"]:::dev
        HomeLayout["_layouts/home.html"]:::dev
        PostLayout["_layouts/post.html"]:::dev
        HeaderInc["_includes/header.html"]:::dev
        FooterInc["_includes/footer.html"]:::dev
        MastheadInc["_includes/masthead.html"]:::dev
        InterestsInc["_includes/interests.html"]:::dev
        ProjectsInc["_includes/projects.html"]:::dev
        RepoCardInc["_includes/repo-card.html"]:::dev
        PostCardInc["_includes/post-card.html"]:::dev
        TopicCardInc["_includes/topic-card.html"]:::dev
        ThoughtsInc["_includes/thoughts.html"]:::dev
        ColorsData["_data/colors.json"]:::dev
        SocialData["_data/social_media.yml"]:::dev
        HighlightSCSS["_sass/_highlight-syntax.scss"]:::dev
        StylesSCSS["assets/styles.scss"]:::dev
    end

    %% Build Engine & Plugins
    subgraph Jekyll_Build_Engine["Jekyll Build Engine"]
    direction TB
        JekyllCore["Jekyll Core<br/>(Liquid & Front Matter)"]:::build
        Plugin["github-metadata Plugin"]:::build
    end

    %% External API
    subgraph External_Service["External Service"]
    direction TB
        GitHubAPI["GitHub API"]:::external
    end

    %% Output Artifact
    subgraph Static_Site_Output["Static Site Output"]
    direction TB
        StaticSite["_site/"]:::build
    end

    %% Hosting Layer
    subgraph Hosting_and_Delivery["Hosting & Delivery"]
    direction TB
        GitHubPages["GitHub Pages<br/>Host & CDN"]:::hosting
    end

    %% Connections
    Gemfile -->|reads config| JekyllCore
    ConfigYml -->|reads config| JekyllCore
    Readme -->|includes in site| JekyllCore
    Index -->|uses layout| JekyllCore
    Gitignore -->|ignored during build| JekyllCore
    Gitattributes -->|repo config| JekyllCore
    License -->|license info| JekyllCore
    PostMD -->|content| JekyllCore
    DefaultLayout -->|template| JekyllCore
    HomeLayout -->|template| JekyllCore
    PostLayout -->|template| JekyllCore
    HeaderInc -->|include| JekyllCore
    FooterInc -->|include| JekyllCore
    MastheadInc -->|include| JekyllCore
    InterestsInc -->|include| JekyllCore
    ProjectsInc -->|include| JekyllCore
    RepoCardInc -->|include| JekyllCore
    PostCardInc -->|include| JekyllCore
    TopicCardInc -->|include| JekyllCore
    ThoughtsInc -->|include| JekyllCore
    ColorsData -->|data| JekyllCore
    SocialData -->|data| JekyllCore
    HighlightSCSS -->|styles| JekyllCore
    StylesSCSS -->|styles| JekyllCore

    JekyllCore -->|invokes| Plugin
    Plugin -->|fetch profile & repos| GitHubAPI
    JekyllCore -->|builds site| StaticSite
    StaticSite -->|deploy| GitHubPages

    %% Click Events
    click Gemfile "https://github.com/github/personal-website/tree/master/Gemfile"
    click ConfigYml "https://github.com/github/personal-website/blob/master/_config.yml"
    click Readme "https://github.com/github/personal-website/blob/master/README.md"
    click Index "https://github.com/github/personal-website/blob/master/index.html"
    click Gitignore "https://github.com/github/personal-website/blob/master/.gitignore"
    click Gitattributes "https://github.com/github/personal-website/blob/master/.gitattributes"
    click License "https://github.com/github/personal-website/blob/master/LICENSE.txt"
    click PostMD "https://github.com/github/personal-website/blob/master/_posts/2019-01-29-hello-world.md"
    click DefaultLayout "https://github.com/github/personal-website/blob/master/_layouts/default.html"
    click HomeLayout "https://github.com/github/personal-website/blob/master/_layouts/home.html"
    click PostLayout "https://github.com/github/personal-website/blob/master/_layouts/post.html"
    click HeaderInc "https://github.com/github/personal-website/blob/master/_includes/header.html"
    click FooterInc "https://github.com/github/personal-website/blob/master/_includes/footer.html"
    click MastheadInc "https://github.com/github/personal-website/blob/master/_includes/masthead.html"
    click InterestsInc "https://github.com/github/personal-website/blob/master/_includes/interests.html"
    click ProjectsInc "https://github.com/github/personal-website/blob/master/_includes/projects.html"
    click RepoCardInc "https://github.com/github/personal-website/blob/master/_includes/repo-card.html"
    click PostCardInc "https://github.com/github/personal-website/blob/master/_includes/post-card.html"
    click TopicCardInc "https://github.com/github/personal-website/blob/master/_includes/topic-card.html"
    click ThoughtsInc "https://github.com/github/personal-website/blob/master/_includes/thoughts.html"
    click ColorsData "https://github.com/github/personal-website/blob/master/_data/colors.json"
    click SocialData "https://github.com/github/personal-website/blob/master/_data/social_media.yml"
    click HighlightSCSS "https://github.com/github/personal-website/blob/master/_sass/_highlight-syntax.scss"
    click StylesSCSS "https://github.com/github/personal-website/blob/master/assets/styles.scss"
    click StaticSite "https://github.com/github/personal-website/tree/master/_site/"

    %% Styles
    classDef dev fill:#D6EAF8,stroke:#21618C,stroke-width:1px;
    classDef build fill:#D5F5E3,stroke:#196F3D,stroke-width:1px;
    classDef external fill:#FDEBD0,stroke:#B9770E,stroke-width:1px;
    classDef hosting fill:#E8DAEF,stroke:#6C3483,stroke-width:1px;
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