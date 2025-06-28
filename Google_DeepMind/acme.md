---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/acme
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




# acme repo project
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
title: "acme repo project"
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
    %% User/Experiment Layer
    subgraph "User / Experiment Layer"
        direction TB
        Examples["Examples / Scripts / Notebooks"]:::user
    end

    %% Environment Layer
    subgraph "Environment Layer"
        direction TB
        EnvExt["External Environments (Gym, dm_control, bsuite)"]:::external
        Wrapper["Wrappers (acme/wrappers)"]:::core
    end

    %% Core RL Loop
    subgraph "Core RL Loop" 
        direction TB
        EnvLoop["EnvironmentLoop"]:::core
        Adder["Adder (acme/adders)"]:::core
        ReverbServer["Reverb Server"]:::external
        Dataset["Dataset Pipeline"]:::core
        Learner["Learner"]:::core
        Actor["Actor"]:::core
        Builder["Agent Builder"]:::core
    end

    %% Backend Abstractions
    subgraph "Backend Abstractions" 
        direction TB
        JAX["JAX Backend (acme/jax)"]:::backend
        TF["TensorFlow Backend (acme/tf)"]:::backend
        InferenceServer["Inference Server"]:::backend
    end

    %% Utilities & Logging
    subgraph "Utilities & Logging"
        direction TB
        Utils["Utilities & Logging (acme/utils)"]:::utils
        Snapshotter["Snapshotter"]:::utils
    end

    %% Connections
    Examples -->|"launches"| Builder
    Builder -->|"configures"| Actor
    Builder -->|"configures"| Learner
    Actor -->|"drives"| EnvLoop
    EnvLoop -->|"- actions ->"| EnvExt
    EnvExt -->|"observations, rewards"| Wrapper
    Wrapper -->|"adapted transitions"| Adder
    Adder -->|"push transitions ->"| ReverbServer
    Learner -->|"pull batches <-"| Dataset
    Dataset -->|"batches ->"| Learner
    Learner -->|"updates params ->"| Snapshotter
    Snapshotter -->|"sync params ->"| Actor
    InferenceServer -->|"serves policy ->"| Actor
    JAX -->|"provides nets, losses"| Learner
    TF -->|"provides nets, losses"| Learner
    Utils -->|"logging & metrics"| EnvLoop
    Utils -->|"logging & metrics"| Learner

    %% Click Events
    click Examples "https://github.com/google-deepmind/acme/tree/master/examples/"
    click Wrapper "https://github.com/google-deepmind/acme/tree/master/acme/wrappers/"
    click EnvLoop "https://github.com/google-deepmind/acme/blob/master/acme/environment_loop.py"
    click Adder "https://github.com/google-deepmind/acme/blob/master/acme/adders/base.py"
    click ReverbServer "https://github.com/google-deepmind/acme/tree/master/acme/adders/reverb/"
    click Dataset "https://github.com/google-deepmind/acme/tree/master/acme/datasets/"
    click Builder "https://github.com/google-deepmind/acme/blob/master/acme/agents/agent.py"
    click JAX "https://github.com/google-deepmind/acme/tree/master/acme/jax/"
    click TF "https://github.com/google-deepmind/acme/tree/master/acme/tf/"
    click InferenceServer "https://github.com/google-deepmind/acme/blob/master/acme/jax/inference_server.py"
    click Utils "https://github.com/google-deepmind/acme/tree/master/acme/utils/"
    click Snapshotter "https://github.com/google-deepmind/acme/blob/master/acme/jax/snapshotter.py"

    %% Styles
    classDef user fill:#e3f2fd,stroke:#90caf9,color:#0d47a1
    classDef external fill:#fff3e0,stroke:#ffb74d,color:#e65100
    classDef core fill:#e8f5e9,stroke:#66bb6a,color:#1b5e20
    classDef backend fill:#e1f5fe,stroke:#29b6f6,color:#01579b
    classDef utils fill:#eeeeee,stroke:#bdbdbd,color:#424242

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