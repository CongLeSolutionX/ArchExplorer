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


# Docling Parse
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
    %% Global User
    U("User<br>(CLI/Python Script)"):::user

    %% User Interface Layer
    subgraph User_Interface_Layer["User Interface Layer"]
    style User_Interface_Layer fill:#FFE55,stroke:#663,stroke-width:1px
        subgraph C_Plus_Plus_Executables["C++ Executables"]
        style C_Plus_Plus_Executables fill:#AA25,stroke:#333,stroke-width:0.5px
            P1("parse_v1.exe"):::cpp
            P2("parse_v2.exe"):::cpp
            P3("parse_v2_fonts tool"):::cpp
        end
        subgraph Python_Interface["Python Interface"]
        style Python_Interface fill:#FCE,stroke:#333,stroke-width:0.5px
            PY1("Python CLI"):::python
            PY2("Visualization Tool"):::python
        end
    end

    %% Core Parsing Engine
    subgraph Core_Parsing_Engine["Core Parsing Engine"]
    style Core_Parsing_Engine fill:#E554,stroke:#663,stroke-width:1px
        subgraph C_Plus_Plus_Parser_Engine_V1["C++ Parser Engine - V1"]
        style C_Plus_Plus_Parser_Engine_V1 fill:#AA25,stroke:#333,stroke-width:0.5px
            V1M("V1 Main Source"):::cpp
            V1Lib("V1 PDF Library"):::cpp
            V1Parser("V1 PDF Parser"):::cpp
            V1Post("V1 Post Processors"):::cpp
            V1Q("V1 QPDF"):::cpp
        end
        subgraph C_Plus_Plus_Parser_Engine_V2["C++ Parser Engine - V2"]
        style C_Plus_Plus_Parser_Engine_V2 fill:#AF25,stroke:#333,stroke-width:0.5px
            V2M("V2 Main Source"):::cpp
            V2Res("V2 PDF Resources"):::cpp
            V2Dec("V2 PDF Decoders"):::cpp
            V2San("V2 PDF Sanitizers"):::cpp
            V2Q("V2 QPDF"):::cpp
        end
    end

    %% Pybind11 Integration Layer
    PBind("Pybind11 Layer"):::cpp

    %% Resource & Utility Libraries
    subgraph Resource_and_Utility_Libraries["Resource & Utility Libraries"]
    style Resource_and_Utility_Libraries fill:#CFF,stroke:#333,stroke-width:0.5px
        U1("C++ Utils V1"):::cpp
        U2("C++ Utils V2"):::cpp
        U3("Python PDF Resources"):::python
        U4("Python PDF Resources V2"):::python
    end

    %% Build & Test Infrastructure
    subgraph Build_and_Test_Infrastructure["Build & Test Infrastructure"]
    style Build_and_Test_Infrastructure fill:#EEF,stroke:#333,stroke-width:0.5px
        B1("CMake Build System"):::infra
        B2("Python Build"):::infra
        B3("CI/CD Workflow"):::infra
        B4("Testing Suite"):::infra
    end

    %% Data Flow Connections
    U -->|"triggers"| P1
    U -->|"triggers"| PY1

    %% UI to Core Parsing
    P1 -->|"invokes"| V1M
    P2 -->|"invokes"| V2M
    P3 -->|"invokes"| V2M

    %% Python flow through bindings
    PY1 -->|"calls"| PBind
    PBind -->|"exposes"| V1M
    PBind -->|"exposes"| V2M
    PBind -->|"returns results"| PY2

    %% V1 Internal Flow
    V1M -->|"loads"| V1Lib
    V1Lib -->|"parses"| V1Parser
    V1Parser -->|"post-processes"| V1Post
    V1Lib -->|"integrates"| V1Q

    %% V2 Internal Flow
    V2M -->|"loads"| V2Res
    V2M -->|"decodes"| V2Dec
    V2M -->|"sanitizes"| V2San
    V2Res -->|"integrates"| V2Q

    %% Utility Dependencies
    V1M ---|"uses"| U1
    V2M ---|"uses"| U2
    PY1 ---|"uses"| U3
    PY1 ---|"uses"| U4

    %% Build & Test Integration
    B1 -->|"builds"| P1
    B1 -->|"builds"| P2
    B1 -->|"builds"| P3
    B2 -->|"packages"| PY1
    B3 -->|"monitors"| B1
    B3 -->|"monitors"| B2
    B4 -->|"tests"| V1M
    B4 -->|"tests"| V2M

    %% Click Events for Component Mapping
    click P1 "https://github.com/docling-project/docling-parse/blob/main/app/parse_v1.cpp"
    click P2 "https://github.com/docling-project/docling-parse/blob/main/app/parse_v2.cpp"
    click P3 "https://github.com/docling-project/docling-parse/blob/main/app/parse_v2_fonts.cpp"
    click PY1 "https://github.com/docling-project/docling-parse/blob/main/docling_parse/__init__.py"
    click PY1 "https://github.com/docling-project/docling-parse/blob/main/docling_parse/pdf_parser.py"
    click PY2 "https://github.com/docling-project/docling-parse/blob/main/docling_parse/visualize.py"
    click V1M "https://github.com/docling-project/docling-parse/tree/main/src/v1/"
    click V1Lib "https://github.com/docling-project/docling-parse/tree/main/src/v1/proj_folders/pdf_library"
    click V1Parser "https://github.com/docling-project/docling-parse/tree/main/src/v1/proj_folders/pdf_parser"
    click V1Post "https://github.com/docling-project/docling-parse/tree/main/src/v1/proj_folders/pdf_parser/post_processors"
    click V1Q "https://github.com/docling-project/docling-parse/tree/main/src/v1/proj_folders/pdf_library/qpdf"
    click V2M "https://github.com/docling-project/docling-parse/tree/main/src/v2/"
    click V2Res "https://github.com/docling-project/docling-parse/tree/main/src/v2/pdf_resources"
    click V2Dec "https://github.com/docling-project/docling-parse/tree/main/src/v2/pdf_decoders"
    click V2San "https://github.com/docling-project/docling-parse/tree/main/src/v2/pdf_sanitators"
    click V2Q "https://github.com/docling-project/docling-parse/tree/main/src/v2/qpdf"
    click PBind "https://github.com/docling-project/docling-parse/tree/main/src/pybind/"
    click U1 "https://github.com/docling-project/docling-parse/tree/main/src/v1/utils"
    click U2 "https://github.com/docling-project/docling-parse/tree/main/src/v2/utils"
    click U3 "https://github.com/docling-project/docling-parse/tree/main/docling_parse/pdf_resources"
    click U4 "https://github.com/docling-project/docling-parse/tree/main/docling_parse/pdf_resources_v2"
    click B1 "https://github.com/docling-project/docling-parse/blob/main/CMakeLists.txt"
    click B2 "https://github.com/docling-project/docling-parse/blob/main/pyproject.toml"
    click B3 "https://github.com/docling-project/docling-parse/tree/main/.github/"
    click B4 "https://github.com/docling-project/docling-parse/tree/main/tests/"

    %% Styles
    classDef cpp fill:#AED6F1,stroke:#2471A3,stroke-width:1px
    classDef python fill:#A9DFBF,stroke:#28B463,stroke-width:1px
    classDef infra fill:#D7DBDD,stroke:#7B7D7D,stroke-width:1px
    classDef user fill:#F9E79F,stroke:#B7950B,stroke-width:1px
    class P1,P2,P3,V1M,V1Lib,V1Parser,V1Post,V1Q,V2M,V2Res,V2Dec,V2San,V2Q,PBind,U1,U2 cpp
    class PY1,PY2,U3,U4 python
    class B1,B2,B3,B4 infra
    class U user

```




---

<!-- 
```mermaid
%% Current Mermaid version
info
```  -->


```mermaid
---
title: "CongLeSolutionX"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%{
  init: {
    'flowchart': { 'htmlLabels': false },
    'fontFamily': 'Bradley Hand',
    'themeVariables': {
      'primaryColor': '#fc82',
      'primaryTextColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#81c784',
      'secondaryTextColor': '#6C3483',
      'lineColor': '#F8B229',
      'fontSize': '20px'
    }
  }
}%%
flowchart LR
  My_Meme@{ img: "https://raw.githubusercontent.com/CongLeSolutionX/CongLeSolutionX/refs/heads/main/assets/images/My-meme-light-bulb-question-marks.png", label: "Ăn uống gì chưa ngừi đẹp?", pos: "b", w: 200, h: 150, constraint: "off" }

  Closing_quote@{ shape: braces, label: "...searching insights in the process of formulating better questions..." }

  Closing_quote ~~~ My_Meme
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }

```

---
> **Licenses:**
>
> - **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
> - **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).
> 
---
