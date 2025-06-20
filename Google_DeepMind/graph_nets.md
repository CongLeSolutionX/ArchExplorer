---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/graph_nets
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




# graph_nets repo project
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


-----

```mermaid
---
title: "graph_nets repo project"
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
    %% API Layer
    subgraph "API Layer"
        GT["GraphTuple"]:::util
        UN["utils_np.py"]:::util
        UT["utils_tf.py"]:::util
    end

    %% Core Engine
    subgraph "Core Engine"
        Base["_base.py"]:::core
        Blocks["blocks.py"]:::core
        Modules["GraphNetwork / GraphIndependent"]:::core
    end

    %% Infrastructure & Tooling
    subgraph "Infrastructure & Tooling"
        Setup["setup.py"]:::infra
        Docs["docs/"]:::demo
        Images["images/"]:::demo
        subgraph "Demos"
            D1["graph_nets_basics.ipynb"]:::demo
            D2["models.py"]:::demo
            D3["physics.ipynb"]:::demo
            D4["shortest_path.ipynb"]:::demo
            D5["sort.ipynb"]:::demo
            D6["graph_nets_basics.ipynb (TF2)"]:::demo
            D7["models.py (TF2)"]:::demo
            D8["sort.ipynb (TF2)"]:::demo
        end
        subgraph "Tests"
            T1["blocks_test.py"]:::infra
            T2["graphs_test.py"]:::infra
            T3["modules_test.py"]:::infra
            T4["test_utils.py"]:::infra
            T5["utils_np_test.py"]:::infra
            T6["utils_tf_test.py"]:::infra
            T7["blocks_test.py (TF2)"]:::infra
            T8["modules_test.py (TF2)"]:::infra
            T9["test_utils.py (TF2)"]:::infra
            T10["utils_tf_test.py (TF2)"]:::infra
        end
        DocTop["README.md / CONTRIBUTING.md / LICENSE"]:::infra
    end

    %% External Dependencies
    subgraph "External Dependencies"
        TF["TensorFlow"]:::external
        Sonnet["Sonnet"]:::external
        TFP["TensorFlow Probability"]:::external
        Python["Python runtime"]:::external
    end

    %% User Code
    User["User Code"]:::external

    %% Connections
    User -->|imports| GT
    GT -->|constructs| Modules
    Modules -->|invokes| Blocks
    Modules -->|relies on| Base
    Modules -->|uses| UN
    Modules -->|uses| UT
    D1 -->|imports| GT
    D1 -->|calls| Modules
    D1 -->|depends on| TF
    D1 -->|depends on| Sonnet
    Setup -->|packages| GT
    Setup -->|distributes| Docs
    Setup -->|includes| Images
    Setup -->|installs into| Python
    TF -->|backend for| Modules
    Sonnet -->|backend for| Modules

    %% Click Events
    click GT "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/graphs.py"
    click UN "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/utils_np.py"
    click UT "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/utils_tf.py"
    click Base "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/_base.py"
    click Blocks "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/blocks.py"
    click Modules "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/modules.py"
    click D1 "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/demos/graph_nets_basics.ipynb"
    click D2 "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/demos/models.py"
    click D3 "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/demos/physics.ipynb"
    click D4 "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/demos/shortest_path.ipynb"
    click D5 "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/demos/sort.ipynb"
    click D6 "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/demos_tf2/graph_nets_basics.ipynb"
    click D7 "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/demos_tf2/models.py"
    click D8 "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/demos_tf2/sort.ipynb"
    click Docs "https://github.com/google-deepmind/graph_nets/tree/master/docs/"
    click Setup "https://github.com/google-deepmind/graph_nets/blob/master/setup.py"
    click Images "https://github.com/google-deepmind/graph_nets/tree/master/images/"
    click T1 "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/tests/blocks_test.py"
    click T2 "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/tests/graphs_test.py"
    click T3 "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/tests/modules_test.py"
    click T4 "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/tests/test_utils.py"
    click T5 "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/tests/utils_np_test.py"
    click T6 "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/tests/utils_tf_test.py"
    click T7 "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/tests_tf2/blocks_test.py"
    click T8 "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/tests_tf2/modules_test.py"
    click T9 "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/tests_tf2/test_utils.py"
    click T10 "https://github.com/google-deepmind/graph_nets/blob/master/graph_nets/tests_tf2/utils_tf_test.py"

    %% Styles
    classDef core fill:#AED6F1,stroke:#21618C
    classDef util fill:#A9DFBF,stroke:#196F3D
    classDef infra fill:#FAD7A0,stroke:#B9770E
    classDef demo fill:#F5CBA7,stroke:#A04000
    classDef external fill:#D5D8DC,stroke:#5D6D7E

```

-----
s
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