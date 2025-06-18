---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/OpenBB-finance/openbb-ai
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExcXQyeTN2Z21qaTFmdXByeGFwb3hrZTFmdjZvM3E1cnE1ZnowczJsNCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/835tA5cRBwEch8YoTi/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# openbb-ai repo project
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
title: "openbb-ai repo project"
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
    %% Consumer Service Layer
    subgraph "Consumer Service" 
        direction TB
        HTTP["HTTP Endpoint\nPOST /query"]:::consumer
        AgentLogic["Agent Logic"]:::consumer
        LLMClient["LLM Client"]:::consumer
    end

    %% OpenBB SDK Library
    subgraph "OpenBB_AI SDK" 
        direction TB
        Models["Models Layer"]:::sdk
        Helpers["Helpers Layer"]:::sdk
        TestingUtils["Testing Utilities"]:::sdk
        PackageInit["Package Init"]:::sdk
    end

    %% Packaging & CI
    subgraph "Packaging & CI" 
        direction TB
        PyProject["pyproject.toml"]:::ci
        Readme["README.md"]:::ci
        LintCI["Lint Pipeline"]:::ci
        TestCI["Test Pipeline"]:::ci
        PublishCI["Publish Pipeline"]:::ci
    end

    %% External Systems
    subgraph "External Systems" 
        direction TB
        Workspace["OpenBB Workspace"]:::external
        LLMAPI["LLM API Service"]:::external
        WidgetAPI["Widget Data API"]:::external
    end

    %% Data Flows
    Workspace -->|"HTTP POST /query (QueryRequest JSON)"| HTTP
    HTTP -->|"Validate JSON"| Models
    HTTP -->|"Import helpers"| Helpers
    HTTP -->|"Invoke logic"| AgentLogic
    AgentLogic -->|"LLM API Call (streamed response)"| LLMClient
    LLMClient -->|"stream"| LLMAPI
    LLMAPI -->|"stream"| LLMClient
    LLMClient -->|"pass to helpers"| Helpers
    Helpers -->|"SSE: message_chunk, reasoning_step, table, chart, cite"| Workspace
    Helpers -->|"get_widget_data event"| Workspace
    Workspace -->|"Widget Data Callback"| WidgetAPI
    WidgetAPI -->|"JSON data"| HTTP
    HTTP -->|"SSE resume"| Helpers

    %% Click Events for SDK
    click Models "https://github.com/openbb-finance/openbb-ai/blob/main/openbb_ai/models.py"
    click Helpers "https://github.com/openbb-finance/openbb-ai/blob/main/openbb_ai/helpers.py"
    click TestingUtils "https://github.com/openbb-finance/openbb-ai/blob/main/openbb_ai/testing.py"
    click PackageInit "https://github.com/openbb-finance/openbb-ai/blob/main/openbb_ai/__init__.py"

    %% Click Events for Packaging & CI
    click PyProject "https://github.com/openbb-finance/openbb-ai/blob/main/pyproject.toml"
    click Readme "https://github.com/openbb-finance/openbb-ai/blob/main/README.md"
    click LintCI "https://github.com/openbb-finance/openbb-ai/blob/main/.github/workflows/lint.yml"
    click TestCI "https://github.com/openbb-finance/openbb-ai/blob/main/.github/workflows/test.yml"
    click PublishCI "https://github.com/openbb-finance/openbb-ai/blob/main/.github/workflows/publish.yml"

    %% Legend Styles
    classDef sdk fill:#cce5ff,stroke:#999,stroke-width:1px
    classDef consumer fill:#d4edda,stroke:#999,stroke-width:1px
    classDef external fill:#ffe5b4,stroke:#999,stroke-width:1px
    classDef ci fill:#f0f0f0,stroke:#999,stroke-width:1px
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
