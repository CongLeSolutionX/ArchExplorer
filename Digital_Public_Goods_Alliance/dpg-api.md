---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/DPGAlliance/dpg-api
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




# dpg-api repo project
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
title: "dpg-api repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright © 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'linear'},
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#22BB',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EEF2',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '15px'
    }
  }
}%%
flowchart TD
    %% Repositories
    subgraph "Repositories"
        A["Source Repo<br/>(DPGAlliance/publicgoods-candidates)"]:::repo
        B["API Repo<br/>(api.digitalpublicgoods.net)"]:::repo
    end

    %% CI/CD Process
    A -->|"on push to main"| GHA["GitHub Actions<br/>(generation script)"]:::process
    GHA -->|"push generated JSON"| B

    %% API Repo File Structure
    subgraph "API Repo Files"
        C["docs/ (JSON Artifacts)"]:::artifact
        D["CNAME"]:::config
        E["README.md"]:::doc
        F["LICENSE"]:::doc
        H["CODE_OF_CONDUCT.md"]:::doc
        I[".gitignore"]:::doc
    end

    %% JSON Endpoints inside docs/
    %% C --> 
    subgraph "JSON Endpoints"
        C1["docs/dpg/"]:::artifact
        C2["docs/dpgs/index.json"]:::artifact
        C3["docs/nominee/"]:::artifact
        C4["docs/nominees/index.json"]:::artifact
    end

    %% Hosting and Clients
    B -->|"deploy via Pages"| GHP["GitHub Pages<br/>(static hosting)"]:::host
    GHP -->|"HTTPS GET"| Client["Client Applications"]:::client

    %% Click Events
    click C "https://github.com/dpgalliance/dpg-api/tree/main/docs/"
    click C1 "https://github.com/dpgalliance/dpg-api/tree/main/docs/dpg/"
    click C2 "https://github.com/dpgalliance/dpg-api/blob/main/docs/dpgs/index.json"
    click C3 "https://github.com/dpgalliance/dpg-api/tree/main/docs/nominee/"
    click C4 "https://github.com/dpgalliance/dpg-api/blob/main/docs/nominees/index.json"
    click D "https://github.com/dpgalliance/dpg-api/tree/main/CNAME"
    click E "https://github.com/dpgalliance/dpg-api/blob/main/README.md"
    click F "https://github.com/dpgalliance/dpg-api/tree/main/LICENSE"
    click H "https://github.com/dpgalliance/dpg-api/blob/main/CODE_OF_CONDUCT.md"
    click I "https://github.com/dpgalliance/dpg-api/blob/main/.gitignore"

    %% Styles
    classDef repo fill:#DAE8FC,stroke:#6C8EBF,stroke-width:1px
    classDef process fill:#F8CECC,stroke:#B85450,stroke-width:1px
    classDef artifact fill:#D5E8D4,stroke:#82B366,stroke-width:1px
    classDef config fill:#FFF2CC,stroke:#D6B656,stroke-width:1px
    classDef doc fill:#E1D5E7,stroke:#9673A6,stroke-width:1px
    classDef host fill:#E1E1E1,stroke:#999999,stroke-width:1px
    classDef client fill:#F2F2F2,stroke:#666666,stroke-width:1px

```

----


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