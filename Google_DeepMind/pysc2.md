---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/pysc2
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




# pysc2 repo project
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
title: "pysc2 repo project"
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
  subgraph "CLI/Entry"
    CLI_Binaries["CLI/Binaries"]:::cli
  end

  subgraph "Agent Layer"
    Agents["Agent Implementations"]:::core
  end

  subgraph "Environment Layer"
    EnvInterface["Environment Interface"]:::core
    Converter["Converter Modules"]:::core
  end

  subgraph "Utilities & Libraries"
    Libs["Libraries & Helpers"]:::util
  end

  subgraph "Configurations"
    Maps["Maps"]:::config
    RunConfigs["Run Configs"]:::config
  end

  subgraph "Build & Testing"
    Build["Build & Dependencies"]:::build
    Testing["Testing"]:::test
  end

  External["StarCraft II API"]:::external

  CLI_Binaries -->|"launches"| Agents
  Agents -->|"sends_commands"| EnvInterface
  EnvInterface -->|"processes_observations"| Converter
  Converter -->|"returns_data"| Agents
  EnvInterface -->|"calls_API"| External
  EnvInterface -->|"loads_maps"| Maps
  EnvInterface -->|"loads_configs"| RunConfigs
  Build -->|"compiles"| Converter
  Libs -->|"supports"| Agents
  Libs -->|"supports"| EnvInterface
  Testing -->|"tests"| Agents
  Testing -->|"tests"| EnvInterface
  Testing -->|"tests"| Converter

  click CLI_Binaries "https://github.com/google-deepmind/pysc2/tree/master/pysc2/bin"
  click Agents "https://github.com/google-deepmind/pysc2/tree/master/pysc2/agents"
  click EnvInterface "https://github.com/google-deepmind/pysc2/tree/master/pysc2/env"
  click Converter "https://github.com/google-deepmind/pysc2/tree/master/pysc2/env/converter"
  click Build "https://github.com/google-deepmind/pysc2/tree/master/bazel"
  click Libs "https://github.com/google-deepmind/pysc2/tree/master/pysc2/lib"
  click Maps "https://github.com/google-deepmind/pysc2/tree/master/pysc2/maps"
  click RunConfigs "https://github.com/google-deepmind/pysc2/tree/master/pysc2/run_configs"
  click Testing "https://github.com/google-deepmind/pysc2/tree/master/pysc2/tests"

  classDef cli fill:#fdebd0,stroke:#d35400,stroke-width:2px;
  classDef core fill:#d5f5e3,stroke:#27ae60,stroke-width:2px;
  classDef util fill:#d6eaf8,stroke:#2980b9,stroke-width:2px;
  classDef config fill:#fcf3cf,stroke:#f1c40f,stroke-width:2px;
  classDef build fill:#f9e79f,stroke:#f39c12,stroke-width:2px;
  classDef test fill:#f5cba7,stroke:#e67e22,stroke-width:2px;
  classDef external fill:#f8d7da,stroke:#c0392b,stroke-width:2px;
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