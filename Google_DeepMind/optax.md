---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: 
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




# optax repo project
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
title: "optax repo project"
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
    classDef runtime fill:#D0E6FF,stroke:#000,stroke-width:1px
    classDef tooling fill:#E1FFD6,stroke:#000,stroke-width:1px
    classDef packaging fill:#FFF3C4,stroke:#000,stroke-width:1px

    %% Runtime Components
    subgraph "Runtime Components"
        direction TB
        UserCode["User Code Examples"]:::runtime
        JAX["JAX (autodiff, JIT)"]:::runtime

        subgraph "Optax Core API"
            direction TB
            OptaxInit["optax/__init__.py"]:::runtime
            Base["base.py<br/>(Params, OptState, Updates)"]:::runtime
            UpdateCore["update.py<br/>(update logic)"]:::runtime
            ApplyUpdates["apply_updates"]:::runtime

            subgraph "Primitive Transforms<br/>(optax/_src)"
                direction TB
                Alias["alias.py"]:::runtime
                ClippingCore["clipping.py"]:::runtime
                CombineCore["combine.py"]:::runtime
                ConstrainCore["constrain.py"]:::runtime
                Factorized["factorized.py"]:::runtime
                LinAlg["linear_algebra.py"]:::runtime
                LineSearch["linesearch.py"]:::runtime
                Lookahead["lookahead.py"]:::runtime
                Numerics["numerics.py"]:::runtime
                ScheduleCore["schedule.py"]:::runtime
                TransformCore["transform.py"]:::runtime
                UtilsCore["utils.py"]:::runtime
                WrappersCore["wrappers.py"]:::runtime
            end

            subgraph "User-Facing API"
                direction TB
                OptaxTest["optax_test.py"]:::runtime
            end
        end

        subgraph "Transforms Subpackage"
            direction TB
            Accumulation["_accumulation.py"]:::runtime
            ClippingTrans["_clipping.py"]:::runtime
            CombiningTrans["_combining.py"]:::runtime
            Conditionality["_conditionality.py"]:::runtime
            Constraining["_constraining.py"]:::runtime
            Freezing["_freezing.py"]:::runtime
            Layouts["_layouts.py"]:::runtime
            Masking["_masking.py"]:::runtime
            Adding["_adding.py"]:::runtime
        end

        subgraph "Category Modules"
            direction TB
            Losses["optax/losses"]:::runtime
            Schedules["optax/schedules"]:::runtime
            Projections["optax/projections"]:::runtime
            Perturbations["optax/perturbations"]:::runtime
            MonteCarlo["optax/monte_carlo"]:::runtime
            SecondOrder["optax/second_order"]:::runtime
        end

        subgraph "Contrib Extensions"
            direction TB
            Contrib["optax/contrib"]:::runtime
        end

        subgraph "Data Structures & Tree Utils"
            direction TB
            TreeUtils["optax/tree_utils"]:::runtime
            PyTree["optax/tree"]:::runtime
        end
    end

    %% Tooling Components
    subgraph "Development Tooling"
        direction TB
        Tests["test.sh & pytest"]:::tooling
        Docs["docs/ (Sphinx)"]:::tooling
        CI[".github/workflows"]:::tooling
    end

    %% Packaging
    subgraph "Packaging & Config"
        direction TB
        PyProject["pyproject.toml"]:::packaging
        PreCommit[".pre-commit-config.yaml"]:::packaging
    end

    %% Data Flow
    UserCode -->|"init(params)"| OptaxInit
    OptaxInit --> Base
    Base -->|"OptState"| UserCode
    UserCode -->|"compute grads"| JAX
    JAX -->|"grads"| UpdateCore
    UpdateCore --> PrimitiveTransforms
    PrimitiveTransforms --> CombineCore
    CombineCore --> UpdateCore
    UpdateCore -->|"Updates & OptState"| ApplyUpdates
    ApplyUpdates --> UserCode

    %% Testing & Documentation & CI
    Tests --> OptaxCore.APIUndefined
    Docs --> OptaxCore.APIUndefined
    CI --> Tests
    CI --> Docs

    %% Packaging flow
    CI --> PyProject
    CI --> PreCommit

    %% Click events
    click UserCode "https://github.com/google-deepmind/optax/tree/main/examples/"
    click OptaxInit "https://github.com/google-deepmind/optax/blob/main/optax/__init__.py"
    click Base "https://github.com/google-deepmind/optax/blob/main/optax/_src/base.py"
    click UpdateCore "https://github.com/google-deepmind/optax/blob/main/optax/_src/update.py"
    click ApplyUpdates "https://github.com/google-deepmind/optax/blob/main/optax/_src/utils.py"
    click Alias "https://github.com/google-deepmind/optax/blob/main/optax/_src/alias.py"
    click ClippingCore "https://github.com/google-deepmind/optax/blob/main/optax/_src/clipping.py"
    click CombineCore "https://github.com/google-deepmind/optax/blob/main/optax/_src/combine.py"
    click ConstrainCore "https://github.com/google-deepmind/optax/blob/main/optax/_src/constrain.py"
    click Factorized "https://github.com/google-deepmind/optax/blob/main/optax/_src/factorized.py"
    click LinAlg "https://github.com/google-deepmind/optax/blob/main/optax/_src/linear_algebra.py"
    click LineSearch "https://github.com/google-deepmind/optax/blob/main/optax/_src/linesearch.py"
    click Lookahead "https://github.com/google-deepmind/optax/blob/main/optax/_src/lookahead.py"
    click Numerics "https://github.com/google-deepmind/optax/blob/main/optax/_src/numerics.py"
    click ScheduleCore "https://github.com/google-deepmind/optax/blob/main/optax/_src/schedule.py"
    click TransformCore "https://github.com/google-deepmind/optax/blob/main/optax/_src/transform.py"
    click UtilsCore "https://github.com/google-deepmind/optax/blob/main/optax/_src/utils.py"
    click WrappersCore "https://github.com/google-deepmind/optax/blob/main/optax/_src/wrappers.py"
    click Accumulation "https://github.com/google-deepmind/optax/blob/main/optax/transforms/_accumulation.py"
    click ClippingTrans "https://github.com/google-deepmind/optax/blob/main/optax/transforms/_clipping.py"
    click CombiningTrans "https://github.com/google-deepmind/optax/blob/main/optax/transforms/_combining.py"
    click Conditionality "https://github.com/google-deepmind/optax/blob/main/optax/transforms/_conditionality.py"
    click Constraining "https://github.com/google-deepmind/optax/blob/main/optax/transforms/_constraining.py"
    click Freezing "https://github.com/google-deepmind/optax/blob/main/optax/transforms/_freezing.py"
    click Layouts "https://github.com/google-deepmind/optax/blob/main/optax/transforms/_layouts.py"
    click Masking "https://github.com/google-deepmind/optax/blob/main/optax/transforms/_masking.py"
    click Adding "https://github.com/google-deepmind/optax/blob/main/optax/transforms/_adding.py"
    click Losses "https://github.com/google-deepmind/optax/tree/main/optax/losses/"
    click Schedules "https://github.com/google-deepmind/optax/tree/main/optax/schedules/"
    click Projections "https://github.com/google-deepmind/optax/blob/main/optax/projections/_projections.py"
    click Perturbations "https://github.com/google-deepmind/optax/blob/main/optax/perturbations/_make_pert.py"
    click MonteCarlo "https://github.com/google-deepmind/optax/tree/main/optax/monte_carlo/"
    click SecondOrder "https://github.com/google-deepmind/optax/tree/main/optax/second_order/"
    click Contrib "https://github.com/google-deepmind/optax/tree/main/optax/contrib/"
    click TreeUtils "https://github.com/google-deepmind/optax/tree/main/optax/tree_utils/"
    click PyTree "https://github.com/google-deepmind/optax/tree/main/optax/tree/"
    click OptaxTest "https://github.com/google-deepmind/optax/blob/main/optax/optax_test.py"
    click Tests "https://github.com/google-deepmind/optax/blob/main/test.sh"
    click Docs "https://github.com/google-deepmind/optax/tree/main/docs/"
    click CI "https://github.com/google-deepmind/optax/tree/main/.github/workflows/"
    click PyProject "https://github.com/google-deepmind/optax/blob/main/pyproject.toml"
    click PreCommit "https://github.com/google-deepmind/optax/blob/main/.pre-commit-config.yaml"

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