---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google/sentencepiece
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




# sentencepiece repo project
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
title: "sentencepiece repo project"
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
    %% External Interfaces Layer
    subgraph Interfaces
        PY["Python API"]:::interface
        CLI["Command Line Interface"]:::interface
        CAPI["C++ API"]:::interface
    end

    %% Core Processing Layer
    subgraph Core
        PROC["Processor Interface"]:::core
        NORM["Normalization System"]:::core
        MI["Model Interface"]:::core
        TI["Trainer Interface"]:::core
    end

    %% Model Types Layer
    subgraph Models
        BPE["BPE Model"]:::model
        UNI["Unigram Model"]:::model
        CHAR["Character Model"]:::model
        WORD["Word Model"]:::model
    end

    %% Supporting Systems
    subgraph Support
        PROTO["Protocol Buffers"]:::support
        UNICODE["Unicode Processing"]:::support
        MF["Model Factory"]:::support
        TF["Trainer Factory"]:::support
    end

    %% Relationships
    PY --> PROC
    CLI --> PROC
    CAPI --> PROC
    
    PROC --> MI
    PROC --> NORM
    
    MI --> MF
    TI --> TF
    
    MF --> BPE
    MF --> UNI
    MF --> CHAR
    MF --> WORD
    
    TF --> BPE
    TF --> UNI
    TF --> CHAR
    TF --> WORD
    
    MI --> PROTO
    NORM --> UNICODE

    %% Styles
    classDef interface fill:#FFA500,stroke:#333,stroke-width:2px
    classDef core fill:#3498DB,stroke:#333,stroke-width:2px
    classDef model fill:#2ECC71,stroke:#333,stroke-width:2px
    classDef support fill:#95A5A6,stroke:#333,stroke-width:2px

    %% Click Events
    click PROC "https://github.com/google/sentencepiece/blob/master/src/sentencepiece_processor.h"
    click NORM "https://github.com/google/sentencepiece/blob/master/src/normalizer.h"
    click MI "https://github.com/google/sentencepiece/blob/master/src/model_interface.h"
    click TI "https://github.com/google/sentencepiece/blob/master/src/trainer_interface.h"
    click BPE "https://github.com/google/sentencepiece/blob/master/src/bpe_model.h"
    click UNI "https://github.com/google/sentencepiece/blob/master/src/unigram_model.h"
    click CHAR "https://github.com/google/sentencepiece/blob/master/src/char_model.h"
    click WORD "https://github.com/google/sentencepiece/blob/master/src/word_model.h"
    click PY "https://github.com/google/sentencepiece/blob/master/python/src/sentencepiece/sentencepiece.i"
    click PROTO "https://github.com/google/sentencepiece/blob/master/src/sentencepiece.proto"
    click UNICODE "https://github.com/google/sentencepiece/blob/master/src/unicode_script.h"
    click MF "https://github.com/google/sentencepiece/blob/master/src/model_factory.h"
    click TF "https://github.com/google/sentencepiece/blob/master/src/trainer_factory.h"


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