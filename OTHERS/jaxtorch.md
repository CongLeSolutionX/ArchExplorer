---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/nshepperd/jaxtorch
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


# nshepperd - jaxtorch repo project
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
title: "jaxtorch repo project"
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
    subgraph User_Layer["User Layer"]
    direction TB
        demo_ipynb["demo.ipynb"]:::user
        scripts_demo_py["scripts/demo.py"]:::user
        scripts_gpt_py["scripts/gpt.py"]:::user
        scripts_main_py["scripts/main.py"]:::user
        scripts_test_py["scripts/test.py"]:::user
        scripts_train_gpt_py["scripts/train_gpt.py"]:::user
    end

    subgraph Public_API["Public API<br/>(jaxtorch)"]
    direction TB
        init_pkg["jaxtorch/__init__.py"]:::api
        init_py["jaxtorch/init.py"]:::api
        version_py["jaxtorch/_version.py"]:::api
    end

    %% Neural-Network API
    subgraph Neural_Network_API["Neural-Network API<br/>(jaxtorch.nn)"]
    direction TB
        nn_init["jaxtorch/nn/__init__.py"]:::api
        modules_py["jaxtorch/nn/modules.py"]:::api
        functional_py["jaxtorch/nn/functional.py"]:::api
        nn_image_py["jaxtorch/nn/image.py"]:::api
    end

    subgraph Core_Engine["Core Engine"]
    direction TB
        core_py["jaxtorch/core.py"]:::core
        util_py["jaxtorch/_util.py"]:::core
        monkeypatches_py["jaxtorch/monkeypatches.py"]:::core
    end

    subgraph Serialization_Layer["Serialization Layer"]
    direction TB
        cbor_py["jaxtorch/cbor.py"]:::serial
    end

    subgraph Utilities["Utilities"]
    direction TB
        image_py["jaxtorch/image.py"]:::util
        pt_py["jaxtorch/pt.py"]:::util
    end

    subgraph External_Dependencies["External Dependencies"]
    direction TB
        JAX["JAX<br/>(jax.numpy, jax.jit, jax.grad)"]:::external
        CBORLib["CBOR Library"]:::external
        PyStd["Standard Python Libs"]:::external
    end

    %% Tests (Auxiliary)
    subgraph Tests["Tests<br/>(not runtime)"]
    direction TB
        test_image["test/test_image.py"]:::test
        test_init["test/test_init.py"]:::test
        test_modules["test/test_modules.py"]:::test
        test_nn["test/test_nn.py"]:::test
    end

    %% Relationships
    demo_ipynb -->|uses API| init_pkg
    scripts_demo_py -->|uses API| init_pkg
    scripts_gpt_py -->|uses API| init_pkg
    scripts_main_py -->|uses API| init_pkg
    scripts_test_py -->|uses API| init_pkg
    scripts_train_gpt_py -->|uses API| init_pkg

    init_pkg -->|imports| init_py
    init_pkg -->|imports| version_py
    init_pkg -->|loads| nn_init
    init_pkg -->|applies| monkeypatches_py

    nn_init -->|defines| modules_py
    nn_init -->|exposes| functional_py
    nn_init -->|exposes| nn_image_py

    modules_py -->|calls| functional_py
    modules_py -->|manages params via| core_py
    functional_py -->|wraps| JAX
    core_py -->|dispatches to| JAX
    core_py -->|uses helpers| util_py
    core_py -->|serializes via| cbor_py
    cbor_py -->|reads/writes| CBORLib

    %% image_py -->|provides| image utilities
    %% nn_image_py -->|provides| layer-specific ops

    pt_py -->|interop| PyStd

    %% Core monkeypatches
    monkeypatches_py -->|tweaks| JAX

    %% Class Definitions
    classDef user fill:#B3CDE3,stroke:#333,stroke-width:1px
    classDef api fill:#6495ED,stroke:#333,stroke-width:1px
    classDef core fill:#C3E6CB,stroke:#333,stroke-width:1px
    classDef serial fill:#D8BFD8,stroke:#333,stroke-width:1px
    classDef util fill:#DDDDDD,stroke:#333,stroke-width:1px
    classDef external fill:#FFF5BA,stroke:#333,stroke-width:1px
    classDef test fill:#EEEEEE,stroke:#999,stroke-dasharray: 5 5

    %% Click Events
    click demo_ipynb "https://github.com/nshepperd/jaxtorch/blob/master/demo.ipynb"
    click scripts_demo_py "https://github.com/nshepperd/jaxtorch/blob/master/scripts/demo.py"
    click scripts_gpt_py "https://github.com/nshepperd/jaxtorch/blob/master/scripts/gpt.py"
    click scripts_main_py "https://github.com/nshepperd/jaxtorch/blob/master/scripts/main.py"
    click scripts_test_py "https://github.com/nshepperd/jaxtorch/blob/master/scripts/test.py"
    click scripts_train_gpt_py "https://github.com/nshepperd/jaxtorch/blob/master/scripts/train_gpt.py"
    click init_pkg "https://github.com/nshepperd/jaxtorch/blob/master/jaxtorch/__init__.py"
    click init_py "https://github.com/nshepperd/jaxtorch/blob/master/jaxtorch/init.py"
    click version_py "https://github.com/nshepperd/jaxtorch/blob/master/jaxtorch/_version.py"
    click core_py "https://github.com/nshepperd/jaxtorch/blob/master/jaxtorch/core.py"
    click util_py "https://github.com/nshepperd/jaxtorch/blob/master/jaxtorch/_util.py"
    click monkeypatches_py "https://github.com/nshepperd/jaxtorch/blob/master/jaxtorch/monkeypatches.py"
    click nn_init "https://github.com/nshepperd/jaxtorch/blob/master/jaxtorch/nn/__init__.py"
    click modules_py "https://github.com/nshepperd/jaxtorch/blob/master/jaxtorch/nn/modules.py"
    click functional_py "https://github.com/nshepperd/jaxtorch/blob/master/jaxtorch/nn/functional.py"
    click nn_image_py "https://github.com/nshepperd/jaxtorch/blob/master/jaxtorch/nn/image.py"
    click cbor_py "https://github.com/nshepperd/jaxtorch/blob/master/jaxtorch/cbor.py"
    click image_py "https://github.com/nshepperd/jaxtorch/blob/master/jaxtorch/image.py"
    click pt_py "https://github.com/nshepperd/jaxtorch/blob/master/jaxtorch/pt.py"
    click test_image "https://github.com/nshepperd/jaxtorch/blob/master/test/test_image.py"
    click test_init "https://github.com/nshepperd/jaxtorch/blob/master/test/test_init.py"
    click test_modules "https://github.com/nshepperd/jaxtorch/blob/master/test/test_modules.py"
    click test_nn "https://github.com/nshepperd/jaxtorch/blob/master/test/test_nn.py"
```

----

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
