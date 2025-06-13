---
created: 2025-06-12 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/openai-realtime-twilio-demo
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




# realtime-twilio-demo repo project
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
title: "realtime-twilio-demo repo project"
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
    %% User Agent
    Browser["Browser / User Agent"]:::frontend

    %% Frontend Layer
    subgraph "Next.js Webapp" 
        direction TB
        Webapp_Page["page.tsx"]:::frontend
        Webapp_Layout["layout.tsx"]:::frontend
        Webapp_CSS["globals.css"]:::frontend

        subgraph "API Routes (app/api/twilio)" 
            direction TB
            API_Twilio["route.ts"]:::control
            API_Numbers["numbers/route.ts"]:::control
            API_Webhook["webhook-local/route.ts"]:::control
        end

        subgraph "React UI Panels" 
            direction TB
            Comp_Call["call-interface.tsx"]:::frontend
            Comp_Transcript["transcript.tsx"]:::frontend
            Comp_SessionConfig["session-configuration-panel.tsx"]:::frontend
            Comp_PhoneChecklist["phone-number-checklist.tsx"]:::frontend
            Comp_FunctionCalls["function-calls-panel.tsx"]:::frontend
            Comp_ToolConfig["tool-configuration-dialog.tsx"]:::frontend
            Comp_TopBar["top-bar.tsx"]:::frontend
            Comp_ChecklistSummary["checklist-and-config.tsx"]:::frontend
        end

        subgraph "Helpers & SDK Wrappers (lib)" 
            direction TB
            Lib_Twilio["twilio.ts"]:::control
            Lib_RealtimeEvent["handle-realtime-event.ts"]:::control
            Lib_BackendTools["use-backend-tools.ts"]:::control
            Lib_Utils["utils.ts"]:::control
            Lib_Templates["tool-templates.ts"]:::control
        end
    end

    %% Backend Layer
    subgraph "WebSocket-Server (Express + WS)" 
        direction TB
        WS_Server["server.ts\n(/twiml, /call, /logs)"]:::backend
        WS_SessionMgr["sessionManager.ts"]:::backend
        WS_Functions["functionHandlers.ts"]:::backend
        WS_Twiml["twiml.xml"]:::backend
        WS_Types["types.ts"]:::backend
    end

    %% Infrastructure
    ngrok["ngrok Tunnel"]:::infra

    %% External Services
    Twilio["Twilio Platform\nREST & Media Stream"]:::external
    OpenAI["OpenAI Realtime API"]:::external

    %% Data Flows & Protocols
    Browser -->|"HTTPS"| Webapp_Page
    Browser -->|"WebSocket /logs"| WS_Server

    Webapp_Page -->|"REST API"| API_Twilio
    API_Twilio -->|"REST API"| Twilio

    Twilio -->|"HTTP Webhook"| ngrok
    ngrok -->|"HTTP /twiml"| WS_Server

    Twilio -->|"WS /call"| ngrok
    ngrok -->|"WebSocket /call"| WS_Server

    WS_Server -->|"Forward audio/text frames"| WS_SessionMgr
    WS_SessionMgr -->|"Invoke handlers"| WS_Functions
    WS_SessionMgr -->|"Bidirectional stream"| OpenAI
    OpenAI -->|"Stream responses"| WS_SessionMgr

    WS_Server -->|"WebSocket /logs"| Browser

    %% Click Events Frontend
    click Webapp_Page "https://github.com/openai/openai-realtime-twilio-demo/blob/main/webapp/app/page.tsx"
    click Webapp_Layout "https://github.com/openai/openai-realtime-twilio-demo/blob/main/webapp/app/layout.tsx"
    click Webapp_CSS "https://github.com/openai/openai-realtime-twilio-demo/blob/main/webapp/app/globals.css"
    click API_Twilio "https://github.com/openai/openai-realtime-twilio-demo/blob/main/webapp/app/api/twilio/route.ts"
    click API_Numbers "https://github.com/openai/openai-realtime-twilio-demo/blob/main/webapp/app/api/twilio/numbers/route.ts"
    click API_Webhook "https://github.com/openai/openai-realtime-twilio-demo/blob/main/webapp/app/api/twilio/webhook-local/route.ts"
    click Comp_Call "https://github.com/openai/openai-realtime-twilio-demo/blob/main/webapp/components/call-interface.tsx"
    click Comp_Transcript "https://github.com/openai/openai-realtime-twilio-demo/blob/main/webapp/components/transcript.tsx"
    click Comp_SessionConfig "https://github.com/openai/openai-realtime-twilio-demo/blob/main/webapp/components/session-configuration-panel.tsx"
    click Comp_PhoneChecklist "https://github.com/openai/openai-realtime-twilio-demo/blob/main/webapp/components/phone-number-checklist.tsx"
    click Comp_FunctionCalls "https://github.com/openai/openai-realtime-twilio-demo/blob/main/webapp/components/function-calls-panel.tsx"
    click Comp_ToolConfig "https://github.com/openai/openai-realtime-twilio-demo/blob/main/webapp/components/tool-configuration-dialog.tsx"
    click Comp_TopBar "https://github.com/openai/openai-realtime-twilio-demo/blob/main/webapp/components/top-bar.tsx"
    click Comp_ChecklistSummary "https://github.com/openai/openai-realtime-twilio-demo/blob/main/webapp/components/checklist-and-config.tsx"
    click Lib_Twilio "https://github.com/openai/openai-realtime-twilio-demo/blob/main/webapp/lib/twilio.ts"
    click Lib_RealtimeEvent "https://github.com/openai/openai-realtime-twilio-demo/blob/main/webapp/lib/handle-realtime-event.ts"
    click Lib_BackendTools "https://github.com/openai/openai-realtime-twilio-demo/blob/main/webapp/lib/use-backend-tools.ts"
    click Lib_Utils "https://github.com/openai/openai-realtime-twilio-demo/blob/main/webapp/lib/utils.ts"
    click Lib_Templates "https://github.com/openai/openai-realtime-twilio-demo/blob/main/webapp/lib/tool-templates.ts"
    click FrontendEnv "https://github.com/openai/openai-realtime-twilio-demo/blob/main/webapp/.env.example"

    %% Click Events Backend
    click WS_Server "https://github.com/openai/openai-realtime-twilio-demo/blob/main/websocket-server/src/server.ts"
    click WS_SessionMgr "https://github.com/openai/openai-realtime-twilio-demo/blob/main/websocket-server/src/sessionManager.ts"
    click WS_Functions "https://github.com/openai/openai-realtime-twilio-demo/blob/main/websocket-server/src/functionHandlers.ts"
    click WS_Twiml "https://github.com/openai/openai-realtime-twilio-demo/blob/main/websocket-server/src/twiml.xml"
    click WS_Types "https://github.com/openai/openai-realtime-twilio-demo/blob/main/websocket-server/src/types.ts"
    click BackendEnv "https://github.com/openai/openai-realtime-twilio-demo/blob/main/websocket-server/.env.example"

    %% Styles
    classDef frontend fill:#E8F0FE,stroke:#4285F4,color:#000
    classDef backend fill:#FFF4E5,stroke:#FB8C00,color:#000
    classDef external fill:#E8F5E9,stroke:#43A047,color:#000
    classDef infra fill:#ECEFF1,stroke:#607D8B,color:#000
    classDef control fill:#F3E5F5,stroke:#8E24AA,color:#000
    classDef data fill:#FFF3E0,stroke:#FB8C00,color:#000

```

-----

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