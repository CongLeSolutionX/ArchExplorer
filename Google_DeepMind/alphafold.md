---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/alphafold
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




# alphafold repo project
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
title: "alphafold repo project"
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
    %% Input & MSA Search Layer
    subgraph "Input & MSA Search"
        Pipeline["Protein Data Pipeline"]:::input
        Tools["MSA Tools"]:::input
    end

    %% Data & Feature Processing Layer
    subgraph "Data & Feature Processing"
        FProc["Feature Processing"]:::processing
        Common["Common Parsing"]:::processing
        Processed["Processed Features"]:::processing
    end

    %% Connect Input to Feature Processing
    Pipeline -->|"sends data"| FProc
    Pipeline -->|"sends data"| Common
    Tools -->|"provides MSA info"| FProc
    Tools -->|"provides MSA info"| Common
    FProc -->|"merges into"| Processed
    Common -->|"merges into"| Processed

    %% Neural Network Inference (with Evoformer)
    subgraph "Neural Network Inference (with Evoformer)"
        Evoformer["Evoformer Module"]:::network
        LS["Layer Stacking"]:::network
        Processed -->|"feeds features"| Evoformer
        Evoformer -->|"integrates results"| LS

        %% Deep Dive into Evoformer
        subgraph "Evoformer Deep Dive"
            MSA["MSA & Pair Representation"]:::deep
            TransBlock["Transformer Block<br>(attention, pair update, MSA update)"]:::deep
            Refined["Refined Features"]:::deep
            MSA -->|"processes"| TransBlock
            TransBlock -->|"iterative_recycling"| TransBlock
            TransBlock -->|"outputs"| Refined
        end
        Evoformer -->|"incorporates"| Refined
        LS -->|"applies stacking"| Evoformer
    end

    %% Geometry and Structure Prediction
    subgraph "Geometry & Structure Prediction"
        Geometry["Geometry Processing"]:::geometry
    end
    LS -->|"passes features"| Geometry

    %% Structure Assembly & Relaxation
    subgraph "Structure Assembly & Relaxation"
        Relax["Relaxation Module"]:::relax
    end
    Geometry -->|"feeds geometry"| Relax

    %% Output Generation
    Output["Output Generation<br>(PDB models, rankings, features)"]:::processing
    Relax -->|"finalizes structure"| Output

    %% Deployment & Monitoring
    subgraph "Deployment & Monitoring"
        Docker["Docker Container"]:::deploy
        Scripts["Deployment Scripts"]:::deploy
        Container["Container Deployment"]:::deploy
        Docker -->|"builds"| Container
        Scripts -->|"orchestrates"| Container
    end
    Output -->|"delivers results to"| Container

    %% Click Events
    click Pipeline "https://github.com/google-deepmind/alphafold/blob/main/alphafold/data/pipeline.py"
    click Tools "https://github.com/google-deepmind/alphafold/tree/main/alphafold/data/tools"
    click FProc "https://github.com/google-deepmind/alphafold/blob/main/alphafold/data/feature_processing.py"
    click Common "https://github.com/google-deepmind/alphafold/tree/main/alphafold/common"
    click Evoformer "https://github.com/google-deepmind/alphafold/blob/main/alphafold/model/modules.py"
    click LS "https://github.com/google-deepmind/alphafold/blob/main/alphafold/model/layer_stack.py"
    click Geometry "https://github.com/google-deepmind/alphafold/tree/main/alphafold/model/geometry"
    click Relax "https://github.com/google-deepmind/alphafold/tree/main/alphafold/relax"
    click Docker "https://github.com/google-deepmind/alphafold/tree/main/docker"
    click Scripts "https://github.com/google-deepmind/alphafold/tree/main/scripts"

    %% Styles
    classDef input fill:#f9c,stroke:#333,stroke-width:2px;
    classDef processing fill:#ccf,stroke:#333,stroke-width:2px;
    classDef network fill:#cfc,stroke:#333,stroke-width:2px;
    classDef deep fill:#fcf,stroke:#333,stroke-width:2px;
    classDef geometry fill:#ff9,stroke:#333,stroke-width:2px;
    classDef relax fill:#f99,stroke:#333,stroke-width:2px;
    classDef deploy fill:#9cf,stroke:#333,stroke-width:2px;
```

---

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