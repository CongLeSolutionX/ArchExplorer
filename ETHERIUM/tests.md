---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/tests
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExcDRnNmlod2F2Zm12dXpyaXh3a2RvbXFzM3A3ZTFwZzV4MjV2a2kyZyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/vN2JgW7mzrXFONSClb/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# tests repo project
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
title: "tests repo project"
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
    subgraph "Source Code"
        Repo["Test Repository (Git)"]:::code
        CI["CI Configuration (.travis.yml, requirements.txt)"]:::code
    end

    subgraph "Generation Pipeline"
        Filler["Filler Generator"]:::code
        Templates["Templates for Custom Fillers"]:::code
        Repo --> Filler
        Filler --> Templates
    end

    subgraph "Static Test Suites"
        Tests["JSON/YAML Test Suites"]:::data
        Templates --> Tests
    end

    subgraph "Validation"
        Schema["JSON Schema Validator"]:::code
        Tests --> Schema
    end

    subgraph "Execution"
        RET["retesteth (Test Harness)"]:::code
        Clients["Ethereum Clients (Geth, Parity, etc.)"]:::external
        Schema --> RET
        RET --> Clients
    end

    subgraph "Infrastructure Provisioning"
        Infra["Infrastructure Provisioner (Ansible/Vagrant)"]:::infra
        Infra --> RET
        Infra --> Clients
        CI --> Infra
    end

    subgraph "Results Aggregation"
        Hive["Results Aggregator (hive)"]:::external
        UI["Web UI"]:::external
        Clients --> Hive
        Hive --> UI
    end

    subgraph "Documentation"
        Docs["Documentation Portal (Sphinx/RST)"]:::code
        Repo --> Docs
    end

    click Repo "https://github.com/ethereum/tests/blob/develop/.gitignore"
    click Filler "https://github.com/ethereum/tests/tree/develop/src/BlockchainTestsFiller/"
    click Templates "https://github.com/ethereum/tests/tree/develop/src/Templates/"
    click Tests "https://github.com/ethereum/tests/tree/develop/BasicTests/"
    click Schema "https://github.com/ethereum/tests/tree/develop/JSONSchema/"
    click Infra "https://github.com/ethereum/tests/tree/develop/ansible/"
    click Docs "https://github.com/ethereum/tests/tree/develop/docs/"
    click CI "https://github.com/ethereum/tests/blob/develop/.travis.yml"

    classDef code fill:#ADD8E6,stroke:#333,stroke-width:1px;
    classDef data fill:#FFA500,stroke:#333,stroke-width:1px;
    classDef external fill:#90EE90,stroke:#333,stroke-width:1px;
    classDef infra fill:#DDA0DD,stroke:#333,stroke-width:1px;

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
