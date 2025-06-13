---
created: 2025-06-012 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/simple-evals
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExcGhxenI1dzRuNGd6a3V5aTJjamNieGx3Nm9ta3puN3Jja2Jva3g0MSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/NKcbZoOFCnuzylpCOd/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# simple-evals repo project
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
title: "simple-evals repo project"
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
    subgraph "CLI Layer"
        CLI["CLI Interface\n(simple_evals.py)"]:::core
    end

    subgraph "Core Framework"
        Orch["Evaluation Manager / Orchestrator\n(common.py)"]:::core
        Types["Shared Types & Data Structures\n(types.py)"]:::core
    end

    subgraph "Benchmark Plugins"
        MMLU["MMLU Benchmark\n(mmlu_eval.py)"]:::plugin
        MATH["MATH Benchmark\n(math_eval.py)"]:::plugin
        GPQA["GPQA Benchmark\n(gpqa_eval.py)"]:::plugin
        DROP["DROP Benchmark\n(drop_eval.py)"]:::plugin
        HE["HumanEval Benchmark\n(humaneval_eval.py)"]:::plugin
        MGSM["MGSM Benchmark\n(mgsm_eval.py)"]:::plugin
        BC["BrowseComp Benchmark\n(browsecomp_eval.py)"]:::plugin
        SQA["SimpleQA Benchmark\n(simpleqa_eval.py)"]:::plugin
        HB["HealthBench Benchmark\n(healthbench_eval.py)"]:::plugin
        HBM["HealthBench Meta-Eval\n(healthbench_meta_eval.py)"]:::plugin
    end

    subgraph "Sampler Plugins"
        Base["Base Chat Completion Sampler\n(chat_completion_sampler.py)"]:::sampler
        OpenAI["OpenAI Chat Completion Sampler\n(o_chat_completion_sampler.py)"]:::sampler
        Claude["Anthropic Claude Sampler\n(claude_sampler.py)"]:::sampler
        Resp["Response-Based Sampler\n(responses_sampler.py)"]:::sampler
    end

    subgraph "External APIs"
        OpenAIAPI["OpenAI API"]:::external
        ClaudeAPI["Anthropic Claude API"]:::external
    end

    Analysis["HealthBench Analysis Notebook\n(healthbench_scripts/healthbench_analysis.ipynb)"]:::analysis

    CLI -->|"parses arguments"| Orch
    CLI -->|"uses types"| Types
    Orch -->|"loads eval plugins"| MMLU
    Orch --> MATH
    Orch --> GPQA
    Orch --> DROP
    Orch --> HE
    Orch --> MGSM
    Orch --> BC
    Orch --> SQA
    Orch --> HB
    Orch --> HBM
    Orch -->|"uses types"| Types
    MMLU -->|"calls sampler"| Base
    MATH --> Base
    GPQA --> Base
    DROP --> Base
    HE --> Base
    MGSM --> Base
    BC --> Base
    SQA --> Base
    HB --> Base
    HBM --> Base
    Base -->|"extended by"| OpenAI
    Base -->|"extended by"| Claude
    Base -->|"extended by"| Resp
    OpenAI -->|"API request"| OpenAIAPI
    Claude -->|"API request"| ClaudeAPI
    MMLU -->|"returns metrics"| Orch
    MATH --> Orch
    GPQA --> Orch
    DROP --> Orch
    HE --> Orch
    MGSM --> Orch
    BC --> Orch
    SQA --> Orch
    HB --> Orch
    HBM --> Orch
    Orch -->|"aggregates results"| CLI
    CLI -->|"outputs reports"| CLI
    CLI -->|"optional analysis"| Analysis

    click CLI "https://github.com/openai/simple-evals/blob/main/simple_evals.py"
    click Orch "https://github.com/openai/simple-evals/blob/main/common.py"
    click Types "https://github.com/openai/simple-evals/blob/main/types.py"
    click MMLU "https://github.com/openai/simple-evals/blob/main/mmlu_eval.py"
    click MATH "https://github.com/openai/simple-evals/blob/main/math_eval.py"
    click GPQA "https://github.com/openai/simple-evals/blob/main/gpqa_eval.py"
    click DROP "https://github.com/openai/simple-evals/blob/main/drop_eval.py"
    click HE "https://github.com/openai/simple-evals/blob/main/humaneval_eval.py"
    click MGSM "https://github.com/openai/simple-evals/blob/main/mgsm_eval.py"
    click BC "https://github.com/openai/simple-evals/blob/main/browsecomp_eval.py"
    click SQA "https://github.com/openai/simple-evals/blob/main/simpleqa_eval.py"
    click HB "https://github.com/openai/simple-evals/blob/main/healthbench_eval.py"
    click HBM "https://github.com/openai/simple-evals/blob/main/healthbench_meta_eval.py"
    click Base "https://github.com/openai/simple-evals/blob/main/sampler/chat_completion_sampler.py"
    click OpenAI "https://github.com/openai/simple-evals/blob/main/sampler/o_chat_completion_sampler.py"
    click Claude "https://github.com/openai/simple-evals/blob/main/sampler/claude_sampler.py"
    click Resp "https://github.com/openai/simple-evals/blob/main/sampler/responses_sampler.py"
    click Analysis "https://github.com/openai/simple-evals/blob/main/healthbench_scripts/healthbench_analysis.ipynb"

    classDef core fill:#CCE5FF,stroke:#3399FF,color:#003366,stroke-width:2px;
    classDef plugin fill:#E6FFE6,stroke:#33CC33,color:#006600,stroke-width:2px;
    classDef sampler fill:#FFF5CC,stroke:#FFCC00,color:#665500,stroke-width:2px;
    classDef external fill:#FFE6E6,stroke:#FF6666,color:#660000,stroke-width:2px;
    classDef analysis fill:#F0E6FF,stroke:#9933CC,color:#330066,stroke-width:2px;

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
