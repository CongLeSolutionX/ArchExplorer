---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/DPGAlliance/publicgoods-form-opens-pr
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




# publicgoods-form-opens-pr repo project
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
title: "publicgoods-form-opens-pr repo project"
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
flowchart TB
    %% Components
    Form["User Browser / Google Form"]:::cloud
    Sheets["Google Sheets (Response Store)"]:::db
    subgraph "Serverless Apps Script" 
        Apps["Apps Script Runtime\n(getHead, createBranch, commitFile, openPR)"]:::function
    end
    GitAPI["GitHub REST API"]:::external
    Repo["GitHub Repo\nDPGAlliance/publicgoods-candidates"]:::external
    Local["Local Node.js Env (Optional)"]:::optional

    %% Data Flow
    Form -->|Submits Form Data| Sheets
    Sheets -->|Trigger: onFormSubmit| Apps
    Apps -->|1: fetch master ref| GitAPI
    GitAPI -->|ref data| Apps
    Apps -->|2: create branch| GitAPI
    GitAPI -->|branch info| Apps
    Apps -->|3: commit JSON file| GitAPI
    GitAPI -->|commit sha| Apps
    Apps -->|4: open pull request| GitAPI
    GitAPI -->|PR created| Repo
    Local -.->|mirrors logic for dev/testing| Apps

    %% Click Events
    click Apps "https://github.com/dpgalliance/publicgoods-form-opens-pr/blob/main/code.gs"
    click Local "https://github.com/dpgalliance/publicgoods-form-opens-pr/blob/main/index.js"
    click package "https://github.com/dpgalliance/publicgoods-form-opens-pr/blob/main/package.json"
    click packlock "https://github.com/dpgalliance/publicgoods-form-opens-pr/blob/main/package-lock.json"
    click readme "https://github.com/dpgalliance/publicgoods-form-opens-pr/blob/main/README.md"
    click license "https://github.com/dpgalliance/publicgoods-form-opens-pr/tree/main/LICENSE"
    click gitignore "https://github.com/dpgalliance/publicgoods-form-opens-pr/blob/main/.gitignore"

    %% Legend
    subgraph "Legend"
        LC["Cloud Component"]:::cloud
        DB["Data Store"]:::db
        FN["Serverless Function"]:::function
        EX["External Service/Repo"]:::external
        OP["Optional / Dev"]:::optional
    end

    %% Styles
    classDef cloud fill:#bbdefb,stroke:#1e88e5,stroke-width:2px
    classDef db fill:#b3e5fc,stroke:#0288d1,stroke-width:2px
    classDef function fill:#c8e6c9,stroke:#388e3c,stroke-width:2px
    classDef external fill:#e0e0e0,stroke:#757575,stroke-width:2px
    classDef optional fill:#ffffff,stroke:#9e9e9e,stroke-width:2px,stroke-dasharray: 5 5
    class Form,LC cloud
    class Sheets,DB db
    class Apps,FN function
    class GitAPI,Repo,EX external
    class Local,OP optional

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