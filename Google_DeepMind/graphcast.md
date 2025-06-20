---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/graphcast
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




# graphcast repo project
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
title: "graphcast repo project"
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
    %% External Systems
    ECMWFZ["ECMWF Zarr Endpoints"]:::ext
    GCS["Google Cloud Storage"]:::ext

    %% Data Layer
    subgraph "Data Layer"
        DU["data_utils.py"]:::data
        NORM["normalization.py"]:::data
        CLEAN["nan_cleaning.py"]:::data
        XJAX["xarray_jax.py"]:::data
        XTREE["xarray_tree.py"]:::data
    end

    %% Graph Layer
    subgraph "Graph Layer"
        IM["icosahedral_mesh.py"]:::data
        GMC["grid_mesh_connectivity.py"]:::data
        TG["typed_graph.py"]:::data
        MU["model_utils.py"]:::data
    end

    %% Model Layer
    subgraph "Model Layer"
        subgraph "GraphCast Core Model"
            GC["graphcast.py"]:::core
            CAST["casting.py"]:::core
            SOL["solar_radiation.py"]:::core
        end
        subgraph "GenCast Core Model"
            GC2["gencast.py"]:::core
            DEN["denoiser.py"]:::core
            DB["denoisers_base.py"]:::core
            DPS["dpm_solver_plus_plus_2s.py"]:::core
        end
        subgraph "Common Building Blocks"
            DTGN["deep_typed_graph_net.py"]:::data
            TGN["typed_graph_net.py"]:::data
            MLP["mlp.py"]:::data
            TRANS["transformer.py"]:::data
            SPARSE["sparse_transformer.py"]:::data
            SPUTIL["sparse_transformer_utils.py"]:::data
        end
    end

    %% Runtime Layer
    subgraph "Runtime Layer"
        AR["autoregressive.py"]:::runtime
        RO["rollout.py"]:::runtime
        PB["predictor_base.py"]:::runtime
        SB["samplers_base.py"]:::runtime
        SU["samplers_utils.py"]:::runtime
        CKPT["checkpoint.py"]:::runtime
        LOSS["losses.py"]:::runtime
    end

    %% Demos & Notebooks
    subgraph "Demos & Notebooks"
        D1["gencast_demo.ipynb"]:::demo
        D2["gencast_demo_cloud_vm.ipynb"]:::demo
        D3["gencast_mini_demo.ipynb"]:::demo
        D4["graphcast_demo.ipynb"]:::demo
    end

    %% Data Flow
    ECMWFZ --> DU
    GCS --> DU
    DU --> IM
    DU --> NORM
    DU --> CLEAN
    DU --> XJAX
    DU --> XTREE
    IM --> TG
    GMC --> TG
    TG --> GC
    TG --> GC2
    DTGN --> GC
    TGN --> GC
    MLP --> GC
    TRANS --> GC
    SPARSE --> GC
    SPUTIL --> GC
    DTGN --> GC2
    TGN --> GC2
    MLP --> GC2
    TRANS --> GC2
    SPARSE --> GC2
    SPUTIL --> GC2
    GC --> AR
    CAST --> AR
    SOL --> AR
    GC2 --> AR
    DEN --> AR
    DB --> AR
    DPS --> AR
    AR --> LOSS
    LOSS --> CKPT
    CKPT --> AR
    AR --> RO
    RO --> GCS
    RO --> D1
    RO --> D2
    RO --> D3
    RO --> D4

    %% Click Events
    click DU "https://github.com/google-deepmind/graphcast/blob/main/graphcast/data_utils.py"
    click NORM "https://github.com/google-deepmind/graphcast/blob/main/graphcast/normalization.py"
    click CLEAN "https://github.com/google-deepmind/graphcast/blob/main/graphcast/nan_cleaning.py"
    click XJAX "https://github.com/google-deepmind/graphcast/blob/main/graphcast/xarray_jax.py"
    click XTREE "https://github.com/google-deepmind/graphcast/blob/main/graphcast/xarray_tree.py"
    click IM "https://github.com/google-deepmind/graphcast/blob/main/graphcast/icosahedral_mesh.py"
    click GMC "https://github.com/google-deepmind/graphcast/blob/main/graphcast/grid_mesh_connectivity.py"
    click TG "https://github.com/google-deepmind/graphcast/blob/main/graphcast/typed_graph.py"
    click MU "https://github.com/google-deepmind/graphcast/blob/main/graphcast/model_utils.py"
    click GC "https://github.com/google-deepmind/graphcast/blob/main/graphcast/graphcast.py"
    click CAST "https://github.com/google-deepmind/graphcast/blob/main/graphcast/casting.py"
    click SOL "https://github.com/google-deepmind/graphcast/blob/main/graphcast/solar_radiation.py"
    click GC2 "https://github.com/google-deepmind/graphcast/blob/main/graphcast/gencast.py"
    click DEN "https://github.com/google-deepmind/graphcast/blob/main/graphcast/denoiser.py"
    click DB "https://github.com/google-deepmind/graphcast/blob/main/graphcast/denoisers_base.py"
    click DPS "https://github.com/google-deepmind/graphcast/blob/main/graphcast/dpm_solver_plus_plus_2s.py"
    click DTGN "https://github.com/google-deepmind/graphcast/blob/main/graphcast/deep_typed_graph_net.py"
    click TGN "https://github.com/google-deepmind/graphcast/blob/main/graphcast/typed_graph_net.py"
    click MLP "https://github.com/google-deepmind/graphcast/blob/main/graphcast/mlp.py"
    click TRANS "https://github.com/google-deepmind/graphcast/blob/main/graphcast/transformer.py"
    click SPARSE "https://github.com/google-deepmind/graphcast/blob/main/graphcast/sparse_transformer.py"
    click SPUTIL "https://github.com/google-deepmind/graphcast/blob/main/graphcast/sparse_transformer_utils.py"
    click AR "https://github.com/google-deepmind/graphcast/blob/main/graphcast/autoregressive.py"
    click RO "https://github.com/google-deepmind/graphcast/blob/main/graphcast/rollout.py"
    click PB "https://github.com/google-deepmind/graphcast/blob/main/graphcast/predictor_base.py"
    click SB "https://github.com/google-deepmind/graphcast/blob/main/graphcast/samplers_base.py"
    click SU "https://github.com/google-deepmind/graphcast/blob/main/graphcast/samplers_utils.py"
    click CKPT "https://github.com/google-deepmind/graphcast/blob/main/graphcast/checkpoint.py"
    click LOSS "https://github.com/google-deepmind/graphcast/blob/main/graphcast/losses.py"

    %% Styles
    classDef data fill:#E0F7FA,stroke:#00838F,color:#004D40
    classDef core fill:#C8E6C9,stroke:#2E7D32,color:#1B5E20
    classDef runtime fill:#FFE0B2,stroke:#EF6C00,color:#E65100
    classDef ext fill:#ECEFF1,stroke:#90A4AE,color:#607D8B
    classDef demo fill:#F3E5F5,stroke:#8E24AA,color:#4A148C

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