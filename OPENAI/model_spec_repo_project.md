---
created: 2025-06-12 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/model_spec
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExMHkxZzEyaXV2YXZ5Mnl4eHljYWl0am11bnR0OWkyOXJkdWFpM3JleiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/S0hxMGYFhEMzm/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# model_spec repo project
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
title: "model_spec repo project"
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
    %% Developer Environment
    subgraph "Developer Environment"
        modelSpec["model_spec.md"]:::content
        examples["examples/"]:::content
        README["README.md"]:::metadata
        CHANGELOG["CHANGELOG.md"]:::metadata
        LICENSE["LICENSE"]:::metadata
    end

    %% Build Step
    SSG["Static Site Generator"]:::build

    %% Build Artifacts
    subgraph "Build & Artifact"
        docsHTML["docs/ (HTML pages)"]:::artifact
        docsFontsDir["docs/fonts/"]:::artifact
        docsFontsCSS["docs/fonts.gen.css"]:::artifact
        docsCNAME["docs/CNAME"]:::artifact
    end

    %% Hosting & Delivery
    subgraph "Hosting & Delivery"
        GitHubPages["GitHub Pages<br/>model-spec.openai.com"]:::hosting
        EndUser["End User (Browser)"]:::user
    end

    %% Connections
    modelSpec -->|commit & CI triggers| SSG
    examples -->|commit & CI triggers| SSG
    README -->|metadata| SSG
    CHANGELOG -->|metadata| SSG
    LICENSE -->|metadata| SSG

    SSG -->|"generates HTML pages"| docsHTML
    SSG -->|"generates assets"| docsFontsDir
    SSG -->|"generates CSS"| docsFontsCSS
    SSG -->|"creates CNAME"| docsCNAME

    docsHTML -->|"deploy to GitHub Pages"| GitHubPages
    docsFontsDir -->|"deploy to GitHub Pages"| GitHubPages
    docsFontsCSS -->|"deploy to GitHub Pages"| GitHubPages
    docsCNAME -->|"deploy to GitHub Pages"| GitHubPages

    GitHubPages -->|"HTTP GET"| EndUser

    %% Click Events
    click modelSpec "https://github.com/openai/model_spec/blob/main/model_spec.md"
    click examples "https://github.com/openai/model_spec/tree/main/examples/"
    click README "https://github.com/openai/model_spec/blob/main/README.md"
    click CHANGELOG "https://github.com/openai/model_spec/blob/main/CHANGELOG.md"
    click LICENSE "https://github.com/openai/model_spec/tree/main/LICENSE"
    click docsHTML "https://github.com/openai/model_spec/tree/main/docs/"
    click docsFontsDir "https://github.com/openai/model_spec/tree/main/docs/fonts/"
    click docsFontsCSS "https://github.com/openai/model_spec/blob/main/docs/fonts.gen.css"
    click docsCNAME "https://github.com/openai/model_spec/tree/main/docs/CNAME"

    %% Styles
    classDef content fill:#BBDEFB,stroke:#000
    classDef build fill:#FFCC80,stroke:#000
    classDef artifact fill:#C8E6C9,stroke:#000
    classDef hosting fill:#E1BEE7,stroke:#000
    classDef user fill:#F8BBD0,stroke:#000
    classDef metadata fill:#E0E0E0,stroke:#000arine

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
