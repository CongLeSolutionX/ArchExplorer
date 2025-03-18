---
created: 2025-03-17 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Continue
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
title: "Continue"
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
    %% Frontend Clients
    subgraph "Frontend Clients"
        jetbrains["IDE Extensions (JetBrains)"]:::frontend
        vscode["IDE Extensions (VS Code)"]:::frontend
        gui["GUI/Web Interface"]:::frontend
    end

    %% Communication/Protocol Layer with detailed protocol modules
    subgraph "Communication/Protocol Layer"
        commCore["Protocol Engine"]:::comm
        ipc["IpcIde"]:::comm
        tcp["TcpMessenger"]:::comm
    end

    %% Core Engine
    coreEngine["Core Engine"]:::core

    %% Configuration & Indexing
    subgraph "Configuration & Indexing"
        coreConfig["Core Config"]:::config
        indexing["Indexing Service"]:::config
        configYaml["YAML Config"]:::config
        configTypes["Config Types"]:::config
    end

    %% LLM Integration
    subgraph "LLM Integration"
        coreLLM["Core LLM Service"]:::llm
        openaiAdapters["OpenAI Adapters"]:::llm
        llmInfo["LLM Info"]:::llm
    end

    %% Other Supporting Packages
    subgraph "Other Supporting Packages"
        fetchService["Fetch Service"]:::support
        syncService["Sync Service"]:::support
    end

    %% Data Flow
    jetbrains -->|"Messaging/Pipeline"| commCore
    vscode -->|"Messaging/Pipeline"| commCore
    commCore -->|"RouteRequest"| coreEngine
    ipc --> commCore
    tcp --> commCore

    coreEngine -->|"LoadConfig"| coreConfig
    coreEngine -->|"Indexing"| indexing

    coreEngine -->|"LLMRequest"| coreLLM
    coreLLM -->|"LLMPluginResponse"| openaiAdapters
    coreLLM -->|"LLMPluginInfo"| llmInfo
    coreLLM -->|"LLMResponse"| coreEngine

    coreEngine -->|"RenderOutput"| gui

    coreEngine -->|"SyncFetchAssets"| fetchService
    coreEngine -->|"SyncFetchAssets"| syncService

    %% Click Events
    click jetbrains "https://github.com/continuedev/continue/tree/main/extensions/intellij"
    click vscode "https://github.com/continuedev/continue/tree/main/extensions/vscode"
    click coreEngine "https://github.com/continuedev/continue/tree/main/core"
    click commCore "https://github.com/continuedev/continue/tree/main/core/protocol"
    click ipc "https://github.com/continuedev/continue/blob/main/binary/src/IpcIde.ts"
    click tcp "https://github.com/continuedev/continue/blob/main/binary/src/TcpMessenger.ts"
    click coreConfig "https://github.com/continuedev/continue/tree/main/core/config"
    click indexing "https://github.com/continuedev/continue/tree/main/core/indexing"
    click configYaml "https://github.com/continuedev/continue/tree/main/packages/config-yaml"
    click configTypes "https://github.com/continuedev/continue/tree/main/packages/config-types"
    click coreLLM "https://github.com/continuedev/continue/tree/main/core/llm"
    click openaiAdapters "https://github.com/continuedev/continue/tree/main/packages/openai-adapters"
    click llmInfo "https://github.com/continuedev/continue/tree/main/packages/llm-info"
    click gui "https://github.com/continuedev/continue/tree/main/gui"
    click fetchService "https://github.com/continuedev/continue/tree/main/packages/fetch"
    click syncService "https://github.com/continuedev/continue/tree/main/sync"

    %% Styles
    classDef frontend fill:#cce5ff,stroke:#004085,stroke-width:2px;
    classDef core fill:#d4edda,stroke:#155724,stroke-width:2px;
    classDef comm fill:#fff3cd,stroke:#856404,stroke-width:2px;
    classDef config fill:#d1ecf1,stroke:#0c5460,stroke-width:2px;
    classDef llm fill:#f8d7da,stroke:#721c24,stroke-width:2px;
    classDef support fill:#e2e3e5,stroke:#6c757d,stroke-width:2px
    
```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---