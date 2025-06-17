---
created: 2025-06-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/github/choosealicense.com
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


# choosealicense.com repo project
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
title: "choosealicense.com repo project"
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
    'flowchart': { 'htmlLabels': true, 'curve': 'natural' },
    'fontFamily': 'Fantasy, Impact',
    'logLevel': 'fatal',
    'themeVariables': {
      'primaryColor': '#22BB',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#E2F1',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '25px'
    }
  }
}%%
flowchart LR
    subgraph Data_Content_Layer["Data & Content Layer"]
    direction TB
    style Data_Content_Layer fill:#ccf2,stroke:#007bff,color:#004085
      
      subgraph Markdown_Pages["Markdown Pages"]
      direction TB
      style Markdown_Pages fill:#2A22,stroke:#72f,color:#FFFF
        page404["404.md"]:::data
        about["about.md"]:::data
        appendix["appendix.md"]:::data
        community["community.md"]:::data
        index["index.html"]:::data
        licensesPage["licenses.html"]:::data
        noPermission["no-permission.md"]:::data
        nonSoftware["non-software.md"]:::data
        robots["robots.txt"]:::data
        terms["terms-of-service.md"]:::data
      end

      licenseCollection["_licenses/*.txt"]:::data
      structuredFields["_data/fields.yml"]:::data
      structuredRules["_data/rules.yml"]:::data
      structuredMeta["_data/meta.yml"]:::data
    end

    subgraph Templating_Layer["Templating Layer"]
    direction TB
    style Templating_Layer fill:#92A2,stroke:#72f,color:#FFFF
      JekyllEngine["Jekyll Engine (Ruby)"]:::processing
      
      subgraph Layouts["Layouts"]
      direction TB
      style Layouts fill:#22BB,stroke:#72f,color:#FFFF
        layoutDefault["default.html"]:::processing
        layoutLicense["license.html"]:::processing
      end

      subgraph Includes["Includes<br/>(Partials)"]
      direction TB
      style Includes fill:#BFF2,stroke:#72f,color:#FFFF
        incHeader["header.html"]:::processing
        incFooter["footer.html"]:::processing
        incSidebar["sidebar.html"]:::processing
        incBreadcrumbs["breadcrumbs.html"]:::processing
        incOverview["license-overview.html"]:::processing
        incUsing["using-sentence.html"]:::processing
        incCss["responsive.css"]:::processing
      end
    end

    subgraph Asset_Pipeline["Asset Pipeline"]
    direction TB
    style Asset_Pipeline fill:#FA22,stroke:#72f,color:#FFFF
      sass["application.scss"]:::processing
      coffee["app.coffee"]:::processing
      vendor["assets/vendor"]:::processing
      bowerJson["bower.json"]:::processing
      bowerrc[".bowerrc"]:::processing
    end

    subgraph Build_and_CI_Layer["Build & CI Layer"]
    direction TB
    style Build_and_CI_Layer fill:#A922,stroke:#72f,color:#FFFF
      bootstrap["script/bootstrap"]:::ci
      server["script/server"]:::ci
      genDocs["script/generate-docs"]:::ci
      ciBuild["script/cibuild"]:::ci
      checkApproval["script/check-approval"]:::ci
      rspec["spec/license_meta_spec.rb"]:::ci
      workflow[".github/workflows/test.yml"]:::ci
    end

    %% Deployment & Hosting
    staticSite["_site"]:::output
    hosting["GitHub Pages"]:::output
    external["Licensee & GitHub API"]:::external
    users["End Users<br/>(Browser)"]:::external

    %% Connections
    page404 & about & appendix & community & index & licensesPage & noPermission & nonSoftware & robots & terms & licenseCollection & structuredFields & structuredRules & structuredMeta -->|build input| JekyllEngine
    sass & coffee & vendor -->|assets| JekyllEngine
    layoutDefault & layoutLicense & incHeader & incFooter & incSidebar & incBreadcrumbs & incOverview & incUsing & incCss -->|templates| JekyllEngine
    bootstrap & workflow -->|trigger build| JekyllEngine
    server -->|serve| JekyllEngine
    JekyllEngine -->|generate| staticSite
    staticSite -->|deploy| hosting
    hosting -->|serve| users
    staticSite -->|vendored static| external
    page404 & about & appendix & community & index & licensesPage & noPermission & nonSoftware & robots & terms & licenseCollection & structuredFields & structuredRules & structuredMeta -->|validate| rspec

    %% Click Events
    click page404 "https://github.com/github/choosealicense.com/blob/gh-pages//404.md"
    click about "https://github.com/github/choosealicense.com/blob/gh-pages//about.md"
    click appendix "https://github.com/github/choosealicense.com/blob/gh-pages//appendix.md"
    click community "https://github.com/github/choosealicense.com/blob/gh-pages//community.md"
    click index "https://github.com/github/choosealicense.com/blob/gh-pages//index.html"
    click licensesPage "https://github.com/github/choosealicense.com/blob/gh-pages//licenses.html"
    click noPermission "https://github.com/github/choosealicense.com/blob/gh-pages//no-permission.md"
    click nonSoftware "https://github.com/github/choosealicense.com/blob/gh-pages//non-software.md"
    click robots "https://github.com/github/choosealicense.com/blob/gh-pages//robots.txt"
    click terms "https://github.com/github/choosealicense.com/blob/gh-pages//terms-of-service.md"
    click licenseCollection "https://github.com/github/choosealicense.com/blob/gh-pages//_licenses/*.txt"
    click structuredFields "https://github.com/github/choosealicense.com/blob/gh-pages//_data/fields.yml"
    click structuredRules "https://github.com/github/choosealicense.com/blob/gh-pages//_data/rules.yml"
    click structuredMeta "https://github.com/github/choosealicense.com/blob/gh-pages//_data/meta.yml"
    click layoutDefault "https://github.com/github/choosealicense.com/blob/gh-pages//_layouts/default.html"
    click layoutLicense "https://github.com/github/choosealicense.com/blob/gh-pages//_layouts/license.html"
    click incHeader "https://github.com/github/choosealicense.com/blob/gh-pages//_includes/header.html"
    click incFooter "https://github.com/github/choosealicense.com/blob/gh-pages//_includes/footer.html"
    click incSidebar "https://github.com/github/choosealicense.com/blob/gh-pages//_includes/sidebar.html"
    click incBreadcrumbs "https://github.com/github/choosealicense.com/blob/gh-pages//_includes/breadcrumbs.html"
    click incOverview "https://github.com/github/choosealicense.com/blob/gh-pages//_includes/license-overview.html"
    click incUsing "https://github.com/github/choosealicense.com/blob/gh-pages//_includes/using-sentence.html"
    click incCss "https://github.com/github/choosealicense.com/blob/gh-pages//_includes/css/responsive.css"
    click sass "https://github.com/github/choosealicense.com/blob/gh-pages//assets/css/application.scss"
    click coffee "https://github.com/github/choosealicense.com/blob/gh-pages//assets/js/app.coffee"
    click vendor "https://github.com/github/choosealicense.com/tree/gh-pages//assets/vendor"
    click bowerJson "https://github.com/github/choosealicense.com/blob/gh-pages//bower.json"
    click bowerrc "https://github.com/github/choosealicense.com/blob/gh-pages//.bowerrc"
    click bootstrap "https://github.com/github/choosealicense.com/tree/gh-pages//script/bootstrap"
    click server "https://github.com/github/choosealicense.com/tree/gh-pages//script/server"
    click genDocs "https://github.com/github/choosealicense.com/tree/gh-pages//script/generate-docs"
    click ciBuild "https://github.com/github/choosealicense.com/tree/gh-pages//script/cibuild"
    click checkApproval "https://github.com/github/choosealicense.com/tree/gh-pages//script/check-approval"
    click rspec "https://github.com/github/choosealicense.com/blob/gh-pages/spec/license_meta_spec.rb"
    click workflow "https://github.com/github/choosealicense.com/blob/gh-pages//.github/workflows/test.yml"

    %% Styles
    classDef data fill:#c222,stroke:#007bff,color:#28a745
    classDef processing fill:#dda2,stroke:#28a745,color:#F33F
    classDef ci fill:#fFA2,stroke:#ffc107,color:#ffc107
    classDef output fill:#e352,stroke:#6c757d,color:#b366ff
    classDef external fill:#fE12,stroke:#b366ff,color:#A569BD
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
