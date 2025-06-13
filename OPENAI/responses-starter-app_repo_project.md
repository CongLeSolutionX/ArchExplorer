---
created: 2025-06-012 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/openai-responses-starter-app
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




# openai-responses-starter-app repo project
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
title: "openai-responses-starter-app repo project"
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
    %% Client Browser Zone
    subgraph "Client Browser"
        direction TB
        Layout["Page Layout"]:::frontend
        Page["Main Page (Chat)"]:::frontend
        ChatUI["Chat UI"]:::frontend
        ToolsPanel["Tools Panel UI"]:::frontend
        FileUpload["File Upload UI"]:::frontend
        FileSearchUI["File Search Setup UI"]:::frontend
        subgraph "State Stores"
            direction TB
            ConvStore["Conversation State Store"]:::state
            ToolsStore["Tools State Store"]:::state
        end
    end

    %% Server Zone
    subgraph "Next.js Server"
        direction TB
        subgraph "API Routes"
            direction TB
            GetJoke["get_joke API"]:::api
            GetWeather["get_weather API"]:::api
            TurnResponse["turn_response API"]:::api
            subgraph "Vector Stores"
                direction TB
                CreateStore["create_store"]:::api
                RetrieveStore["retrieve_store"]:::api
                ListFiles["list_files"]:::api
                AddFile["add_file"]:::api
                UploadFile["upload_file"]:::api
            end
        end

        subgraph "Business Logic"
            direction TB
            Assistant["OpenAI Wrapper"]:::logic
            ToolsLogic["Tools Dispatch Logic"]:::logic
            ToolsDef["Tool Definitions"]:::logic
        end

        subgraph "Config"
            direction TB
            FuncConfig["functions.ts"]:::config
            ToolsConfig["tools-list.ts"]:::config
            ConstConfig["constants.ts"]:::config
        end
    end

    %% External Services
    subgraph "External Services"
        direction TB
        OpenAI["OpenAI Responses API"]:::external
        WebSearch["Web Search Tool"]:::external
        VectorService["Vector Store Service"]:::external
    end

    %% Connections: Client -> Server
    ChatUI -->|"POST /api/turn_response"| TurnResponse
    ToolsPanel -->|"GET /api/functions/get_joke"| GetJoke
    ToolsPanel -->|"GET /api/functions/get_weather"| GetWeather
    FileUpload -->|"upload file request"| UploadFile
    FileUpload -->|"add file request"| AddFile
    FileSearchUI -->|"list files request"| ListFiles
    FileSearchUI -->|"retrieve store request"| RetrieveStore

    %% Server Internal flows
    TurnResponse -->|"calls"| Assistant
    Assistant -->|"invoke tools"| ToolsLogic
    ToolsLogic -->|"web search"| WebSearch
    ToolsLogic -->|"vector ops"| VectorService
    Assistant -->|"streaming response"| ChatUI

    %% Config influences
    FuncConfig --> GetJoke
    FuncConfig --> GetWeather
    FuncConfig --> TurnResponse
    ToolsConfig --> ToolsLogic
    ConstConfig --> Assistant

    %% Click Events
    click ChatUI "https://github.com/openai/openai-responses-starter-app/blob/main/components/chat.tsx"
    click ToolsPanel "https://github.com/openai/openai-responses-starter-app/blob/main/components/tools-panel.tsx"
    click FileUpload "https://github.com/openai/openai-responses-starter-app/blob/main/components/file-upload.tsx"
    click FileSearchUI "https://github.com/openai/openai-responses-starter-app/blob/main/components/file-search-setup.tsx"
    click Layout "https://github.com/openai/openai-responses-starter-app/blob/main/app/layout.tsx"
    click Page "https://github.com/openai/openai-responses-starter-app/blob/main/app/page.tsx"
    click ConvStore "https://github.com/openai/openai-responses-starter-app/blob/main/stores/useConversationStore.ts"
    click ToolsStore "https://github.com/openai/openai-responses-starter-app/blob/main/stores/useToolsStore.ts"
    click GetJoke "https://github.com/openai/openai-responses-starter-app/blob/main/app/api/functions/get_joke/route.ts"
    click GetWeather "https://github.com/openai/openai-responses-starter-app/blob/main/app/api/functions/get_weather/route.ts"
    click TurnResponse "https://github.com/openai/openai-responses-starter-app/blob/main/app/api/turn_response/route.ts"
    click CreateStore "https://github.com/openai/openai-responses-starter-app/blob/main/app/api/vector_stores/create_store/route.ts"
    click RetrieveStore "https://github.com/openai/openai-responses-starter-app/blob/main/app/api/vector_stores/retrieve_store/route.ts"
    click ListFiles "https://github.com/openai/openai-responses-starter-app/blob/main/app/api/vector_stores/list_files/route.ts"
    click AddFile "https://github.com/openai/openai-responses-starter-app/blob/main/app/api/vector_stores/add_file/route.ts"
    click UploadFile "https://github.com/openai/openai-responses-starter-app/blob/main/app/api/vector_stores/upload_file/route.ts"
    click Assistant "https://github.com/openai/openai-responses-starter-app/blob/main/lib/assistant.ts"
    click ToolsLogic "https://github.com/openai/openai-responses-starter-app/blob/main/lib/tools/tools-handling.ts"
    click ToolsDef "https://github.com/openai/openai-responses-starter-app/blob/main/lib/tools/tools.ts"
    click FuncConfig "https://github.com/openai/openai-responses-starter-app/blob/main/config/functions.ts"
    click ToolsConfig "https://github.com/openai/openai-responses-starter-app/blob/main/config/tools-list.ts"
    click ConstConfig "https://github.com/openai/openai-responses-starter-app/blob/main/config/constants.ts"

    %% Styles
    classDef frontend fill:#cce5ff,stroke:#005b99,color:#003366,stroke-width:1px
    classDef api fill:#d4edda,stroke:#155724,color:#0b2e13,stroke-width:1px
    classDef logic fill:#ffe5b4,stroke:#cc7a00,color:#663c00,stroke-width:1px
    classDef external fill:#f8d7da,stroke:#721c24,color:#491217,stroke-width:1px
    classDef state fill:#e2e3e5,stroke:#6c757d,color:#343a40,stroke-width:1px
    classDef config fill:#f5f5f5,stroke:#999999,color:#333333,stroke-width:1px

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