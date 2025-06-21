---
created: 2025-06-12 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/openai-agents-js
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExd2FzNXNqMHhiNmxqZ2JnNnk3eTF1cHY3eGI5aWVhMmNjYWhzcDV0MiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/7vUBOECvNpUOs/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# openai-agents-js repo project
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
title: "openai-agents-js repo project"
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
    Developer["Developer Application"]:::dev
    subgraph "Agents SDK (Monorepo)"
        Umbrella["Agents (Umbrella Package)"]:::sdk
        Core["Agents Core Engine"]:::sdk
        OpenAIProv["Model Provider - OpenAI"]:::sdk
        Extensions["Extensions (Twilio, AI SDK)"]:::sdk
        Realtime["Realtime Client (WebSocket/WebRTC)"]:::sdk
    end
    subgraph "External Services"
        OpenAIAPI["OpenAI API"]:::ext
        Twilio["Twilio"]:::ext
        MCP["Local MCP Server"]:::ext
    end
    Docs["Documentation Site"]:::docs
    Tests["Integration Tests"]:::tests
    Config["Monorepo Workspace Config"]:::config
    TSconf["TypeScript Configuration"]:::config
    VitestUnit["Vitest Unit Config"]:::config
    VitestInt["Vitest Integration Config"]:::config
    CI["CI/CD Workflows"]:::config

    Developer -->|imports| Umbrella
    Umbrella --> Core
    Umbrella --> OpenAIProv
    Umbrella --> Extensions
    Umbrella --> Realtime

    Core -->|invoke LLM| OpenAIProv
    OpenAIProv -->|HTTP/WS calls| OpenAIAPI
    Core -->|tool call| MCP
    Core -->|handoff| Core

    Realtime -->|stream events| Developer
    Realtime -->|connect| Twilio

    Core -->|emit traces| OpenAIProv
    OpenAIProv -->|export traces| TracingStorage["Tracing Storage/UI"]:::ext

    Developer --> Docs
    Developer --> Tests
    Developer --> Config
    Developer --> TSconf
    Developer --> VitestUnit
    Developer --> VitestInt
    Developer --> CI

    click Developer "https://github.com/openai/openai-agents-js/tree/main/examples/"
    click Umbrella "https://github.com/openai/openai-agents-js/tree/main/packages/agents/"
    click Core "https://github.com/openai/openai-agents-js/tree/main/packages/agents-core/"
    click OpenAIProv "https://github.com/openai/openai-agents-js/tree/main/packages/agents-openai/"
    click Extensions "https://github.com/openai/openai-agents-js/tree/main/packages/agents-extensions/"
    click Realtime "https://github.com/openai/openai-agents-js/tree/main/packages/agents-realtime/"
    click Docs "https://github.com/openai/openai-agents-js/tree/main/docs/"
    click Tests "https://github.com/openai/openai-agents-js/tree/main/integration-tests/"
    click Config "https://github.com/openai/openai-agents-js/blob/main/pnpm-workspace.yaml"
    click TSconf "https://github.com/openai/openai-agents-js/blob/main/tsconfig.json"
    click VitestUnit "https://github.com/openai/openai-agents-js/blob/main/vitest.config.ts"
    click VitestInt "https://github.com/openai/openai-agents-js/blob/main/vitest.integration.config.ts"
    click CI "https://github.com/openai/openai-agents-js/tree/main/.github/workflows/"

    classDef sdk fill:#e0f7fa,stroke:#006064,color:#006064
    classDef dev fill:#e8f5e9,stroke:#2e7d32,color:#2e7d32
    classDef ext fill:#fff3e0,stroke:#ef6c00,color:#e65100
    classDef docs fill:#eeeeee,stroke:#757575,color:#424242
    classDef tests fill:#f3e5f5,stroke:#6a1b9a,color:#4a148c
    classDef config fill:#e3f2fd,stroke:#1565c0,color:#0d47a1

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
