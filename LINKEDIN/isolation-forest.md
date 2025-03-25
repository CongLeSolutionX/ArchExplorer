---
created: 2025-03-24 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# isolation-forest
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---



```mermaid
---
title: "LinkedIn - Isolation Forest"
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
    'graph': { 'htmlLabels': false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    %% External Data and Services
    dataIngestion["Data Ingestion (CSV/Raw Data)"]:::external
    sparkCluster["Spark Cluster"]:::external
    gradleBuild["Gradle Build & Dependency"]:::build
    pythonPackaging["Python Packaging & Configuration"]:::python
    ciCd["CI/CD Pipeline"]:::ci

    %% Isolation Forest Engine (Scala/Spark Module)
    subgraph "Isolation Forest Engine (Scala/Spark Module)"
        engine["Isolation Forest Engine"]:::scala
        engine --> df["Spark DataFrame"]:::scala
        df --> training["IsolationForest Training Process"]:::scala
        training --> persistence["Model Persistence (HDFS/Disk)"]:::storage
        training --> coreClasses["Core Classes: IsolationForest, IsolationForestModel, IsolationTree, Nodes"]:::scala
        training --> supportUtilities["Support Utilities (BaggedPoint, SharedTrainLogic, Utils)"]:::scala
    end

    %% ONNX Converter (Python Module)
    subgraph "ONNX Converter (Python Module)"
        onnxConversion["ONNX Conversion Process"]:::python
        onnxConversion --> inference["Python Inference Workflow (ONNXRuntime)"]:::python
    end

    %% Data Flow Connections
    dataIngestion --> df
    sparkCluster --> df
    persistence --> onnxConversion
    gradleBuild --> engine
    pythonPackaging --> onnxConversion
    ciCd --> gradleBuild
    ciCd --> pythonPackaging

    %% Click Events
    click engine "https://github.com/linkedin/isolation-forest/tree/master/isolation-forest/src/main/scala/com/linkedin/relevance/isolationforest/"
    click coreClasses "https://github.com/linkedin/isolation-forest/tree/master/isolation-forest/src/main/scala/com/linkedin/relevance/isolationforest/"
    click supportUtilities "https://github.com/linkedin/isolation-forest/tree/master/isolation-forest/src/main/scala/com/linkedin/relevance/isolationforest/core/"
    click onnxConversion "https://github.com/linkedin/isolation-forest/blob/master/isolation-forest-onnx/src/isolationforestonnx/isolation_forest_converter.py"
    click pythonPackaging "https://github.com/linkedin/isolation-forest/tree/master/isolation-forest-onnx/"
    click ciCd "https://github.com/linkedin/isolation-forest/blob/master/.github/workflows/ci.yml"
    click gradleBuild "https://github.com/linkedin/isolation-forest/blob/master/build.gradle"

    %% Styles
    classDef scala fill:#AD22,stroke:#1F618D,stroke-width:2px;
    classDef python fill:#AF22,stroke:#196F3D,stroke-width:2px;
    classDef external fill:#FE79F,stroke:#B7950B,stroke-width:2px;
    classDef storage fill:#EDAEF,stroke:#8E44AD,stroke-width:2px;
    classDef build fill:#F7B1,stroke:#C0392B,stroke-width:2px;
    classDef ci fill:#FDD1,stroke:#D35400,stroke-width:2px
    
```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---