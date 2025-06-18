---
created: 2025-06-12 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/openai-cua-sample-app
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




# openai-cua-sample-app repo project
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
title: "openai-cua-sample-app repo project"
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
    %% Core Components
    CLI["CLI"]:::internal
    AgentLoop["Agent Loop"]:::internal
    OpenAIAPI["OpenAI API"]:::external

    CLI -->|"start"| AgentLoop
    AgentLoop -->|"ModelCall"| OpenAIAPI
    OpenAIAPI -->|"ModelResponse"| AgentLoop

    %% Computer Abstraction and Implementations
    subgraph "Computer Abstraction & Implementations"
        ComputerInterface["Computer Interface"]:::internal
        LocalPlaywright["Local Playwright"]:::internal
        DockerImpl["Docker Implementation"]:::internal
        BrowserbaseImpl["Browserbase Implementation"]:::internal
        ScrapybaraImpl["Scrapybara Implementation"]:::internal
    end

    AgentLoop -->|"ActionCommand"| ComputerInterface
    ComputerInterface -->|"ExecuteAction"| AgentLoop

    ComputerInterface -->|"impl"| LocalPlaywright
    ComputerInterface -->|"impl"| DockerImpl
    ComputerInterface -->|"impl"| BrowserbaseImpl
    ComputerInterface -->|"impl"| ScrapybaraImpl

    %% Examples & Utility Scripts
    subgraph "Examples & Utilities"
        Example1["Function Calling Example"]:::example
        Example2["Playwright with Custom Functions"]:::example
        Example3["Weather Example"]:::example
        SimpleCUALoop["Simple CUA Loop"]:::example
    end

    CLI -->|"demoUsage"| Example1
    CLI -->|"demoUsage"| Example2
    CLI -->|"demoUsage"| Example3
    CLI -->|"demoUsage"| SimpleCUALoop

    %% Click Events
    click CLI "https://github.com/openai/openai-cua-sample-app/blob/main/cli.py"
    click AgentLoop "https://github.com/openai/openai-cua-sample-app/blob/main/agent/agent.py"
    click ComputerInterface "https://github.com/openai/openai-cua-sample-app/blob/main/computers/computer.py"
    click LocalPlaywright "https://github.com/openai/openai-cua-sample-app/blob/main/computers/local_playwright.py"
    click DockerImpl "https://github.com/openai/openai-cua-sample-app/blob/main/computers/docker.py"
    click BrowserbaseImpl "https://github.com/openai/openai-cua-sample-app/blob/main/computers/browserbase.py"
    click ScrapybaraImpl "https://github.com/openai/openai-cua-sample-app/blob/main/computers/scrapybara.py"
    click Example1 "https://github.com/openai/openai-cua-sample-app/blob/main/examples/function_calling_example.py"
    click Example2 "https://github.com/openai/openai-cua-sample-app/blob/main/examples/playwright_with_custom_functions.py"
    click Example3 "https://github.com/openai/openai-cua-sample-app/blob/main/examples/weather_example.py"
    click SimpleCUALoop "https://github.com/openai/openai-cua-sample-app/blob/main/simple_cua_loop.py"

    %% Styles
    classDef internal fill:#cce5ff,stroke:#004085,stroke-width:2px;
    classDef external fill:#f5c6cb,stroke:#721c24,stroke-width:2px;
    classDef example fill:#d4edda,stroke:#155724,stroke-width:2px;

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