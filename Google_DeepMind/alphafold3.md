---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/alphafold3
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




# alphafold3 repo project
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
title: "alphafold3 repo project"
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
    classDef database fill:#B8D4FF,stroke:#2E75B6
    classDef dataProcessing fill:#ADE8F4,stroke:#0077B6
    classDef modelComponent fill:#90EE90,stroke:#2D5A27
    classDef structureComponent fill:#FFE5B4,stroke:#FF8C00
    classDef utility fill:#D3D3D3,stroke:#808080

    subgraph Input
        InputJSON[Input JSON]:::utility
    end

    subgraph "Data Pipeline Layer"
        MSA["MSA Processing"]:::dataProcessing
        TemplateProc["Template Processing"]:::dataProcessing
        FeatureGen["Feature Generation"]:::dataProcessing
        ExtTools["External Tools Integration"]:::dataProcessing
    end

    subgraph "Database Layer"
        BFD[(BFD Database)]:::database
        PDB[(PDB Database)]:::database
        UniProt[(UniProt Database)]:::database
    end

    subgraph "Model Layer"
        Pipeline["Pipeline Processing"]:::modelComponent
        NeuralNet["Neural Network Components"]:::modelComponent
        subgraph "Network Components"
            Evoformer["Evoformer"]:::modelComponent
            DiffTrans["Diffusion Transformer"]:::modelComponent
        end
        Attention["Attention Mechanisms"]:::modelComponent
        Geometry["Geometry Processing"]:::modelComponent
        Confidence["Confidence Assessment"]:::modelComponent
    end

    subgraph "Structure Processing Layer"
        StructAnalysis["Structure Analysis"]:::structureComponent
        ChemComp["Chemical Component Processing"]:::structureComponent
        BondAnalysis["Bond Analysis"]:::structureComponent
        Scoring["Structure Scoring"]:::structureComponent
        PostProc["Post-Processing"]:::structureComponent
    end

    InputJSON --> MSA
    InputJSON --> TemplateProc
    MSA --> FeatureGen
    TemplateProc --> FeatureGen
    ExtTools --> FeatureGen

    BFD --> MSA
    PDB --> TemplateProc
    UniProt --> MSA

    FeatureGen --> Pipeline
    Pipeline --> NeuralNet
    NeuralNet --> Evoformer
    NeuralNet --> DiffTrans
    Evoformer --> Attention
    DiffTrans --> Attention
    Attention --> Geometry
    Geometry --> Confidence

    Confidence --> StructAnalysis
    StructAnalysis --> ChemComp
    ChemComp --> BondAnalysis
    BondAnalysis --> Scoring
    Scoring --> PostProc

    %% Click events for component mapping
    click MSA "https://github.com/google-deepmind/alphafold3/blob/main/src/alphafold3/data/msa.py"
    click TemplateProc "https://github.com/google-deepmind/alphafold3/blob/main/src/alphafold3/data/templates.py"
    click FeatureGen "https://github.com/google-deepmind/alphafold3/blob/main/src/alphafold3/data/featurisation.py"
    click ExtTools "https://github.com/google-deepmind/alphafold3/tree/main/src/alphafold3/data/tools/"
    click Evoformer "https://github.com/google-deepmind/alphafold3/blob/main/src/alphafold3/model/network/evoformer.py"
    click DiffTrans "https://github.com/google-deepmind/alphafold3/blob/main/src/alphafold3/model/network/diffusion_transformer.py"
    click Attention "https://github.com/google-deepmind/alphafold3/blob/main/src/alphafold3/jax/attention/attention.py"
    click Geometry "https://github.com/google-deepmind/alphafold3/tree/main/src/alphafold3/jax/geometry/"
    click Confidence "https://github.com/google-deepmind/alphafold3/blob/main/src/alphafold3/model/confidence_types.py"
    click StructAnalysis "https://github.com/google-deepmind/alphafold3/blob/main/src/alphafold3/structure/structure.py"
    click ChemComp "https://github.com/google-deepmind/alphafold3/blob/main/src/alphafold3/structure/chemical_components.py"
    click BondAnalysis "https://github.com/google-deepmind/alphafold3/blob/main/src/alphafold3/structure/bonds.py"
    click Pipeline "https://github.com/google-deepmind/alphafold3/blob/main/src/alphafold3/model/pipeline/pipeline.py"
    click PostProc "https://github.com/google-deepmind/alphafold3/blob/main/src/alphafold3/model/post_processing.py"
    click Scoring "https://github.com/google-deepmind/alphafold3/blob/main/src/alphafold3/model/scoring/scoring.py"
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