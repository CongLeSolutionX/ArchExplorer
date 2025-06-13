---
created: 2025-06-012 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/openai-openapi
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExZXphanUyaXdybmp5Nm9zZzcyczlmYzFlMmJiaTV0YnoxNmxqYWo4aCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/KeVT1MQ6fDo40GMOws/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# openai-openapi repo project
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
title: "openai-openapi repo project"
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
%%{init: {
  'theme': 'base',
  'themeVariables': {
    'primaryColor': '#e6f3ff',
    'primaryTextColor': '#000',
    'primaryBorderColor': '#7C0000',
    'lineColor': '#F8B229',
    'secondaryColor': '#006100',
    'tertiaryColor': '#fff'
  }
}}%%
flowchart TB
    classDef core fill:#2496ed,stroke:#000,stroke-width:2px,color:white
    classDef service fill:#95DAC1,stroke:#000,stroke-width:1px
    classDef schema fill:#FD6F96,stroke:#000,stroke-width:1px
    classDef workflow fill:#FBB13C,stroke:#000,stroke-width:1px
    classDef integration fill:#73A9AD,stroke:#000,stroke-width:1px
    classDef legend fill:none,stroke:#000,stroke-width:1px

    subgraph Legend
        L1[Core Specification]:::core
        L2[Service Category]:::service
        L3[Schema Definition]:::schema
        L4[Workflow Component]:::workflow
        L5[Integration Point]:::integration
    end

    SPEC{{OpenAPI Specification}}:::core
    click SPEC "https://github.com/openai/openai-openapi/blob/master/openapi.yaml"

    subgraph ServiceCategories
        direction TB
        Models[Models API]:::service
        Completions[Completions API]:::service
        Chat[Chat API]:::service
        Images[Images API]:::service
        Audio[Audio API]:::service
    end

    subgraph Schemas
        direction TB
        ModelSchema[Model Definitions]:::schema
        RequestSchema[Request Schemas]:::schema
        ResponseSchema[Response Schemas]:::schema
        ErrorSchema[Error Definitions]:::schema
    end

    subgraph Workflows
        direction TB
        Validator[OpenAPI Validator]:::workflow
        click Validator "https://github.com/openai/openai-openapi/blob/master/.github/workflows/validate-openapi.yml"
        StainlessUpload[Stainless Upload Pipeline]:::workflow
        click StainlessUpload "https://github.com/openai/openai-openapi/blob/master/.github/workflows/upload-to-stainless.yml"
    end

    subgraph IntegrationPoints
        direction TB
        APIClients[API Clients]:::integration
        DocGen[Documentation Generators]:::integration
        SDKs[SDK Generation]:::integration
    end

    SPEC --> ServiceCategories
    SPEC --> Schemas
    SPEC --> Workflows
    Workflows --> IntegrationPoints
    ServiceCategories --> Schemas

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
