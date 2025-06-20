---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/mujoco
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




# mujoco repo project
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
title: "mujoco repo project"
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
    Build["Build & Configuration Infrastructure"]:::build
    XML["Model Definition and XML Compiler"]:::xml
    Engine["Core Simulation Engine"]:::engine
    Plugin["Plugin Architecture"]:::plugin
    Renderer["OpenGL Renderer"]:::view
    Viewer["Interactive Viewer (simulate)"]:::view
    API["User/API Interface"]:::api
    APIHdr["Header (include/mujoco)"]:::api
    Python["Python Bindings"]:::binding
    Unity["Unity Plugin"]:::binding
    MJX["MJX (JAX/XLA Integration)"]:::binding

    Build -->|"build_config"| XML
    Build -->|"build_config"| Engine
    XML -->|"Model_Compilation"| Engine
    Engine -->|"Plugin_Processing"| Plugin
    Engine -->|"Simulation_Step"| Renderer
    Renderer -->|"Display_Output"| Viewer
    Engine -->|"Expose_API"| API
    API -->|"Include_Headers"| APIHdr
    API -->|"Python_Interface"| Python
    API -->|"Unity_Integration"| Unity
    API -->|"Diff_Physics"| MJX

    click Build "https://github.com/google-deepmind/mujoco/tree/main/cmake/"
    click XML "https://github.com/google-deepmind/mujoco/tree/main/src/xml/"
    click Engine "https://github.com/google-deepmind/mujoco/tree/main/src/engine/"
    click Plugin "https://github.com/google-deepmind/mujoco/tree/main/plugin/"
    click Renderer "https://github.com/google-deepmind/mujoco/tree/main/src/render/"
    click Viewer "https://github.com/google-deepmind/mujoco/tree/main/simulate/"
    click API "https://github.com/google-deepmind/mujoco/tree/main/src/user/"
    click APIHdr "https://github.com/google-deepmind/mujoco/tree/main/include/mujoco/"
    click Python "https://github.com/google-deepmind/mujoco/tree/main/python/"
    click Unity "https://github.com/google-deepmind/mujoco/tree/main/unity/"
    click MJX "https://github.com/google-deepmind/mujoco/tree/main/mjx/"

    classDef build fill:#cff,stroke:#333,stroke-width:2px;
    classDef xml fill:#cce,stroke:#333,stroke-width:2px;
    classDef engine fill:#f9c,stroke:#333,stroke-width:2px;
    classDef plugin fill:#fc9,stroke:#333,stroke-width:2px;
    classDef view fill:#ccf,stroke:#333,stroke-width:2px;
    classDef api fill:#cfc,stroke:#333,stroke-width:2px;
    classDef binding fill:#ffc,stroke:#333,stroke-width:2px;

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