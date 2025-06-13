---
created: 2025-06-12 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/democratic-inputs
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




# democratic-inputs repo project
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
title: "democratic-inputs repo project"
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
    subgraph "Monorepo"
        direction TB
        README["README.md"]:::gray
        Projects["projects/"]:::gray
    end
    README --> Projects

    subgraph "Projects Container"
        direction TB
        APE["Aligned-Platform-EnergizeAI"]:::module
        Ubuntu["Ubuntu_AI_a_platform_for_equitable_and_inclusive_model_training"]:::module
        CaseLaw["case_law_for_ai_policy"]:::module
        Collective["collective_dialogues_for_democratic_input"]:::module
        Deliberation["deliberation_at_scale"]:::module
        DemFine["democratic_fine_tuning"]:::module
        Inclusive["inclusive_ai_chatgpt_plugin_and_dao_to_engage_marginalized_groups_in_ai"]:::module
        Rappler["making_ai_transparent_and_accountable (rappler_aidialogue)"]:::module
    end

    Projects --> APE
    Projects --> Ubuntu
    Projects --> CaseLaw
    Projects --> Collective
    Projects --> Deliberation
    Projects --> DemFine
    Projects --> Inclusive
    Projects --> Rappler

    %% Aligned-Platform-EnergizeAI detail
    subgraph "Aligned-Platform-EnergizeAI"
        direction TB
        APE_FE["Frontend (Next.js)"]:::frontend
        APE_AGG["Aggregation Pipelines"]:::batch
        APE_TAX["Taxonomy Builder"]:::batch
        APE_FE -->|"uses data from"| APE_AGG
        APE_FE -->|"generates taxonomy via"| APE_TAX
    end
    click APE_FE "https://github.com/openai/democratic-inputs/tree/main/projects/Aligned-Platform-EnergizeAI/app"
    click APE_AGG "https://github.com/openai/democratic-inputs/tree/main/projects/Aligned-Platform-EnergizeAI/aggregation"
    click APE_TAX "https://github.com/openai/democratic-inputs/blob/main/projects/Aligned-Platform-EnergizeAI/taxonomybuilder/tbm.py"

    %% Ubuntu AI detail
    subgraph "Ubuntu_AI Frontend"
        direction TB
        Ubuntu_FE["Pure Frontend (Vite + React)"]:::frontend
    end
    click Ubuntu_FE "https://github.com/openai/democratic-inputs/tree/main/projects/Ubuntu_AI_a_platform_for_equitable_and_inclusive_model_training/frontend/frontend"

    %% case_law_for_ai_policy detail
    subgraph "case_law_for_ai_policy"
        direction TB
        CL_Data["Data & Preprocessing"]:::batch
        CL_Notebooks["Jupyter Experiments"]:::batch
        CL_Docs["Static Docs"]:::batch
        CL_BE["Backend Server"]:::backend
        CL_FE["Frontend Prototype"]:::frontend
        CL_Data --> CL_Notebooks
        CL_Notebooks --> CL_BE
        CL_BE -->|"serves UI to"| CL_FE
    end
    click CL_Data "https://github.com/openai/democratic-inputs/tree/main/projects/case_law_for_ai_policy/data"
    click CL_Notebooks "https://github.com/openai/democratic-inputs/tree/main/projects/case_law_for_ai_policy/case-tools"
    click CL_Docs "https://github.com/openai/democratic-inputs/tree/main/projects/case_law_for_ai_policy/docs"
    click CL_BE "https://github.com/openai/democratic-inputs/blob/main/projects/case_law_for_ai_policy/interactive/backend/server.py"
    click CL_FE "https://github.com/openai/democratic-inputs/tree/main/projects/case_law_for_ai_policy/interactive/frontend"

    %% collective_dialogues_for_democratic_input detail
    subgraph "collective_dialogues_for_democratic_input"
        direction TB
        CD_Exp["Experiment Notebooks & CSVs"]:::batch
        CD_Tools["Support Tools"]:::batch
        CD_Exp --> CD_Tools
    end
    click CD_Exp "https://github.com/openai/democratic-inputs/tree/main/projects/collective_dialogues_for_democratic_input/experiments"
    click CD_Tools "https://github.com/openai/democratic-inputs/tree/main/projects/collective_dialogues_for_democratic_input/tools"

    %% deliberation_at_scale detail
    subgraph "deliberation_at_scale"
        direction TB
        DAS_Data["Data Layer (Drizzle ORM)"]:::database
        DAS_Edge["Edge Functions"]:::backend
        DAS_FE["Frontend (Next.js + GraphQL)"]:::frontend
        DAS_Orch["Orchestrator Service"]:::backend
        DAS_Data --> DAS_Edge
        DAS_Edge --> DAS_FE
        DAS_Orch --> DAS_Data
    end
    click DAS_Data "https://github.com/openai/democratic-inputs/tree/main/projects/deliberation_at_scale/packages/data-core"
    click DAS_Edge "https://github.com/openai/democratic-inputs/tree/main/projects/deliberation_at_scale/packages/edge-functions"
    click DAS_FE "https://github.com/openai/democratic-inputs/tree/main/projects/deliberation_at_scale/packages/frontend"
    click DAS_Orch "https://github.com/openai/democratic-inputs/tree/main/projects/deliberation_at_scale/packages/orchestrator"

    %% democratic_fine_tuning detail
    subgraph "democratic_fine_tuning"
        direction TB
        DF_App["Remix Full-stack App"]:::frontend
        DF_Schema["Prisma Schema"]:::database
        DF_Mig["Migrations"]:::database
        DF_Data["Survey Data"]:::database
        DF_App --> DF_Schema
        DF_Schema --> DF_Mig
        DF_App --> DF_Data
    end
    click DF_Schema "https://github.com/openai/democratic-inputs/blob/main/projects/democratic_fine_tuning/schema.prisma"
    click DF_Mig "https://github.com/openai/democratic-inputs/tree/main/projects/democratic_fine_tuning/migrations"
    click DF_Data "https://github.com/openai/democratic-inputs/tree/main/projects/democratic_fine_tuning/data"

    %% inclusive_ai detail
    subgraph "inclusive_ai_chatgpt_plugin_and_dao"
        direction TB
        IA_FE["Next.js ChatGPT Plugin UI"]:::frontend
    end
    click IA_FE "https://github.com/openai/democratic-inputs/tree/main/projects/inclusive_ai_a_chatgpt_plugin_and_dao_to_engage_marginalized_groups_in_ai/Inclusive.AI app/website"

    %% rappler_aidialogue detail
    subgraph "making_ai_transparent_and_accountable (rappler_aidialogue)"
        direction TB
        RA_FE["Hosted Frontend"]:::frontend
        RA_FN["Serverless Functions"]:::backend
        RA_FE --> RA_FN
    end
    click RA_FN "https://github.com/openai/democratic-inputs/tree/main/projects/making_ai_transparent_and_accountable/rappler_aidialogue/functions"
    click RA_FE "https://github.com/openai/democratic-inputs/tree/main/projects/making_ai_transparent_and_accountable/rappler_aidialogue/hosting"

    classDef monorepo fill:#f0f0f0,stroke:#333,stroke-width:2px
    classDef module fill:#e8e8e8,stroke:#555,stroke-width:1px
    classDef frontend fill:#ADD8E6,stroke:#036,stroke-width:1px
    classDef backend fill:#90EE90,stroke:#036,stroke-width:1px
    classDef database fill:#FFA500,stroke:#963,stroke-width:1px
    classDef batch fill:#D3D3D3,stroke:#666,stroke-width:1px
    classDef gray fill:#CCCCCC,stroke:#333,stroke-width:1px

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