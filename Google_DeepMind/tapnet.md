---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/tapnet
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




# tapnet repo project
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
title: "tapnet repo project"
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
    %% Data Sources
    subgraph "Data Sources"
        direction TB
        DS1["TAP-Vid Dataset"]:::data
        DS2["RoboTAP Dataset"]:::data
        DS3["Kubric (Synthetic)"]:::data
        DS4["TAPVid-3D Dataset"]:::data
        DS5["External Video (Camera)"]:::data
    end

    %% Configuration Layer
    Conf["Configuration Layer\n(configs/)"]:::config

    %% Core Library
    subgraph "Core Library"
        direction TB
        subgraph "Data Utilities"
            direction TB
            DH["TAP-Vid Dataset Helpers"]:::data
            DH2["TAPVid-3D Annotation Generation"]:::data
        end
        subgraph Models
            direction TB
            M1["TAPNet Models (JAX)"]:::model
            M2["PyTorch Re-implementations"]:::model
            M3["TAPNext Module & Losses"]:::model
            M4["TRAJAN Autoencoder"]:::model
            M5["RoboTAP Clustering Code"]:::model
        end
        U["Core Utilities"]:::util
    end

    %% Training Pipeline
    T1["JAX Training Pipeline"]:::train

    %% Evaluation & Metrics
    subgraph "Evaluation & Metrics"
        direction TB
        E1["TAP-Vid Evaluation Datasets"]:::eval
        E2["TAPVid-3D Evaluation & Metrics"]:::eval
    end

    %% Inference & Visualization
    subgraph "Inference & Visualization"
        direction TB
        I1["Live Demo (JAX)"]:::infer
        I2["Live Demo (PyTorch)"]:::infer
        VI["Visualization Utilities"]:::vis
    end

    %% Demos
    Colab["Colab Demo Notebooks"]:::demo

    %% Checkpoint Storage
    Chk["Checkpoint Storage\n(local/GCS)"]:::storage

    %% External Dependencies
    subgraph "External Dependencies"
        direction TB
        Ext1["JAX"]:::external
        Ext2["PyTorch"]:::external
        Ext3["Kubric Reader"]:::external
        Ext4["Google Cloud Storage"]:::external
    end

    %% Connections
    DS1 -->|loads data| T1
    DS2 -->|loads data| T1
    DS3 -->|loads data| T1
    DS4 -->|loads data| T1
    DS5 -->|live feed| I1

    T1 -->|"saves checkpoints"| Chk
    Conf -->|configures| T1
    Conf -->|configures| I1
    Conf -->|configures| I2

    DS1 -->|evaluation data| E1
    DS4 -->|evaluation data| E2

    M1 --> T1
    U --> T1

    E1 -->|"computes metrics"| E2
    E2 -->|"reports"| T1

    Chk -->|checkpoints & configs| I1
    Chk -->|checkpoints & configs| I2
    U --> I1
    U --> I2

    I1 --> VI
    I2 --> VI
    VI --> Colab

    Colab --> U
    Colab --> M1

    Ext1 --> T1
    Ext2 --> I2
    Ext3 --> DS3
    Ext4 --> Chk

    %% Click Events
    click Conf "https://github.com/google-deepmind/tapnet/tree/main/configs/"
    click DH "https://github.com/google-deepmind/tapnet/blob/main/tapnet/tapvid/generate_tapvid.py"
    click DH2 "https://github.com/google-deepmind/tapnet/tree/main/tapnet/tapvid3d/annotation_generation/"
    click E1 "https://github.com/google-deepmind/tapnet/blob/main/tapnet/tapvid/evaluation_datasets.py"
    click E2 "https://github.com/google-deepmind/tapnet/blob/main/tapnet/tapvid3d/evaluation/metrics.py"
    click M1 "https://github.com/google-deepmind/tapnet/tree/main/tapnet/models/"
    click M2 "https://github.com/google-deepmind/tapnet/tree/main/tapnet/torch/"
    click M3 "https://github.com/google-deepmind/tapnet/tree/main/tapnet/tapnext/"
    click M4 "https://github.com/google-deepmind/tapnet/blob/main/tapnet/trajan/track_autoencoder.py"
    click M5 "https://github.com/google-deepmind/tapnet/blob/main/tapnet/robotap/tapir_clustering.py"
    click U "https://github.com/google-deepmind/tapnet/tree/main/tapnet/utils/"
    click T1 "https://github.com/google-deepmind/tapnet/blob/main/tapnet/training/experiment.py"
    click T1 "https://github.com/google-deepmind/tapnet/blob/main/tapnet/training/supervised_point_prediction.py"
    click I1 "https://github.com/google-deepmind/tapnet/blob/main/tapnet/live_demo.py"
    click I2 "https://github.com/google-deepmind/tapnet/blob/main/tapnet/pytorch_live_demo.py"
    click Colab "https://github.com/google-deepmind/tapnet/tree/main/colabs/"

    %% Styles
    classDef data fill:#cce5ff,stroke:#004085,color:#004085;
    classDef config fill:#e2e3e5,stroke:#6c757d,color:#383d41;
    classDef model fill:#d4edda,stroke:#155724,color:#155724;
    classDef util fill:#f0f0f0,stroke:#adb5bd,color:#495057;
    classDef train fill:#fff3cd,stroke:#856404,color:#856404;
    classDef eval fill:#ffe5b4,stroke:#cc7a00,color:#cc7a00;
    classDef infer fill:#d6d8db,stroke:#1b1e21,color:#1b1e21;
    classDef vis fill:#f5d0a9,stroke:#873e23,color:#873e23;
    classDef demo fill:#e2d4f0,stroke:#5a3e85,color:#5a3e85;
    classDef storage fill:#d1ecf1,stroke:#0c5460,color:#0c5460;
    classDef external fill:#f8d7da,stroke:#721c24,color:#721c24;

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