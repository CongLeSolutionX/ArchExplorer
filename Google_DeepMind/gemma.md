---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/gemma
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




# gemma repo project
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
title: "gemma repo project"
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
    subgraph "User Interaction"
        E["External Interface (notebooks/API)"]:::external
    end

    subgraph "Data Preprocessing"
        DP["Preprocessing (gemma/gm/data)"]:::data
        MM["Multi-modal Processing (gemma/multimodal)"]:::data
        V["Vision Processing (gemma/gm/vision)"]:::data
    end

    subgraph "Utility Support"
        U["Utilities (gemma/gm/utils)"]:::utilities
    end

    subgraph "Checkpoint & Model Initialization"
        CP["Checkpoint Loader (gemma/gm/ckpts)"]:::checkpoint
        subgraph "Model Components"
            NN["NN Module (gemma/gm/nn)"]:::model
            TR["Transformer (gemma/transformer.py)"]:::model
            LYR["Layers (gemma/layers.py)"]:::model
            PE["Positional Embeddings (gemma/positional_embeddings.py)"]:::model
        end
    end

    subgraph "Inference & Sampling"
        TS["Chat/Text Sampler (gemma/gm/text)"]:::inference
        EV["Evaluation (gemma/gm/evals)"]:::inference
    end

    subgraph "Fine-Tuning"
        PEFT["PEFT Module (gemma/peft)"]:::peft
    end

    %% Connections
    E -->|"input"| DP
    E -->|"input"| MM
    E -->|"input"| V

    DP -->|"processed"| CP
    MM -->|"processed"| CP
    V -->|"processed"| CP

    CP -->|"initializes"| NN
    CP -->|"initializes"| TR
    CP -->|"initializes"| LYR
    CP -->|"initializes"| PE

    U -->|"supports"| DP
    U -->|"supports"| NN

    NN -->|"generates"| TS
    TR -->|"generates"| EV

    TS -->|"output"| E
    EV -->|"output"| E

    TR -->|"fine-tunes"| PEFT
    PEFT -->|"modifies"| NN

    %% Click Events
    click NN "https://github.com/google-deepmind/gemma/tree/main/gemma/gm/nn"
    click TR "https://github.com/google-deepmind/gemma/blob/main/gemma/transformer.py"
    click LYR "https://github.com/google-deepmind/gemma/blob/main/gemma/layers.py"
    click PE "https://github.com/google-deepmind/gemma/blob/main/gemma/positional_embeddings.py"
    click CP "https://github.com/google-deepmind/gemma/tree/main/gemma/gm/ckpts"
    click DP "https://github.com/google-deepmind/gemma/tree/main/gemma/gm/data"
    click MM "https://github.com/google-deepmind/gemma/tree/main/gemma/multimodal"
    click V "https://github.com/google-deepmind/gemma/tree/main/gemma/gm/vision"
    click TS "https://github.com/google-deepmind/gemma/tree/main/gemma/gm/text"
    click EV "https://github.com/google-deepmind/gemma/tree/main/gemma/gm/evals"
    click PEFT "https://github.com/google-deepmind/gemma/tree/main/gemma/peft"
    click U "https://github.com/google-deepmind/gemma/tree/main/gemma/gm/utils"

    %% Styles
    classDef external fill:#ffcccc,stroke:#333,stroke-width:2px;
    classDef data fill:#ccffcc,stroke:#333,stroke-width:2px;
    classDef checkpoint fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef model fill:#ccccff,stroke:#333,stroke-width:2px;
    classDef inference fill:#ffffcc,stroke:#333,stroke-width:2px;
    classDef peft fill:#d9ccff,stroke:#333,stroke-width:2px;
    classDef utilities fill:#e6e6fa,stroke:#333,stroke-width:2px;

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