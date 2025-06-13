---
created: 2025-06-012 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/openai-realtime-agents
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




# openai-realtime-agents repo project
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
title: "openai-realtime-agents repo project"
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
    subgraph Client["Client-Side Layer"]
        UI["Main Application UI"]
        TS["Transcript View"]
        EL["Event Log"]
        BT["Bottom Toolbar"]
        EC["Event Context"]
        TC["Transcript Context"]
    end

    subgraph NextJS["Next.js Application Layer"]
        API["API Routes"]
        RT["Real-time Connection"]
        SH["Server Event Handler"]
        
        subgraph Routes["Route Handlers"]
            CC["/api/chat/completions"]
            SM["/api/session"]
        end
    end

    subgraph Agents["Agent Configuration System"]
        direction TB
        AU["Agent Utils"]
        VP["Voice Agent Base Prompt"]
        
        subgraph CSR["Customer Service Retail"]
            direction TB
            RA["Retail Authentication"]
            RET["Returns Agent"]
            SA["Sales Agent"]
            SH2["Simulated Human"]
        end
        
        subgraph FDA["Front Desk Authentication"]
            direction TB
            FA["Front Desk Auth"]
            TG["Tour Guide Agent"]
        end
        
        SE["Simple Example Agent"]
    end

    subgraph External["External Services"]
        OAPI["OpenAI API"]
        RTS["Real-time Services"]
        AS["Authentication Services"]
        LLM["Background LLM (o1-mini)"]
    end

    %% Connections
    Client --> NextJS
    NextJS --> Agents
    Agents --> External
    External --> NextJS
    NextJS --> Client

    %% Click Events
    click UI "https://github.com/openai/openai-realtime-agents/blob/main/src/app/App.tsx"
    click TS "https://github.com/openai/openai-realtime-agents/blob/main/src/app/components/Transcript.tsx"
    click EL "https://github.com/openai/openai-realtime-agents/blob/main/src/app/components/Events.tsx"
    click BT "https://github.com/openai/openai-realtime-agents/blob/main/src/app/components/BottomToolbar.tsx"
    click EC "https://github.com/openai/openai-realtime-agents/blob/main/src/app/contexts/EventContext.tsx"
    click TC "https://github.com/openai/openai-realtime-agents/blob/main/src/app/contexts/TranscriptContext.tsx"
    click CC "https://github.com/openai/openai-realtime-agents/blob/main/src/app/api/chat/completions/route.ts"
    click SM "https://github.com/openai/openai-realtime-agents/blob/main/src/app/api/session/route.ts"
    click RT "https://github.com/openai/openai-realtime-agents/blob/main/src/app/lib/realtimeConnection.ts"
    click SH "https://github.com/openai/openai-realtime-agents/blob/main/src/app/hooks/useHandleServerEvent.ts"
    click CSR "https://github.com/openai/openai-realtime-agents/tree/main/src/app/agentConfigs/customerServiceRetail"
    click FDA "https://github.com/openai/openai-realtime-agents/tree/main/src/app/agentConfigs/frontDeskAuthentication"
    click SE "https://github.com/openai/openai-realtime-agents/blob/main/src/app/agentConfigs/simpleExample.ts"
    click AU "https://github.com/openai/openai-realtime-agents/blob/main/src/app/agentConfigs/utils.ts"
    click VP "https://github.com/openai/openai-realtime-agents/blob/main/src/app/agentConfigs/voiceAgentMetaprompt.txt"
    click RA "https://github.com/openai/openai-realtime-agents/blob/main/src/app/agentConfigs/customerServiceRetail/authentication.ts"
    click RET "https://github.com/openai/openai-realtime-agents/blob/main/src/app/agentConfigs/customerServiceRetail/returns.ts"
    click SA "https://github.com/openai/openai-realtime-agents/blob/main/src/app/agentConfigs/customerServiceRetail/sales.ts"
    click SH2 "https://github.com/openai/openai-realtime-agents/blob/main/src/app/agentConfigs/customerServiceRetail/simulatedHuman.ts"
    click FA "https://github.com/openai/openai-realtime-agents/blob/main/src/app/agentConfigs/frontDeskAuthentication/authentication.ts"
    click TG "https://github.com/openai/openai-realtime-agents/blob/main/src/app/agentConfigs/frontDeskAuthentication/tourGuide.ts"

    %% Styling
    classDef client fill:#a8d1ff
    classDef server fill:#90EE90
    classDef agent fill:#FFE5B4
    classDef external fill:#DDA0DD
    classDef auth fill:#FF9999

    class UI,TS,EL,BT,EC,TC client
    class API,RT,SH,CC,SM server
    class AU,VP,CSR,FDA,SE,RA,RET,SA,SH2,FA,TG agent
    class OAPI,RTS,AS,LLM external
    class RA,FA auth
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