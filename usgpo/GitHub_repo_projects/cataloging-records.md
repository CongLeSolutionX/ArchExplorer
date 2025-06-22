---
created: 2025-06-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/usgpo/cataloging-records
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExMnlyczdqa2hwemJ5NDdudGpianNvYnlhYTN4bzN3aW8xM3g2MXhodiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/EYqGrbF2DG0mc/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# cataloging-records repo project
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
title: "cataloging-records repo project"
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
    %% External Data Source
    CGP["CGP Catalog<br/>(external)"]:::external

    %% Processing Pipeline
    Pipeline["Ingestion Pipeline<br/>(scripts/tools)"]:::pipeline

    %% GitHub Repository Storage
    subgraph GitHub_Repository["GitHub Repository"]
    style GitHub_Repository fill:#F2F2,stroke:#333,stroke-width:1px, color: #FFFF
        Repo_README["README.md"] 
        Repo_Images["images/"]
        subgraph Collections["Collections"]
        style Collections fill:#2B2B,stroke:#333,stroke-width:1px, color: #FFFF
            C1["1950_Census_Collection"]
            C2["AIANNH_Subject-Based-Resources"]
            C3["Artificial_Intelligence_Subject-Based-Resources"]
            C4["COVID-19_Coronavirus"]
            C5["Congressional_Research_Service_Reports"]
            C6["Department_of_Transportation"]
            C7["HBCU_Subject-Based-Resources"]
            C8["Jan6_Committee"]
            C9["Law_Library_Congress"]
            C10["Legal_Publications_Collection"]
            C11["NIST_Collection"]
            C12["Online_FDLP_Basic_Collection"]
            C13["SPOT_Records"]
            C14["Updating_Databases"]
        end
    end

    %% Consumers
    Users["End-Users<br/>(clone/pull/download)"]:::consumer

    %% Data Flow
    CGP -->|"HTTP pull"| Pipeline
    Pipeline -->|"git push"| Repo_README
    Pipeline -->|"git push"| Repo_Images
    Pipeline -->|"git push"| C1
    Pipeline -->|"git push"| C2
    Pipeline -->|"git push"| C3
    Pipeline -->|"git push"| C4
    Pipeline -->|"git push"| C5
    Pipeline -->|"git push"| C6
    Pipeline -->|"git push"| C7
    Pipeline -->|"git push"| C8
    Pipeline -->|"git push"| C9
    Pipeline -->|"git push"| C10
    Pipeline -->|"git push"| C11
    Pipeline -->|"git push"| C12
    Pipeline -->|"git push"| C13
    Pipeline -->|"git push"| C14
    
    Repo_README -->|version control| Repo_README
    Repo_Images -->|version control| Repo_Images
    
    C1 -->|version control| C1
    C2 -->|version control| C2
    C3 -->|version control| C3
    C4 -->|version control| C4
    C5 -->|version control| C5
    C6 -->|version control| C6
    C7 -->|version control| C7
    C8 -->|version control| C8
    C9 -->|version control| C9
    C10 -->|version control| C10
    C11 -->|version control| C11
    C12 -->|version control| C12
    C13 -->|version control| C13
    C14 -->|version control| C14
    
    Repo_README -->|"git clone/ZIP"| Users
    Repo_Images -->|"git clone/ZIP"| Users
    
    C1 -->|"git clone/ZIP"| Users
    C2 -->|"git clone/ZIP"| Users
    C3 -->|"git clone/ZIP"| Users
    C4 -->|"git clone/ZIP"| Users
    C5 -->|"git clone/ZIP"| Users
    C6 -->|"git clone/ZIP"| Users
    C7 -->|"git clone/ZIP"| Users
    C8 -->|"git clone/ZIP"| Users
    C9 -->|"git clone/ZIP"| Users
    C10 -->|"git clone/ZIP"| Users
    C11 -->|"git clone/ZIP"| Users
    C12 -->|"git clone/ZIP"| Users
    C13 -->|"git clone/ZIP"| Users
    C14 -->|"git clone/ZIP"| Users

    %% Click Events
    click Repo_README "https://github.com/usgpo/cataloging-records/blob/main/README.md"
    click Repo_Images "https://github.com/usgpo/cataloging-records/tree/main/images/"
    click C1 "https://github.com/usgpo/cataloging-records/tree/main/1950_Census_Collection"
    click C2 "https://github.com/usgpo/cataloging-records/tree/main/AIANNH_Subject-Based-Resources"
    click C3 "https://github.com/usgpo/cataloging-records/tree/main/Artificial_Intelligence_Subject-Based-Resources"
    click C4 "https://github.com/usgpo/cataloging-records/tree/main/COVID-19_Coronavirus"
    click C5 "https://github.com/usgpo/cataloging-records/tree/main/Congressional_Research_Service_Reports"
    click C6 "https://github.com/usgpo/cataloging-records/tree/main/Department_of_Transportation"
    click C7 "https://github.com/usgpo/cataloging-records/tree/main/HBCU_Subject-Based-Resources"
    click C8 "https://github.com/usgpo/cataloging-records/tree/main/Jan6_Committee"
    click C9 "https://github.com/usgpo/cataloging-records/tree/main/Law_Library_Congress"
    click C10 "https://github.com/usgpo/cataloging-records/tree/main/Legal_Publications_Collection"
    click C11 "https://github.com/usgpo/cataloging-records/tree/main/NIST_Collection"
    click C12 "https://github.com/usgpo/cataloging-records/tree/main/Online_FDLP_Basic_Collection"
    click C13 "https://github.com/usgpo/cataloging-records/tree/main/SPOT_Records"
    click C14 "https://github.com/usgpo/cataloging-records/tree/main/Updating_Databases"

    %% Styles
    classDef external fill:#c2ff,stroke:#4aa3df,stroke-width:2px
    classDef pipeline fill:#ed22,stroke:#28a745,stroke-width:2px
    classDef storage fill:#f5b4,stroke:#ff9f00,stroke-width:2px
    classDef consumer fill:#f222,stroke:#ffcd39,stroke-width:2px

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
