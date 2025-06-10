---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExanp1djJjMWRrdW1lc2t2dDY0djJ2bXozMDlsdHNqbGNtdzgwbjJuZyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/mcdVjcUtgJz9603joH/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----



# Lobe Chat System
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## A Diagrammatic Guide 

```mermaid
---
title: "Lobe Hub - Lobe Chat"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "flowchart": {"htmlLabels": true, 'curve': 'natural'},
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#f231',
      'primaryTextColor': '#239',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TB
    subgraph Legend
    style Legend fill:#cf32,stroke:#333,stroke-width:2px
        UI[User Interface]:::frontend
        CS[Core Service]:::core
        EX[External Service]:::external
        IN[Infrastructure]:::infra
        SEC[Security Component]:::security
    end

    subgraph Frontend_Layer["Frontend Layer"]
    style Frontend_Layer fill:#2f32,stroke:#333,stroke-width:2px
        MainRoutes["Main App Routes"]:::frontend
        AuthRoutes["Auth Routes"]:::frontend
        ModalSystem["Modal System"]:::frontend
        I18N["Internationalization"]:::frontend
        
        Features["Features"]:::frontend
        Chat["Chat Implementation"]:::frontend
        PluginMgmt["Plugin Management"]:::frontend
        FileMgmt["File Management"]:::frontend
        Settings["Settings Management"]:::frontend
    end

    subgraph Core_Services_Layer["Core Services Layer"]
    style Core_Services_Layer fill:#232,stroke:#333,stroke-width:2px
        AgentRuntime["Agent Runtime"]:::core
        PluginSystem["Plugin System"]:::core
        
        subgraph State_Management["State Management"]
        style State_Management fill:#2fd2,stroke:#333,stroke-width:2px
            GlobalState["Global State"]:::core
            ChatState["Chat State"]:::core
            UserState["User State"]:::core
        end
        
        subgraph Database_Layer["Database Layer"]
        style Database_Layer fill:#f1d1,stroke:#333,stroke-width:2px
            ClientDB[(Client Database)]:::infra
            ServerDB[(Server Database)]:::infra
        end
        
        subgraph Authentication["Authentication"]
        style Authentication fill:#2fd2,stroke:#333,stroke-width:2px
            NextAuth["Next-Auth"]:::security
            ClerkAuth["Clerk Integration"]:::security
            AuthProvider["Auth Provider"]:::security
        end
    end

    subgraph Backend_Layer["Backend Layer"]
    style Backend_Layer fill:#2cc5,stroke:#333,stroke-width:2px
        APIRoutes["API Routes"]:::core
        TRPCEndpoints["TRPC Endpoints"]:::core
        WebAPIServices["WebAPI Services"]:::core
    end

    subgraph External_Services["External Services"]
    style External_Services fill:#55c5,stroke:#333,stroke-width:2px
        LLMProviders["LLM Providers"]:::external
        Storage["Storage Services"]:::external
        AuthProviders["Auth Providers"]:::external
        PluginGateway["Plugin Gateway"]:::external
    end

    MainRoutes --> Features
    Features --> AgentRuntime
    PluginSystem --> LLMProviders
    AgentRuntime --> APIRoutes
    APIRoutes --> LLMProviders
    AuthRoutes --> AuthProvider
    AuthProvider --> AuthProviders
    FileMgmt --> Storage
    PluginMgmt --> PluginGateway
    
    %% Component Mappings
    click MainRoutes "https://github.com/lobehub/lobe-chat/tree/main/src/app/(main)"
    click AuthRoutes "https://github.com/lobehub/lobe-chat/tree/main/src/app/(auth)"
    click ModalSystem "https://github.com/lobehub/lobe-chat/tree/main/src/app/@modal"
    click I18N "https://github.com/lobehub/lobe-chat/tree/main//locales"
    click AgentRuntime "https://github.com/lobehub/lobe-chat/tree/main/src/libs/agent-runtime"
    click PluginSystem "https://github.com/lobehub/lobe-chat/tree/main/src/libs/plugin"
    click ClientDB "https://github.com/lobehub/lobe-chat/tree/main/src/database/client"
    click ServerDB "https://github.com/lobehub/lobe-chat/tree/main/src/database/server"
    click NextAuth "https://github.com/lobehub/lobe-chat/tree/main/src/libs/next-auth"
    click AuthProvider "https://github.com/lobehub/lobe-chat/tree/main/src/layout/AuthProvider"
    click APIRoutes "https://github.com/lobehub/lobe-chat/tree/main/src/app/(backend)/api"
    click TRPCEndpoints "https://github.com/lobehub/lobe-chat/tree/main/src/app/(backend)/trpc"
    click WebAPIServices "https://github.com/lobehub/lobe-chat/tree/main/src/app/(backend)/webapi"
    click Chat "https://github.com/lobehub/lobe-chat/tree/main/src/features/Conversation"
    click PluginMgmt "https://github.com/lobehub/lobe-chat/tree/main/src/features/PluginStore"
    click FileMgmt "https://github.com/lobehub/lobe-chat/tree/main/src/features/FileManager"
    click Settings "https://github.com/lobehub/lobe-chat/tree/main/src/features/Setting"
    click GlobalState "https://github.com/lobehub/lobe-chat/tree/main/src/store/global"
    click ChatState "https://github.com/lobehub/lobe-chat/tree/main/src/store/chat"
    click UserState "https://github.com/lobehub/lobe-chat/tree/main/src/store/user"

    classDef frontend fill:#2196F,stroke:#1565C0,color:white
    classDef core fill:#4CAF5,stroke:#2E7D32,color:white
    classDef external fill:#FF980,stroke:#EF6C00,color:white
    classDef infra fill:#9E9E9,stroke:#616161,color:white
    classDef security fill:#F4433,stroke:#C62828,color:white
    
```


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
