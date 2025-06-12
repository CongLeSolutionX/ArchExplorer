---
created: 2025-06-012 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/mle-bench
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExY2tvYWIyOGRpbWZodTQ2YTI2bjQ1eHpoaDY0YTZ3Mms2aWhneHNlYSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/fR6aYF0SUJAeoypyub/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# mle-bench repo project
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


```mermaid
---
title: "mle-bench repo project"
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
    subgraph "CLI Layer"
        CLI["mlebench CLI"]:::cli
        PyProj["pyproject.toml"]:::cli
    end

    %% Core Library
    subgraph "Core Library (Backend Service)"
        Reg["Competition Registry & Config"]:::core
        CompDefs["Competition Definitions & Grading Hooks"]:::core
        DataPrep["Data Preparation Module"]:::core
        Utils["Utility Functions"]:::core
        GradeCore["Grading Core Logic"]:::core
        GradeHelp["Grading Helper Functions"]:::core
        Metrics["Metrics Utilities"]:::core
    end

    %% Data Storage
    subgraph "Local Data Storage"
        RawCache["Raw Kaggle Data (Git-LFS Cache)"]:::storage
        PreparedCache["Prepared Splits"]:::storage
        Splits["Experiment Splits Definitions"]:::storage
    end

    %% External Service
    Kaggle["Kaggle API"]:::external

    %% Docker Environments
    subgraph "Docker Environments"
        subgraph "Base Environment"
            EnvImage["Base Env Image"]:::container
            GradingServ["Grading Server"]:::container
        end
        subgraph "Agent Containers"
            AgentReg["Agent Plugin Registry & Runner"]:::container
            AgentsRun["Agent Launch Script"]:::container
            AIDE["Agent: aide"]:::container
            Dummy["Agent: dummy"]:::container
            MLAgent["Agent: mlagentbench"]:::container
            OpenDevIn["Agent: opendevin"]:::container
            AgentUtils["Agent Utility Functions"]:::container
        end
    end

    %% Outputs & Reports
    Submission["Submission Files (JSONL/CSV)"]:::storage
    Reports["Grading Reports"]:::storage
    RunsStore["Recorded Outputs & Reports Store"]:::storage

    %% Tests
    subgraph "Tests"
        UnitTests["Unit Tests"]:::core
        IntTests["Integration Tests"]:::core
    end

    %% Relationships
    CLI -->|"invokes data-prep"| DataPrep
    DataPrep -->|"downloads raw data"| Kaggle
    Kaggle -->|"stores raw data"| RawCache
    DataPrep -->|"writes splits"| PreparedCache
    PreparedCache --> Splits

    CLI -->|"builds & runs env"| EnvImage
    CLI -->|"builds & runs grading server"| GradingServ

    CLI -->|"builds & runs agents"| AgentReg
    AgentReg --> AgentsRun
    AgentsRun --> AIDE
    AgentsRun --> Dummy
    AgentsRun --> MLAgent
    AgentsRun --> OpenDevIn
    AIDE --> Submission
    Dummy --> Submission
    MLAgent --> Submission
    OpenDevIn --> Submission

    CLI -->|"collects submissions"| Submission
    CLI -->|"invokes grading"| GradeCore
    GradeCore --> GradingServ
    GradingServ -->|"returns report"| Reports
    Reports --> RunsStore

    %% Core internal links
    CLI --> Reg
    CLI --> CompDefs
    CLI --> Utils
    CLI --> GradeHelp
    CLI --> Metrics

    %% Tests relations
    UnitTests --> DataPrep
    UnitTests --> GradeCore
    IntTests --> CLI
    IntTests --> GradingServ

    %% Click Events
    click CLI "https://github.com/openai/mle-bench/blob/main/mlebench/cli.py"
    click PyProj "https://github.com/openai/mle-bench/blob/main/pyproject.toml"
    click Reg "https://github.com/openai/mle-bench/blob/main/mlebench/registry.py"
    click CompDefs "https://github.com/openai/mle-bench/tree/main/mlebench/competitions/"
    click DataPrep "https://github.com/openai/mle-bench/blob/main/mlebench/data.py"
    click Utils "https://github.com/openai/mle-bench/blob/main/mlebench/utils.py"
    click GradeCore "https://github.com/openai/mle-bench/blob/main/mlebench/grade.py"
    click GradeHelp "https://github.com/openai/mle-bench/blob/main/mlebench/grade_helpers.py"
    click Metrics "https://github.com/openai/mle-bench/blob/main/mlebench/metrics.py"
    click EnvImage "https://github.com/openai/mle-bench/tree/main/environment/Dockerfile"
    click GradingServ "https://github.com/openai/mle-bench/blob/main/environment/grading_server.py"
    click AgentReg "https://github.com/openai/mle-bench/blob/main/agents/registry.py"
    click AgentsRun "https://github.com/openai/mle-bench/blob/main/agents/run.py"
    click AgentUtils "https://github.com/openai/mle-bench/blob/main/agents/utils.py"
    click AIDE "https://github.com/openai/mle-bench/tree/main/agents/aide/Dockerfile"
    click Dummy "https://github.com/openai/mle-bench/tree/main/agents/dummy/Dockerfile"
    click MLAgent "https://github.com/openai/mle-bench/tree/main/agents/mlagentbench/Dockerfile"
    click OpenDevIn "https://github.com/openai/mle-bench/tree/main/agents/opendevin/Dockerfile"
    click RunsStore "https://github.com/openai/mle-bench/tree/main/runs/"

    %% Styles
    classDef cli fill:#ADD8E6,stroke:#333,stroke-width:1px
    classDef core fill:#90EE90,stroke:#333,stroke-width:1px
    classDef storage fill:#FFA500,stroke:#333,stroke-width:1px
    classDef container fill:#D8BFD8,stroke:#333,stroke-width:1px
    classDef external fill:#D3D3D3,stroke:#333,stroke-width:1px

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