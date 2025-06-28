---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/dnc
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




# dnc repo project
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
title: "dnc repo project"
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
    %% Training Pipeline Layer
    subgraph "Training Pipeline" 
    direction TB
        Train["Training Script (train.py)"]:::train
        Generator["Sample Task Generator"]:::train
        DynamicRNN["tf.nn.dynamic_rnn"]:::train
        LossOpt["Loss & Optimizer"]:::train
        Checkpoint[(Checkpoint Dir)]:::train
    end

    %% Model Core Layer
    subgraph "DNC Model Core"
    direction TB
        DNCWrapper["DNC Wrapper (RNNCore)"]:::core
        Controller["Controller (Feedforward/LSTM)"]:::core
        AccessMod["Access Module"]:::core
        
        subgraph "Addressing Submodules"
        direction TB
            Temporal["TemporalLinkage"]:::core
            Freeness["Freeness"]:::core
        end
        
        Memory[(External Memory Matrix)]:::core
    end

    %% External & Packaging Layer
    subgraph "External Dependencies & Packaging"
    direction TB
        TF["TensorFlow"]:::external
        Sonnet["Sonnet"]:::external
        Util["Utilities"]:::util
        
        subgraph "Tests"
        direction TB
            AccessTest["Access Module Tests"]:::util
            AddressTest["Addressing Tests"]:::util
            UtilTest["Utilities Tests"]:::util
        end
    end

    %% Data Flow & Dependencies
    Train -->|"uses"| Generator
    Generator -->|"provides input sequence"| DNCWrapper
    DNCWrapper -->|"Input Sequence"| Controller
    Controller -->|"interface & control signals"| AccessMod
    AccessMod -->|"read/write"| Memory
    Memory -->|"read vectors"| AccessMod
    AccessMod -->|"read vectors"| Controller
    Controller -->|"output vector"| DynamicRNN
    DynamicRNN -->|"outputs"| LossOpt
    LossOpt -->|"updates params"| DNCWrapper
    LossOpt -->|"saves checkpoint"| Checkpoint

    %% Dependencies
    DNCWrapper -.->|"imports"| Controller
    DNCWrapper -.->|"imports"| AccessMod
    AccessMod -.->|"imports"| Temporal
    AccessMod -.->|"imports"| Freeness
    %% TrainerExt(( ))-.->| "dependent on"| TF
    TrainerExt -.->|"dependent on"| Sonnet
    DNCWrapper -.->|"built on"| TF
    DNCWrapper -.->|"built on"| Sonnet
    Util -.->|"helper routines"| DNCWrapper

    %% Click Events
    click Controller "https://github.com/google-deepmind/dnc/blob/master/dnc/dnc.py"
    click DNCWrapper "https://github.com/google-deepmind/dnc/blob/master/dnc/dnc.py"
    click AccessMod "https://github.com/google-deepmind/dnc/blob/master/dnc/access.py"
    click Temporal "https://github.com/google-deepmind/dnc/blob/master/dnc/addressing.py"
    click Freeness "https://github.com/google-deepmind/dnc/blob/master/dnc/addressing.py"
    click Util "https://github.com/google-deepmind/dnc/blob/master/dnc/util.py"
    click Generator "https://github.com/google-deepmind/dnc/blob/master/dnc/repeat_copy.py"
    click Train "https://github.com/google-deepmind/dnc/blob/master/train.py"
    click AccessTest "https://github.com/google-deepmind/dnc/blob/master/dnc/access_test.py"
    click AddressTest "https://github.com/google-deepmind/dnc/blob/master/dnc/addressing_test.py"
    click UtilTest "https://github.com/google-deepmind/dnc/blob/master/dnc/util_test.py"

    %% Styles
    classDef core fill:#D0E6FF,stroke:#036;stroke-width:1px
    classDef train fill:#D0FFD0,stroke:#0A0;stroke-width:1px
    classDef external fill:#FFE0B2,stroke:#C60,stroke-width:1px,stroke-dasharray: 5 5
    classDef util fill:#E0E0E0,stroke:#666,stroke-width:1px,stroke-dasharray: 2 2

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