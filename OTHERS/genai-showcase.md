---
created: 2025-03-23 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExZzdnYnN3NXZhMzFnc2FxN2dtNmViczVpZXQ0bmEyN3kwNnZ4a3JmOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/Bzjdu3qiu1IezrKQ1p/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----



# GenAI Showcase
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---



```mermaid
---
title: "MongoDB - GenAI Showcase"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: default
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'lineColor': '#F8B229'
    }
  }
}%%
flowchart TD
    %% Frontend/UI Layer
    subgraph "Frontend/UI Layer"
        UI1["RT-voice-ts-store-agent UI"]:::frontend
        UI2["mongo-feed UI"]:::frontend
        UI3["mongo-mp UI"]:::frontend
        UI4["mongostory UI"]:::frontend
        UI5["vercel_sdk_hr_agent UI"]:::frontend
    end

    %% API/Backend Layer
    subgraph "API/Backend Layer"
        API1["RT-voice-ts-store-agent API"]:::backend
        API2["mongo-feed API"]:::backend
        API3["mongo-mp API"]:::backend
        API4["mongostory API"]:::backend
        API5["vercel_sdk_hr_agent API"]:::backend
        API6["local-bot Service"]:::backend
    end

    %% Database & Storage
    subgraph "Database & Storage"
        DB1["RT-voice-ts-store-agent MongoDB"]:::database
        DB2["mongo-feed MongoDB"]:::database
        DB3["mongo-mp MongoDB"]:::database
        DB4["mongostory MongoDB"]:::database
    end

    %% AI/Generative Components
    subgraph "AI/Generative Components"
        AI_NB["Notebooks & Agents"]:::ai
        AI_Tools["Embeddings Generator"]:::ai
        AI_Module1["mongostory AI Agent"]:::ai
        AI_Module2["vercel_sdk_hr_agent Embeddings"]:::ai
    end

    %% Infrastructure & Deployment
    subgraph "Infrastructure & Deployment"
        INF1["Local Bot Deployments"]:::infrastructure
        INF2["Terraform Deployments"]:::infrastructure
    end

    %% Experimentation Environment
    subgraph "Experimentation Environment"
        EXP["Jupyter Notebooks Sandbox"]:::experimentation
    end

    %% Connections between Frontend and API
    UI1 -->|"calls"| API1
    UI2 -->|"calls"| API2
    UI3 -->|"calls"| API3
    UI4 -->|"calls"| API4
    UI5 -->|"calls"| API5

    %% Connections between API and Database
    API1 -->|"reads/writes"| DB1
    API2 -->|"reads/writes"| DB2
    API3 -->|"reads/writes"| DB3
    API4 -->|"reads/writes"| DB4
    API5 -->|"reads/writes"| DB4
    API6 -->|"reads/writes"| DB1

    %% Connections between API and AI Components
    API1 -->|"integrates"| AI_Tools
    API4 -->|"integrates"| AI_Module1
    API5 -->|"integrates"| AI_Module2

    %% Connection from Experimentation to AI
    EXP -->|"tests"| AI_NB

    %% Infrastructure supports API and Deployment of Services
    INF1 -->|"deploys"| API6
    INF2 -->|"deploys"| API6

    %% Class Definitions for styling
    classDef frontend fill:#f9c74f,stroke:#333,stroke-width:1px;
    classDef backend fill:#90be6d,stroke:#333,stroke-width:1px;
    classDef database fill:#f9844a,stroke:#333,stroke-width:1px;
    classDef ai fill:#277da1,stroke:#333,stroke-width:1px,color:#fff;
    classDef infrastructure fill:#f3722c,stroke:#333,stroke-width:1px,color:#fff;
    classDef experimentation fill:#a9a9a9,stroke:#333,stroke-width:1px;

    %% Click Events
    click UI1 "https://github.com/mongodb-developer/genai-showcase/tree/main/apps/RT-voice-ts-store-agent/app"
    click UI2 "https://github.com/mongodb-developer/genai-showcase/tree/main/apps/mongo-feed/app"
    click UI3 "https://github.com/mongodb-developer/genai-showcase/tree/main/apps/mongo-mp/app"
    click UI4 "https://github.com/mongodb-developer/genai-showcase/tree/main/apps/mongostory/app"
    click UI5 "https://github.com/mongodb-developer/genai-showcase/tree/main/apps/vercel_sdk_hr_agent/app"

    click API1 "https://github.com/mongodb-developer/genai-showcase/tree/main/apps/RT-voice-ts-store-agent/app/api"
    click API2 "https://github.com/mongodb-developer/genai-showcase/tree/main/apps/mongo-feed/app/api"
    click API3 "https://github.com/mongodb-developer/genai-showcase/tree/main/apps/mongo-mp/app/api"
    click API4 "https://github.com/mongodb-developer/genai-showcase/tree/main/apps/mongostory/app/api"
    click API5 "https://github.com/mongodb-developer/genai-showcase/tree/main/apps/vercel_sdk_hr_agent/app/api"
    click API6 "https://github.com/mongodb-developer/genai-showcase/blob/main/apps/local-bot/app.py"

    click DB1 "https://github.com/mongodb-developer/genai-showcase/blob/main/apps/RT-voice-ts-store-agent/lib/mongodb.ts"
    click DB2 "https://github.com/mongodb-developer/genai-showcase/blob/main/apps/mongo-feed/lib/mongodb.ts"
    click DB3 "https://github.com/mongodb-developer/genai-showcase/blob/main/apps/mongo-mp/lib/mongodb.ts"
    click DB4 "https://github.com/mongodb-developer/genai-showcase/blob/main/apps/mongostory/lib/mongodb.ts"

    click AI_NB "https://github.com/mongodb-developer/genai-showcase/tree/main/notebooks/"
    click AI_Tools "https://github.com/mongodb-developer/genai-showcase/blob/main/tools/embeddings_generator/create_embeddings.py"
    click AI_Module1 "https://github.com/mongodb-developer/genai-showcase/blob/main/apps/mongostory/lib/ai-agent.ts"
    click AI_Module2 "https://github.com/mongodb-developer/genai-showcase/blob/main/apps/vercel_sdk_hr_agent/utils/embeddings.ts"

    click INF1 "https://github.com/mongodb-developer/genai-showcase/tree/main/apps/local-bot/Dockerfile"
    click INF1 "https://github.com/mongodb-developer/genai-showcase/blob/main/apps/local-bot/compose.yaml"
    click INF2 "https://github.com/mongodb-developer/genai-showcase/blob/main/apps/springai-terraform-rag/main.tf"
    click INF2 "https://github.com/mongodb-developer/genai-showcase/blob/main/apps/springai-terraform-rag/variables.tf"

    click EXP "https://github.com/mongodb-developer/genai-showcase/tree/main/notebooks/"

```


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
