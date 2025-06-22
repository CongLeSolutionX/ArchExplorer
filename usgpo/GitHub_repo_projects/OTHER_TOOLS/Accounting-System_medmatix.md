---
created: 2025-06-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/medmatix/Accounting-System
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExNTF5b2l5ZXc1OHhlZnptdGkxd3dtbDVhYThtZm9mM3Jjc3A0a2QyMyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/jpcXipl3oSBu1n9y61/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# medmatix - Accounting-System repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


---

```mermaid
---
title: "medmatix - Accounting-System repo project"
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
    %% User Interface Layer
    subgraph "User Interface Layer"
        direction TB
        Splash["Splash Screen"]:::ui
        MainUI["Main Window & Tabs"]:::ui
        Dialogs["Dialog Forms (Journal/Chart/Memo)"]:::ui
    end

    %% Controller Layer
    subgraph "Controller Layer"
        direction TB
        Reports["Report Generation Routines"]:::controller
        Tooltips["UI Helper for Tooltips"]:::controller
    end

    %% Model Layer
    subgraph "Model Layer"
        direction TB
        AccountDB["AccountDB (Model)"]:::model
    end

    %% Persistence
    subgraph "Persistence"
        direction TB
        DBFile[(OpenAccounting.db)]
        Schema[(OpenAccounting.sql)]
    end

    %% Project Packaging & Docs
    subgraph "Project Packaging & Documentation"
        direction TB
        SLN["Accounting-System.sln"]:::packaging
        PROJ["Accounting-System.pyproj"]:::packaging
        README["README.md"]:::docs
        LICENSE["LICENSE"]:::docs
        TEST["testcode.py"]:::docs
        VS[".vs/"]:::packaging
        SETTINGS[".settings/"]:::packaging
    end

    %% External Libraries & Environment
    subgraph "External Libraries & Environment"
        direction TB
        Python["Python 3.7"]:::external
        TK["Tkinter"]:::external
        SQLiteLib["SQLite3"]:::external
        Pytz["pytz / numpy"]:::external
    end

    %% Connections
    Splash -->|"handoff"| MainUI
    MainUI -->|"opens"| Dialogs
    Dialogs -->|"invokes CRUD"| AccountDB
    MainUI -->|"direct calls"| AccountDB
    Reports -->|"queries"| AccountDB
    Reports -->|"outputs data to"| MainUI
    Tooltips -->|"provides UI helpers to"| MainUI
    AccountDB -->|"reads/writes"| DBFile
    AccountDB -->|"schema init from"| Schema

    Python --> Splash
    TK --> MainUI
    SQLiteLib --> AccountDB
    Pytz --> Reports

    %% Click Events
    click Splash "https://github.com/medmatix/accounting-system/blob/master/splash.py"
    click MainUI "https://github.com/medmatix/accounting-system/blob/master/OpenAccounting.py"
    click Dialogs "https://github.com/medmatix/accounting-system/blob/master/FormDialogs.py"
    click Reports "https://github.com/medmatix/accounting-system/blob/master/ReportPreps.py"
    click Tooltips "https://github.com/medmatix/accounting-system/blob/master/Tooltips.py"
    click AccountDB "https://github.com/medmatix/accounting-system/blob/master/AccountDB.py"
    click DBFile "https://github.com/medmatix/accounting-system/blob/master/OpenAccounting.db"
    click Schema "https://github.com/medmatix/accounting-system/blob/master/OpenAccounting.sql"
    click SLN "https://github.com/medmatix/accounting-system/blob/master/Accounting-System.sln"
    click PROJ "https://github.com/medmatix/accounting-system/blob/master/Accounting-System.pyproj"
    click README "https://github.com/medmatix/accounting-system/blob/master/README.md"
    click LICENSE "https://github.com/medmatix/accounting-system/tree/master/LICENSE"
    click TEST "https://github.com/medmatix/accounting-system/blob/master/testcode.py"
    click VS "https://github.com/medmatix/accounting-system/tree/master/.vs/"
    click SETTINGS "https://github.com/medmatix/accounting-system/tree/master/.settings/"

    %% Styles
    classDef ui fill:#ADD8E6,stroke:#333,stroke-width:1px
    classDef controller fill:#90EE90,stroke:#333,stroke-width:1px
    classDef model fill:#FFA500,stroke:#333,stroke-width:1px
    classDef packaging fill:#D8BFD8,stroke:#333,stroke-width:1px
    classDef docs fill:#FFFFE0,stroke:#333,stroke-width:1px
    classDef external fill:#D3D3D3,stroke:#333,stroke-width:1px

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
