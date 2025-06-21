---
created: 2025-06-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google/flax
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


# flax repo project
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
title: "flax repo project"
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
    %% Main Layers
    subgraph User["User Applications"]
    style User fill:#FF52,stroke:#333,stroke-width:2px, color: #FFFF
      UA[User Code]
    end

    subgraph HighLevel["High-Level APIs"]
    style HighLevel fill:#B5F2,stroke:#333,stroke-width:2px, color: #FFFF
        NNX["Neural Network API"]:::api
        Training["Training Infrastructure"]:::training
    end

    subgraph Core["Core Systems"]
    style Core fill:#B332,stroke:#333,stroke-width:2px, color: #FFFF
        ModSys["Module System"]:::core
        VarMgmt["Variable Management"]:::core
        RNGMgmt["RNG Management"]:::core
        Transform["Transform System"]:::core
        Graph["Graph System"]:::core
    end

    subgraph JAXLayer["JAX Integration Layer"]
    style JAXLayer fill:#BFF2,stroke:#333,stroke-width:1px, color: #FFFF
        JAX["JAX Runtime"]:::jax
        SPMD["SPMD/Parallelism"]:::jax
    end

    %% Neural Network Components
    subgraph NeuralComponents["Neural Network Components"]
    style NeuralComponents fill:#FF22,stroke:#333,stroke-width:1px, color: #FFFF
        Attention["Attention Layers"]:::nn
        Linear["Linear Layers"]:::nn
        Norm["Normalization Layers"]:::nn
        Recurrent["Recurrent Layers"]:::nn
        Stochastic["Stochastic Layers"]:::nn
    end

    %% Training Components
    subgraph TrainingComponents["Training Components"]
    style TrainingComponents fill:#CC22,stroke:#333,stroke-width:1px, color: #FFFF
        TrainState["Training State"]:::training
        Checkpoint["Checkpointing"]:::training
        Serial["Serialization"]:::training
    end

    %% Relationships
    UA --> NNX
    UA --> Training

    NNX --> ModSys
    NNX --> VarMgmt
    NNX --> RNGMgmt
    NNX --> Transform
    NNX --> Graph
    NNX --> NeuralComponents

    Training --> TrainingComponents
    Training --> ModSys

    ModSys --> JAX
    VarMgmt --> JAX
    RNGMgmt --> JAX
    Transform --> JAX
    SPMD --> JAX

    %% Styles
    classDef core fill:#74ab
    classDef api fill:#a025
    classDef training fill:#f2F7
    classDef nn fill:#F2F2
    classDef jax fill:#d62828

    %% Click Events
    click ModSys "https://github.com/google/flax/tree/main/flax/core/"
    click NNX "https://github.com/google/flax/tree/main/flax/nnx/"
    click Training "https://github.com/google/flax/tree/main/flax/training/"
    click Serial "https://github.com/google/flax/blob/main/flax/serialization.py"
    click VarMgmt "https://github.com/google/flax/blob/main/flax/nnx/variablelib.py"
    click RNGMgmt "https://github.com/google/flax/blob/main/flax/nnx/rnglib.py"
    click SPMD "https://github.com/google/flax/blob/main/flax/nnx/spmd.py"
    click Transform "https://github.com/google/flax/tree/main/flax/nnx/transforms/"
    click Attention "https://github.com/google/flax/blob/main/flax/nnx/nn/attention.py"
    click Linear "https://github.com/google/flax/blob/main/flax/nnx/nn/linear.py"
    click Norm "https://github.com/google/flax/blob/main/flax/nnx/nn/normalization.py"
    click Recurrent "https://github.com/google/flax/blob/main/flax/nnx/nn/recurrent.py"
    click Stochastic "https://github.com/google/flax/blob/main/flax/nnx/nn/stochastic.py"
    click TrainState "https://github.com/google/flax/blob/main/flax/training/train_state.py"
    click Checkpoint "https://github.com/google/flax/blob/main/flax/training/checkpoints.py"
    click Graph "https://github.com/google/flax/blob/main/flax/nnx/graph.py"

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