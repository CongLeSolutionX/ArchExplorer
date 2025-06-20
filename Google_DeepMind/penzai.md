---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/penzai
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




# penzai repo project
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
title: "penzai repo project"
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
    %% External Dependencies
    subgraph "External Dependencies"
        JAX(("JAX (jax.numpy, jax.random, jax.tree_util)")):::external
        IPY(("IPython/Colab Display")):::external
    end

    %% Core Package
    subgraph "Core Utilities" 
        direction TB
        SELECTORS["selectors.py"]:::core
        NAMED_AXES["named_axes.py"]:::core
        PARTITIONING["partitioning.py"]:::core
        RANDOM_STREAM["random_stream.py"]:::core
        STRUCT["struct.py"]:::core
        SHAPECHECK["shapecheck.py"]:::core
        TREE_UTIL["tree_util.py"]:::core
        VARIABLES["variables.py"]:::core
    end

    %% Neural Network Library
    subgraph "Declarative NN Library" 
        direction TB
        LAYER["layer.py"]:::nn
        LINEAR_AFFINE["linear_and_affine.py"]:::nn
        ATTENTION["attention.py"]:::nn
        DROPOUT["dropout.py"]:::nn
        EMBEDDINGS["embeddings.py"]:::nn
        COMBINATORS["combinators.py"]:::nn
        GROUPING["grouping.py"]:::nn
        PARAMETERS["parameters.py"]:::nn
        LAYER_STACK["layer_stack.py"]:::nn
    end

    %% Models Package
    subgraph "Models Package"
        direction TB
        SIMPLE_MLP["simple_mlp.py"]:::models
        subgraph "Transformer" 
            direction TB
            MODEL_PARTS["model_parts.py"]:::models
            SAMPLING_MODE["sampling_mode.py"]:::models
            DECODING_LOOP["simple_decoding_loop.py"]:::models
            VARIANTS["variants/"]:::models
        end
    end

    %% Treescope Visualization
    subgraph "Treescope Visualization"
        direction TB
        FORMAT_UTIL["formatting_util.py"]:::viz
        REPR_LIB["repr_lib.py"]:::viz
        COMPAT_SETUP["_compatibility_setup.py"]:::viz
    end

    %% Toolshed Scripts
    subgraph "Toolshed Scripts"
        direction TB
        BASIC_TRAIN["basic_training.py"]:::toolshed
        GRAD_CHECK["gradient_checkpointing.py"]:::toolshed
        MODEL_REWIRE["model_rewiring.py"]:::toolshed
        UNFLAXIFY["unflaxify.py"]:::toolshed
        ISOLATE_SUB["isolate_submodel.py"]:::toolshed
        JIT_WRAP["jit_wrapper.py"]:::toolshed
        LORA["lora.py"]:::toolshed
    end

    %% Alias Namespace
    subgraph "Alias Namespace"
        direction TB
        PZ_NN["pz/nn.py"]:::alias
        PZ_TS["pz/ts.py"]:::alias
    end

    %% Deprecated & Experimental
    subgraph "Legacy & Experimental" 
        direction TB
        classDef dashed fill-opacity:0 stroke-dasharray: 5 5
        DEPRECATED["penzai/deprecated/v1/"]:::dashed
        EXPERIMENTAL["penzai/experimental/v2/"]:::dashed
    end

    %% Documentation & Notebooks
    DOCS[/docs/]:::docs
    NOTEBOOKS[/notebooks/]:::docs

    %% Relationships
    JAX -->|"calls/invokes"| SELECTORS
    JAX -->|"calls/invokes"| NAMED_AXES
    JAX -->|"calls/invokes"| PARTITIONING
    JAX -->|"calls/invokes"| RANDOM_STREAM
    JAX -->|"calls/invokes"| STRUCT
    JAX -->|"calls/invokes"| SHAPECHECK
    JAX -->|"calls/invokes"| TREE_UTIL
    JAX -->|"calls/invokes"| VARIABLES

    SELECTORS -->|"used by"| LAYER
    NAMED_AXES -->|"used by"| LAYER
    TREE_UTIL -->|"used by"| PARAMETERS

    LAYER -->|"depends on"| STRUCT
    LAYER -->|"depends on"| VARIABLES
    LINEAR_AFFINE -->|"combines"| LAYER
    ATTENTION -->|"combines"| LINEAR_AFFINE
    DROPOUT -->|"combines"| LAYER
    EMBEDDINGS -->|"combines"| LAYER
    COMBINATORS -->|"composes"| LAYER
    GROUPING -->|"organizes"| PARAMETERS
    LAYER_STACK -->|"stacks"| LAYER

    SIMPLE_MLP -->|"built on"| LAYER
    MODEL_PARTS -->|"built on"| ATTENTION
    SAMPLING_MODE -->|"built on"| MODEL_PARTS
    DECODING_LOOP -->|"built on"| SAMPLING_MODE
    VARIANTS -->|"extends"| MODEL_PARTS

    BASIC_TRAIN -->|"imports"| SELECTORS
    BASIC_TRAIN -->|"imports"| LAYER
    GRAD_CHECK -->|"imports"| RANDOM_STREAM
    MODEL_REWIRE -->|"imports"| TREE_UTIL
    UNFLAXIFY -->|"imports"| STRUCT
    ISOLATE_SUB -->|"imports"| PARAMETERS
    JIT_WRAP -->|"imports"| COMBINATORS
    LORA -->|"imports"| LINEAR_AFFINE

    FORMAT_UTIL -->|"imports"| TREE_UTIL
    REPR_LIB -->|"imports"| STRUCT
    COMPAT_SETUP -->|"hooks into"| IPY

    IPY -->|"hosts"| FORMAT_UTIL
    IPY -->|"hosts"| REPR_LIB

    PZ_NN -->|"alias for"| LAYER
    PZ_NN -->|"alias for"| COMBINATORS
    PZ_TS -->|"alias for"| FORMAT_UTIL
    PZ_TS -->|"alias for"| REPR_LIB

    DEPRECATED -.->|"optional"| SELECTORS
    DEPRECATED -.->|"optional"| LAYER
    EXPERIMENTAL -.->|"prototype"| SELECTORS
    EXPERIMENTAL -.->|"prototype"| LAYER

    DOCS -->|"documents"| SELECTORS
    DOCS -->|"documents"| LAYER
    NOTEBOOKS -->|"demos"| FORMAT_UTIL
    NOTEBOOKS -->|"demos"| LAYER

    %% Click Events
    click SELECTORS "https://github.com/google-deepmind/penzai/blob/main/penzai/core/selectors.py"
    click NAMED_AXES "https://github.com/google-deepmind/penzai/blob/main/penzai/core/named_axes.py"
    click PARTITIONING "https://github.com/google-deepmind/penzai/blob/main/penzai/core/partitioning.py"
    click RANDOM_STREAM "https://github.com/google-deepmind/penzai/blob/main/penzai/core/random_stream.py"
    click STRUCT "https://github.com/google-deepmind/penzai/blob/main/penzai/core/struct.py"
    click SHAPECHECK "https://github.com/google-deepmind/penzai/blob/main/penzai/core/shapecheck.py"
    click TREE_UTIL "https://github.com/google-deepmind/penzai/blob/main/penzai/core/tree_util.py"
    click VARIABLES "https://github.com/google-deepmind/penzai/blob/main/penzai/core/variables.py"

    click LAYER "https://github.com/google-deepmind/penzai/blob/main/penzai/nn/layer.py"
    click LINEAR_AFFINE "https://github.com/google-deepmind/penzai/blob/main/penzai/nn/linear_and_affine.py"
    click ATTENTION "https://github.com/google-deepmind/penzai/blob/main/penzai/nn/attention.py"
    click DROPOUT "https://github.com/google-deepmind/penzai/blob/main/penzai/nn/dropout.py"
    click EMBEDDINGS "https://github.com/google-deepmind/penzai/blob/main/penzai/nn/embeddings.py"
    click COMBINATORS "https://github.com/google-deepmind/penzai/blob/main/penzai/nn/combinators.py"
    click GROUPING "https://github.com/google-deepmind/penzai/blob/main/penzai/nn/grouping.py"
    click PARAMETERS "https://github.com/google-deepmind/penzai/blob/main/penzai/nn/parameters.py"
    click LAYER_STACK "https://github.com/google-deepmind/penzai/blob/main/penzai/nn/layer_stack.py"

    click SIMPLE_MLP "https://github.com/google-deepmind/penzai/blob/main/penzai/models/simple_mlp.py"
    click MODEL_PARTS "https://github.com/google-deepmind/penzai/blob/main/penzai/models/transformer/model_parts.py"
    click SAMPLING_MODE "https://github.com/google-deepmind/penzai/blob/main/penzai/models/transformer/sampling_mode.py"
    click DECODING_LOOP "https://github.com/google-deepmind/penzai/blob/main/penzai/models/transformer/simple_decoding_loop.py"
    click VARIANTS "https://github.com/google-deepmind/penzai/tree/main/penzai/models/transformer/variants/"

    click FORMAT_UTIL "https://github.com/google-deepmind/penzai/blob/main/penzai/treescope/formatting_util.py"
    click REPR_LIB "https://github.com/google-deepmind/penzai/blob/main/penzai/treescope/repr_lib.py"
    click COMPAT_SETUP "https://github.com/google-deepmind/penzai/blob/main/penzai/treescope/_compatibility_setup.py"

    click BASIC_TRAIN "https://github.com/google-deepmind/penzai/blob/main/penzai/toolshed/basic_training.py"
    click GRAD_CHECK "https://github.com/google-deepmind/penzai/blob/main/penzai/toolshed/gradient_checkpointing.py"
    click MODEL_REWIRE "https://github.com/google-deepmind/penzai/blob/main/penzai/toolshed/model_rewiring.py"
    click UNFLAXIFY "https://github.com/google-deepmind/penzai/blob/main/penzai/toolshed/unflaxify.py"
    click ISOLATE_SUB "https://github.com/google-deepmind/penzai/blob/main/penzai/toolshed/isolate_submodel.py"
    click JIT_WRAP "https://github.com/google-deepmind/penzai/blob/main/penzai/toolshed/jit_wrapper.py"
    click LORA "https://github.com/google-deepmind/penzai/blob/main/penzai/toolshed/lora.py"

    click PZ_NN "https://github.com/google-deepmind/penzai/blob/main/penzai/pz/nn.py"
    click PZ_TS "https://github.com/google-deepmind/penzai/blob/main/penzai/pz/ts.py"

    click DOCS "https://github.com/google-deepmind/penzai/tree/main/docs/"
    click NOTEBOOKS "https://github.com/google-deepmind/penzai/tree/main/notebooks/"

    %% Styles
    classDef core fill:#bfdfff,stroke:#3399ff
    classDef nn fill:#bfffbf,stroke:#33aa33
    classDef models fill:#e0b3ff,stroke:#8844cc
    classDef viz fill:#ffd9b3,stroke:#ff8c00
    classDef toolshed fill:#b3f2f2,stroke:#009999
    classDef alias fill:#f2e6b3,stroke:#999900
    classDef external fill:#e0e0e0,stroke:#888888,stroke-width:1px
    classDef docs fill:#fff5b3,stroke:#e6c200,stroke-width:1px
    classDef dashed fill:#ffffff,stroke:#cccccc,stroke-dasharray:5 5,stroke-width:1px
    class SELECTORS,NAMED_AXES,PARTITIONING,RANDOM_STREAM,STRUCT,SHAPECHECK,TREE_UTIL,VARIABLES core
    class LAYER,LINEAR_AFFINE,ATTENTION,DROPOUT,EMBEDDINGS,COMBINATORS,GROUPING,PARAMETERS,LAYER_STACK nn
    class SIMPLE_MLP,MODEL_PARTS,SAMPLING_MODE,DECODING_LOOP,VARIANTS models
    class FORMAT_UTIL,REPR_LIB,COMPAT_SETUP viz
    class BASIC_TRAIN,GRAD_CHECK,MODEL_REWIRE,UNFLAXIFY,ISOLATE_SUB,JIT_WRAP,LORA toolshed
    class PZ_NN,PZ_TS alias
    class JAX,IPY external
    class DOCS,NOTEBOOKS docs

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