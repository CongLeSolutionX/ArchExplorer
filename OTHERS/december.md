---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ntegrals/december
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExZmdoYWhxb3c2NmR6OGZoMzN5NWxqNjJmbmVxd3U0NDFobjc4ZHdvNyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/xUA7bjPYcgAvwq5CKc/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# ntegrals - december repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes (<ins>sometimes, entertainment purposes</ins>), personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


----

```mermaid
---
title: "december repo project"
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
    %% User
    User["User’s Browser"]:::external

    %% Frontend Layer
    subgraph "Frontend Layer (Port 3000)"
        direction TB
        FEApp["Next.js Frontend"]:::frontend
        CodeEditor["Monaco Editor"]:::frontend
        FileManager["File Manager"]:::frontend
        LivePreview["Live Preview (Iframe)"]:::frontend

        subgraph "Chat UI Components"
            direction TB
            ChatInput["ChatInput"]:::frontend
            ChatMessage["ChatMessage"]:::frontend
            ChatSidebar["ChatSidebar"]:::frontend
        end

        subgraph "Dashboard UI"
            direction TB
            CreateDashboard["CreateDashboard"]:::frontend
            ProjectsPage["ProjectsPage"]:::frontend
            WorkspaceDashboard["WorkspaceDashboard"]:::frontend
        end
    end

    %% Backend Layer
    subgraph "Backend Layer (Port 4000)"
        direction TB
        APIServer["Backend API Server"]:::backend

        subgraph "Routes"
            direction TB
            ChatRoute["/chat Endpoint"]:::backend
            ContainersRoute["/containers Endpoint"]:::backend
        end

        subgraph "Services"
            direction TB
            DockerService["Docker Service"]:::backend
            LLMService["LLM Service"]:::backend
            FileService["File Service"]:::backend
            ExportService["Export Service"]:::backend
            PackageService["Package Service"]:::backend
        end

        PromptUtil["Prompt Template"]:::backend
    end

    %% Infrastructure Layer
    subgraph "Infrastructure"
        direction TB
        DockerEngine["Docker Engine"]:::external
        LivePreviewContainer["Live Preview Container"]:::external
        LLMAPI["External LLM Service"]:::external
        LocalFS["Local File System"]:::storage
        ConfigStore["Config Store (config.ts)"]:::orchestration
        StartupScript["Startup Script (start.sh)"]:::orchestration
    end

    %% Connections Frontend
    User -->|interacts with| FEApp
    FEApp -->|uses Editor| CodeEditor
    FEApp -->|uses FileManager| FileManager
    FEApp -->|renders| LivePreview
    FEApp -->|uses| ChatInput
    FEApp -->|uses| ChatMessage
    FEApp -->|uses| ChatSidebar
    FEApp -->|uses| CreateDashboard
    FEApp -->|uses| ProjectsPage
    FEApp -->|uses| WorkspaceDashboard

    FEApp -->|HTTP REST| APIServer
    FEApp -->|"WebSocket/SSE"| ChatRoute
    FEApp -->|HTTP REST| ContainersRoute
    FEApp -->|HTTP REST| FileService
    FEApp -->|HTTP REST| ExportService
    FEApp -->|HTTP REST| PackageService

    %% Backend connections
    APIServer -->|routes to| ChatRoute
    APIServer -->|routes to| ContainersRoute
    APIServer -->|calls| FileService
    APIServer -->|calls| ExportService
    APIServer -->|calls| PackageService

    ChatRoute -->|invokes| LLMService
    ContainersRoute -->|invokes| DockerService

    LLMService -->|HTTP API| LLMAPI
    DockerService -->|CLI/API| DockerEngine
    DockerEngine -->|runs| LivePreviewContainer
    LivePreviewContainer -->|iframe proxy| LivePreview

    FileService -->|read/write| LocalFS
    ExportService -->|writes| LocalFS
    PackageService -->|builds in| DockerEngine

    %% Orchestration
    StartupScript -->|injects| ConfigStore
    ConfigStore -->|provides| APIServer

    %% Click Events
    click FEApp "https://github.com/ntegrals/december/tree/main/frontend/src/app"
    click CodeEditor "https://github.com/ntegrals/december/blob/main/frontend/src/app/editor/CodeEditor.tsx"
    click CodeEditor "https://github.com/ntegrals/december/blob/main/frontend/src/app/editor/IDE.tsx"
    click FileManager "https://github.com/ntegrals/december/blob/main/frontend/src/app/editor/utils/FileManager.tsx"
    click LivePreview "https://github.com/ntegrals/december/blob/main/frontend/src/app/projects/components/LivePreview.tsx"
    click ChatInput "https://github.com/ntegrals/december/blob/main/frontend/src/app/create/components/ChatInput.tsx"
    click ChatMessage "https://github.com/ntegrals/december/blob/main/frontend/src/app/create/components/ChatMessage.tsx"
    click ChatSidebar "https://github.com/ntegrals/december/blob/main/frontend/src/app/create/components/ChatSidebar.tsx"
    click CreateDashboard "https://github.com/ntegrals/december/blob/main/frontend/src/app/create/components/CreateDashboard.tsx"
    click ProjectsPage "https://github.com/ntegrals/december/blob/main/frontend/src/app/projects/components/ProjectsPage.tsx"
    click WorkspaceDashboard "https://github.com/ntegrals/december/blob/main/frontend/src/app/projects/components/WorkspaceDashboard.tsx"
    click APIServer "https://github.com/ntegrals/december/blob/main/backend/src/index.ts"
    click DockerService "https://github.com/ntegrals/december/blob/main/backend/src/services/docker.ts"
    click LLMService "https://github.com/ntegrals/december/blob/main/backend/src/services/llm.ts"
    click FileService "https://github.com/ntegrals/december/blob/main/backend/src/services/file.ts"
    click ExportService "https://github.com/ntegrals/december/blob/main/backend/src/services/export.ts"
    click PackageService "https://github.com/ntegrals/december/blob/main/backend/src/services/package.ts"
    click ChatRoute "https://github.com/ntegrals/december/blob/main/backend/src/routes/chat.ts"
    click ContainersRoute "https://github.com/ntegrals/december/blob/main/backend/src/routes/containers.ts"
    click PromptUtil "https://github.com/ntegrals/december/blob/main/backend/src/utils/prompt.txt"
    click StartupScript "https://github.com/ntegrals/december/blob/main/start.sh"
    click ConfigStore "https://github.com/ntegrals/december/blob/main/config.ts"
    click APIServer "https://github.com/ntegrals/december/tree/main/backend/src/Dockerfile"

    %% Styles
    classDef frontend fill:#D0E8FF,stroke:#333,stroke-width:1px
    classDef backend fill:#D0FFD8,stroke:#333,stroke-width:1px
    classDef external fill:#FFD8A8,stroke:#333,stroke-width:1px
    classDef storage fill:#E0E0E0,stroke:#333,stroke-width:1px
    classDef orchestration fill:#FFE0E0,stroke:#333,stroke-width:1px

```

----


```mermaid
---
title: "❓...CongLeSolutionX....❓"
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

  Closing_quote ~~~ My_Meme
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }

```

---
><b>Licenses</b>:
>
>- <b>MIT License</b>:  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
>- <b>Creative Commons Attribution-ShareAlike 4.0 International</b>: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) [![CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/88x31.png)](https://creativecommons.org/licenses/by-sa/4.0/) - Legal details in [LICENSE-CC-BY-SA-4.0](THE_PAST/LICENSE-CC-BY-SA-4.0) and at [Creative Commons official site](https://creativecommons.org/licenses/by-sa/4.0/).
>
---
