---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/github/gh-ost
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


# gh-ost repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>

---


```mermaid
---
title: "gh-ost repo project"
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
    'flowchart': { 'htmlLabels': true, 'curve': 'step' },
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
    subgraph CLI_and_Config["CLI & Config"]
    style CLI_and_Config fill:#f9f2,stroke:#333,stroke-width:1px, color:#FF2
      CLI["CLI Parser & Flag Loader"]:::cli
      Config["Configuration & Context Manager"]:::config
    end

    subgraph MySQL_Connection["MySQL Connection"]
    style MySQL_Connection fill:#f9f2,stroke:#333,stroke-width:1px, color:#FF2
      ConnMgr["MySQL Connection Manager"]:::mysql
    end

    subgraph Binlog_Reader["Binlog Reader"]
    style Binlog_Reader fill:#f9f2,stroke:#333,stroke-width:1px, color:#FF2
        BLReader["Binlog Reader"]:::pipeline
    end

    subgraph Pipeline["Pipeline<br/>(go/logic)"]
    style Pipeline fill:#f9f2,stroke:#333,stroke-width:1px, color:#FF2
        Streamer["Event Streamer"]:::pipeline
        Applier["Row Applier"]:::pipeline
        Throttler["Throttler"]:::control
        Migrator["Migrator / Cut-Over Controller"]:::control
        Server["Interactive Control Server"]:::control
        HooksRunner["External Hooks Runner"]:::control
    end

    subgraph SQL_Layer["SQL Layer"]
    style SQL_Layer fill:#f9f2,stroke:#333,stroke-width:1px, color:#FF2
        SQLBuilder["SQL Builder & Parser"]:::sql
    end

    subgraph External_Hooks["External Hooks"]
    style External_Hooks fill:#f9f2,stroke:#333,stroke-width:1px, color:#FF2
      HooksSample["Hook Scripts"]:::hooks
    end

    subgraph MySQL_Server["MySQL Server"]
    style MySQL_Server fill:#f9f2,stroke:#333,stroke-width:1px, color:#FF2
        OriginDB["Original Table"]:::db
        GhostDB["Ghost Table"]:::db
    end

    CLI --> Config
    Config --> ConnMgr
    ConnMgr --> BLReader
    ConnMgr --> OriginDB
    BLReader --> Streamer
    Streamer --> Applier
    Applier --> GhostDB
    Streamer --> Throttler
    Applier --> Throttler
    Throttler -.-> Streamer
    Throttler -.-> Applier
    Migrator --> GhostDB
    Migrator --> OriginDB
    Server --> Throttler
    Server --> Migrator
    HooksRunner --> HooksSample
    HooksRunner --> Migrator
    SQLBuilder --> Applier

    click CLI "https://github.com/github/gh-ost/blob/master/go/cmd/gh-ost/main.go"
    click Config "https://github.com/github/gh-ost/tree/master/go/base"
    click ConnMgr "https://github.com/github/gh-ost/tree/master/go/mysql"
    click BLReader "https://github.com/github/gh-ost/tree/master/go/binlog"
    click Streamer "https://github.com/github/gh-ost/blob/master/go/logic/streamer.go"
    click Applier "https://github.com/github/gh-ost/blob/master/go/logic/applier.go"
    click Throttler "https://github.com/github/gh-ost/blob/master/go/logic/throttler.go"
    click Migrator "https://github.com/github/gh-ost/blob/master/go/logic/migrator.go"
    click Server "https://github.com/github/gh-ost/blob/master/go/logic/server.go"
    click HooksRunner "https://github.com/github/gh-ost/blob/master/go/logic/hooks.go"
    click SQLBuilder "https://github.com/github/gh-ost/tree/master/go/sql"
    click HooksSample "https://github.com/github/gh-ost/tree/master/resources/hooks-sample"

    classDef cli fill:#f9f2,stroke:#333,stroke-width:1px
    classDef config fill:#fcf5,stroke:#333
    classDef mysql fill:#ccf5,stroke:#333
    classDef pipeline fill:#bbf5,stroke:#333
    classDef control fill:#fbb5,stroke:#333
    classDef sql fill:#bfb5,stroke:#333
    classDef hooks fill:#f2F9,stroke:#333
    classDef db fill:#9ff5,stroke:#333
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

  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

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