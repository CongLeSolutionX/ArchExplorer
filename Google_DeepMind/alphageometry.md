---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/alphageometry
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




# alphageometry repo project
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
title: "alphageometry repo project"
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
    %% CLI Layer
    subgraph "CLI / Orchestration"
        direction TB
        ALPHA["alphageometry.py"]:::cli
        RUNSH["run.sh"]:::cli
        DOWNLOADSH["download.sh"]:::cli
        RUNTESTSH["run_tests.sh"]:::cli
    end

    %% Configuration Layer
    subgraph "Configuration / Data"
        direction TB
        GIN["geometry_150M_generate.gin"]:::config
        DEFS["defs.txt"]:::config
        RULES["rules.txt"]:::config
    end

    %% Input Layer
    subgraph "Input Layer"
        direction TB
        PROB["problem.py"]:::symbol
        EXAMPLES["examples.txt"]:::config
        IMO["imo_ag_30.txt"]:::config
        JGEX["jgex_ag_231.txt"]:::config
    end

    %% Symbolic Engine
    subgraph "Symbolic Engine"
        direction TB
        GRAPHUTIL["graph_utils.py"]:::symbol
        GRAPH["graph.py"]:::symbol
        GEOM["geometry.py"]:::symbol
        NUM["numericals.py"]:::symbol
        DD["dd.py"]:::symbol
        AR["ar.py"]:::symbol
        TRACE["trace_back.py"]:::symbol
        DDAR["ddar.py"]:::symbol
        PRETTY["pretty.py"]:::symbol
    end

    %% ML Engine
    subgraph "ML Engine"
        direction TB
        TRANSFORMER["transformer_layer.py"]:::ml
        DECODER["decoder_stack.py"]:::ml
        MODELS["models.py"]:::ml
        LMINF["lm_inference.py"]:::ml
        BEAM["beam_search.py"]:::ml
    end

    %% External Dependencies
    subgraph "External Dependencies"
        direction TB
        MELIAD["Meliad Library"]:::external
        JAX["JAX/Flax"]:::external
        OTHERLIBS["TensorFlow, NumPy, SciPy, SentencePiece, Gin"]:::external
    end

    %% Data Artifacts
    subgraph "Model & Artifacts"
        direction TB
        CHECKPT["Model Checkpoint & Vocab"]:::config
    end

    %% Data Flow
    ALPHA -->|"load configs & flags"| GIN
    ALPHA -->|"read problem file"| PROB

    PROB -->|"parsed problem"| GRAPHUTIL
    GRAPHUTIL -->|"build proof graph"| GRAPH

    GRAPH -->|"initial graph state"| DDAR
    DEFS --> DDAR
    RULES --> DDAR

    DDAR -->|proof found| PRETTY
    PRETTY -->|"formatted proof"| OUTPUT["Console / Output File"]:::config

    DDAR -->|fail: export graph state| LMINF
    LMINF -->|"tokenized sequence"| BEAM
    BEAM -->|"auxiliary constructions"| DDAR

    %% ML model dependencies
    LMINF --> MODELS
    MODELS --> TRANSFORMER
    TRANSFORMER --> DECODER

    %% External
    DDAR -.-> MELIAD
    LMINF -.-> OTHERLIBS
    ALPHA -.-> JAX
    CHECKPT -.-> LMINF

    %% Click Events
    click ALPHA "https://github.com/google-deepmind/alphageometry/blob/main/alphageometry.py"
    click RUNSH "https://github.com/google-deepmind/alphageometry/blob/main/run.sh"
    click DOWNLOADSH "https://github.com/google-deepmind/alphageometry/blob/main/download.sh"
    click RUNTESTSH "https://github.com/google-deepmind/alphageometry/blob/main/run_tests.sh"
    click GIN "https://github.com/google-deepmind/alphageometry/blob/main/geometry_150M_generate.gin"
    click DEFS "https://github.com/google-deepmind/alphageometry/blob/main/defs.txt"
    click RULES "https://github.com/google-deepmind/alphageometry/blob/main/rules.txt"
    click PROB "https://github.com/google-deepmind/alphageometry/blob/main/problem.py"
    click EXAMPLES "https://github.com/google-deepmind/alphageometry/blob/main/examples.txt"
    click IMO "https://github.com/google-deepmind/alphageometry/blob/main/imo_ag_30.txt"
    click JGEX "https://github.com/google-deepmind/alphageometry/blob/main/jgex_ag_231.txt"
    click GRAPHUTIL "https://github.com/google-deepmind/alphageometry/blob/main/graph_utils.py"
    click GRAPH "https://github.com/google-deepmind/alphageometry/blob/main/graph.py"
    click GEOM "https://github.com/google-deepmind/alphageometry/blob/main/geometry.py"
    click NUM "https://github.com/google-deepmind/alphageometry/blob/main/numericals.py"
    click DD "https://github.com/google-deepmind/alphageometry/blob/main/dd.py"
    click AR "https://github.com/google-deepmind/alphageometry/blob/main/ar.py"
    click TRACE "https://github.com/google-deepmind/alphageometry/blob/main/trace_back.py"
    click DDAR "https://github.com/google-deepmind/alphageometry/blob/main/ddar.py"
    click PRETTY "https://github.com/google-deepmind/alphageometry/blob/main/pretty.py"
    click TRANSFORMER "https://github.com/google-deepmind/alphageometry/blob/main/transformer_layer.py"
    click DECODER "https://github.com/google-deepmind/alphageometry/blob/main/decoder_stack.py"
    click MODELS "https://github.com/google-deepmind/alphageometry/blob/main/models.py"
    click LMINF "https://github.com/google-deepmind/alphageometry/blob/main/lm_inference.py"
    click BEAM "https://github.com/google-deepmind/alphageometry/blob/main/beam_search.py"

    %% Styles
    classDef cli fill:#fdd,stroke:#f00
    classDef config fill:#ffd,stroke:#cc0
    classDef symbol fill:#ddf,stroke:#00f
    classDef ml fill:#dfd,stroke:#0a0
    classDef external fill:#eee,stroke:#888

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