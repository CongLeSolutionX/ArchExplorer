---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/deepmind-research
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




# deepmind-research repo project
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
title: "deepmind-research repo project"
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
    %% Developer Flow
    Dev["Developer Environment"]:::dev
    Dev -->|"git clone"| Clone["Clone Monorepo"]:::action
    Clone --> EnvSetup["Setup Virtual Env & Install Tools"]:::action
    EnvSetup --> SelectProj["Select Project Folder"]:::action
    SelectProj --> AR_Run
    SelectProj --> AVAE_Run
    SelectProj --> DFA_Run
    SelectProj --> WG_Main

    %% Monorepo Root
    subgraph "Monorepo Root"
        MR["Monorepo Root"]:::codePkg
        README["README.md"]:::doc
        TRAVIS[".travis.yml"]:::pipeline
        CONTRIB["CONTRIBUTING.md"]:::doc
        LIC["LICENSE"]:::doc
    end
    click README "https://github.com/google-deepmind/deepmind-research/blob/master/README.md"
    click TRAVIS "https://github.com/google-deepmind/deepmind-research/blob/master/.travis.yml"
    click CONTRIB "https://github.com/google-deepmind/deepmind-research/blob/master/CONTRIBUTING.md"
    click LIC "https://github.com/google-deepmind/deepmind-research/tree/master/LICENSE"

    %% CI/CD Pipeline
    GH["GitHub"]:::external
    GH -->|"push"| CICD["CI/CD Pipeline (TravisCI)"]:::pipeline
    click CICD "https://github.com/google-deepmind/deepmind-research/blob/master/.travis.yml"
    CICD -->|"checkout monorepo"| MR
    CICD -->|"install deps & run tests"| AR_Test
    CICD -->|"install deps & run tests"| AVAE_Test
    CICD -->|"install deps & run tests"| DFA_Test
    CICD -->|"install deps & run tests"| WG_Test
    CICD -->|"report status"| GH

    %% Adversarial Robustness Project
    subgraph "Adversarial Robustness" 
        AR_Code["Source (jax/*.py)"]:::codePkg
        AR_Test["Tests (jax/experiment_test.py)"]:::codePkg
        AR_PT["PyTorch variant"]:::codePkg
        AR_Req["requirements.txt"]:::codePkg
        AR_Run["run.sh"]:::action
    end
    click AR_Code "https://github.com/google-deepmind/deepmind-research/blob/master/adversarial_robustness/jax/*.py"
    click AR_Test "https://github.com/google-deepmind/deepmind-research/blob/master/adversarial_robustness/jax/experiment_test.py"
    click AR_PT "https://github.com/google-deepmind/deepmind-research/tree/master/adversarial_robustness/pytorch/"
    click AR_Req "https://github.com/google-deepmind/deepmind-research/blob/master/adversarial_robustness/requirements.txt"
    click AR_Run "https://github.com/google-deepmind/deepmind-research/blob/master/adversarial_robustness/run.sh"

    %% AVAE Project
    subgraph "AVAE"
        AVAE_Code["vae.py, train.py, train_main.py"]:::codePkg
        AVAE_Util["checkpointer, data_iterators, types"]:::codePkg
        AVAE_Req["requirements.txt"]:::codePkg
        AVAE_Run["run.sh"]:::action
        AVAE_Test["tests"]:::codePkg
    end
    click AVAE_Code "https://github.com/google-deepmind/deepmind-research/blob/master/avae/vae.py"
    click AVAE_Code "https://github.com/google-deepmind/deepmind-research/blob/master/avae/train.py"
    click AVAE_Code "https://github.com/google-deepmind/deepmind-research/blob/master/avae/train_main.py"
    click AVAE_Util "https://github.com/google-deepmind/deepmind-research/blob/master/avae/checkpointer.py"
    click AVAE_Util "https://github.com/google-deepmind/deepmind-research/blob/master/avae/data_iterators.py"
    click AVAE_Util "https://github.com/google-deepmind/deepmind-research/blob/master/avae/types.py"
    click AVAE_Req "https://github.com/google-deepmind/deepmind-research/blob/master/avae/requirements.txt"
    click AVAE_Run "https://github.com/google-deepmind/deepmind-research/blob/master/avae/run.sh"

    %% Density Functional Approximation DM21
    subgraph "Density Functional Approximation DM21"
        DFA_Bazel["BUILD.bazel, WORKSPACE.bazel, .bazelrc"]:::codePkg
        DFA_CPP["C++ examples (cc/*.cc, *.h)"]:::codePkg
        DFA_Py["Python package (*.py)"]:::codePkg
        DFA_CKPT["Checkpoints (data assets)"]:::data
        DFA_Req["requirements.txt, requirements_aot_compilation.txt"]:::codePkg
        DFA_Run["run.sh"]:::action
        DFA_Test["tests"]:::codePkg
    end
    click DFA_Bazel "https://github.com/google-deepmind/deepmind-research/blob/master/density_functional_approximation_dm21/BUILD.bazel"
    click DFA_Bazel "https://github.com/google-deepmind/deepmind-research/blob/master/density_functional_approximation_dm21/.bazelrc"
    click DFA_Bazel "https://github.com/google-deepmind/deepmind-research/blob/master/density_functional_approximation_dm21/WORKSPACE.bazel"
    click DFA_CPP "https://github.com/google-deepmind/deepmind-research/tree/master/density_functional_approximation_dm21/cc/"
    click DFA_Py "https://github.com/google-deepmind/deepmind-research/blob/master/density_functional_approximation_dm21/density_functional_approximation_dm21/*.py"
    click DFA_CKPT "https://github.com/google-deepmind/deepmind-research/tree/master/density_functional_approximation_dm21/density_functional_approximation_dm21/checkpoints/"
    click DFA_Req "https://github.com/google-deepmind/deepmind-research/blob/master/density_functional_approximation_dm21/requirements.txt"
    click DFA_Run "https://github.com/google-deepmind/deepmind-research/blob/master/density_functional_approximation_dm21/run.sh"

    %% WikiGraphs Project
    subgraph "WikiGraphs"
        WG_Main["main.py, setup.py"]:::codePkg
        WG_Scripts["scripts/*.py"]:::codePkg
        WG_Pkg["wikigraphs package"]:::codePkg
        WG_Data["data layer"]:::codePkg
        WG_Model["model layer"]:::codePkg
        WG_Req["requirements.txt"]:::codePkg
        WG_Test["tests"]:::codePkg
    end
    click WG_Main "https://github.com/google-deepmind/deepmind-research/blob/master/wikigraphs/main.py"
    click WG_Main "https://github.com/google-deepmind/deepmind-research/blob/master/wikigraphs/setup.py"
    click WG_Scripts "https://github.com/google-deepmind/deepmind-research/blob/master/wikigraphs/scripts/*.py"
    click WG_Pkg "https://github.com/google-deepmind/deepmind-research/tree/master/wikigraphs/wikigraphs/"
    click WG_Data "https://github.com/google-deepmind/deepmind-research/blob/master/wikigraphs/wikigraphs/data/*.py"
    click WG_Model "https://github.com/google-deepmind/deepmind-research/blob/master/wikigraphs/wikigraphs/model/*.py"
    click WG_Req "https://github.com/google-deepmind/deepmind-research/blob/master/wikigraphs/requirements.txt"

    %% External Services
    subgraph "External Hosts/Services"
        GH2["GitHub"]:::external
        TFH["TFHub"]:::external
        ExtData["External Dataset Hosts"]:::external
    end
    AR_Run -->|"download data"| ExtData
    AVAE_Run -->|"download data"| ExtData
    DFA_Run -->|"download checkpoints"| TFH
    WG_Scripts -->|"fetch data"| ExtData

    %% Styles
    classDef codePkg fill:#D6EAF8,stroke:#2874A6,color:#1B4F72;
    classDef data fill:#FCF3CF,stroke:#B7950B,color:#7D6608,stroke-dasharray: 5 5;
    classDef external fill:#EBDEF0,stroke:#8E44AD,color:#512E5F;
    classDef pipeline fill:#D5F5E3,stroke:#27AE60,color:#1D8348,stroke-width:2px;
    classDef dev fill:#FADBD8,stroke:#C0392B,color:#78281F;
    classDef action fill:#FDEBD0,stroke:#D35400,color:#7E5109;

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