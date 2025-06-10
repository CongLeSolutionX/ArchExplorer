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


# Docling MCP
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
    %% External Components
    Clients["Client Applications"]:::client
    Integration["Claude Desktop Integration"]:::external
    CICD["CI/CD Pipelines"]:::infrastructure

    %% Internal Service Components
    subgraph Docling_MCP_Service["Docling MCP Service"]
        DMS["Docling MCP Server"]:::service
        CT["Conversion Tools"]:::tools
        GT["Generation Tools"]:::tools
        CC["Caching Component"]:::cache
        DS["Settings Component"]:::settings
        LG["Logging Component"]:::logging
    end

    %% Relationships and Data Flows
    Clients -->|"sends request"| DMS
    Integration -->|"provides config"| DMS
    DMS -->|"executes"| CT
    DMS -->|"executes"| GT
    DMS -->|"utilizes"| CC
    DMS -->|"loads"| DS
    DMS -->|"records logs"| LG
    CICD -->|"automates build test deploy"| DMS

    %% Click Events
    click DMS "https://github.com/docling-project/docling-mcp/blob/main/docling_mcp/server.py"
    click CT "https://github.com/docling-project/docling-mcp/blob/main/docling_mcp/tools/conversion.py"
    click GT "https://github.com/docling-project/docling-mcp/blob/main/docling_mcp/tools/generation.py"
    click CC "https://github.com/docling-project/docling-mcp/blob/main/docling_mcp/docling_cache.py"
    click DS "https://github.com/docling-project/docling-mcp/blob/main/docling_mcp/docling_settings.py"
    click LG "https://github.com/docling-project/docling-mcp/blob/main/docling_mcp/logger.py"
    click Clients "https://github.com/docling-project/docling-mcp/blob/main/clients/test_llama_stack.py"
    click CICD "https://github.com/docling-project/docling-mcp/tree/main/.github/workflows"
    click Integration "https://github.com/docling-project/docling-mcp/blob/main/docs/integrations/claude_desktop_config.json"

    %% Styles
    classDef service fill:#f9c3,stroke:#333,stroke-width:2px
    classDef tools fill:#bbf3,stroke:#333,stroke-width:2px
    classDef cache fill:#afa3,stroke:#333,stroke-width:2px
    classDef settings fill:#ffa3,stroke:#333,stroke-width:2px
    classDef logging fill:#fcc3,stroke:#333,stroke-width:2px
    classDef client fill:#cfc3,stroke:#333,stroke-width:2px
    classDef external fill:#fcf3,stroke:#333,stroke-width:2px
    classDef infrastructure fill:#ddd3,stroke:#333,stroke-width:2px

```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
