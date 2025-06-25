---
created: 2025-06-25 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/Orange-Cyberdefense/KeePwn
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




# KeePwn repo project
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
title: "KeePwn repo project"
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
    subgraph KeePwn_Application["KeePwn Application"]
    style KeePwn_Application fill:#F2F2,stroke:#333,stroke-width:1px, color: #FFFF
        subgraph CLI_Layer["CLI Layer"]
        style CLI_Layer fill:#22F2,stroke:#333,stroke-width:1px, color: #FFFF
            CLI1["<b>KeePwn.py</b>"]:::cli
            CLI2["<b>keepwn/__main__.py</b>"]:::cli
        end

        subgraph Core_Modules_Layer["Core Modules Layer"]
        style Core_Modules_Layer fill:#62F2,stroke:#333,stroke-width:1px, color: #FFFF
            Search["Search Module<br/>(smb discovery)"]:::core
            Plugin["Plugin Module<br/>(DLL abuse)"]:::core
            Trigger["Trigger Module<br/>(XML triggers)"]:::core
            ParseDump["ParseDump Module<br/>(memory dump)"]:::core
            Convert["Convert Module<br/>(KDBX→hash)"]:::core
        end

        subgraph Utility_Layer["Utility Layer"]
        style Utility_Layer fill:#92F2,stroke:#333,stroke-width:1px, color: #FFFF
            SMBUtils["SMB Utilities"]:::util
            ParserUtils["Parser Utilities"]:::util
            Logging["Logging Utilities"]:::util
            ThreadTools["Threading Tools"]:::util
            JohnHelper["KDBX→John Helper"]:::util
            XMLTemplate["<b>export_database_trigger.xml</b>"]:::util
        end
    end

    RemoteHost(("Remote Hosts<br/>(Windows <code>C$</code> share)")):::ext
    LocalFS(("Local File System")):::ext

    CLI1 -->|dispatch| Search
    CLI1 -->|dispatch| Plugin
    CLI1 -->|dispatch| Trigger
    CLI1 -->|dispatch| ParseDump
    CLI1 -->|dispatch| Convert

    CLI2 -->|dispatch| Search
    CLI2 -->|dispatch| Plugin
    CLI2 -->|dispatch| Trigger
    CLI2 -->|dispatch| ParseDump
    CLI2 -->|dispatch| Convert

    Search -->|uses| SMBUtils
    Search -->|threads| ThreadTools
    Plugin -->|uses| SMBUtils
    Trigger -->|uses| SMBUtils
    Trigger -->|template| XMLTemplate
    ParseDump -->|parses| ParserUtils
    Convert -->|parses| ParserUtils
    Convert -->|generates| JohnHelper

    SMBUtils -->|SMB/C$| RemoteHost
    ParserUtils -->|file I/O| LocalFS
    JohnHelper -->|output hashes| LocalFS

    classDef cli fill:#004085,stroke:#004085
    classDef core fill:#155724,stroke:#155724
    classDef util fill:#856404,stroke:#856404
    classDef ext fill:#6c757d,stroke:#6c757d

    click CLI1 "https://github.com/orange-cyberdefense/keepwn/blob/main/KeePwn.py"
    click CLI2 "https://github.com/orange-cyberdefense/keepwn/blob/main/keepwn/__main__.py"
    click Search "https://github.com/orange-cyberdefense/keepwn/blob/main/keepwn/core/search.py"
    click Plugin "https://github.com/orange-cyberdefense/keepwn/blob/main/keepwn/core/plugin.py"
    click Trigger "https://github.com/orange-cyberdefense/keepwn/blob/main/keepwn/core/trigger.py"
    click ParseDump "https://github.com/orange-cyberdefense/keepwn/blob/main/keepwn/core/parse_dump.py"
    click Convert "https://github.com/orange-cyberdefense/keepwn/blob/main/keepwn/core/convert.py"
    click SMBUtils "https://github.com/orange-cyberdefense/keepwn/blob/main/keepwn/utils/smb.py"
    click ParserUtils "https://github.com/orange-cyberdefense/keepwn/blob/main/keepwn/utils/parser.py"
    click Logging "https://github.com/orange-cyberdefense/keepwn/blob/main/keepwn/utils/logging.py"
    click ThreadTools "https://github.com/orange-cyberdefense/keepwn/blob/main/keepwn/utils/tstools.py"
    click JohnHelper "https://github.com/orange-cyberdefense/keepwn/blob/main/keepwn/utils/keepass2john.py"
    click XMLTemplate "https://github.com/orange-cyberdefense/keepwn/blob/main/keepwn/data/export_database_trigger.xml"

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