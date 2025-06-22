---
created: 2025-06-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/usgpo/collections
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




# collections repo project
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


---

```mermaid
---
title: "collections repo project"
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
    %% Actors
    Dev["Developer"]:::user
    EndUser["End User<br/>(Integrators)"]:::user

    %% Repository Layer
    subgraph "GitHub Repository" 
        direction TB
        Repo["Repository"]:::repo
        subgraph "Root Files"
            direction TB
            README["README.md"]:::code
            CONTRIBUTING["CONTRIBUTING.md"]:::code
            CODEOWNERS["CODEOWNERS"]:::code
            LICENSE["LICENSE.md"]:::code
        end
        subgraph "Documentation Modules"
            direction TB
            subgraph "CHRG Collection"
                direction TB
                CHRG_MD["CHRG-Metadata.md"]:::docs
                CHRG_RE["CHRG-RegEx.md"]:::docs
                subgraph "pdf/"
                    direction TB
                    CHRG_MD_PDF["CHRG-Metadata.pdf"]:::artifact
                    CHRG_RE_PDF["CHRG-RegEx.pdf"]:::artifact
                end
            end
        end
    end

    %% CI/CD Pipeline
    CICD["CI/CD Pipeline<br/>(GitHub Actions)"]:::build

    %% Generated Artifacts
    subgraph "Build Artifacts"
        direction TB
        Site["Static Site (HTML)"]:::artifact
        PDFs["Collection PDFs"]:::artifact
    end

    %% Hosting
    Hosting["GitHub Pages"]:::hosting

    %% Flows
    Dev -->|"push/pr"| Repo
    Repo -->|"trigger build"| CICD
    CICD -->|"generate"| Site
    CICD -->|"generate"| PDFs
    Site -->|"deploy"| Hosting
    PDFs -->|"deploy"| Hosting
    EndUser -->|"access docs"| Hosting

    %% Click Events
    click README "https://github.com/usgpo/collections/blob/master/README.md"
    click CONTRIBUTING "https://github.com/usgpo/collections/blob/master/CONTRIBUTING.md"
    click CODEOWNERS "https://github.com/usgpo/collections/tree/master/CODEOWNERS"
    click LICENSE "https://github.com/usgpo/collections/blob/master/LICENSE.md"
    click CHRG_MD "https://github.com/usgpo/collections/blob/master/CHRG/CHRG-Metadata.md"
    click CHRG_RE "https://github.com/usgpo/collections/blob/master/CHRG/CHRG-RegEx.md"
    click CHRG_MD_PDF "https://github.com/usgpo/collections/blob/master/CHRG/pdf/CHRG-Metadata.pdf"
    click CHRG_RE_PDF "https://github.com/usgpo/collections/blob/master/CHRG/pdf/CHRG-RegEx.pdf"

    %% Styles
    classDef repo fill:#f0f8ff,stroke:#0366d6,stroke-width:2px
    classDef code fill:#fff5b1,stroke:#d4a017,stroke-width:1px
    classDef docs fill:#e3fcef,stroke:#1b7b1b,stroke-width:1px
    classDef build fill:#fff0f6,stroke:#d63384,stroke-width:2px
    classDef artifact fill:#e7f5ff,stroke:#1c7ed6,stroke-width:1px
    classDef hosting fill:#f0f5ff,stroke:#4263eb,stroke-width:2px
    classDef user fill:#fffbeb,stroke:#f08c00,stroke-width:1px,stroke-dasharray: 5 5
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