---
created: 2025-06-27 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/grpc/proposal
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExejYxenp0MGtkbGlyanpxZXg0Njk3MWJmNXVkMnQ1bzI1eTJtandtNiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/ejJdvF43YlAbR7nUxx/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# proposal repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for 👨‍🎓 <ins>educational purposes</ins> 👨‍🎓 (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), 📖 <ins> personal study </ins> 📖, and 🔖 <ins> reference </ins> 🔖.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>



----

```mermaid
---
title: "proposal repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
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
flowchart LR
    %% Personas
    Developer["Developer"]:::contributor
    Approver["Approver (Approver ‘a11r’, etc.)"]:::approver
    Forum(("grpc-io Forum")):::forum

    %% Repository and Contents
    subgraph "grpc-rfcs GitHub Repo"
        direction TB
        RepoMain["grpc-rfcs GitHub Repo"]:::repo

        subgraph "Governance Documents"
            GOV["GOVERNANCE.md"]:::repo
            COC["CODE-OF-CONDUCT.md"]:::repo
        end

        subgraph "Contribution Guidelines & Process Docs"
            RD["README.md"]:::repo
            RT["GRFC-TEMPLATE.md"]:::repo
        end

        subgraph "Cross-Language Design Proposals (A*)"
            AFiles["A*.md files"]:::repo
            AGraphics["A*_graphics/"]:::repo
        end

        subgraph "Protocol-Level Changes (G*)"
            G1["G1-true-binary-metadata.md"]:::repo
            G2["G2-http3-protocol.md"]:::repo
        end

        subgraph "Language-Specific API Changes (L*)"
            LFiles["L*.md files"]:::repo
            LGraphics["L*_graphics/"]:::repo
        end

        subgraph "Process Proposals (P*)"
            P1["P1-cloud-native.md"]:::repo
            P3["P3-grfcs-for-core-api-changes.md"]:::repo
            P4["P4-grpc-cve-process.md"]:::repo
            P5["P5-jdk-version-support.md"]:::repo
            P6["P6-grpc-io-announce.md"]:::repo
        end
    end

    %% Process Flow
    Developer -->|"fork & clone"| RepoMain
    Developer -->|"draft RFC & submit PR"| PR["Pull Request"]:::repo
    PR -->|"review"| Approver
    PR -->|"discussion"| Forum
    Approver -->|"approve & merge"| RepoMain

    %% Click Events
    click RepoMain "https://github.com/grpc/proposal/tree/master//"
    click GOV "https://github.com/grpc/proposal/blob/master/GOVERNANCE.md"
    click COC "https://github.com/grpc/proposal/blob/master/CODE-OF-CONDUCT.md"
    click RD "https://github.com/grpc/proposal/blob/master/README.md"
    click RT "https://github.com/grpc/proposal/blob/master/GRFC-TEMPLATE.md"
    click AFiles "https://github.com/grpc/proposal/tree/master//"
    click AGraphics "https://github.com/grpc/proposal/tree/master/A14_graphics/"
    click G1 "https://github.com/grpc/proposal/blob/master/G1-true-binary-metadata.md"
    click G2 "https://github.com/grpc/proposal/blob/master/G2-http3-protocol.md"
    click LFiles "https://github.com/grpc/proposal/tree/master//"
    click LGraphics "https://github.com/grpc/proposal/tree/master/L38_graphics/"
    click P1 "https://github.com/grpc/proposal/blob/master/P1-cloud-native.md"
    click P3 "https://github.com/grpc/proposal/blob/master/P3-grfcs-for-core-api-changes.md"
    click P4 "https://github.com/grpc/proposal/blob/master/P4-grpc-cve-process.md"
    click P5 "https://github.com/grpc/proposal/blob/master/P5-jdk-version-support.md"
    click P6 "https://github.com/grpc/proposal/blob/master/P6-grpc-io-announce.md"

    %% Styles
    classDef contributor fill:#ADD8E6,stroke:#000,color:#000
    classDef approver fill:#90EE90,stroke:#000,color:#000
    classDef repo fill:#D3D3D3,stroke:#000,color:#000
    classDef forum fill:#FFD700,stroke:#000,color:#000

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
