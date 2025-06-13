---
created: 2025-06-12 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/swarm
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExdXpjdmt3Mzk4aXRqaHRjczNwNmNydDV5dGJvbnA2c25ybmRqcmhrZyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/yb9B8kpH1oCqKHd8kW/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# swarm repo project
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
title: "swarm repo project"
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
    subgraph Application
        ClientApps["Client Applications"]:::app
        Examples["Basic Examples & Patterns"]:::app
        CustomImpl["Custom Implementations"]:::app
    end

    subgraph SwarmCore["Swarm Core Layer"]
        SwarmClient["Swarm Client"]:::core
        AgentSystem["Agent System"]:::core
        MessageHandler["Message Handler"]:::core
        ContextManager["Context Variable Manager"]:::core
        FunctionEngine["Function Execution Engine"]:::core
        StreamHandler["Streaming Handler"]:::core
        TypesRegistry["Types & Function Registry"]:::core
        Utils["Utility Functions"]:::core
        REPL["REPL Interface"]:::core
    end

    subgraph Integration
        OpenAI["OpenAI API Interface"]:::external
        ChatAPI["Chat Completions API"]:::external
        ToolsRegistry["Tools/Functions Registry"]:::external
    end

    %% Relationships
    ClientApps --> SwarmClient
    Examples --> SwarmClient
    CustomImpl --> SwarmClient

    SwarmClient --> AgentSystem
    SwarmClient --> MessageHandler
    SwarmClient --> ContextManager
    SwarmClient --> FunctionEngine

    AgentSystem --> MessageHandler
    MessageHandler --> ContextManager
    MessageHandler --> FunctionEngine
    FunctionEngine --> StreamHandler

    FunctionEngine --> OpenAI
    OpenAI --> ChatAPI
    FunctionEngine --> ToolsRegistry

    %% Click Events
    click SwarmClient "https://github.com/openai/swarm/blob/main/swarm/core.py"
    click MessageHandler "https://github.com/openai/swarm/blob/main/swarm/core.py"
    click TypesRegistry "https://github.com/openai/swarm/blob/main/swarm/types.py"
    click Utils "https://github.com/openai/swarm/blob/main/swarm/util.py"
    click REPL "https://github.com/openai/swarm/blob/main/swarm/repl/repl.py"
    click StreamHandler "https://github.com/openai/swarm/blob/main/examples/customer_service_streaming/src/swarm/engines/engine.py"
    click ToolsRegistry "https://github.com/openai/swarm/tree/main/examples/customer_service_streaming/configs/tools/"
    click AgentSystem "https://github.com/openai/swarm/blob/main/examples/customer_service_streaming/src/swarm/assistants.py"
    click FunctionEngine "https://github.com/openai/swarm/blob/main/examples/customer_service_streaming/src/swarm/engines/local_engine.py"
    click Examples "https://github.com/openai/swarm/tree/main/examples/basic/"
    click ContextManager "https://github.com/openai/swarm/blob/main/examples/basic/context_variables.py"
    click FunctionEngine "https://github.com/openai/swarm/blob/main/examples/basic/function_calling.py"

    %% Styles
    classDef core fill:#2374ab,stroke:#2374ab,color:#fff
    classDef external fill:#57a773,stroke:#57a773,color:#fff
    classDef app fill:#ffc857,stroke:#ffc857,color:#000

    %% Legend
    subgraph Legend
        CoreComponent["Core Component"]:::core
        ExternalService["External Service"]:::external
        ApplicationLayer["Application Layer"]:::app
    end

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
