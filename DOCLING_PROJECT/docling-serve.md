---
created: 2025-03-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExNTIzMjFxZmYwcXBqeGZ0eWR4cXduOGtndzlrZXNjOWd4eDl1YTRjMyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/Kn5YFlengdRmw/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Docling Serve
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
  theme: base
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
    %% External Clients
    Clients["External Clients<br>(HTTP Requests)"]:::external

    %% Configuration & Deployment subgraph
    subgraph Configuration_and_Deployment["Configuration & Deployment"]
        Env[".env.example"]:::config
        Settings["settings.py"]:::config
        Container["Containerfile"]:::config
        Docs["Documentation<br>(docs/)"]:::config
    end

    %% API Server Module subgraph
    subgraph API_Server_Module["API Server Module"]
        App["API Server:<br>app.py"]:::api
        Main["API Server:<br>__main__.py"]:::api
    end

    %% Data Modeling & Conversion subgraph
    subgraph Data_Modeling_and_Conversion["Data Modeling & Conversion"]
        DataModel["Datamodel Folder"]:::conversion
        Controller["Conversion Controller<br>(docling_conversion.py)"]:::conversion
    end

    %% Decision node for engine delegation
    Decision["Conversion Type?"]:::conversion

    %% Async Conversion Engine subgraph
    subgraph Async_Conversion_Engine["Async Conversion Engine"]
        AsyncOrch["Async Orchestrator"]:::engine
        Worker["Worker"]:::engine
    end

    %% Blocking Conversion Engine subgraph
    subgraph Blocking_Conversion_Engine["Blocking Conversion Engine"]
        Block["Blocking Engine"]:::engine
    end

    %% Base Orchestrator node
    BaseOrch["Base Orchestrator"]:::engine

    %% Optional UI Service
    UI["Optional UI Service<br>(gradio_ui.py)"]:::ui

    %% Flow connections
    Env --> App
    Settings --> App
    Container --> App
    Docs --> App

    Clients --> App
    App --> DataModel
    App --> Controller
    Controller --> Decision

    Decision -- "async" --> AsyncOrch
    Decision -- "block" --> Block

    AsyncOrch --> Worker
    AsyncOrch --- BaseOrch
    Block --- BaseOrch

    AsyncOrch --> Controller
    Worker --> Controller
    Block --> Controller

    Controller --> App
    App --> Clients

    App --> UI
    Clients --> UI

    %% Click Events for API Server Module
    click App "https://github.com/docling-project/docling-serve/blob/main/docling_serve/app.py"
    click Main "https://github.com/docling-project/docling-serve/blob/main/docling_serve/__main__.py"

    %% Click Events for Data Modeling & Conversion
    click DataModel "https://github.com/docling-project/docling-serve/tree/main/docling_serve/datamodel"
    click Controller "https://github.com/docling-project/docling-serve/blob/main/docling_serve/docling_conversion.py"

    %% Click Events for Async Conversion Engine
    click AsyncOrch "https://github.com/docling-project/docling-serve/blob/main/docling_serve/engines/async_local/orchestrator.py"
    click Worker "https://github.com/docling-project/docling-serve/blob/main/docling_serve/engines/async_local/worker.py"

    %% Click Event for Blocking Conversion Engine
    click Block "https://github.com/docling-project/docling-serve/tree/main/docling_serve/engines/block_local"

    %% Click Event for Base Orchestrator
    click BaseOrch "https://github.com/docling-project/docling-serve/blob/main/docling_serve/engines/base_orchestrator.py"

    %% Click Event for Optional UI Service
    click UI "https://github.com/docling-project/docling-serve/blob/main/docling_serve/gradio_ui.py"

    %% Click Events for Configuration & Deployment
    click Env "https://github.com/docling-project/docling-serve/blob/main/.env.example"
    click Settings "https://github.com/docling-project/docling-serve/blob/main/docling_serve/settings.py"
    click Container "https://github.com/docling-project/docling-serve/tree/main/Containerfile"
    click Docs "https://github.com/docling-project/docling-serve/tree/main/docs/"

    %% Styles
    classDef external fill:#AED6F1,stroke:#2471A3,stroke-width:2px,color:#000
    classDef api fill:#A3E4D7,stroke:#117864,stroke-width:2px,color:#000
    classDef conversion fill:#F9E79F,stroke:#B7950B,stroke-width:2px,color:#000
    classDef engine fill:#FAD7A0,stroke:#E67E22,stroke-width:2px,color:#000
    classDef ui fill:#F5B7B1,stroke:#C0392B,stroke-width:2px,color:#000
    classDef config fill:#D5DBDB,stroke:#7B7D7D,stroke-width:2px,color:#000


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

  Closing_quote ~~~ My_Meme
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }

```

---
> **Licenses:**
>
> - **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
> - **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).
> 
---
