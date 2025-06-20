---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/VSCodium/vscodium.github.io
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExZDZpZDNteWF3cHI4YmR1dHo1Zm01cm5jZGVrNGE5ZG1yYjQybzBnMCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/kg4gaF4zJr57JfjgkO/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# vscodium.github.io repo project
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
title: "vscodium.github.io repo project"
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
flowchart LR
  subgraph Developer_Environment["Developer Environment"]
  style Developer_Environment fill:#F2F2,stroke:#333,stroke-width:1px, color: #FFFF
    Dev["Developer"]:::dev
    Repo["Git Repository<br/>(GitHub)"]:::dev
    CLI["Jekyll CLI"]:::dev
  end

  subgraph Source_Files["Source Files"]
  style Source_Files fill:#FF22,stroke:#333,stroke-width:1px, color: #FFFF
    Posts["Markdown Posts <br/>(_posts/)"]:::dev
    Includes["Layouts & Includes <br/>(_includes/)"]:::dev
    BaseCSS["base.css"]:::dev
    MainCSS["main.css"]:::dev
    SkelCSS["skeleton.css"]:::dev
    Footer["footer.md"]:::dev
    Index["Home Page (index.html)"]:::dev
    Combo["Bundled Stylesheet <br/>(combo.css)"]:::dev
    SiteJS["Site JavaScript <br/>(site.js)"]:::dev
    Config["Jekyll Configuration <br/>(_config.yml)"]:::config
    CNAME["CNAME"]:::config
    WellKnown["Flatpak Verification <br/>(.well-known/org.flathub.VerifiedApps.txt)"]:::config
    Readme["README.md"]:::dev
    License["LICENSE.txt"]:::dev
  end

  subgraph Build_Output["Build Output"]
  style Build_Output fill:#BB22,stroke:#333,stroke-width:1px, color: #FFFF
    SiteOut["_site/ (Static Files)"]:::storage
  end

  subgraph Hosting_and_Delivery["Hosting & Delivery"]
  style Hosting_and_Delivery fill:#B2F2,stroke:#333,stroke-width:1px, color: #FFFF
    Pages["GitHub Pages /<br/> Webserver"]:::runtime
    Users["End Users<br/>(Browsers)"]:::runtime
  end

  Dev -->|git push| Repo
  Dev -->|jekyll serve| CLI
  Repo -->|CI build| CLI
  Posts -->|jekyll build| CLI
  Includes -->|jekyll build| CLI
  Index -->|jekyll build| CLI
  Combo -->|jekyll build| CLI
  SiteJS -->|jekyll build| CLI
  Config -->|jekyll build| CLI
  CNAME -->|jekyll build| CLI
  WellKnown -->|jekyll build| CLI
  CLI -->|outputs| SiteOut
  SiteOut -->|deploy| Pages
  Pages -->|HTTP GET| Users

  click Config "https://github.com/vscodium/vscodium.github.io/blob/master/_config.yml"
  click Includes "https://github.com/vscodium/vscodium.github.io/tree/master/_includes/"
  click BaseCSS "https://github.com/vscodium/vscodium.github.io/blob/master/_includes/css/base.css"
  click MainCSS "https://github.com/vscodium/vscodium.github.io/blob/master/_includes/css/main.css"
  click SkelCSS "https://github.com/vscodium/vscodium.github.io/blob/master/_includes/css/skeleton.css"
  click Footer "https://github.com/vscodium/vscodium.github.io/blob/master/_includes/footer.md"
  click Posts "https://github.com/vscodium/vscodium.github.io/tree/master/_posts/"
  click Index "https://github.com/vscodium/vscodium.github.io/blob/master/index.html"
  click Combo "https://github.com/vscodium/vscodium.github.io/blob/master/combo.css"
  click SiteJS "https://github.com/vscodium/vscodium.github.io/blob/master/site.js"
  click WellKnown "https://github.com/vscodium/vscodium.github.io/blob/master/.well-known/org.flathub.VerifiedApps.txt"
  click CNAME "https://github.com/vscodium/vscodium.github.io/tree/master/CNAME"
  click Readme "https://github.com/vscodium/vscodium.github.io/blob/master/README.md"
  click License "https://github.com/vscodium/vscodium.github.io/blob/master/LICENSE.txt"

  classDef dev fill:#D0FF,stroke:#0288D1,color:#FFFF
  classDef config fill:#FF25,stroke:#FB8C00,color:#FFFF
  classDef runtime fill:#E229,stroke:#2E7D32,color:#FFFF
  classDef storage fill:#EFF6,stroke:#5E35B1,color:#FFFF

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
