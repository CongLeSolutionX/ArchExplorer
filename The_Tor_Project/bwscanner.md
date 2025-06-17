---
created: 2025-06-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/TheTorProject/bwscanner
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


# bwscanner repo project
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
title: "bwscanner repo project"
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
    %% CLI Layer
    subgraph "CLI Layer"
        CLI["bwscan CLI"]:::internal
        Scanner["scanner.py"]:::internal
        AggCmd["aggregate.py"]:::internal
        scriptsAgg["scripts/aggregate.py"]:::aux
    end

    %% Core Modules
    subgraph "Core Modules"
        Config["config.py"]:::internal
        Logger["logger.py"]:::internal
        Fetcher["fetcher.py"]:::internal
        Circuit["circuit.py"]:::internal
        Attacher["attacher.py"]:::internal
        Measurement["measurement.py"]:::internal
        Writer["writer.py"]:::internal
    end

    %% External Systems
    subgraph "External Systems"
        TorInstance["Tor ControlPort"]:::external
        TorNetwork["Tor Network/Relays"]:::external
    end

    %% Storage
    subgraph "Storage"
        RawStore["Raw Measurements Store"]:::storage
        AggregatedStore["Aggregated Output Store"]:::storage
    end

    %% CI/Test/Docs
    subgraph "CI/Test/Docs"
        testCircuit["test/test_circuit.py"]:::aux
        testMeasurement["test/test_measurement.py"]:::aux
        testWriter["test/test_writer.py"]:::aux
        Docs["docs/source/bwscanner.rst"]:::aux
        CI[".travis.yml & tox.ini"]:::aux
    end

    %% Workflow
    User["User Terminal"]:::external
    User -->|"invoke scan/aggregate"| CLI
    CLI -->|"scan command"| Scanner
    CLI -->|"aggregate command"| AggCmd

    Scanner -->|"load config"| Config
    Scanner -->|"initialize logger"| Logger
    Scanner -->|"fetch consensus"| Fetcher
    Fetcher -->|"write raw consensus"| RawStore

    Scanner -->|"build circuit"| Circuit
    Circuit -->|"connect"| TorInstance
    TorInstance -->|"relay info"| TorNetwork

    Scanner -->|"attach streams"| Attacher
    Scanner -->|"run tests"| Measurement
    Measurement -->|"persist records"| Writer
    Writer -->|"store measurements"| RawStore

    AggCmd -->|"read measurements"| RawStore
    AggCmd -->|"merge results"| AggCmd
    AggCmd -->|"write summary"| AggregatedStore

    User -->|"run script"| scriptsAgg
    scriptsAgg -->|"invoke aggregation"| AggCmd

    %% Click Events
    click CLI "https://github.com/thetorproject/bwscanner/blob/develop/setup.py"
    click Scanner "https://github.com/thetorproject/bwscanner/blob/develop/bwscanner/scanner.py"
    click AggCmd "https://github.com/thetorproject/bwscanner/blob/develop/bwscanner/aggregate.py"
    click scriptsAgg "https://github.com/thetorproject/bwscanner/blob/develop/scripts/aggregate.py"
    click Config "https://github.com/thetorproject/bwscanner/blob/develop/bwscanner/config.py"
    click Logger "https://github.com/thetorproject/bwscanner/blob/develop/bwscanner/logger.py"
    click Fetcher "https://github.com/thetorproject/bwscanner/blob/develop/bwscanner/fetcher.py"
    click Circuit "https://github.com/thetorproject/bwscanner/blob/develop/bwscanner/circuit.py"
    click Attacher "https://github.com/thetorproject/bwscanner/blob/develop/bwscanner/attacher.py"
    click Measurement "https://github.com/thetorproject/bwscanner/blob/develop/bwscanner/measurement.py"
    click Writer "https://github.com/thetorproject/bwscanner/blob/develop/bwscanner/writer.py"
    click testCircuit "https://github.com/thetorproject/bwscanner/blob/develop/test/test_circuit.py"
    click testMeasurement "https://github.com/thetorproject/bwscanner/blob/develop/test/test_measurement.py"
    click testWriter "https://github.com/thetorproject/bwscanner/blob/develop/test/test_writer.py"
    click Docs "https://github.com/thetorproject/bwscanner/blob/develop/docs/source/bwscanner.rst"
    click CI "https://github.com/thetorproject/bwscanner/blob/develop/.travis.yml, tox.ini"

    %% Styles
    classDef internal fill:#cce5ff,stroke:#1f78b4;
    classDef external fill:#d4edda,stroke:#28a745;
    classDef storage fill:#fff3cd,stroke:#ff9800;
    classDef aux fill:#e2e3e5,stroke:#6c757d;
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