---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# uco3d
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
title: "Meta Research - UCO3D"
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
    "graph": {"htmlLabels": true, 'curve': 'natural'},
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
    %% A. Download Manager Subgraph
    subgraph Download_Manager["Download Manager"]
    style Download_Manager fill:#c2c3,stroke:#333,stroke-width:2px
        DM1["download_dataset.py"]:::download
        DM2["download_dataset_impl.py"]:::download
        DM3["category_to_archives.json"]:::download
    end

    %% B. Data Storage Subgraph
    subgraph Data_Storage["Data Storage"]
    style Data_Storage fill:#c2c3,stroke:#333,stroke-width:2px
        DS1["File System Hierarchy"]:::datastore
        DS2["Metadata Database<br>(metadata.sqlite & set_lists)"]:::datastore
    end

    %% C. Core API Subgraph
    subgraph Core_API["Core API"]
    style Core_API fill:#c2c3,stroke:#333,stroke-width:2px
        API1["UCO3DDataset"]:::api
        API2["UCO3DFrameDataBuilder"]:::api
    end

    %% D. Utilities & Modules Subgraph
    subgraph Utilities_and_Modules["Utilities & Modules"]
    style Utilities_and_Modules fill:#c2c3,stroke:#333,stroke-width:2px
        DU["Dataset Utilities"]:::utils
        CM["Conversion Module"]:::conversion
        RM["Rendering Module"]:::rendering
    end

    %% E. External Libraries Subgraph
    subgraph External["External"]
    style External fill:#c2c3,stroke:#333,stroke-width:2px
        EX1["OpenCV & PyTorch3D"]:::external
        EX2["gsplat"]:::external
    end

    %% F. Usage Layer Subgraph
    subgraph Usage["Usage"]
    style Usage fill:#c2c3,stroke:#333,stroke-width:2px
        EXM["Examples"]:::usage
        TEST["Testing"]:::usage
    end

    %% Connections from Download Manager to Data Storage
    DM1 -->|"download and store"| DS1
    DM2 -->|"download and store"| DS1
    DM3 -->|"download and store"| DS1

    %% Connections from Data Storage to Core API
    DS1 -->|"readcfiles"| API1
    DS1 -->|"read files"| API2
    DS2 -->|"parse metadata"| API1
    DS2 -->|"parse metadata"| API2

    %% Connections from Core API to Utilities & Modules
    API1 -->|"process data"| DU
    API2 -->|"process data"| DU

    %% Connections from Dataset Utilities to Conversion and Rendering Modules
    DU -->|"conversion"| CM
    DU -->|"rendering"| RM

    %% Connections from Conversion and Rendering Modules to External Libraries
    CM -->|"convert camera format"| EX1
    RM -->|"render scene"| EX2

    %% Connections from Core API to Usage layer
    API1 -->|"usage"| EXM
    API2 -->|"usage"| TEST

    %% Styles
    classDef download fill:#FC55,stroke:#000,stroke-width:2px
    classDef datastore fill:#FE62,stroke:#000,stroke-width:2px
    classDef api fill:#9B53,stroke:#000,stroke-width:2px
    classDef utils fill:#AD83,stroke:#000,stroke-width:2px
    classDef conversion fill:#FBC3,stroke:#000,stroke-width:2px
    classDef rendering fill:#D4D2,stroke:#000,stroke-width:2px
    classDef external fill:#FD74,stroke:#000,stroke-width:2px
    classDef usage fill:#C0CC,stroke:#000,stroke-width:2px

    %% Click Events
    click DM1 "https://github.com/facebookresearch/uco3d/blob/main/dataset_download/download_dataset.py"
    click DM2 "https://github.com/facebookresearch/uco3d/blob/main/dataset_download/download_dataset_impl.py"
    click DM3 "https://github.com/facebookresearch/uco3d/blob/main/dataset_download/category_to_archives.json"
    click API1 "https://github.com/facebookresearch/uco3d/blob/main/uco3d/uco3d_dataset.py"
    click API2 "https://github.com/facebookresearch/uco3d/blob/main/uco3d/uco3d_frame_data_builder.py"
    click DU "https://github.com/facebookresearch/uco3d/tree/main/uco3d/dataset_utils/"
    click CM "https://github.com/facebookresearch/uco3d/blob/main/uco3d/dataset_utils/gauss3d_convert.py"
    click RM "https://github.com/facebookresearch/uco3d/blob/main/uco3d/dataset_utils/gauss3d_rendering.py"
    click EXM "https://github.com/facebookresearch/uco3d/tree/main/examples/"
    click TEST "https://github.com/facebookresearch/uco3d/tree/main/tests/"
    
```


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---