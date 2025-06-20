---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/VSCodium/versions
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExbjFnamh5cW90bzFsazV6ZDZ4MjZ1ZzgwYnQ2YjRocGtxOXc4bDQ1eCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/kl5ctZSctCbE4/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# versions repo project
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
title: "versions repo project"
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
      'secondaryColor': '#6483',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '20px'
    }
  }
}%%
flowchart TD
    %% Storage Layer
    subgraph STORAGE["Version Metadata Storage"]
    style STORAGE fill:#F2F2,stroke:#333,stroke-width:1px, color: #FFFF
        subgraph INSIDER["insider/"]
        style INSIDER fill:#22F2,stroke:#333,stroke-width:1px, color: #FFFF
            subgraph INS_LINUX["linux"]
            style INS_LINUX fill:#FF22,stroke:#333,stroke-width:1px, color: #FFFF
                IL_X64["x64/latest.json"]:::storage
                IL_ARM64["arm64/latest.json"]:::storage
            end
            subgraph INS_DARWIN["darwin"]
            style INS_DARWIN fill:#F2B5,stroke:#333,stroke-width:1px, color: #FFFF
                ID_X64["x64/latest.json"]:::storage
                ID_ARM64["arm64/latest.json"]:::storage
            end
            subgraph INS_WIN32["win32"]
            style INS_WIN32 fill:#22B5,stroke:#333,stroke-width:1px, color: #FFFF
                IW_X64["x64/latest.json"]:::storage
                IW_IA32["ia32/latest.json"]:::storage
            end
        end
        subgraph STABLE["stable/"]
        style STABLE fill:#2DB5,stroke:#333,stroke-width:1px, color: #FFFF
            subgraph ST_LINUX["linux"]
            style ST_LINUX fill:#FF22,stroke:#333,stroke-width:1px, color: #FFFF
                SL_X64["x64/latest.json"]:::storage
                SL_ARM64["arm64/latest.json"]:::storage
            end
            subgraph ST_DARWIN["darwin"]
            style ST_DARWIN fill:#F2B5,stroke:#333,stroke-width:1px, color: #FFFF
                SD_X64["x64/latest.json"]:::storage
            end
            subgraph ST_WIN32["win32"]
            style ST_WIN32 fill:#22B5,stroke:#333,stroke-width:1px, color: #FFFF
                SW_X64["x64/latest.json"]:::storage
            end
        end
    end

    %% Validation Layer
    subgraph VALIDATION["Validation Layer"]
    style VALIDATION fill:#2B25,stroke:#333,stroke-width:1px, color: #FFFF
        INTEGRITY["Integrity Utility<br/>(integrity.js)"]:::validation
    end

    %% CI/CD Pipeline
    CI_CD["CI/CD Pipeline"]:::ci
    PACKAGE["package.json"]:::ci

    %% Service/API Layer
    subgraph SERVICE["Service/API Layer"]
    style SERVICE fill:#B225,stroke:#333,stroke-width:1px, color: #FFFF
        API["Update Service API"]:::service
    end

    %% CDN Layer
    CDN["CDN /<br/> Edge Cache"]:::cdn

    %% Client
    CLIENT["Client<br/>(Electron App / Installer)"]:::client

    %% Connections
    CI_CD -->|deploy JSON| INSIDER
    CI_CD -->|deploy JSON| STABLE
    INSIDER -.->|validate| INTEGRITY
    STABLE -.->|validate| INTEGRITY
    INTEGRITY -->|write-back| INSIDER
    INTEGRITY -->|write-back| STABLE
    PACKAGE -->|defines scripts & deps| INTEGRITY
    INSIDER -->|read metadata| API
    STABLE -->|read metadata| API
    API -->|serve JSON| CDN
    CLIENT -->|fetch metadata| CDN
    CLIENT -->|fallback fetch| API

    %% Click Events
    click INSIDER "https://github.com/vscodium/versions/tree/master/insider/"
    click STABLE "https://github.com/vscodium/versions/tree/master/stable/"
    click INTEGRITY "https://github.com/vscodium/versions/blob/master/integrity.js"
    click PACKAGE "https://github.com/vscodium/versions/blob/master/package.json"

    %% Styles
    classDef storage fill:#D0FF,stroke:#0366d6,color:#FFFF
    classDef validation fill:#CFACC,stroke:#2c662d,color:#FFFF
    classDef service fill:#F2B8,stroke:#d97706,color:#FFFF
    classDef cdn fill:#E2FF,stroke:#6b21a8,color:#FFFF
    classDef client fill:#FB22,stroke:#374151,color:#FFFF
    classDef ci fill:#FBB2,stroke:#b91c1c,color:#b91c1c

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
