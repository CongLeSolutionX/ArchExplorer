---
created: 2025-06-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/usgpo/house-manual
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




# house-manual repo project
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
title: "house-manual repo project"
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
  %% Data Store: GitHub Repository
  subgraph "GitHub Repository (Data Store)"
    direction TB
    README["README.md"]:::data
    CODEOWNERS["CODEOWNERS"]:::data
    GUIDE_MD["HMAN-XML_User-Guide.md"]:::data
    GUIDE_PDF["HMAN-XML_User-Guide-v1.pdf"]:::data
    subgraph "Congress Content Folders"
      direction TB
      %% Congress folders with govinfo and original
      subgraph "112"
        direction TB
        GOV112["govinfo-file-names/"]:::data
        ORIG112["original-file-names/"]:::data
        GSD112["graphics-support-documents/"]:::data
      end
      subgraph "113"
        direction TB
        GOV113["govinfo-file-names/"]:::data
        ORIG113["original-file-names/"]:::data
        GSD113["graphics-support-documents/"]:::data
      end
      subgraph "114"
        direction TB
        GOV114["govinfo-file-names/"]:::data
        ORIG114["original-file-names/"]:::data
        GSD114["graphics-support-documents/"]:::data
      end
      subgraph "115"
        direction TB
        GOV115["govinfo-file-names/"]:::data
        ORIG115["original-file-names/"]:::data
        GSD115["graphics-support-documents/"]:::data
      end
      subgraph "116"
        direction TB
        GOV116["govinfo-file-names/"]:::data
        ORIG116["original-file-names/"]:::data
        GSD116["graphics-support-documents/"]:::data
      end
      subgraph "117"
        direction TB
        GOV117["govinfo-file-names/"]:::data
        ORIG117["original-file-names/"]:::data
        GSD117["graphics-support-documents/"]:::data
      end
    end
  end

  %% Ingestion Pipeline
  Ingestion["Bulk Data Ingestion Pipeline"]:::process

  %% Bulk Data Store
  BulkStore[(govinfo Bulk Data Store)]:::data

  %% XSLT/CSS Processing
  Processor["XSLT/CSS Processing Engine"]:::process
  Output["HTML Output"]:::external

  %% Consumers
  subgraph "Consumers"
    direction TB
    WebUI["govinfo.gov Web UI"]:::external
    CLI["CLI/3rd-party Apps"]:::external
    Browser["End-user Browser"]:::external
    StaticHost["Static Site Host"]:::external
  end

  %% Data Flows
  GitRepo["GitHub Repository"]:::data
  GitRepo -->|"push"| Ingestion
  Ingestion -->|"publish"| BulkStore
  BulkStore -->|"download raw XML/CSS/XSL"| CLI
  BulkStore -->|"download raw XML/CSS/XSL"| WebUI
  GitRepo -->|"clone"| CLI

  %% Processing Flow
  GSD112 -->|"transform"| Processor
  GSD113 -->|"transform"| Processor
  GSD114 -->|"transform"| Processor
  GSD115 -->|"transform"| Processor
  GSD116 -->|"transform"| Processor
  GSD117 -->|"transform"| Processor
  Processor -->|"generate HTML"| Output
  Output --> Browser
  Output --> StaticHost

  %% Click Events for component mappings
  click README "https://github.com/usgpo/house-manual/blob/main/README.md"
  click CODEOWNERS "https://github.com/usgpo/house-manual/tree/main/CODEOWNERS"
  click GUIDE_MD "https://github.com/usgpo/house-manual/blob/main/HMAN-XML_User-Guide.md"
  click GUIDE_PDF "https://github.com/usgpo/house-manual/blob/main/HMAN-XML_User-Guide-v1.pdf"
  click GOV112 "https://github.com/usgpo/house-manual/tree/main/112/govinfo-file-names/"
  click ORIG112 "https://github.com/usgpo/house-manual/tree/main/112/original-file-names/"
  click GSD112 "https://github.com/usgpo/house-manual/tree/main/112/govinfo-file-names/graphics-support-documents/"
  click GOV113 "https://github.com/usgpo/house-manual/tree/main/113/govinfo-file-names/"
  click ORIG113 "https://github.com/usgpo/house-manual/tree/main/113/original-file-names/"
  click GSD113 "https://github.com/usgpo/house-manual/tree/main/113/govinfo-file-names/graphics-support-documents/"
  click GOV114 "https://github.com/usgpo/house-manual/tree/main/114/govinfo-file-names/"
  click ORIG114 "https://github.com/usgpo/house-manual/tree/main/114/original-file-names/"
  click GSD114 "https://github.com/usgpo/house-manual/tree/main/114/govinfo-file-names/graphics-support-documents/"
  click GOV115 "https://github.com/usgpo/house-manual/tree/main/115/govinfo-file-names/"
  click ORIG115 "https://github.com/usgpo/house-manual/tree/main/115/original-file-names/"
  click GSD115 "https://github.com/usgpo/house-manual/tree/main/115/govinfo-file-names/graphics-support-documents/"
  click GOV116 "https://github.com/usgpo/house-manual/tree/main/116/govinfo-file-names/"
  click ORIG116 "https://github.com/usgpo/house-manual/tree/main/116/original-file-names/"
  click GSD116 "https://github.com/usgpo/house-manual/tree/main/116/govinfo-file-names/graphics-support-documents/"
  click GOV117 "https://github.com/usgpo/house-manual/tree/main/117/govinfo-file-names/"
  click ORIG117 "https://github.com/usgpo/house-manual/tree/main/117/original-file-names/"
  click GSD117 "https://github.com/usgpo/house-manual/tree/main/117/govinfo-file-names/graphics-support-documents/"

  %% Styles
  classDef data fill:#cce5ff,stroke:#004085,color:#004085
  classDef process fill:#d4edda,stroke:#155724,color:#155724
  classDef external fill:#fff3cd,stroke:#856404,color:#856404

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