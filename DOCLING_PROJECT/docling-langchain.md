---
created: 2025-03-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Docling Langchain
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
title: "Docling Langchain"
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
    %% Main Runtime Architecture
    Client["Client<br>(User Code / Notebook)"]:::client
    Input["Input Source<br>(File Paths/External Files)"]:::source

    %% langchain_docling Package Container
    subgraph langchain_docling_Package["langchain_docling Package"]
        Loader["DoclingLoader"]:::loader
        Converter["Converter"]:::module
        Chunker["Chunker"]:::module
        MetaExtractor["Meta Extractor"]:::module
        ExportHandler["Export Handler"]:::module
        Loader -->|"uses"| Converter
        Converter -->|"transforms"| Chunker
        Chunker -->|"splits_into"| MetaExtractor
        MetaExtractor -->|"attaches"| ExportHandler
    end

    %% Data Flow Connections
    Client -->|"calls"| Loader
    Input -->|"provides"| Loader
    ExportHandler -->|"produces"| Output["Documents for LangChain"]:::output
    Output -->|"consumed by"| LangChain["LangChain"]:::external
    Output -->|"integrates with"| Docling["Docling"]:::external

    %% Supporting Components (Non-Runtime but Quality Assurance)
    Tests["Tests<br>(Loader Behavior)"]:::support
    CICD["CI/CD & Config"]:::support
    Loader ---|"verified by"| Tests
    Loader ---|"maintained by"| CICD

    %% Click Events
    click Client "https://github.com/docling-project/docling-langchain/blob/main/examples/docling_loader.ipynb"
    click Loader "https://github.com/docling-project/docling-langchain/blob/main/langchain_docling/loader.py"
    click Output "https://github.com/docling-project/docling-langchain/tree/main/langchain_docling/"
    click Tests "https://github.com/docling-project/docling-langchain/blob/main/test/test_loader.py"
    click CICD "https://github.com/docling-project/docling-langchain/tree/main/.github/"

    %% Styles
    classDef client fill:#ffcccc,stroke:#aa0000,stroke-width:2px
    classDef source fill:#ccffcc,stroke:#009900,stroke-width:2px
    classDef loader fill:#ffffcc,stroke:#999900,stroke-width:2px
    classDef module fill:#cce5ff,stroke:#0066cc,stroke-width:2px
    classDef output fill:#d9ccff,stroke:#6600cc,stroke-width:2px
    classDef external fill:#ffedcc,stroke:#cc6600,stroke-width:2px
    classDef support fill:#e6e6e6,stroke:#999999,stroke-width:2px
    
```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---