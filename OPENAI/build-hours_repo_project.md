---
created: 2025-06-012 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/build-hours
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExdTc4eTF5ZGpodHZoN2Y2cXpzcjZ0N3Y5aXlrOHQyOHYzcTk5cXNieCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/CdUPebPzF2kOQ/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# build-hours repo project
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
title: "build-hours repo project"
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
    %% Monorepo Overview
    subgraph "Build Hours Monorepo"
        subgraph "Infrastructure"
            Dev["Developer Environment"]:::external
            CI["CI/CD Pipeline"]:::external
            PM["Package Manager (pip / npm)"]:::external
            DH["Docker Host"]:::external
        end
        subgraph "Demo Modules"
            Rec["11-recommendation"]:::module
            IMG["13-image-gen"]:::module
            AGT["12-agentic-tool-calling"]:::module
            DST["10-distillation"]:::module
            STR["6-structured_outputs_assistant-final"]:::module
            RT["9-realtime-console-example"]:::module
            SP["7-shipmentPlanning"]:::module
            FT["3-4o_mini_fine_tuning"]:::module
        end
    end

    %% Detailed 11-recommendation Architecture
    subgraph "11-recommendation Detailed Architecture"
        UI["Streamlit UI Pages"]:::ui
        BE["Backend Service Logic"]:::service
        CFG["Configuration Layer"]:::service
        DB["Qdrant Vector DB"]:::data
        SCRIPT["Data Ingestion Script"]:::service
        DATA["Sample Data (CSV)"]:::data
        API["OpenAI Embedding API"]:::external
        Docker["Docker Compose Orchestration"]:::service
    end

    %% Relationships
    Dev --> Rec
    PM --> Rec
    DH --> Rec
    CI --> Rec

    Rec -->|"contains"| UI
    Rec -->|"contains"| BE
    Rec -->|"contains"| CFG
    Rec -->|"contains"| DB
    Rec -->|"contains"| SCRIPT
    Rec -->|"contains"| DATA
    Rec -->|"contains"| Docker

    UI -->|"requests"| BE
    BE -->|"queries"| DB
    BE -->|"calls"| API
    SCRIPT -->|"loads data into"| DB
    SCRIPT -->|"reads"| DATA
    Docker -->|"orchestrates"| BE
    Docker -->|"orchestrates"| DB

    %% Click Events for 11-recommendation
    click Rec "https://github.com/openai/build-hours/tree/main/11-recommendation"
    click UI "https://github.com/openai/build-hours/blob/main/11-recommendation/pages/page_1_semantic_search.py"
    click UI "https://github.com/openai/build-hours/blob/main/11-recommendation/pages/page_2_explainable_recommendations.py"
    click BE "https://github.com/openai/build-hours/blob/main/11-recommendation/app.py"
    click BE "https://github.com/openai/build-hours/blob/main/11-recommendation/helper_functions.py"
    click CFG "https://github.com/openai/build-hours/blob/main/11-recommendation/config.py"
    click SCRIPT "https://github.com/openai/build-hours/blob/main/11-recommendation/upload-to-qdrant.py"
    click DATA "https://github.com/openai/build-hours/blob/main/11-recommendation/upload-data/fake_hardware_data.csv"
    click Docker "https://github.com/openai/build-hours/blob/main/11-recommendation/docker-compose.yaml"
    click CFG "https://github.com/openai/build-hours/blob/main/11-recommendation/requirements.txt"

    %% Click Events for other demo modules
    click IMG "https://github.com/openai/build-hours/tree/main/13-image-gen/imagegen-demo"
    click AGT "https://github.com/openai/build-hours/tree/main/12-agentic-tool-calling"
    click DST "https://github.com/openai/build-hours/tree/main/10-distillation"
    click STR "https://github.com/openai/build-hours/tree/main/6-structured_outputs-assistant-final"
    click RT "https://github.com/openai/build-hours/tree/main/9-realtime/openai-realtime-console-example"
    click SP "https://github.com/openai/build-hours/tree/main/7-reasoning/shipmentPlanning"
    click FT "https://github.com/openai/build-hours/tree/main/3-4o_mini_fine_tuning"

    %% Styling
    classDef ui fill:#cce5ff,stroke:#0366d6,color:#000
    classDef service fill:#d4edda,stroke:#237a1d,color:#000
    classDef data fill:#fff3cd,stroke:#856404,color:#000
    classDef external fill:#e2e3e5,stroke:#6c757d,color:#000
    classDef module fill:#f0f0f0,stroke:#343a40,color:#000

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
