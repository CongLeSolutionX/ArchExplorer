---
created: 2025-03-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Docling
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
title: "Docling"
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
    'flowchart': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'lineColor': '#F8B229'
    }
  }
}%%
flowchart TD
    %% User Input Layer
    subgraph User_Input["User Input"]
        CLI["CLI Tool"]:::interface
        Actor["Actor Interface"]:::interface
    end

    %% Conversion Core
    subgraph Conversion_Core["Conversion Core"]
        DC["DocumentConverter"]:::core
    end

    %% Pipeline Management
    subgraph Pipeline_Management["Pipeline Management"]
        PM["Pipeline Manager"]:::pipelines
    end

    %% Processing Backends
    subgraph Processing_Backends["Processing Backends"]
        GB["General Backends"]:::backends
        DOCX["DOCX + LaTeX Backend"]:::backends
        JSONB["JSON Backend"]:::backends
        XMLB["XML Backend"]:::backends
    end

    %% Data Models & Document Representation
    subgraph Data_Models_and_Document_Representation["Data Models & Document Representation"]
        DM["DoclingDocument & Models"]:::models
    end

    %% ML Models & Plugins
    subgraph ML_Models_and_Plugins["ML Models & Plugins"]
        ML["ML Models & Plugins"]:::models
    end

    %% Utilities & Chunking
    subgraph Utilities_and_Chunking["Utilities & Chunking"]
        UT["Utilities"]:::utilities
        CH["Chunking"]:::utilities
    end

    %% External Integrations & Supporting Infrastructure
    subgraph External_and_Support["External & Support"]
        EXT["External Integrations"]:::external
        CI["CI/CD & Support"]:::cicd
    end

    %% Data Flow Connections
    CLI -->|"initiates"| DC
    Actor -->|"initiates"| DC
    DC -->|"orchestrates"| PM
    PM -->|"selects"| GB
    PM -->|"selects"| DOCX
    PM -->|"selects"| JSONB
    PM -->|"selects"| XMLB
    GB -->|"parses to"| DM
    DOCX -->|"parses to"| DM
    JSONB -->|"parses to"| DM
    XMLB -->|"parses to"| DM
    DM -->|"exports via"| UT
    DM -->|"enhanced by"| ML
    ML -->|"updates"| DM
    UT -->|"prepares segments"| CH
    PM -->|"integrates with"| EXT
    UT -->|"supported by"| CI

    %% Click Events
    click CLI "https://github.com/docling-project/docling/blob/main/docling/cli/main.py"
    click Actor "https://github.com/docling-project/docling/tree/main/.actor/Dockerfile"
    click DC "https://github.com/docling-project/docling/blob/main/docling/document_converter.py"
    click PM "https://github.com/docling-project/docling/tree/main/docling/pipeline"
    click GB "https://github.com/docling-project/docling/tree/main/docling/backend"
    click DOCX "https://github.com/docling-project/docling/tree/main/docling/backend/docx"
    click JSONB "https://github.com/docling-project/docling/tree/main/docling/backend/json"
    click XMLB "https://github.com/docling-project/docling/tree/main/docling/backend/xml"
    click DM "https://github.com/docling-project/docling/tree/main/docling/datamodel"
    click ML "https://github.com/docling-project/docling/tree/main/docling/models"
    click UT "https://github.com/docling-project/docling/tree/main/docling/utils"
    click CH "https://github.com/docling-project/docling/tree/main/docling/chunking"

    %% Styles
    classDef interface fill:#AFF7,stroke:#333,stroke-width:0.5px
    classDef core fill:#FCC3,stroke:#333,stroke-width:0.5px
    classDef pipelines fill:#DFE3,stroke:#333,stroke-width:0.5px
    classDef backends fill:#FCF2,stroke:#333,stroke-width:0.5px
    classDef models fill:#DEA8,stroke:#333,stroke-width:0.5px
    classDef utilities fill:#FEF9,stroke:#333,stroke-width:0.5px
    classDef external fill:#CBD3,stroke:#333,stroke-width:0.5px
    classDef cicd fill:#EDF3,stroke:#333,stroke-width:0.5px
    
```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---