---
created: 2025-03-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Docling Core
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
title: "Docling Core"
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
    User["User<br>(Command Line)"]:::external

    subgraph "Presentation Layer"
        CLI["CLI Component"]:::cli
    end

    subgraph "Business Logic Layer"
        TYPES["Data Types Module<br>(doc, gen, legacy_doc, io, nlp, rec)"]:::core
        EXP["Experimental & Serializer Modules"]:::core
        TRANSFORMS["Transforms<br>(Chunker)"]:::core
    end

    subgraph "Integration Layer"
        SEARCH["Search Module"]:::integration
        RESOURCES["Resources"]:::integration
        UTILITIES["Utilities"]:::integration
    end

    User -->|"triggers"| CLI
    CLI -->|"invokes"| TYPES
    CLI -->|"calls"| UTILITIES
    TYPES -->|"converts"| EXP
    TYPES -->|"prepares"| TRANSFORMS
    TYPES -->|"emits"| RESOURCES
    TRANSFORMS -->|"processes with"| UTILITIES
    RESOURCES -->|"provides mapping to"| SEARCH

    click CLI "https://github.com/docling-project/docling-core/tree/main/docling_core/cli"
    click TYPES "https://github.com/docling-project/docling-core/tree/main/docling_core/types"
    click EXP "https://github.com/docling-project/docling-core/tree/main/docling_core/experimental/serializer"
    click TRANSFORMS "https://github.com/docling-project/docling-core/tree/main/docling_core/transforms/chunker"
    click SEARCH "https://github.com/docling-project/docling-core/tree/main/docling_core/search"
    click RESOURCES "https://github.com/docling-project/docling-core/tree/main/docling_core/resources"
    click UTILITIES "https://github.com/docling-project/docling-core/tree/main/docling_core/utils"

    classDef cli fill:#cecef2,stroke:#003366,stroke-width:2px,color:#003366;
    classDef core fill:#cec222,stroke:#155724,stroke-width:2px,color:#155724;
    classDef integration fill:#fff3cd,stroke:#856404,stroke-width:2px,color:#856404;
    classDef external fill:#f8d7da,stroke:#721c24,stroke-width:2px,color:#721c24
    
```





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---