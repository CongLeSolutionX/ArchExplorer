---
created: 2025-06-12 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/emoclassifiers
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExMGd1NW51YmdxdWFucGZneDNuZWk1ZWVycXNxZTEwdnF5bm1uaTl0ZiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/l4Ki1fHZorEdWAPsc/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# emoclassifiers repo project
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
title: "emoclassifiers repo project"
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
        direction TB
        Simple["run_simple_classification.py"]:::cli
        Hierarchical["run_hierarchical_emoclassifiers_v1.py"]:::cli
    end

    %% Core Library
    subgraph "Core Library"
        direction TB
        Classification["Classification Orchestrator"]:::core
        Chunking["Chunking Module"]:::core
        Prompt["Prompt-Template Module"]:::core
        Aggregation["Aggregation Module"]:::core
        IOUtils["I/O Utilities"]:::core
    end

    %% Asset Store
    subgraph "Asset Store"
        direction TB
        DefV1["emoclassifiers_v1_definition.json"]:::asset
        DepGraph["emoclassifiers_v1_dependency.json"]:::asset
        TopLevel["emoclassifiers_v1_top_level_definition.json"]:::asset
        DefV2["emoclassifiers_v2_definition.json"]:::asset
        ExampleConvs["example_conversations.jsonl"]:::asset
    end

    %% External Service
    OpenAI["OpenAI API"]:::external

    %% Data Stores
    Input["Input JSONL"]:::data
    Output["Output JSONL"]:::data

    %% Connections
    Simple -->|"load Input JSONL"| IOUtils
    Hierarchical -->|"load Input JSONL"| IOUtils
    Simple -->|"start classification"| Classification
    Hierarchical -->|"start classification"| Classification

    IOUtils -->|"read Input JSONL"| Input
    Input -->|"conversations"| IOUtils

    Classification -->|"load definitions"| DefV1
    Classification -->|"load definitions"| DepGraph
    Classification -->|"load definitions"| TopLevel
    Classification -->|"load definitions"| DefV2

    Classification -->|"invoke chunking"| Chunking
    Chunking -->|"chunks"| Classification

    Classification -->|"construct prompts"| Prompt

    Classification -->|"async call"| OpenAI
    OpenAI -->|"LLM responses"| Classification

    Classification -->|"raw outputs"| Aggregation
    Aggregation -->|"aggregated results"| IOUtils

    IOUtils -->|"write Output JSONL"| Output

    %% Click Events
    click Simple "https://github.com/openai/emoclassifiers/blob/main/examples/run_simple_classification.py"
    click Hierarchical "https://github.com/openai/emoclassifiers/blob/main/examples/run_hierarchical_emoclassifiers_v1.py"
    click Chunking "https://github.com/openai/emoclassifiers/blob/main/emoclassifiers/chunking.py"
    click Prompt "https://github.com/openai/emoclassifiers/blob/main/emoclassifiers/prompt_templates.py"
    click Classification "https://github.com/openai/emoclassifiers/blob/main/emoclassifiers/classification.py"
    click Aggregation "https://github.com/openai/emoclassifiers/blob/main/emoclassifiers/aggregation.py"
    click IOUtils "https://github.com/openai/emoclassifiers/blob/main/emoclassifiers/io_utils.py"
    click DefV1 "https://github.com/openai/emoclassifiers/blob/main/assets/definitions/emoclassifiers_v1_definition.json"
    click DepGraph "https://github.com/openai/emoclassifiers/blob/main/assets/definitions/emoclassifiers_v1_dependency.json"
    click TopLevel "https://github.com/openai/emoclassifiers/blob/main/assets/definitions/emoclassifiers_v1_top_level_definition.json"
    click DefV2 "https://github.com/openai/emoclassifiers/blob/main/assets/definitions/emoclassifiers_v2_definition.json"
    click ExampleConvs "https://github.com/openai/emoclassifiers/blob/main/assets/example_conversations.jsonl"

    %% Styles
    classDef cli fill:#D0E1F9,stroke:#333,stroke-width:1px
    classDef core fill:#D5F5E3,stroke:#333,stroke-width:1px
    classDef asset fill:#FAD7A0,stroke:#333,stroke-width:1px
    classDef external fill:#D2B4DE,stroke:#333,stroke-width:1px
    classDef data fill:#AED6F1,stroke:#333,stroke-width:1px


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
