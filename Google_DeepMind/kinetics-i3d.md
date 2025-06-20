---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/kinetics-i3d
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




# kinetics-i3d repo project
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


---

```mermaid
---
title: "kinetics-i3d repo project"
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
    %% Data Storage
    subgraph "Data Storage" 
        direction TB
        CP["Checkpoints"]:::data
        subgraph "Checkpoint Variants"
            direction TB
            CP1["rgb_imagenet"]:::data
            CP2["rgb_scratch"]:::data
            CP3["flow_imagenet"]:::data
            CP4["flow_scratch"]:::data
            CP5["rgb_scratch_kin600"]:::data
        end
        SV1["v_CricketShot_g04_c01_flow.npy"]:::data
        SV2["v_CricketShot_g04_c01_rgb.npy"]:::data
        LM1["label_map.txt"]:::data
        LM2["label_map_600.txt"]:::data
    end

    %% Preprocessing
    Pre["MediaPipe/OpenCV Preprocessor"]:::process

    %% Model Definition
    ModelDef["i3d.py"]:::process

    %% Inference Pipeline
    Eval["evaluate_sample.py"]:::script

    %% Orchestration
    Multi["multi_evaluate.sh"]:::script

    %% Testing
    Test["i3d_test.py"]:::test

    %% Outputs
    subgraph "Outputs" 
        direction TB
        OutDir["out/"]:::output
        O1["imagenet_rgb.txt"]:::output
        O2["imagenet_flow.txt"]:::output
        O3["imagenet_joint.txt"]:::output
        O4["no_imagenet_rgb.txt"]:::output
        O5["no_imagenet_flow.txt"]:::output
        O6["no_imagenet_joint.txt"]:::output
    end

    %% External Dependencies
    subgraph "External Dependencies"
        direction TB
        TF["TensorFlow"]:::external
        Sonnet["DeepMind Sonnet"]:::external
        NumPy["NumPy"]:::external
        Bash["Bash"]:::external
    end

    %% Data Flow
    Pre --> SV1
    Pre --> SV2
    SV1 --> Eval
    SV2 --> Eval
    CP1 --> Eval
    CP2 --> Eval
    CP3 --> Eval
    CP4 --> Eval
    CP5 --> Eval
    LM1 --> Eval
    LM2 --> Eval

    Eval -->|builds TF graph| ModelDef
    ModelDef --> Eval
    Eval -->|"logits & probs"| OutDir
    Multi --> Eval
    Multi --> O1
    Multi --> O2
    Multi --> O3
    Multi --> O4
    Multi --> O5
    Multi --> O6

    Test --> ModelDef

    %% External Links
    TF --> ModelDef
    Sonnet --> ModelDef
    NumPy --> Eval
    Bash --> Multi
    NumPy --> Pre

    %% Click Events
    click CP "https://github.com/google-deepmind/kinetics-i3d/tree/master/data/checkpoints"
    click CP1 "https://github.com/google-deepmind/kinetics-i3d/tree/master/data/checkpoints/rgb_imagenet"
    click CP2 "https://github.com/google-deepmind/kinetics-i3d/tree/master/data/checkpoints/rgb_scratch"
    click CP3 "https://github.com/google-deepmind/kinetics-i3d/tree/master/data/checkpoints/flow_imagenet"
    click CP4 "https://github.com/google-deepmind/kinetics-i3d/tree/master/data/checkpoints/flow_scratch"
    click CP5 "https://github.com/google-deepmind/kinetics-i3d/tree/master/data/checkpoints/rgb_scratch_kin600"
    click SV1 "https://github.com/google-deepmind/kinetics-i3d/blob/master/data/v_CricketShot_g04_c01_flow.npy"
    click SV2 "https://github.com/google-deepmind/kinetics-i3d/blob/master/data/v_CricketShot_g04_c01_rgb.npy"
    click LM1 "https://github.com/google-deepmind/kinetics-i3d/blob/master/data/label_map.txt"
    click LM2 "https://github.com/google-deepmind/kinetics-i3d/blob/master/data/label_map_600.txt"
    click ModelDef "https://github.com/google-deepmind/kinetics-i3d/blob/master/i3d.py"
    click Eval "https://github.com/google-deepmind/kinetics-i3d/blob/master/evaluate_sample.py"
    click Multi "https://github.com/google-deepmind/kinetics-i3d/blob/master/multi_evaluate.sh"
    click Test "https://github.com/google-deepmind/kinetics-i3d/blob/master/i3d_test.py"
    click OutDir "https://github.com/google-deepmind/kinetics-i3d/tree/master/out"
    click O1 "https://github.com/google-deepmind/kinetics-i3d/blob/master/out/imagenet_rgb.txt"
    click O2 "https://github.com/google-deepmind/kinetics-i3d/blob/master/out/imagenet_flow.txt"
    click O3 "https://github.com/google-deepmind/kinetics-i3d/blob/master/out/imagenet_joint.txt"
    click O4 "https://github.com/google-deepmind/kinetics-i3d/blob/master/out/no_imagenet_rgb.txt"
    click O5 "https://github.com/google-deepmind/kinetics-i3d/blob/master/out/no_imagenet_flow.txt"
    click O6 "https://github.com/google-deepmind/kinetics-i3d/blob/master/out/no_imagenet_joint.txt"

    %% Styles
    classDef data fill:#cce5ff,stroke:#1f78b4
    classDef process fill:#d4edda,stroke:#2e7d32
    classDef script fill:#fff3cd,stroke:#ff8f00
    classDef test fill:#f8d7da,stroke:#c62828
    classDef output fill:#e1bee7,stroke:#6a1b9a
    classDef external fill:#f0f0f0,stroke:#555555,stroke-dasharray:5 5

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