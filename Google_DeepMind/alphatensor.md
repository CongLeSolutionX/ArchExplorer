---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/alphatensor
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




# alphatensor repo project
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
title: "alphatensor repo project"
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
    %% External Environments
    Colab("Google Colab"):::external
    CLI("Local CLI"):::external

    %% Shared Data Stores Section Title
    subgraph "Data Stores"
        direction TB
        AlgoDR["factorizations_r.npz"]:::datastore
        AlgoDF2["factorizations_f2.npz"]:::datastore
        NoneqData["alphatensor_14236_factorizations.npz"]:::datastore
    end

    %% Algorithms Pipeline
    subgraph "Algorithms Pipeline"
        direction TB
        AlgoDR
        AlgoDF2
        ExploreNotebook["explore_factorizations.ipynb"]:::notebook
    end

    AlgoDR -->|loads| ExploreNotebook
    AlgoDF2 -->|loads| ExploreNotebook
    Colab -->|interactive use| ExploreNotebook

    %% Benchmarking Pipeline
    subgraph "Benchmarking Pipeline"
        direction TB
        BenchmarkLoader["factorizations.py"]:::script
        BenchmarkRun["run_gpu_benchmark.py"]:::script
        BenchmarkTest["test_correctness.py"]:::script
        BenchmarkUtils["utils.py"]:::script
        RequirementsBM["requirements.txt"]:::script
    end

    AlgoDR -->|input data| BenchmarkLoader
    AlgoDF2 -->|input data| BenchmarkLoader
    BenchmarkLoader -->|provides data| BenchmarkRun
    BenchmarkLoader -->|provides data| BenchmarkTest
    BenchmarkRun -->|uses| BenchmarkUtils
    BenchmarkTest -->|uses| BenchmarkUtils
    CLI -->|execute scripts| BenchmarkRun
    CLI -->|execute scripts| BenchmarkTest

    %% Nonequivalence Pipeline
    subgraph "Nonequivalence Pipeline"
        direction TB
        NoneqData
        InspectNotebook["inspect_factorizations_notebook.ipynb"]:::notebook
    end

    NoneqData -->|loads| InspectNotebook
    Colab -->|interactive use| InspectNotebook

    %% Recombination Pipeline
    subgraph "Recombination Pipeline"
        direction TB
        RecombModule["recombination.py"]:::script
        SotaModule["sota.py"]:::script
        ExampleCLI["example.py"]:::script
        RecombTest["recombination_test.py"]:::script
        RequirementsRec["requirements.txt"]:::script
    end

    AlgoDR -->|base factorizations| RecombModule
    AlgoDF2 -->|base factorizations| RecombModule
    RecombModule -->|advanced algos| SotaModule
    RecombModule -->|provides API| ExampleCLI
    ExampleCLI -->|runs tests| RecombTest
    CLI -->|run example| ExampleCLI

    %% Click Events
    click AlgoDR "https://github.com/google-deepmind/alphatensor/blob/main/algorithms/factorizations_r.npz"
    click AlgoDF2 "https://github.com/google-deepmind/alphatensor/blob/main/algorithms/factorizations_f2.npz"
    click ExploreNotebook "https://github.com/google-deepmind/alphatensor/blob/main/algorithms/explore_factorizations.ipynb"
    click BenchmarkLoader "https://github.com/google-deepmind/alphatensor/blob/main/benchmarking/factorizations.py"
    click BenchmarkRun "https://github.com/google-deepmind/alphatensor/blob/main/benchmarking/run_gpu_benchmark.py"
    click BenchmarkTest "https://github.com/google-deepmind/alphatensor/blob/main/benchmarking/test_correctness.py"
    click BenchmarkUtils "https://github.com/google-deepmind/alphatensor/blob/main/benchmarking/utils.py"
    click InspectNotebook "https://github.com/google-deepmind/alphatensor/blob/main/nonequivalence/inspect_factorizations_notebook.ipynb"
    click NoneqData "https://github.com/google-deepmind/alphatensor/blob/main/nonequivalence/alphatensor_14236_factorizations.npz"
    click RecombModule "https://github.com/google-deepmind/alphatensor/blob/main/recombination/recombination.py"
    click SotaModule "https://github.com/google-deepmind/alphatensor/blob/main/recombination/sota.py"
    click ExampleCLI "https://github.com/google-deepmind/alphatensor/blob/main/recombination/example.py"
    click RecombTest "https://github.com/google-deepmind/alphatensor/blob/main/recombination/recombination_test.py"

    %% Styles
    classDef datastore fill:#f9f,stroke:#333,stroke-width:1px;
    classDef notebook fill:#ff9,stroke:#333,stroke-width:1px,stroke-dasharray: 5 5;
    classDef script fill:#9ff,stroke:#333,stroke-width:1px;
    classDef external fill:#fcf,stroke:#333,stroke-width:1px,stroke-dasharray: 5 5;

```

------


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