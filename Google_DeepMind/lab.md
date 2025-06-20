---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/lab
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




# lab repo project
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
title: "lab repo project"
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
    subgraph "Core Game Engine"
        EngineDir["Game Engine Directory"]:::engineStyle
        EngineCode["Game Engine Code Base"]:::engineStyle
    end

    subgraph "DeepMind Lab Modules"
        DMEngine["DeepMind Engine Extension"]:::dmStyle
        DMLevelGen["DeepMind Level Generation"]:::dmStyle
        DMModelGen["DeepMind Model Generation"]:::dmStyle
        DMTensor["DeepMind Tensor Ops"]:::dmStyle
        DMUtil["DeepMind Utilities"]:::dmStyle
        DMLua["DeepMind Lua Integration"]:::dmStyle
    end

    subgraph "Scripting and Configuration"
        LuaScripts["Lua Scripts & Config"]:::configStyle
    end

    subgraph "Interfaces"
        PythonAPI["Python Agent Interface"]:::apiStyle
    end

    subgraph "Map Generation Tools"
        MapGen["Map Generation (q3map2)"]:::mapStyle
    end

    subgraph "External Dependencies"
        ThirdParty["Third Party Dependencies"]:::extStyle
        Bazel["Build Infrastructure (Bazel)"]:::extStyle
    end

    LuaScripts -->|"configures"| EngineDir
    PythonAPI <-->|"observations_actions"| EngineDir
    DMEngine -->|"extends"| EngineDir
    DMLevelGen -->|"extends"| EngineDir
    DMModelGen -->|"extends"| EngineDir
    DMTensor -->|"extends"| EngineDir
    DMUtil -->|"extends"| EngineDir
    DMLua -->|"extends"| EngineDir
    MapGen -->|"map_data"| EngineDir
    ThirdParty -->|"build"| EngineDir
    Bazel -->|"build"| EngineDir
    ThirdParty -->|"deps"| DMEngine
    Bazel -->|"deps"| DMEngine

    classDef engineStyle fill:#AED6F1,stroke:#1B4F72,stroke-width:2px;
    classDef dmStyle fill:#A9DFBF,stroke:#196F3D,stroke-width:2px;
    classDef configStyle fill:#FAD7A0,stroke:#D35400,stroke-width:2px;
    classDef apiStyle fill:#F5B7B1,stroke:#922B21,stroke-width:2px;
    classDef mapStyle fill:#F9E79F,stroke:#B7950B,stroke-width:2px;
    classDef extStyle fill:#D2B4DE,stroke:#6C3483,stroke-width:2px;

    click EngineDir "https://github.com/google-deepmind/lab/tree/master/engine/"
    click EngineCode "https://github.com/google-deepmind/lab/tree/master/engine/code/"
    click DMEngine "https://github.com/google-deepmind/lab/tree/master/deepmind/"
    click LuaScripts "https://github.com/google-deepmind/lab/tree/master/game_scripts/"
    click PythonAPI "https://github.com/google-deepmind/lab/tree/master/python/"
    click MapGen "https://github.com/google-deepmind/lab/tree/master/q3map2/"
    click ThirdParty "https://github.com/google-deepmind/lab/tree/master/third_party/"
    click Bazel "https://github.com/google-deepmind/lab/tree/master/bazel/"
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