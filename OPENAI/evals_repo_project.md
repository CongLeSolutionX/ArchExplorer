---
created: 2025-06-012 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/evals
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExNXd5azJ1dWk1eXBybnhrNXg4Zm9vbmo4bnNnczFlbjcxY3BzcHNjOSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/qzXuYR7fmrQpcOpvxt/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# evals repo project
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
title: "evals repo project"
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
    subgraph CLI
        CLI_Main["CLI Interface"]:::cli
        CLI_EvalSet["Eval Set CLI"]:::cli
    end

    subgraph Core["Core Components"]
        EvalEngine["Evaluation Engine"]:::core
        TaskState["Task State Manager"]:::core
        Metrics["Metrics Calculator"]:::core
        Results["Results Aggregator"]:::core
    end

    subgraph Registry["Registry System"]
        EvalReg["Eval Registry"]:::registry
        DataReg["Data Registry"]:::registry
        SolverReg["Solver Registry"]:::registry
        CompFnReg["Completion Function Registry"]:::registry
    end

    subgraph CompFns["Completion Functions"]
        OpenAIHandler["OpenAI Handler"]:::comp
        LangChain["LangChain Integration"]:::comp
        CoT["Chain-of-Thought"]:::comp
        Retrieval["Retrieval"]:::comp
    end

    subgraph Solvers
        BaseSolver["Base Solver Interface"]:::solver
        ProviderSolvers["Provider-specific Solvers"]:::solver
        HumanCLI["Human CLI Solver"]:::solver
        NestedSolvers["Nested Solvers"]:::solver
    end

    subgraph Support["Supporting Systems"]
        Logging["Logging System"]:::support
        APIInteg["API Integration"]:::support
        BaseClasses["Base Classes"]:::support
    end

    subgraph External["External Services"]
        OpenAI_API["OpenAI API"]:::external
        Storage["Data Storage"]:::external
    end

    CLI_Main --> EvalEngine
    CLI_EvalSet --> EvalEngine
    
    EvalEngine --> TaskState
    EvalEngine --> Metrics
    EvalEngine --> Results
    
    EvalEngine <--> Registry
    Registry --> CompFns
    Registry --> Solvers
    
    CompFns --> APIInteg
    APIInteg --> OpenAI_API
    
    Solvers <--> CompFns
    
    Results --> Logging
    Logging --> Storage

    %% Click Events
    click EvalEngine "https://github.com/openai/evals/blob/main/evals/eval.py"
    click EvalReg "https://github.com/openai/evals/tree/main/evals/registry/evals/"
    click DataReg "https://github.com/openai/evals/tree/main/evals/registry/data/"
    click SolverReg "https://github.com/openai/evals/tree/main/evals/registry/solvers/"
    click CompFnReg "https://github.com/openai/evals/tree/main/evals/registry/completion_fns/"
    click OpenAIHandler "https://github.com/openai/evals/blob/main/evals/completion_fns/openai.py"
    click LangChain "https://github.com/openai/evals/blob/main/evals/completion_fns/langchain_llm.py"
    click CoT "https://github.com/openai/evals/blob/main/evals/completion_fns/cot.py"
    click Retrieval "https://github.com/openai/evals/blob/main/evals/completion_fns/retrieval.py"
    click BaseSolver "https://github.com/openai/evals/blob/main/evals/solvers/solver.py"
    click ProviderSolvers "https://github.com/openai/evals/tree/main/evals/solvers/providers/"
    click HumanCLI "https://github.com/openai/evals/blob/main/evals/solvers/human_cli_solver.py"
    click NestedSolvers "https://github.com/openai/evals/tree/main/evals/solvers/nested/"
    click CLI_Main "https://github.com/openai/evals/blob/main/evals/cli/oaieval.py"
    click CLI_EvalSet "https://github.com/openai/evals/blob/main/evals/cli/oaievalset.py"
    click Logging "https://github.com/openai/evals/blob/main/evals/utils/log_utils.py"
    click APIInteg "https://github.com/openai/evals/blob/main/evals/api.py"
    click BaseClasses "https://github.com/openai/evals/blob/main/evals/base.py"
    click Metrics "https://github.com/openai/evals/blob/main/evals/metrics.py"
    click TaskState "https://github.com/openai/evals/blob/main/evals/task_state.py"

    %% Styling
    classDef core fill:#2374ab
    classDef registry fill:#48a9a6
    classDef comp fill:#4ea5d9
    classDef solver fill:#44cfcb
    classDef support fill:#9b5de5
    classDef external fill:#f15bb5
    classDef cli fill:#fee440

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
