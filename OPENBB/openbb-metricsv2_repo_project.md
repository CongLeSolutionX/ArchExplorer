---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/OpenBB-finance/openbb-metricsv2
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExY2Vmb2hoZWo1bjB1MmdmYTZpYzZmeXZiZTkwZWF4Mmszc3dzMzIzMSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/YUUFqPfYVUrvIFzEUJ/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----

# openbb-metricsv2 repo project
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
title: "openbb-metricsv2 repo project"
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
    %% Scheduler and Runner
    Scheduler["GitHub Actions Scheduler (cron)"]:::gh
    Scheduler --> Runner["Runner VM/Container"]:::gh

    %% Workflow Steps
    subgraph "Workflow Steps"
        direction TB
        Checkout["Checkout Code"]:::gh
        SetupPy["Setup Python Environment"]:::gh
        LoadCfg["Load Config (.env)"]:::py
        RunOrch["Run Orchestrator Script"]:::py
        Commit["Commit metrics.json"]:::gh
    end

    Runner --> Checkout
    Checkout --> SetupPy
    SetupPy --> LoadCfg
    LoadCfg --> RunOrch
    RunOrch --> Commit

    %% Orchestrator and Modules
    RunOrch --> Main["main.py"]:::py
    Main --> Config["utilities/config.py"]:::py
    Main --> Helpers["utilities/helpers.py"]:::py

    %% External Services
    subgraph "External APIs"
        direction TB
        YT["YouTube Data API"]:::ext
        Discord["Discord API"]:::ext
        PyPI["PyPI API"]:::ext
    end

    Helpers --> YT
    Helpers --> Discord
    Helpers --> PyPI

    %% Output Store
    Helpers --> Metrics["metrics.json"]:::store

    %% Repository Files
    subgraph "Repository Files"
        direction TB
        PyProj["pyproject.toml"]:::doc
        ReqTxt["requirements.txt"]:::doc
        Readme["README.md"]:::doc
    end

    Checkout --> PyProj
    Checkout --> ReqTxt
    Checkout --> Readme

    %% Click Events
    click Scheduler "https://github.com/openbb-finance/openbb-metricsv2/blob/main/.github/workflows/metrics-runner.yml"
    click Main "https://github.com/openbb-finance/openbb-metricsv2/blob/main/main.py"
    click Config "https://github.com/openbb-finance/openbb-metricsv2/blob/main/utilities/config.py"
    click Helpers "https://github.com/openbb-finance/openbb-metricsv2/blob/main/utilities/helpers.py"
    click Metrics "https://github.com/openbb-finance/openbb-metricsv2/blob/main/metrics.json"
    click PyProj "https://github.com/openbb-finance/openbb-metricsv2/blob/main/pyproject.toml"
    click ReqTxt "https://github.com/openbb-finance/openbb-metricsv2/blob/main/requirements.txt"
    click Readme "https://github.com/openbb-finance/openbb-metricsv2/blob/main/README.md"

    %% Styles
    classDef gh fill:#0366d6,stroke:#024ea2,color:#fff;
    classDef py fill:#2d8fdd,stroke:#1b6fa8,color:#fff;
    classDef ext fill:#f08d49,stroke:#d17c37,color:#fff;
    classDef store fill:#6a737d,stroke:#52565c,color:#fff;
    classDef doc fill:#6f42c1,stroke:#593185,color:#fff;
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
