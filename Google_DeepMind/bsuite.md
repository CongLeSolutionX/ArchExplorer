---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google-deepmind/bsuite
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




# bsuite repo project
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
title: "bsuite repo project"
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
    %% CLI / Orchestration
    subgraph "CLI / Orchestration" 
        direction TB
        SweepPy["sweep.py"]:::script
        RunGCP["run_on_gcp.sh"]:::script
        TestSh["test.sh"]:::script
    end

    %% Core API Layer
    subgraph "Core API Layer" 
        direction TB
        Init["__init__.py"]:::core
        Metadata["_metadata.py"]:::core
        BsuitePy["bsuite.py"]:::core
        SweepCore["sweep.py"]:::core
        SweepTest["sweep_test.py"]:::core
    end

    %% Experiment Definitions
    subgraph "Experiment Definitions" 
        direction TB
        ExpDir["bsuite/experiments/"]:::exp
        SumAnalysis["summary_analysis.py"]:::exp
        SumAnalysisTest["summary_analysis_test.py"]:::exp
    end

    %% Environments
    subgraph "Environments Implementation"
        direction TB
        EnvsDir["bsuite/environments/"]:::env
        EnvBase["base.py"]:::env
        EnvOthers["*.py"]:::env
    end

    %% Logging Subsystem
    subgraph "Logging Subsystem"
        direction TB
        LogDir["bsuite/logging/"]:::logging
        LogBase["base.py"]:::logging
        CsvLog["csv_logging.py"]:::logging
        SqliteLog["sqlite_logging.py"]:::logging
        TermLog["terminal_logging.py"]:::logging
        CsvLoad["csv_load.py"]:::logging
        SqlLoad["sqlite_load.py"]:::logging
    end

    %% Baseline Agents
    subgraph "Baseline Agents"
        direction TB
        BasDir["bsuite/baselines/"]:::baseline
        BasBase["base.py"]:::baseline
        BasExp["experiment.py"]:::baseline
        JaxDir["jax/"]:::baseline
        TfDir["tf/"]:::baseline
        RandomDir["random/"]:::baseline
        ThirdParty["third_party/"]:::baseline
        BasUtils["utils/"]:::baseline
    end

    %% Utility Modules
    subgraph "Utility Modules"
        direction TB
        UtilDir["bsuite/utils/"]:::util
        Datasets["datasets.py"]:::util
        GymWrap["gym_wrapper.py"]:::util
        Plotting["plotting.py"]:::util
        Smoothers["smoothers.py"]:::util
        Wrappers["wrappers.py"]:::util
    end

    %% Analysis & Reporting
    subgraph "Analysis & Reporting"
        direction TB
        Notebook["results.ipynb"]:::analysis
        ReportsDir["reports/"]:::analysis
    end

    %% Storage
    CSV["CSV Output"]:::storage
    SQLite["SQLite DB"]:::storage

    %% CI/CD Pipeline
    subgraph "CI/CD Pipeline"
        direction TB
        CIci[".github/workflows/ci.yml"]:::ci
        CIrel[".github/workflows/release.yml"]:::ci
    end

    %% Packaging & Metadata
    subgraph "Packaging & Installation"
        direction TB
        Setup["setup.py"]:::pkg
        Readme["README.md"]:::pkg
        License["LICENSE"]:::pkg
        Contrib["CONTRIBUTING.md"]:::pkg
        Gitignore[".gitignore"]:::pkg
    end

    %% Relationships
    SweepPy -->|invokes| BsuitePy
    RunGCP -->|invokes| SweepCore
    TestSh -->|runs tests| SweepTest

    BsuitePy -->|loads| ExpDir
    BsuitePy -->|loads| EnvsDir

    ExpDir -->|defines| EnvOthers
    EnvBase -->|base interface| EnvsDir

    EnvsDir -->|emits steps| LogBase
    CsvLog -->|writes| CSV
    SqliteLog -->|writes| SQLite
    TermLog -->|writes| Terminal

    BasExp -->|uses| BsuitePy
    BasDir -->|implements| BasExp
    JaxDir --> BasDir
    TfDir --> BasDir
    RandomDir --> BasDir
    ThirdParty --> BasDir
    BasUtils -->|helpers| BasDir

    UtilDir -->|adapts| EnvsDir
    GymWrap -->|wraps| EnvsDir
    Plotting -->|visualizes| CSV
    Smoothers -->|processes| CSV
    Wrappers -->|wraps| EnvsDir

    CSV -->|loaded by| Notebook
    SQLite -->|loaded by| Notebook
    Notebook -->|generates| ReportsDir

    CIci -->|tests| Init
    CIci -->|tests| ExpDir
    CIci -->|tests| LogDir
    CIrel -->|publishes| Setup

    Setup -->|includes| Init
    Readme -->|docs| Setup
    License -->|contains| Setup
    Contrib -->|guides| Setup

    %% Click Events
    click Init "https://github.com/google-deepmind/bsuite/blob/main/bsuite/__init__.py"
    click Metadata "https://github.com/google-deepmind/bsuite/blob/main/bsuite/_metadata.py"
    click BsuitePy "https://github.com/google-deepmind/bsuite/blob/main/bsuite/bsuite.py"
    click SweepCore "https://github.com/google-deepmind/bsuite/blob/main/bsuite/sweep.py"
    click SweepTest "https://github.com/google-deepmind/bsuite/blob/main/bsuite/sweep_test.py"
    click ExpDir "https://github.com/google-deepmind/bsuite/tree/main/bsuite/experiments/"
    click SumAnalysis "https://github.com/google-deepmind/bsuite/blob/main/bsuite/experiments/summary_analysis.py"
    click SumAnalysisTest "https://github.com/google-deepmind/bsuite/blob/main/bsuite/experiments/summary_analysis_test.py"
    click EnvsDir "https://github.com/google-deepmind/bsuite/tree/main/bsuite/environments/"
    click EnvBase "https://github.com/google-deepmind/bsuite/blob/main/bsuite/environments/base.py"
    click LogDir "https://github.com/google-deepmind/bsuite/tree/main/bsuite/logging/"
    click LogBase "https://github.com/google-deepmind/bsuite/blob/main/bsuite/logging/base.py"
    click CsvLog "https://github.com/google-deepmind/bsuite/blob/main/bsuite/logging/csv_logging.py"
    click SqliteLog "https://github.com/google-deepmind/bsuite/blob/main/bsuite/logging/sqlite_logging.py"
    click TermLog "https://github.com/google-deepmind/bsuite/blob/main/bsuite/logging/terminal_logging.py"
    click CsvLoad "https://github.com/google-deepmind/bsuite/blob/main/bsuite/logging/csv_load.py"
    click SqlLoad "https://github.com/google-deepmind/bsuite/blob/main/bsuite/logging/sqlite_load.py"
    click BasDir "https://github.com/google-deepmind/bsuite/tree/main/bsuite/baselines/"
    click BasBase "https://github.com/google-deepmind/bsuite/blob/main/bsuite/baselines/base.py"
    click BasExp "https://github.com/google-deepmind/bsuite/blob/main/bsuite/baselines/experiment.py"
    click JaxDir "https://github.com/google-deepmind/bsuite/tree/main/bsuite/baselines/jax/"
    click TfDir "https://github.com/google-deepmind/bsuite/tree/main/bsuite/baselines/tf/"
    click RandomDir "https://github.com/google-deepmind/bsuite/tree/main/bsuite/baselines/random/"
    click ThirdParty "https://github.com/google-deepmind/bsuite/tree/main/bsuite/baselines/third_party/"
    click BasUtils "https://github.com/google-deepmind/bsuite/tree/main/bsuite/baselines/utils/"
    click UtilDir "https://github.com/google-deepmind/bsuite/tree/main/bsuite/utils/"
    click Datasets "https://github.com/google-deepmind/bsuite/blob/main/bsuite/utils/datasets.py"
    click GymWrap "https://github.com/google-deepmind/bsuite/blob/main/bsuite/utils/gym_wrapper.py"
    click Plotting "https://github.com/google-deepmind/bsuite/blob/main/bsuite/utils/plotting.py"
    click Smoothers "https://github.com/google-deepmind/bsuite/blob/main/bsuite/utils/smoothers.py"
    click Wrappers "https://github.com/google-deepmind/bsuite/blob/main/bsuite/utils/wrappers.py"
    click Notebook "https://github.com/google-deepmind/bsuite/blob/main/bsuite/analysis/results.ipynb"
    click ReportsDir "https://github.com/google-deepmind/bsuite/tree/main/reports/"
    click CIci "https://github.com/google-deepmind/bsuite/blob/main/.github/workflows/ci.yml"
    click CIrel "https://github.com/google-deepmind/bsuite/blob/main/.github/workflows/release.yml"
    click Setup "https://github.com/google-deepmind/bsuite/blob/main/setup.py"
    click Readme "https://github.com/google-deepmind/bsuite/blob/main/README.md"
    click License "https://github.com/google-deepmind/bsuite/tree/main/LICENSE"
    click Contrib "https://github.com/google-deepmind/bsuite/blob/main/CONTRIBUTING.md"

    %% Styles
    classDef core fill:#bbdefb,stroke:#1e88e5,color:#0d47a1;
    classDef exp fill:#c8e6c9,stroke:#388e3c,color:#1b5e20;
    classDef env fill:#c8e6c9,stroke:#388e3c,color:#1b5e20;
    classDef logging fill:#fff9c4,stroke:#f9a825,color:#f57f17;
    classDef baseline fill:#ffe0b2,stroke:#fb8c00,color:#e65100;
    classDef util fill:#b2ebf2,stroke:#0097a7,color:#006064;
    classDef analysis fill:#e1bee7,stroke:#8e24aa,color:#4a148c;
    classDef storage fill:#d7ccc8,stroke:#5d4037,color:#3e2723,shape:cylinder;
    classDef script fill:#eeeeee,stroke:#616161,color:#212121,shape:parallelogram;
    classDef ci fill:#e0e0e0,stroke:#757575,color:#212121;
    classDef pkg fill:#f5f5f5,stroke:#9e9e9e,color:#212121;

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