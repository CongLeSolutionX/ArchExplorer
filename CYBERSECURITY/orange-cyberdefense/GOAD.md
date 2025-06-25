---
created: 2025-06-25 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/Orange-Cyberdefense/GOAD
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




# GOAD repo project
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
title: "GOAD repo project"
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
    %% Global Entities
    U["User Command"]:::orchestration

    %% Orchestrator/Provisioning Engine Subgraph
    subgraph "Orchestrator/Provisioning Engine"
        OPY["goad.py (CLI)"]:::orchestration
        OMOD["goad/ (Modules)"]:::orchestration
    end

    %% Lab Environment Variants
    LV["Lab Variants (ad/)"]:::lab

    %% Infrastructure Providers
    PR["Providers (goad/provider)"]:::provider

    %% Automation/Configuration Management
    ANS["Ansible Provisioning (ansible/)"]:::automation

    %% Virtual Machine Image Builders
    PACK["VM Image Builder (packer/)"]:::vm
    VAGR["VM Manager (vagrant/)"]:::vm

    %% Extensions
    EXT["Extensions (extensions/)"]:::extension

    %% Documentation and Templates
    DOC["Documentation (docs/)"]:::docs
    TEMP["Templates (template/)"]:::docs

    %% Connections
    U -->|"invokes"| OPY
    OPY -->|"loads_modules"| OMOD
    OMOD -->|"parses_config"| LV
    OMOD -->|"calls_provider_logic"| PR
    PR -->|"applies_Packer/Terraform"| PACK
    PR -->|"applies_Vagrant_config"| VAGR
    PR -->|"deploys_VMs"| LV
    OMOD -->|"triggers_Ansible"| ANS
    LV -->|"loads_extensions"| EXT
    LV -->|"references_docs"| DOC
    LV -->|"references_templates"| TEMP

    %% Click Events
    click OPY "https://github.com/orange-cyberdefense/goad/blob/main/goad.py"
    click OMOD "https://github.com/orange-cyberdefense/goad/tree/main/goad/"
    click PR "https://github.com/orange-cyberdefense/goad/tree/main/goad/provider/"
    click ANS "https://github.com/orange-cyberdefense/goad/tree/main/ansible/"
    click PACK "https://github.com/orange-cyberdefense/goad/tree/main/packer/"
    click VAGR "https://github.com/orange-cyberdefense/goad/tree/main/vagrant/"
    click LV "https://github.com/orange-cyberdefense/goad/tree/main/ad/"
    click EXT "https://github.com/orange-cyberdefense/goad/tree/main/extensions/"
    click DOC "https://github.com/orange-cyberdefense/goad/tree/main/docs/"
    click TEMP "https://github.com/orange-cyberdefense/goad/tree/main/template/"

    %% Styles
    classDef orchestration fill:#FFCC00,stroke:#000,stroke-width:2px;
    classDef lab fill:#BBDEFB,stroke:#000,stroke-width:2px;
    classDef provider fill:#C8E6C9,stroke:#000,stroke-width:2px;
    classDef automation fill:#FFECB3,stroke:#000,stroke-width:2px;
    classDef vm fill:#B2EBF2,stroke:#000,stroke-width:2px;
    classDef extension fill:#FFCDD2,stroke:#000,stroke-width:2px;
    classDef docs fill:#E0E0E0,stroke:#000,stroke-width:2px;
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