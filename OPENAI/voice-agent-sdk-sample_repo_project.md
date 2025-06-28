---
created: 2025-06-12 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/openai-voice-agent-sdk-sample
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExMnpncTQzMDg5NGNrYnYyMmdjbjN6N29uMTR0MW1scms5d2JkdG9oMiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zKAThXPf8zboY/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# voice-agent-sdk-sample repo project
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
title: "openai_voice-agent-sdk-sample repo project"
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
    %% Frontend Layer
    subgraph "Frontend (Next.js Client)"
        NC["Next.js Client UI"]:::frontend
        AC["AudioChat Component"]:::frontend
        CD["ChatDialog Component"]:::frontend
        CP["Composer Component"]:::frontend
        AP["AudioPlayback Component"]:::frontend
        MB["MessageBubble Components"]:::frontend
        WH["useWebsocket Hook"]:::frontend
        AU["useAudio Hook"]:::frontend
        TC["Tailwind CSS Config"]:::frontend
    end

    %% Backend Layer
    subgraph "Backend (FastAPI Server)"
        SE["server.py (Entry Point)"]:::backend
        AI["app/__init__.py (App Init & Routes)"]:::backend
        WS["WebSocket Handler & Streaming"]:::backend
        SD["Agents SDK Core"]:::backend
        ACfg["agent_config.py"]:::backend
        MAPI["mock_api.py (Tool Adapter)"]:::backend
        MK["Makefile (Orchestration)"]:::backend
        ENV["Env Vars (OPENAI_API_KEY)"]:::config
    end

    %% External Services
    OpenAI["OpenAI API"]:::external

    %% Connections
    NC -.->|"audio & text events"| WS
    WS -->|"streamed responses"| NC
    WS -->|"route to agent logic"| SD
    SD -->|"HTTP streaming (chat & function calls)"| OpenAI
    SD -->|"function/tool call"| MAPI

    %% Click Events
    click NC "https://github.com/openai/openai-voice-agent-sdk-sample/tree/main/frontend/src/"
    click AC "https://github.com/openai/openai-voice-agent-sdk-sample/blob/main/frontend/src/components/AudioChat.tsx"
    click CD "https://github.com/openai/openai-voice-agent-sdk-sample/blob/main/frontend/src/components/ChatDialog.tsx"
    click CP "https://github.com/openai/openai-voice-agent-sdk-sample/blob/main/frontend/src/components/Composer.tsx"
    click AP "https://github.com/openai/openai-voice-agent-sdk-sample/blob/main/frontend/src/components/AudioPlayback.tsx"
    click MB "https://github.com/openai/openai-voice-agent-sdk-sample/blob/main/frontend/src/components/MessageBubble.tsx"
    click MB "https://github.com/openai/openai-voice-agent-sdk-sample/tree/main/frontend/src/components/messages/"
    click WH "https://github.com/openai/openai-voice-agent-sdk-sample/blob/main/frontend/src/hooks/useWebsocket.ts"
    click AU "https://github.com/openai/openai-voice-agent-sdk-sample/blob/main/frontend/src/hooks/useAudio.ts"
    click TC "https://github.com/openai/openai-voice-agent-sdk-sample/blob/main/frontend/tailwind.config.mjs"
    click TC "https://github.com/openai/openai-voice-agent-sdk-sample/blob/main/frontend/src/app/globals.css"
    click SE "https://github.com/openai/openai-voice-agent-sdk-sample/blob/main/server/server.py"
    click AI "https://github.com/openai/openai-voice-agent-sdk-sample/blob/main/server/app/__init__.py"
    click WS "https://github.com/openai/openai-voice-agent-sdk-sample/blob/main/server/app/utils.py"
    click ACfg "https://github.com/openai/openai-voice-agent-sdk-sample/blob/main/server/app/agent_config.py"
    click MAPI "https://github.com/openai/openai-voice-agent-sdk-sample/blob/main/server/app/mock_api.py"
    click MK "https://github.com/openai/openai-voice-agent-sdk-sample/tree/main/Makefile"

    %% Styles
    classDef frontend fill:#cce5ff,stroke:#004085,color:#004085
    classDef backend fill:#d4edda,stroke:#155724,color:#155724
    classDef external fill:#ffeeba,stroke:#856404,color:#856404
    classDef config fill:#f8d7da,stroke:#721c24,color:#721c24
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
