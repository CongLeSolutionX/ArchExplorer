---
created: 2025-06-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/torproject/chutney
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

# chutney repo project
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
title: "chutney repo project"
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
    %% Top-level entry points
    CLI["chutney CLI"]:::scripts
    Script["tools/test-network.sh"]:::scripts

    %% Configuration inputs
    subgraph "Config Inputs"
        Networks["networks/"]:::config
        Templates["torrc_templates/"]:::config
    end

    %% Core engine grouping
    subgraph "Core Engine"
        CoreEngine["Core Engine"]:::pythoncore
        Debug["Debug Module"]:::pythoncore
        Host["Host Abstraction"]:::pythoncore
        Templating["Templating Engine"]:::pythoncore
        TorNet["TorNet Manager"]:::pythoncore
        Traffic["Traffic & Testing"]:::pythoncore
        Util["Utilities"]:::pythoncore
    end

    %% Runtime directory
    NetDir["net/ (runtime working dir)"]:::config

    %% External binaries
    TorBin["tor & tor-gencert"]:::external

    %% Tor processes
    subgraph "Tor Processes"
        Node1["Node 1"]
        Node2["Node 2"]
        Node3["Node 3"]
    end

    %% Test scripts
    subgraph "Tests"
        BuiltIn["tests/*.sh"]:::scripts
        Custom["scripts/chutney_tests/verify.py"]:::scripts
    end

    %% Connections
    CLI -->|"invoke"| CoreEngine
    Script -->|"invoke"| CoreEngine

    CoreEngine --> Debug
    CoreEngine --> Host
    CoreEngine --> Templating
    CoreEngine --> TorNet
    CoreEngine --> Traffic
    CoreEngine --> Util

    Networks -->|"defines network"| Templating
    Templates -->|"provides templates"| Templating
    Templating -->|"renders torrc files"| NetDir

    NetDir -->|"reads torrcs"| TorNet
    TorNet -->|"spawns processes"| TorBin
    TorBin -->|"runs binaries"| Node1
    TorBin -->|"runs binaries"| Node2
    TorBin -->|"runs binaries"| Node3

    Node1 -->|"bootstrap data"| Traffic
    Node2 -->|"bootstrap data"| Traffic
    Node3 -->|"bootstrap data"| Traffic

    Traffic -->|"writes logs"| NetDir
    Debug -->|"logs and monitors"| NetDir

    BuiltIn -->|"executes standard tests"| Traffic
    Custom -.->|"overrides verify logic"| Traffic
    Custom -.->|"overrides debug hooks"| Debug

    %% Click events
    click CLI "https://github.com/torproject/chutney/tree/main/chutney"
    click Script "https://github.com/torproject/chutney/blob/main/tools/test-network.sh"
    click Debug "https://github.com/torproject/chutney/blob/main/lib/chutney/Debug.py"
    click Host "https://github.com/torproject/chutney/blob/main/lib/chutney/Host.py"
    click Templating "https://github.com/torproject/chutney/blob/main/lib/chutney/Templating.py"
    click TorNet "https://github.com/torproject/chutney/blob/main/lib/chutney/TorNet.py"
    click Traffic "https://github.com/torproject/chutney/blob/main/lib/chutney/Traffic.py"
    click Util "https://github.com/torproject/chutney/blob/main/lib/chutney/Util.py"
    click Networks "https://github.com/torproject/chutney/tree/main/networks/"
    click Templates "https://github.com/torproject/chutney/tree/main/torrc_templates/"
    click NetDir "https://github.com/torproject/chutney/tree/main/net/"
    click Custom "https://github.com/torproject/chutney/blob/main/scripts/chutney_tests/verify.py"
    click BuiltIn "https://github.com/torproject/chutney/blob/main/tests/unit-tests.sh"

    %% Styles
    classDef pythoncore fill:#D0E6FF,stroke:#333,stroke-width:1px
    classDef config fill:#E2F0D9,stroke:#333,stroke-width:1px
    classDef external fill:#FFE5CC,stroke:#333,stroke-width:1px
    classDef scripts fill:#FFF2CC,stroke:#333,stroke-width:1px
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