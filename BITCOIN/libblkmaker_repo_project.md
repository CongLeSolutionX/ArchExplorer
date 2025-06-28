---
created: 2025-06-11 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
spurce: https://github.com/bitcoin/libblkmaker
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExdXF3ZzQ5c3FjaDE4c2Zuam9kOGNydjUwd2tjZDNtMHJrODY0N3UwMSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/QnU6mOrBbElaIQz4Fe/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# libblkmaker repo project
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
title: "libblkmaker repo project"
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
    %% External JSON Source
    JSON["JSON RPC / stdin"]:::external

    %% Caller Layer
    subgraph "Caller/CLI Layer"
        EX1["example.c"]:::cli
        EX2["test.c"]:::cli
        EX3["testinput.c"]:::cli
        EX4["test.sh"]:::cli
    end

    %% Core Library Modules
    subgraph "libblkmaker Core API and Modules"
        BM_C["blkmaker.c"]:::library
        BM_H["blkmaker.h"]:::library
        PH_H["private.h"]:::library
        BT_C["blktemplate.c"]:::library
        BT_H["blktemplate.h"]:::library
        BJ_C["blkmaker_jansson.c"]:::library
        BJ_H["blkmaker_jansson.h"]:::library
        PC_IN["libblkmaker_jansson.pc.in"]:::library
        B58["base58.c"]:::library
        HEX["hex.c"]:::library
    end

    %% External Dependencies
    subgraph "External Dependencies"
        JAN[(Jansson ≥2.0)]:::external
        GCR[(libgcrypt)]:::external
    end

    %% Build & Config
    subgraph "Build & Configuration"
        AG["autogen.sh"]:::config
        CA["configure.ac"]:::config
        MA["Makefile.am"]:::config
        TR[".travis.yml"]:::config
        RD["README"]:::config
        CP["COPYING"]:::config
        AU["AUTHORS"]:::config
        GI[".gitignore"]:::config
    end

    %% Data Flow
    JSON -->|"JSON template"| BJ_C
    BJ_C -->|"parsed JSON"| BT_C
    BT_C -->|"template struct"| BM_C
    EX1 -->|"sets blkmk_sha256_impl"| BM_C
    EX2 -->|"sets blkmk_sha256_impl"| BM_C
    BM_C -->|"calls SHA256 via callback"| GCR
    BM_C -->|"encodes coinbase height"| B58
    BM_C -->|"hex encode header"| HEX
    BM_C -->|"returns block header"| EX1
    BM_C -->|"returns block header"| EX2
    BM_C -->|"returns block header"| EX3

    %% Dependency Links
    BJ_C --> JAN
    BM_C --> BM_H
    BM_C --> PH_H
    BT_C --> BT_H

    %% Build pipeline
    AG --> CA --> MA --> PC_IN
    CA --> MA
    MA --> TR
    MA --> RD
    MA --> CP
    MA --> AU
    MA --> GI

    %% Click Events
    click EX1 "https://github.com/bitcoin/libblkmaker/blob/master/example.c"
    click EX2 "https://github.com/bitcoin/libblkmaker/blob/master/test.c"
    click EX3 "https://github.com/bitcoin/libblkmaker/blob/master/testinput.c"
    click EX4 "https://github.com/bitcoin/libblkmaker/blob/master/test.sh"
    click BM_C "https://github.com/bitcoin/libblkmaker/blob/master/blkmaker.c"
    click BM_H "https://github.com/bitcoin/libblkmaker/blob/master/blkmaker.h"
    click PH_H "https://github.com/bitcoin/libblkmaker/blob/master/private.h"
    click BJ_C "https://github.com/bitcoin/libblkmaker/blob/master/blkmaker_jansson.c"
    click BJ_H "https://github.com/bitcoin/libblkmaker/blob/master/blkmaker_jansson.h"
    click PC_IN "https://github.com/bitcoin/libblkmaker/blob/master/libblkmaker_jansson.pc.in"
    click BT_C "https://github.com/bitcoin/libblkmaker/blob/master/blktemplate.c"
    click BT_H "https://github.com/bitcoin/libblkmaker/blob/master/blktemplate.h"
    click B58 "https://github.com/bitcoin/libblkmaker/blob/master/base58.c"
    click HEX "https://github.com/bitcoin/libblkmaker/blob/master/hex.c"
    click AG "https://github.com/bitcoin/libblkmaker/blob/master/autogen.sh"
    click CA "https://github.com/bitcoin/libblkmaker/blob/master/configure.ac"
    click MA "https://github.com/bitcoin/libblkmaker/blob/master/Makefile.am"
    click TR "https://github.com/bitcoin/libblkmaker/blob/master/.travis.yml"
    click RD "https://github.com/bitcoin/libblkmaker/tree/master/README"
    click CP "https://github.com/bitcoin/libblkmaker/tree/master/COPYING"
    click AU "https://github.com/bitcoin/libblkmaker/tree/master/AUTHORS"
    click GI "https://github.com/bitcoin/libblkmaker/blob/master/.gitignore"

    %% Styles
    classDef library fill:#ADD8E6,stroke:#333;
    classDef external fill:#90EE90,stroke:#333,stroke-dasharray: 5 5;
    classDef cli fill:#FFD700,stroke:#333;
    classDef config fill:#FFA07A,stroke:#333;
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