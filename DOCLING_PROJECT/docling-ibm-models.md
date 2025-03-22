---
created: 2025-03-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Docling IBM Models
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
title: "Docling IBM Models"
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
    Document_Input["Document Input<br>(PDF/PNG)"]:::input
    Preprocessing["Preprocessing"]:::preprocess

    Document_Input --> Preprocessing

    subgraph Core_AI_Modules["Core AI Modules"]
        CF("Code Formula Predictor"):::ai
        DFC("Document Figure Classifier"):::ai
        LP("Layout Predictor"):::ai
        TF("TableFormer Module"):::ai
        RO("Reading Order Module"):::ai
    end

    Preprocessing --> CF
    Preprocessing --> DFC
    Preprocessing --> LP
    Preprocessing --> TF
    Preprocessing --> RO

    CF --> Demo("Visualization / Demo Applications"):::demo
    DFC --> Demo
    LP --> Demo
    TF --> Demo
    RO --> Demo

    subgraph Configuration_and_Pipeline["Configuration & Pipeline"]
        TestConfig("Test Config<br>(tests/test_tf_predictor.py)"):::config
        PoetryConfig("Poetry Config<br>(pyproject.toml)"):::config
    end

    TestConfig --> Preprocessing
    PoetryConfig --> Preprocessing

    CI_CD("CI/CD & Packaging<br>(.github)"):::ci
    CI_CD --> TestConfig
    CI_CD --> PoetryConfig

    click CF "https://github.com/docling-project/docling-ibm-models/tree/main/docling_ibm_models/code_formula_model"
    click DFC "https://github.com/docling-project/docling-ibm-models/tree/main/docling_ibm_models/document_figure_classifier_model"
    click LP "https://github.com/docling-project/docling-ibm-models/tree/main/docling_ibm_models/layoutmodel"
    click TF "https://github.com/docling-project/docling-ibm-models/tree/main/docling_ibm_models/tableformer"
    click RO "https://github.com/docling-project/docling-ibm-models/tree/main/docling_ibm_models/reading_order"
    click Demo "https://github.com/docling-project/docling-ibm-models/tree/main/demo"
    click TestConfig "https://github.com/docling-project/docling-ibm-models/blob/main/tests/test_tf_predictor.py"
    click PoetryConfig "https://github.com/docling-project/docling-ibm-models/blob/main/pyproject.toml"
    click CI_CD "https://github.com/docling-project/docling-ibm-models/blob/main/.github"

    classDef input fill:#ccffcc,stroke:#333,stroke-width:2px
    classDef preprocess fill:#ffffcc,stroke:#333,stroke-width:2px
    classDef ai fill:#ffcccc,stroke:#333,stroke-width:2px
    classDef demo fill:#cce5ff,stroke:#333,stroke-width:2px
    classDef config fill:#d9d2e9,stroke:#333,stroke-width:2px
    classDef ci fill:#f4cccc,stroke:#333,stroke-width:2px
    
```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---