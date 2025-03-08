---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Detectron 2
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
title: "Meta Research - Detectron 2"
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
    subgraph Configuration_and_Data_Input["Configuration & Data Input"]
    style Configuration_and_Data_Input fill:#c491,stroke:#333,stroke-width:2px
        conf("Configuration/Model Zoo"):::config
        data("Data Pipeline"):::data
    end

    subgraph Model_Construction_and_Training["Model Construction & Training"]
    style Model_Construction_and_Training fill:#c491,stroke:#333,stroke-width:2px
        ml("Modeling & Layers"):::core
        train("Training & Inference Engine"):::training
        plug("Projects/Extensions"):::plugin
    end

    subgraph Evaluation_and_Deployment["Evaluation & Deployment"]
    style Evaluation_and_Deployment fill:#c491,stroke:#333,stroke-width:2px
        eval("Evaluation Module"):::training
        deploy("Export & Deployment"):::deploy
    end

    ci("CI/CD & Testing"):::testing

    conf -->|"configures"| train
    data -->|"supplies_data"| train
    train <-->|"integrated"| ml
    plug -->|"extends"| train
    train -->|"outputs"| eval
    eval -->|"feeds"| deploy
    ci --- train

    click conf "https://github.com/facebookresearch/detectron2/tree/main/configs/"
    click data "https://github.com/facebookresearch/detectron2/tree/main/detectron2/data/datasets"
    click train "https://github.com/facebookresearch/detectron2/tree/main/detectron2/engine"
    click ml "https://github.com/facebookresearch/detectron2/tree/main/detectron2/modeling"
    click deploy "https://github.com/facebookresearch/detectron2/tree/main/detectron2/export"
    click plug "https://github.com/facebookresearch/detectron2/tree/main/detectron2/projects"
    click ci "https://github.com/facebookresearch/detectron2/tree/main/tests"

    classDef config fill:#DAD2,stroke:#000,stroke-width:1px
    classDef data fill:#9E92,stroke:#000,stroke-width:1px
    classDef training fill:#AD82,stroke:#000,stroke-width:1px
    classDef core fill:#ADF2,stroke:#000,stroke-width:1px
    classDef deploy fill:#FA25,stroke:#000,stroke-width:1px
    classDef plugin fill:#F5E2,stroke:#000,stroke-width:1px
    classDef testing fill:#C25,stroke:#000,stroke-width:1px
    
```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---