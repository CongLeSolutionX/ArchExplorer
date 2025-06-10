---
created: 2025-03-09 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExbTZsd3ljN3AwYzFvbWN1aXZmZG1xMW9zb3o5cmcxM2F0NzI4dWEwYyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/J4z7Q5KUXT8F9rfmcL/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# semantic-kernel
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
title: "MICROSOFT - Semantic Kernel"
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
flowchart TD
    %% Client Application
    U("Client Application"):::client

    %% Core Kernel & Abstractions (Central Brain)
    CK("Core Kernel & Abstractions<br>(Ties AI functions & Orchestration)"):::kernel

    %% Service Connectors
    SC("Service Connectors<br>(LLM providers integration)"):::connector

    %% Memory & Vector Stores
    MS("Memory & Vector Stores<br>(Vector DBs and Cache)"):::memory

    %% Plugin/Agent Framework
    PA("Plugin/Agent Framework<br>(Plugins and Agents)"):::plugin

    %% Template Engine & Prompt Rendering
    TE("Template Engine & Prompt Rendering<br>(Prompt Processing)"):::template

    %% Planners
    PL("Planners<br>(Execution planning)"):::planner

    %% Process Orchestration
    PO("Process Orchestration<br>(Cloud & Local)"):::orchestration

    %% Integrations & External Connectors
    IE("Integrations & External Connectors<br>(External APIs & Search)"):::integration

    %% Data Flow Connections
    U -->|"request"| CK
    CK -->|"calls"| SC
    CK -->|"queries"| MS
    CK -->|"invokes"| PA
    CK -->|"renders"| TE
    CK -->|"plans"| PL
    CK -->|"orchestrates"| PO
    CK -->|"integrates"| IE

    %% Feedback and Supplementary Flows
    PA -->|"feedback"| CK
    PL -->|"instructions"| PA
    TE -->|"template output"| PA

    %% Click Events for Component Mappings
    click CK "https://github.com/microsoft/semantic-kernel/blob/main/python/semantic_kernel/kernel.py"
    click CK "https://github.com/microsoft/semantic-kernel/blob/main/python/semantic_kernel/kernel_types.py"
    click CK "https://github.com/microsoft/semantic-kernel/tree/main/python/semantic_kernel"
    click SC "https://github.com/microsoft/semantic-kernel/tree/main/python/semantic_kernel/connectors/ai/"
    click MS "https://github.com/microsoft/semantic-kernel/tree/main/python/semantic_kernel/connectors/memory/"
    click PA "https://github.com/microsoft/semantic-kernel/tree/main/python/semantic_kernel/agents/"
    click TE "https://github.com/microsoft/semantic-kernel/tree/main/python/semantic_kernel/prompt_template/"
    click PL "https://github.com/microsoft/semantic-kernel/tree/main/python/semantic_kernel/planners/"
    click PO "https://github.com/microsoft/semantic-kernel/tree/main/python/semantic_kernel/processes/"
    click IE "https://github.com/microsoft/semantic-kernel/tree/main/python/semantic_kernel/connectors/openapi_plugin/"
    click IE "https://github.com/microsoft/semantic-kernel/tree/main/python/semantic_kernel/connectors/search_engine/"

    %% Style Definitions
    classDef client fill:#f9f7,stroke:#333,stroke-width:2px;
    classDef kernel fill:#faa3,stroke:#333,stroke-width:2px;
    classDef connector fill:#adf5,stroke:#333,stroke-width:2px;
    classDef memory fill:#daf5,stroke:#333,stroke-width:2px;
    classDef plugin fill:#fc93,stroke:#333,stroke-width:2px;
    classDef template fill:#ff94,stroke:#333,stroke-width:2px;
    classDef planner fill:#cfc5,stroke:#333,stroke-width:2px;
    classDef orchestration fill:#9ff3,stroke:#333,stroke-width:2px;
    classDef integration fill:#fda4,stroke:#333,stroke-width:2px;

```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
