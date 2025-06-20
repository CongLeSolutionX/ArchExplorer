---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/open_spiel
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




# open_spiel repo project
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
title: "open_spiel repo project"
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
    %% Build System
    subgraph "Build System"
        CMakeRoot["CMakeLists.txt"]:::build
        CMakeCore["open_spiel/CMakeLists.txt"]:::build
        CMakeRoot --> CMakeCore
    end

    %% Core Engine & Artifacts
    CMakeCore --> Core["C++ Core Engine"]:::core
    Core --> Lib["libspiel (.so/.a)"]:::artifact

    %% Language Bindings
    subgraph "Bindings"
        PyBind["pybind11 modules"]:::bindings
        JuliaBind["Julia wrapper"]:::bindings
        RustBind["Rust bindings"]:::bindings
        GoBind["Go bindings"]:::bindings
    end
    Lib --> PyBind
    Lib --> JuliaBind
    Lib --> RustBind
    Lib --> GoBind

    %% Python Frontend Library
    subgraph "Python Frontend Library"
        PyAlg["Algorithms"]:::python
        PyBots["Bots"]:::python
        PyGames["Games API"]:::python
        PyMFG["Mean-Field Games"]:::python
        PyJAX["JAX support"]:::python
        PyTORCH["PyTorch support"]:::python
        PyTF["TensorFlow support"]:::python
        PyUtils["Utilities"]:::python
        PyExamples["Examples"]:::python
        PyPackage["setup.py / requirements.txt / MANIFEST.in"]:::python
    end
    PyBind --> PyAlg
    PyBind --> PyBots
    PyBind --> PyGames
    PyBind --> PyMFG
    PyBind --> PyJAX
    PyBind --> PyTORCH
    PyBind --> PyTF
    PyBind --> PyUtils
    PyBind --> PyExamples
    PyBind --> PyPackage

    %% Runtime Environment
    subgraph "Runtime Environment"
        PythonUser["Python / Jupyter Notebook"]:::env
    end
    PythonUser --> PyAlg
    PythonUser --> PyBots
    PythonUser --> PyGames
    PythonUser --> PyMFG
    PythonUser --> PyJAX
    PythonUser --> PyTORCH
    PythonUser --> PyTF
    PythonUser --> PyUtils

    %% External ML Frameworks
    subgraph "External ML Frameworks"
        Torch["PyTorch"]:::external
        TF["TensorFlow"]:::external
        JAX["JAX"]:::external
        ORTOOLS["OR-Tools"]:::external
    end
    PyTORCH --> Torch
    PyTF --> TF
    PyJAX --> JAX
    Core --> ORTOOLS

    %% Multilingual Clients
    subgraph "Multilingual Clients"
        JuliaClient["Julia Code"]:::client
        RustClient["Rust Code"]:::client
        GoClient["Go Code"]:::client
    end
    JuliaClient --> JuliaBind
    RustClient --> RustBind
    GoClient --> GoBind

    %% Documentation & Notebooks
    subgraph "Documentation & Notebooks"
        Docs["docs/"]:::docs
        Colab["open_spiel/colabs/"]:::docs
    end

    %% Click Events
    click Core "https://github.com/google-deepmind/open_spiel/tree/master/open_spiel/"
    click CMakeRoot "https://github.com/google-deepmind/open_spiel/blob/master/CMakeLists.txt"
    click CMakeCore "https://github.com/google-deepmind/open_spiel/blob/master/open_spiel/CMakeLists.txt"
    click PyBind "https://github.com/google-deepmind/open_spiel/tree/master/open_spiel/python/pybind11/"
    click JuliaBind "https://github.com/google-deepmind/open_spiel/tree/master/open_spiel/julia/wrapper/"
    click RustBind "https://github.com/google-deepmind/open_spiel/tree/master/open_spiel/rust/src/"
    click GoBind "https://github.com/google-deepmind/open_spiel/tree/master/open_spiel/go/"
    click PyAlg "https://github.com/google-deepmind/open_spiel/tree/master/open_spiel/python/algorithms/"
    click PyBots "https://github.com/google-deepmind/open_spiel/tree/master/open_spiel/python/bots/"
    click PyGames "https://github.com/google-deepmind/open_spiel/tree/master/open_spiel/python/games/"
    click PyMFG "https://github.com/google-deepmind/open_spiel/tree/master/open_spiel/python/mfg/"
    click PyJAX "https://github.com/google-deepmind/open_spiel/tree/master/open_spiel/python/jax/"
    click PyTORCH "https://github.com/google-deepmind/open_spiel/tree/master/open_spiel/python/pytorch/"
    click PyTF "https://github.com/google-deepmind/open_spiel/tree/master/open_spiel/python/algorithms/tf/"
    click PyUtils "https://github.com/google-deepmind/open_spiel/tree/master/open_spiel/python/utils/"
    click PyExamples "https://github.com/google-deepmind/open_spiel/tree/master/open_spiel/python/examples/"
    click PyPackage "https://github.com/google-deepmind/open_spiel/blob/master/setup.py"
    click Docs "https://github.com/google-deepmind/open_spiel/tree/master/docs/"
    click Colab "https://github.com/google-deepmind/open_spiel/tree/master/open_spiel/colabs/"

    %% Styles
    classDef build fill:#f9c,stroke:#333;
    classDef core fill:#ccf,stroke:#333;
    classDef artifact fill:#ace,stroke:#333;
    classDef bindings fill:#cfc,stroke:#333;
    classDef python fill:#fc9,stroke:#333;
    classDef env fill:#fcf,stroke:#333;
    classDef external fill:#ddd,stroke:#333;
    classDef client fill:#c9f,stroke:#333;
    classDef docs fill:#9cf,stroke:#333;

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