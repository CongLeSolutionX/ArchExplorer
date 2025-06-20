---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/learning-to-learn
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




# learning-to-learn repo project
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
title: "learning-to-learn repo project"
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
        Train["train.py: Training Pipeline"]:::script
        Evaluate["evaluate.py: Evaluation Pipeline"]:::script
    end

    %% Core Meta-Learning Engine
    subgraph "Core Meta-Learning Engine"
    direction TB
        Meta["meta.py: MetaOptimizer & meta_minimize"]:::core
    end

    %% Problem & Data Layer
    subgraph "Problem & Data Layer"
    direction TB
        Problems["problems.py: Loss & Model Definitions"]:::core
        Preprocess["preprocess.py: Data Preprocessing"]:::core
        Util["util.py: Helpers & Config"]:::core
    end

    %% Network Layer
    subgraph "Network Layer"
    direction TB
        Networks["networks.py: Model Architectures"]:::core
    end

    %% Testing Layer
    subgraph "Testing"
    direction TB
        ConvTest["convergence_test.py"]:::script
        MetaTest["meta_test.py"]:::script
        NetTest["networks_test.py"]:::script
        PrepTest["preprocess_test.py"]:::script
        ProbTest["problems_test.py"]:::script
    end

    %% External Dependencies & Storage
    subgraph "External & Storage"
    direction TB
        TF["TensorFlow Runtime"]:::external
        Sonnet["Sonnet Modules"]:::external
        FS["File System (Checkpoints)"]:::storage
    end

    %% Connections
    Train -->|"instantiates"| Meta
    Evaluate -->|"loads optimizer / configures Adam"| Meta
    Meta -->|"calls loss_fn()"|Problems
    Problems -->|"imports data queues"| Preprocess
    Problems -->|"imports model"| Networks
    Meta -->|"uses helpers"| Util
    Train -->|"uses helpers"| Util
    Evaluate -->|"uses helpers"| Util
    Networks -->|"builds graph ops"| TF
    Preprocess -->|"feeds data"| TF
    Meta -->|"executes graph"| TF
    TF -->|"uses modules"| Sonnet
    Meta -->|"checkpoint save/load"| FS
    Evaluate -->|"reads checkpoints"| FS

    %% Click Events
    click Train "https://github.com/google-deepmind/learning-to-learn/blob/master/train.py"
    click Evaluate "https://github.com/google-deepmind/learning-to-learn/blob/master/evaluate.py"
    click Meta "https://github.com/google-deepmind/learning-to-learn/blob/master/meta.py"
    click Problems "https://github.com/google-deepmind/learning-to-learn/blob/master/problems.py"
    click Preprocess "https://github.com/google-deepmind/learning-to-learn/blob/master/preprocess.py"
    click Util "https://github.com/google-deepmind/learning-to-learn/blob/master/util.py"
    click Networks "https://github.com/google-deepmind/learning-to-learn/blob/master/networks.py"
    click ConvTest "https://github.com/google-deepmind/learning-to-learn/blob/master/convergence_test.py"
    click MetaTest "https://github.com/google-deepmind/learning-to-learn/blob/master/meta_test.py"
    click NetTest "https://github.com/google-deepmind/learning-to-learn/blob/master/networks_test.py"
    click PrepTest "https://github.com/google-deepmind/learning-to-learn/blob/master/preprocess_test.py"
    click ProbTest "https://github.com/google-deepmind/learning-to-learn/blob/master/problems_test.py"

    %% Styles
    classDef script fill:#D0E6FF,stroke:#5A9,stroke-width:1px
    classDef core fill:#E6FFE6,stroke:#2A9,stroke-width:1px
    classDef external fill:#F0F0F0,stroke:#888,stroke-width:1px,stroke-dasharray: 5 5
    classDef storage fill:#FFE6CC,stroke:#D9822B,stroke-width:1px

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