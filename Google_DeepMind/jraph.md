---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/jraph
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




# jraph repo project
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
title: "jraph repo project"
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
    %% User Code & Examples Layer
    subgraph "User Code & Examples" 
        direction TB
        basic["basic.py"]:::examples
        evote["e_voting.py"]:::examples
        gol["game_of_life.py"]:::examples
        hgn["hamiltonian_graph_network.py"]:::examples
        higgs["higgs_detection.py"]:::examples
        lstm["lstm.py"]:::examples
        sat["sat.py"]:::examples
        karate["zacharys_karate_club.py"]:::examples

        subgraph "Experimental Modules"
            sharded["sharded_graphnet.py"]:::experimental
        end

        subgraph "OGB Examples"
            data_utils["data_utils.py"]:::examples
            train_jax["train.py"]:::examples
            train_flax["train_flax.py"]:::examples
            train_pmap["train_pmap.py"]:::examples

            subgraph "OGB Tests"
                data_utils_test["data_utils_test.py"]:::tests
                train_flax_test["train_flax_test.py"]:::tests
                train_pmap_test["train_pmap_test.py"]:::tests
                train_test["train_test.py"]:::tests
                test_data["test_data/"]:::data
            end
        end
    end

    %% Core Library Layer
    subgraph "Core Library (jraph/_src)" 
    direction TB
        %% graph["graph.py"]:::core
        utils["utils.py"]:::core
        models["models.py"]:::core

        subgraph "Core Tests"
            models_test["models_test.py"]:::tests
            utils_test["utils_test.py"]:::tests
        end
    end

    %% External Dependencies
    subgraph "External Dependencies" 
        direction TB
        jax["JAX Runtime"]:::external
        ogb_data["OGB Datasets"]:::data
        flax["Flax/Haiku"]:::external
    end

    %% Documentation
    docs["Documentation (docs/)"]:::docs

    %% CI/CD & Packaging
    ci["CI/CD & Packaging"]:::cicd

    %% Relationships
    %% basic -->|imports| graph
    basic -->|imports| utils
    basic -->|imports| models
    %% evote -->|imports| graph
    %% gol -->|imports| graph
    hgn -->|imports| models
    higgs -->|imports| models
    lstm -->|imports| utils
    sat -->|imports| models
    karate -->|imports| utils

    sharded -->|extends| models
    %% sharded -->|imports| graph
    sharded -->|imports| utils

    data_utils -->|loads| ogb_data
    train_jax -->|imports| data_utils
    %% train_jax -->|imports| graph
    train_flax -->|imports| data_utils
    train_flax -->|imports| models
    train_pmap -->|imports| data_utils
    %% train_pmap -->|imports| graph

    models -->|tested by| models_test
    utils -->|tested by| utils_test

    data_utils -->|tested by| data_utils_test
    train_flax -->|tested by| train_flax_test
    train_pmap -->|tested by| train_pmap_test
    train_jax -->|tested by| train_test

    %% graph -->|uses| jax
    utils -->|uses| jax
    models -->|jit compile| jax

    train_flax -->|uses| flax
    train_pmap -->|pmap| jax

    docs -->|generates| ReadTheDocs["ReadTheDocs"]:::external
    ci -->|on push runs| models_test
    ci -->|on push runs| utils_test
    ci -->|on push runs| data_utils_test
    ci -->|on push runs| train_flax_test
    ci -->|publishes via| pypi["PyPI"]:::external

    setup["setup.py"]:::cicd
    reqs["requirements.txt"]:::cicd
    ci -->|uses| setup
    ci -->|uses| reqs

    %% Click Events
    click graph "https://github.com/google-deepmind/jraph/blob/master/jraph/_src/graph.py"
    click utils "https://github.com/google-deepmind/jraph/blob/master/jraph/_src/utils.py"
    click models "https://github.com/google-deepmind/jraph/blob/master/jraph/_src/models.py"
    click models_test "https://github.com/google-deepmind/jraph/blob/master/jraph/_src/models_test.py"
    click utils_test "https://github.com/google-deepmind/jraph/blob/master/jraph/_src/utils_test.py"

    click basic "https://github.com/google-deepmind/jraph/blob/master/jraph/examples/basic.py"
    click evote "https://github.com/google-deepmind/jraph/blob/master/jraph/examples/e_voting.py"
    click gol "https://github.com/google-deepmind/jraph/blob/master/jraph/examples/game_of_life.py"
    click hgn "https://github.com/google-deepmind/jraph/blob/master/jraph/examples/hamiltonian_graph_network.py"
    click higgs "https://github.com/google-deepmind/jraph/blob/master/jraph/examples/higgs_detection.py"
    click lstm "https://github.com/google-deepmind/jraph/blob/master/jraph/examples/lstm.py"
    click sat "https://github.com/google-deepmind/jraph/blob/master/jraph/examples/sat.py"
    click karate "https://github.com/google-deepmind/jraph/blob/master/jraph/examples/zacharys_karate_club.py"

    click sharded "https://github.com/google-deepmind/jraph/blob/master/jraph/experimental/sharded_graphnet.py"
    click data_utils "https://github.com/google-deepmind/jraph/blob/master/jraph/ogb_examples/data_utils.py"
    click data_utils_test "https://github.com/google-deepmind/jraph/blob/master/jraph/ogb_examples/data_utils_test.py"
    click train_jax "https://github.com/google-deepmind/jraph/blob/master/jraph/ogb_examples/train.py"
    click train_flax "https://github.com/google-deepmind/jraph/blob/master/jraph/ogb_examples/train_flax.py"
    click train_flax_test "https://github.com/google-deepmind/jraph/blob/master/jraph/ogb_examples/train_flax_test.py"
    click train_pmap "https://github.com/google-deepmind/jraph/blob/master/jraph/ogb_examples/train_pmap.py"
    click train_pmap_test "https://github.com/google-deepmind/jraph/blob/master/jraph/ogb_examples/train_pmap_test.py"
    click train_test "https://github.com/google-deepmind/jraph/blob/master/jraph/ogb_examples/train_test.py"
    click test_data "https://github.com/google-deepmind/jraph/tree/master/jraph/ogb_examples/test_data/"

    click docs "https://github.com/google-deepmind/jraph/tree/master/docs/"
    click ci "https://github.com/google-deepmind/jraph/blob/master/.github/workflows/pypi-publish.yml"
    click setup "https://github.com/google-deepmind/jraph/blob/master/setup.py"
    click reqs "https://github.com/google-deepmind/jraph/blob/master/requirements.txt"

    %% Styles
    classDef core fill:#cce5ff,stroke:#0062cc,color:#004085;
    classDef examples fill:#d4edda,stroke:#155724,color:#155724;
    classDef experimental fill:#e2e3e5,stroke:#383d41,color:#383d41;
    classDef tests fill:#f8d7da,stroke:#721c24,color:#721c24;
    classDef data fill:#fff3cd,stroke:#856404,color:#856404;
    classDef external fill:#fff5e6,stroke:#e08e0b,color:#e08e0b;
    classDef docs fill:#d1ecf1,stroke:#0c5460,color:#0c5460;
    classDef cicd fill:#e2e3e5,stroke:#383d41,color:#383d41;

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