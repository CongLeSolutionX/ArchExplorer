---
created: 2025-06-012 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/openai-support-agent-demo
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExZHVjcHo2ZDA3N2g1Y2xkeXlhZHZwNjA2b3dpdDVtMzZyYjA4cGFvYyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/AwDzQ8SzP9Spwllt7V/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# openai-support-agent-demo repo project
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
title: "openai-support-agent-demo repo project"
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
    subgraph "Frontend (Client)" 
        direction TB
        CustomerUI["Customer UI"]:::frontend
        click CustomerUI "https://github.com/openai/openai-support-agent-demo/blob/main/app/page.tsx"
        CustomerKB["Knowledge Base Page"]:::frontend
        click CustomerKB "https://github.com/openai/openai-support-agent-demo/blob/main/app/kb/page.tsx"
        CustomerFAQ["FAQ Page"]:::frontend
        click CustomerFAQ "https://github.com/openai/openai-support-agent-demo/blob/main/app/faq/page.tsx"
        AgentUI["Agent UI"]:::frontend
        click AgentUI "https://github.com/openai/openai-support-agent-demo/blob/main/app/page.tsx"
        SharedUI["Shared UI Components"]:::frontend
        click SharedUI "https://github.com/openai/openai-support-agent-demo/blob/main/components/ui/button.tsx"
        StateStore["Client State Stores"]:::frontend
    end

    %% Backend Layer
    subgraph "Backend (Next.js)" 
        direction TB
        %% API Routes
        subgraph "API Layer – Customer Support Resources"
            direction TB
            OrdersAPI["Orders API"]:::backend
            click OrdersAPI "https://github.com/openai/openai-support-agent-demo/blob/main/app/api/orders/[order_id]/route.ts"
            CancelAPI["Cancel Order API"]:::backend
            click CancelAPI "https://github.com/openai/openai-support-agent-demo/blob/main/app/api/orders/[order_id]/cancel/route.ts"
            RefundAPI["Create Refund API"]:::backend
            click RefundAPI "https://github.com/openai/openai-support-agent-demo/blob/main/app/api/orders/[order_id]/create_refund/route.ts"
            ReturnAPI["Create Return API"]:::backend
            click ReturnAPI "https://github.com/openai/openai-support-agent-demo/blob/main/app/api/orders/[order_id]/create_return/route.ts"
            ReplacementAPI["Send Replacement API"]:::backend
            click ReplacementAPI "https://github.com/openai/openai-support-agent-demo/blob/main/app/api/orders/[order_id]/send_replacement/route.ts"
            TicketsAPI["Create Ticket API"]:::backend
            click TicketsAPI "https://github.com/openai/openai-support-agent-demo/blob/main/app/api/tickets/create/route.ts"
            ComplaintsAPI["Create Complaint API"]:::backend
            click ComplaintsAPI "https://github.com/openai/openai-support-agent-demo/blob/main/app/api/complaints/create/route.ts"
            UsersHistoryAPI["User Order History API"]:::backend
            click UsersHistoryAPI "https://github.com/openai/openai-support-agent-demo/blob/main/app/api/users/[user_id]/order_history/route.ts"
            UsersResetAPI["User Reset Password API"]:::backend
            click UsersResetAPI "https://github.com/openai/openai-support-agent-demo/blob/main/app/api/users/[user_id]/reset_password/route.ts"
            UsersUpdateAPI["User Update Info API"]:::backend
            click UsersUpdateAPI "https://github.com/openai/openai-support-agent-demo/blob/main/app/api/users/[user_id]/update_info/route.ts"
            VouchersAPI["Create Voucher API"]:::backend
            click VouchersAPI "https://github.com/openai/openai-support-agent-demo/blob/main/app/api/vouchers/create/route.ts"
            TurnResponseAPI["Turn Response API"]:::backend
            click TurnResponseAPI "https://github.com/openai/openai-support-agent-demo/blob/main/app/api/turn_response/route.ts"
        end

        subgraph "API Layer – Vector Store & File Search"
            direction TB
            VSCreate["Create Store API"]:::backend
            click VSCreate "https://github.com/openai/openai-support-agent-demo/blob/main/app/api/vector_stores/create_store/route.ts"
            VSAddFile["Add File API"]:::backend
            click VSAddFile "https://github.com/openai/openai-support-agent-demo/blob/main/app/api/vector_stores/add_file/route.ts"
            VSUpload["Upload File API"]:::backend
            click VSUpload "https://github.com/openai/openai-support-agent-demo/blob/main/app/api/vector_stores/upload_file/route.ts"
            VSListFiles["List Files API"]:::backend
            click VSListFiles "https://github.com/openai/openai-support-agent-demo/blob/main/app/api/vector_stores/list_files/route.ts"
            VSGetFile["Get File API"]:::backend
            click VSGetFile "https://github.com/openai/openai-support-agent-demo/blob/main/app/api/vector_stores/get_file/route.ts"
            VSRetrieve["Retrieve Store API"]:::backend
            click VSRetrieve "https://github.com/openai/openai-support-agent-demo/blob/main/app/api/vector_stores/retrieve_store/route.ts"
            ListFilesAPI["General List Files API"]:::backend
            click ListFilesAPI "https://github.com/openai/openai-support-agent-demo/blob/main/app/api/list_files/route.ts"
        end

        VSInitPage["Vector Store Init Page"]:::backend
        click VSInitPage "https://github.com/openai/openai-support-agent-demo/blob/main/app/init_vs/page.tsx"

        subgraph "Business Logic"
            direction TB
            Assistant["AI Assistant Service"]:::backend
            click Assistant "https://github.com/openai/openai-support-agent-demo/blob/main/lib/assistant.ts"
            Tools["Tool Definitions"]:::backend
            click Tools "https://github.com/openai/openai-support-agent-demo/blob/main/lib/tools/tools.ts"
            ToolHandler["Tool Handling"]:::backend
            click ToolHandler "https://github.com/openai/openai-support-agent-demo/blob/main/lib/tools/tools-handling.ts"
            Utils["Utilities"]:::backend
            click Utils "https://github.com/openai/openai-support-agent-demo/blob/main/lib/utils.ts"
            ConfigConstants["Config Constants"]:::backend
            click ConfigConstants "https://github.com/openai/openai-support-agent-demo/blob/main/config/constants.ts"
            ConfigFunctions["Function Definitions"]:::backend
            click ConfigFunctions "https://github.com/openai/openai-support-agent-demo/blob/main/config/functions.ts"
            ConfigToolsList["Tools List"]:::backend
            click ConfigToolsList "https://github.com/openai/openai-support-agent-demo/blob/main/config/tools-list.ts"
            ConfigDemo["Demo Data"]:::backend
            click ConfigDemo "https://github.com/openai/openai-support-agent-demo/blob/main/config/demoData.ts"
        end
    end

    %% External Services
    subgraph "External Services"
        direction TB
        OpenAIChat["OpenAI Responses API"]:::external
        VectorStoreService["OpenAI Vector Store API"]:::external
    end

    %% Static Content
    subgraph "Static Content"
        direction TB
        KBMarkdown["Knowledge Base Markdown"]:::static
        FAQMarkdown["FAQ Markdown"]:::static
    end

    %% Connections
    CustomerUI -->|"HTTP Requests"| OrdersAPI
    CustomerUI --> TicketsAPI
    CustomerUI --> ComplaintsAPI
    CustomerUI --> UsersHistoryAPI
    CustomerUI --> VouchersAPI
    AgentUI --> OrdersAPI
    AgentUI --> TurnResponseAPI
    SharedUI --> OrdersAPI
    StateStore --> OrdersAPI

    OrdersAPI --> Assistant
    CancelAPI --> Assistant
    RefundAPI --> Assistant
    ReturnAPI --> Assistant
    ReplacementAPI --> Assistant
    TicketsAPI --> Assistant
    ComplaintsAPI --> Assistant
    UsersHistoryAPI --> Assistant
    UsersResetAPI --> Assistant
    UsersUpdateAPI --> Assistant
    VouchersAPI --> Assistant
    TurnResponseAPI --> Assistant

    VSCreate --> Assistant
    VSAddFile --> Assistant
    VSUpload --> Assistant
    VSListFiles --> Assistant
    VSGetFile --> Assistant
    VSRetrieve --> Assistant
    ListFilesAPI --> Assistant

    VSInitPage --> VSCreate
    VSInitPage --> VSAddFile
    VSInitPage --> VSUpload

    Assistant -->|"Calls"| OpenAIChat
    Assistant -->|"Searches"| VectorStoreService
    Assistant --> ConfigDemo

    KBMarkdown -->|"Served as static"| CustomerKB
    FAQMarkdown -->|"Served as static"| CustomerFAQ

    %% Styles
    classDef frontend fill:#D0E8FF,stroke:#0366D6,color:#0366D6
    classDef backend fill:#DDF4DD,stroke:#22863A,color:#22863A
    classDef external fill:#FFF5B1,stroke:#DBAB09,color:#735C0F
    classDef static fill:#F0F0F0,stroke:#6A737D,color:#6A737D


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
