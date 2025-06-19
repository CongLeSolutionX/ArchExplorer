---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/xdit-project/xDiT
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExZmdoYWhxb3c2NmR6OGZoMzN5NWxqNjJmbmVxd3U0NDFobjc4ZHdvNyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/xUA7bjPYcgAvwq5CKc/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# xdit-project - xDiT repo project
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
title: "xDiT repo project"
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
    %% Client Layer
    subgraph "Client Layer"
        LAUNCH["entrypoints/launch.py"]:::frontend
        CURL["entrypoints/curl.sh"]:::frontend
        RUNSH["examples/run.sh"]:::frontend
        HTTPDOC["docs/developer/Http_Service.md"]:::frontend
        RAYEX["examples/ray/"]:::frontend
    end

    %% Configuration & Initialization
    subgraph "Configuration & Initialization"
        ARGS["xfuser/config/args.py"]:::config
        CFG["xfuser/config/config.py"]:::config
        ENVS["xfuser/envs.py"]:::config
        LOG["xfuser/logger.py"]:::config
    end

    %% Core Orchestration
    subgraph "Core Orchestration"
        DIST["xfuser/core/distributed/"]:::orchestration
        PAR["xfuser/parallel.py"]:::orchestration
        RAYWORKER["xfuser/ray/worker/"]:::orchestration
        RAYPIPE["xfuser/ray/pipeline/"]:::orchestration
    end

    %% Model Execution Stack
    subgraph "Model Execution Stack"
        PIPE["xfuser/model_executor/pipelines/"]:::execution
        SCHED["xfuser/model_executor/schedulers/"]:::execution
        BASEWRAP["xfuser/model_executor/base_wrapper.py"]:::execution
        MODELS["xfuser/model_executor/models/"]:::execution
        LAYERS["xfuser/model_executor/layers/"]:::execution
        FASTATTN["xfuser/core/fast_attention/"]:::execution
        LONGATTN["xfuser/core/long_ctx_attention/"]:::execution
        CACHE1["xfuser/core/cache_manager/cache_manager.py"]:::execution
        CACHE2["xfuser/model_executor/cache/"]:::execution
    end

    %% External Libraries
    subgraph "External Libraries"
        TORCH["PyTorch"]:::external
        DIFF["Diffusers"]:::external
        FLASH["FlashAttention"]:::external
        ONEDIFF["onediff"]:::external
        COMPILE["torch.compile"]:::external
    end

    %% Hardware & Deployment
    subgraph "Hardware & Deployment"
        GPU["GPU Nodes"]:::hardware
        DOCKER["Docker Container"]:::hardware
    end

    %% Connections
    LAUNCH -->|parse args| ARGS
    CURL -->|parse args| ARGS
    RUNSH -->|parse args| ARGS
    HTTPDOC -->|load docs| ARGS
    RAYEX -->|submit job| ARGS

    ARGS --> CFG
    ARGS --> ENVS
    ARGS --> LOG

    CFG --> PAR
    ENVS --> PAR
    LOG --> PAR

    PAR --> PIPE
    PAR --> DIST
    DIST --> PAR

    PAR --> RAYWORKER
    PAR --> RAYPIPE

    PIPE --> SCHED
    SCHED --> BASEWRAP
    BASEWRAP --> MODELS
    MODELS --> LAYERS
    LAYERS --> GPU
    FASTATTN --> LAYERS
    LONGATTN --> LAYERS
    CACHE1 --> GPU
    CACHE2 --> GPU
    BASEWRAP --> CACHE2

    TORCH --> BASEWRAP
    DIFF -.-> PIPE
    FLASH -.-> LAYERS
    ONEDIFF -.-> LAYERS
    COMPILE -.-> BASEWRAP

    GPU --> DOCKER

    %% Click Events
    click LAUNCH "https://github.com/xdit-project/xdit/blob/main/entrypoints/launch.py"
    click CURL "https://github.com/xdit-project/xdit/blob/main/entrypoints/curl.sh"
    click RUNSH "https://github.com/xdit-project/xdit/blob/main/examples/run.sh"
    click HTTPDOC "https://github.com/xdit-project/xdit/blob/main/docs/developer/Http_Service.md"
    click RAYEX "https://github.com/xdit-project/xdit/tree/main/examples/ray/"
    click ARGS "https://github.com/xdit-project/xdit/blob/main/xfuser/config/args.py"
    click CFG "https://github.com/xdit-project/xdit/blob/main/xfuser/config/config.py"
    click ENVS "https://github.com/xdit-project/xdit/blob/main/xfuser/envs.py"
    click LOG "https://github.com/xdit-project/xdit/blob/main/xfuser/logger.py"
    click DIST "https://github.com/xdit-project/xdit/tree/main/xfuser/core/distributed/"
    click PAR "https://github.com/xdit-project/xdit/blob/main/xfuser/parallel.py"
    click RAYWORKER "https://github.com/xdit-project/xdit/tree/main/xfuser/ray/worker/"
    click RAYPIPE "https://github.com/xdit-project/xdit/tree/main/xfuser/ray/pipeline/"
    click PIPE "https://github.com/xdit-project/xdit/tree/main/xfuser/model_executor/pipelines/"
    click SCHED "https://github.com/xdit-project/xdit/tree/main/xfuser/model_executor/schedulers/"
    click BASEWRAP "https://github.com/xdit-project/xdit/blob/main/xfuser/model_executor/base_wrapper.py"
    click MODELS "https://github.com/xdit-project/xdit/tree/main/xfuser/model_executor/models/"
    click LAYERS "https://github.com/xdit-project/xdit/tree/main/xfuser/model_executor/layers/"
    click FASTATTN "https://github.com/xdit-project/xdit/tree/main/xfuser/core/fast_attention/"
    click LONGATTN "https://github.com/xdit-project/xdit/tree/main/xfuser/core/long_ctx_attention/"
    click CACHE1 "https://github.com/xdit-project/xdit/blob/main/xfuser/core/cache_manager/cache_manager.py"
    click CACHE2 "https://github.com/xdit-project/xdit/tree/main/xfuser/model_executor/cache/"
    click DOCKER "https://github.com/xdit-project/xdit/tree/main/docker/Dockerfile"

    %% Styles
    classDef frontend fill:#D0E6FF,stroke:#0366d6,color:#0366d6,stroke-width:1px;
    classDef config fill:#DFFFD0,stroke:#28a745,color:#28a745,stroke-width:1px;
    classDef orchestration fill:#DFFFE0,stroke:#22863a,color:#22863a,stroke-width:1px;
    classDef execution fill:#FFF5D0,stroke:#d97706,color:#d97706,stroke-width:1px;
    classDef external fill:#E2E2E2,stroke:#6a737d,color:#6a737d,stroke-width:1px,stroke-dasharray: 5 5;
    classDef hardware fill:#F0E6FF,stroke:#6f42c1,color:#6f42c1,stroke-width:1px;

```

-----


```mermaid
---
title: "❓...CongLeSolutionX....❓"
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

  Closing_quote ~~~ My_Meme
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }

```

---
><b>Licenses</b>:
>
>- <b>MIT License</b>:  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
>- <b>Creative Commons Attribution-ShareAlike 4.0 International</b>: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) [![CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/88x31.png)](https://creativecommons.org/licenses/by-sa/4.0/) - Legal details in [LICENSE-CC-BY-SA-4.0](THE_PAST/LICENSE-CC-BY-SA-4.0) and at [Creative Commons official site](https://creativecommons.org/licenses/by-sa/4.0/).
>
---
