---
created: 2025-03-09 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Mark It Down
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
title: "MICROSOFT - Mark It Down"
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
graph TB
    subgraph Input
        CLI["CLI Interface"]:::cli
        API["Python API"]:::api
        Docker["Docker Container"]:::docker
        InputFormats["Supported Formats"]:::formats
    end

    subgraph Core
        Engine["Core Processing Engine"]:::core
        Detection["Format Detection"]:::core
        Conversion["Conversion Logic"]:::core
        PackageInterface["Package Interface"]:::core
    end

    subgraph External
        LLM["OpenAI LLM"]:::external
        OCR["OCR Engine"]:::external
        Speech["Speech-to-Text"]:::external
    end

    subgraph Testing
        Tests["Test Framework"]:::test
        TestFiles["Test Files"]:::test
    end

    subgraph Config
        PyConfig["Package Config"]:::config
        CI["CI/CD"]:::config
    end

    subgraph Output
        MD["Markdown Output"]:::output
    end

    %% Relationships
    CLI --> Engine
    API --> Engine
    Docker --> Engine
    InputFormats --> Detection
    Detection --> Conversion
    Engine --> External
    External --> Conversion
    Conversion --> MD
    PackageInterface --> Engine
    Engine --> Tests
    TestFiles --> Tests

    %% Click Events
    click Engine "https://github.com/microsoft/markitdown/blob/main/src/markitdown/_markitdown.py"
    click CLI "https://github.com/microsoft/markitdown/blob/main/src/markitdown/__main__.py"
    click PackageInterface "https://github.com/microsoft/markitdown/blob/main/src/markitdown/__init__.py"
    click Docker "https://github.com/microsoft/markitdown/tree/main/Dockerfile"
    click Tests "https://github.com/microsoft/markitdown/blob/main/tests/test_markitdown.py"
    click TestFiles "https://github.com/microsoft/markitdown/tree/main/tests/test_files"
    click PyConfig "https://github.com/microsoft/markitdown/blob/main/pyproject.toml"
    click CI "https://github.com/microsoft/markitdown/tree/main/.github/workflows"

    %% Styling
    classDef core fill:#23f5
    classDef external fill:#f544
    classDef output fill:#c3a5
    classDef cli fill:#35e2
    classDef api fill:#395f
    classDef docker fill:#395f
    classDef formats fill:#3954
    classDef test fill:#c27
    classDef config fill:#7d22

    %% Legend
    subgraph Legend
        L1["Core Components"]:::core
        L2["External Services"]:::external
        L3["Output"]:::output
        L4["Input Interfaces"]:::cli
        L5["Testing"]:::test
        L6["Configuration"]:::config
    end
    
```





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---