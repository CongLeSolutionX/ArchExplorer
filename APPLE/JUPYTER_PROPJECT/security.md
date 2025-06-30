---
created: 2025-06-29 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/jupyter/security
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExZnhlc2FvOWU5b2IxNno3M2xla3JuMW1tMDA0MnFndWo3ZWg3aDN1cyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/QjBgJRiftlaGhGn9wE/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# security repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for 👨‍🎓 <ins>educational purposes</ins> 👨‍🎓 (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), 📖 <ins> personal study </ins> 📖, and 🔖 <ins> technical reference </ins> 🔖.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>



---

```mermaid
---
title: "security repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright © 2025 Cong Le. All Rights Reserved."
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
    %% External Services
    github["GitHub API"]:::external
    onepass["1Password"]:::external
    jssc["Jupyter SSC"]:::external

    %% CI/CD Orchestration
    subgraph "CI/CD Pipeline" 
        style CI_CD stroke-dasharray: 5 5
        CI_CD["CI/CD (GitHub Actions)"]:::ci
    end

    %% Repository Structure
    subgraph "Repository (Central Hub)"
        direction TB
        docs["docs/"]:::code
        meetings["meetings/"]:::code
        tools_dir["tools/"]:::code
        json["last_user_activity.json"]:::data
        readme["README.md"]:::code
        ignore1["private_sec_ignore.txt"]:::code
        ignore2["psc_ignore.txt"]:::code
    end

    %% Automation Tools
    subgraph "tools/"
        direction TB
        allrepos["all_repos.py"]:::code
        lastupdate["last_user_activity.py"]:::code
        privsec_report["private-sec-reporting.py"]:::code
        privsec_alt["private_sec_report.py"]:::code
        tide["tide.py"]:::code
    end

    %% Docs Build and Hosting
    docsbuild["Docs Build (Sphinx)"]:::code
    hosting["Hosting (jupyter.org)"]:::external

    %% Flows: CI/CD triggers tools and docs build
    CI_CD -->|runs| allrepos
    CI_CD -->|runs| lastupdate
    CI_CD -->|runs| privsec_report
    CI_CD -->|runs| privsec_alt
    CI_CD -->|runs| tide
    CI_CD -->|triggers| docsbuild

    %% External Services to Tools
    github --> allrepos
    github --> tide
    onepass --> privsec_report
    onepass --> privsec_alt
    jssc --> tide

    %% Tools output to Data Store
    allrepos --> json
    lastupdate --> json
    privsec_report --> json
    privsec_alt --> json
    tide --> json

    %% Data Store commits back to Repository
    json -->|commit updates| docsbuild
    json -->|persist| docsbuild

    %% Docs Build pipeline sources
    docs --> docsbuild
    meetings --> docsbuild
    json --> docsbuild

    %% Docs Build to Hosting
    docsbuild -->|deploy| hosting

    %% Click Events
    click docs "https://github.com/jupyter/security/tree/main/docs/"
    click meetings "https://github.com/jupyter/security/tree/main/meetings/"
    click tools_dir "https://github.com/jupyter/security/tree/main/tools/"
    click allrepos "https://github.com/jupyter/security/blob/main/tools/all_repos.py"
    click lastupdate "https://github.com/jupyter/security/blob/main/tools/last_user_activity.py"
    click privsec_report "https://github.com/jupyter/security/blob/main/tools/private-sec-reporting.py"
    click privsec_alt "https://github.com/jupyter/security/blob/main/tools/private_sec_report.py"
    click tide "https://github.com/jupyter/security/blob/main/tools/tide.py"
    click json "https://github.com/jupyter/security/blob/main/last_user_activity.json"
    click readme "https://github.com/jupyter/security/blob/main/README.md"
    click ignore1 "https://github.com/jupyter/security/blob/main/private_sec_ignore.txt"
    click ignore2 "https://github.com/jupyter/security/blob/main/psc_ignore.txt"

    %% Styles
    classDef code fill:#E0F7FA,stroke:#006064,color:#006064;
    classDef data fill:#E8F5E9,stroke:#2E7D32,color:#2E7D32;
    classDef external fill:#FFF3E0,stroke:#EF6C00,color:#EF6C00;
    classDef ci fill:none,stroke:#9E9E9E,color:#616161,stroke-dasharray: 5 5;

```

---

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
