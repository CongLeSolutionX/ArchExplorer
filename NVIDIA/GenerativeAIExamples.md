---
created: 2025-03-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExYTAwbDRqbDh6ZmlvcWs1Z255NHc0MGllcXc4Z3BtMWtzcGpqdTV3ZiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/4L7kCOvDDpJw4/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Generative AI Examples
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
title: "CHANGE_ME_DADDY"
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
    "graph": { "htmlLabels": false, 'curve': 'linear' },
    'themeVariables': {
        'fontFamily': 'Fantasy',
        'fontSize': '20px',
        'primaryColor': '#ffff',
        'primaryTextColor': '#55ff',
        'primaryBorderColor': '#7c2',
        'lineColor': '#F8B229',
        'secondaryColor': '#006100',
        'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TB
    %% Presentation Layer
    subgraph Presentation_Layer["Presentation Layer"]
        UI1["RAG Playground Web UI"]:::frontend
        UI2["Community Sample Chat UI"]:::frontend
    end

    %% Application/Microservice Layer
    subgraph Application_Layer["Application Layer"]
        CMS["Chain Server Microservice"]:::backend
        CS["Chain Server"]:::backend
        CS_DF["Chain Server Dockerfile"]:::deployment
        RM["Retrieval Module"]:::backend
        LLM["LLM Integration"]:::backend
        DCD["Docker Compose Deployments"]:::deployment
        API["NVIDIA API Catalog"]:::deployment
    end

    %% Data Layer
    subgraph Data_Layer["Data Layer"]
        ING["Ingestion Pipeline"]:::ingestion
        MMR["Multimodal Retrieval Ingestion"]:::ingestion
    end

    %% Observability and Evaluation Layer
    subgraph Observability_and_Evaluation["Observability & Evaluation"]
        EVAL["Evaluation Tools"]:::observability
        OBS["Observability Tools"]:::observability
    end

    %% Experimentation Layer
    subgraph Experimentation_Layer["Experimentation Layer"]
        NOTE["Experimentation Notebooks"]:::experimental
        EVALNB["Evaluator Notebook"]:::experimental
        SYNNB["Synthetic Data Generation Notebook"]:::experimental
    end

    %% Data Flow Connections
    UI1 -->|"submits query"| CMS
    UI2 -->|"submits query"| CMS

    CMS -->|"processes request"| CS
    CMS -->|"uses Docker"| DCD
    CS -->|"invokes retrieval"| RM
    CS -->|"invokes LLM"| LLM
    CS -->|"uses Docker file"| CS_DF
    CMS -->|"fetches API key"| API

    ING -->|"provides data"| RM
    MMR -->|"provides Multi-modal data"| RM

    CS -->|"reports metrics"| OBS
    CS -->|"evaluated by"| EVAL

    %% Integration of Experimentation
    NOTE --> |"prototypes and experiments"| CS
    EVALNB --> |"validates components"| CS
    SYNNB --> |"generates synthetic data"| RM

    %% Styles
    classDef frontend fill:#cef3,stroke:#333,stroke-width:2px;
    classDef backend fill:#c3d9,stroke:#333,stroke-width:2px;
    classDef ingestion fill:#fcc5,stroke:#333,stroke-width:2px;
    classDef observability fill:#f9d2,stroke:#333,stroke-width:2px;
    classDef experimental fill:#fce2,stroke:#333,stroke-width:2px;
    classDef deployment fill:#ff95,stroke:#333,stroke-width:2px;

    %% Click Events
    click CMS "https://github.com/nvidia/generativeaiexamples/blob/main/RAG/src/chain_server/server.py"
    click CS "https://github.com/nvidia/generativeaiexamples/tree/main/RAG/src/chain_server"
    click CS_DF "https://github.com/nvidia/generativeaiexamples/tree/main/RAG/src/chain_server/Dockerfile"
    click RM "https://github.com/nvidia/generativeaiexamples/tree/main/RAG/examples/advanced_rag/multimodal_rag/retriever"
    click LLM "https://github.com/nvidia/generativeaiexamples/tree/main/RAG/examples/advanced_rag/multimodal_rag/llm"
    click DCD "https://github.com/nvidia/generativeaiexamples/blob/main/RAG/examples/advanced_rag/multi_turn_rag/docker-compose.yaml"
    click UI1 "https://github.com/nvidia/generativeaiexamples/tree/main/RAG/src/rag_playground"
    click UI2 "https://github.com/nvidia/generativeaiexamples/tree/main/community/fm-asr-streaming-rag/frontend"
    click ING "https://github.com/nvidia/generativeaiexamples/tree/main/community/streaming_ingest_rag"
    click MMR "https://github.com/nvidia/generativeaiexamples/tree/main/community/multimodal_retrieval"
    click EVAL "https://github.com/nvidia/generativeaiexamples/tree/main/RAG/tools/evaluation"
    click OBS "https://github.com/nvidia/generativeaiexamples/tree/main/RAG/tools/observability"
    click NOTE "https://github.com/nvidia/generativeaiexamples/tree/main/RAG/notebooks"
    click EVALNB "https://github.com/nvidia/generativeaiexamples/tree/main/nemo/Evaluator"
    click SYNNB "https://github.com/nvidia/generativeaiexamples/tree/main/nemo/retriever-synthetic-data-generation/notebooks"

```





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
