---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExYXlxYzd5bHoyOXN2OTZuOXdrbXk4MDN2aHc0dDQ0cW52ZHNkZmt4cSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/l0NwMDQtV5ttjvUUU/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Detectron
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
title: "Meta Research - Detectron"
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
    subgraph Input_Data_Layer["Input/Data Layer"]
    style Input_Data_Layer fill:#22c3,stroke:#333,stroke-width:2px
        dataset["Datasets & Data Loading"] 
        roi["ROI Data & Minibatching"]
        config["Configuration Files"]
    end

    subgraph Model_Processing_Layer["Model/Processing Layer"]
    style Model_Processing_Layer fill:#22c3,stroke:#333,stroke-width:2px
        core["Core Modules"]
        model["Modeling and Network Architecture"]
        ops["Custom Ops/Kernels"]
    end

    subgraph Execution_Layer["Execution Layer"]
    style Execution_Layer fill:#22c3,stroke:#333,stroke-width:2px
        tools["Training & Inference Tools"]
    end

    subgraph Deployment_Build_Layer["Deployment/Build Layer"]
    style Deployment_Build_Layer fill:#22c3,stroke:#333,stroke-width:2px
        build["Build System & Utilities"]
        docker["Docker Environment"]
        ext["External Modules"]
    end

    %% Data flow connections
    config -->|"feeds"| core
    dataset -->|"feeds"| core
    roi -->|"feeds"| core
    core -->|"drives"| model
    core -->|"calls"| ops
    build -->|"builds"| ops
    model -->|"supplies"| tools
    ops -->|"integrates"| tools
    tools -->|"triggers"| build
    build -->|"supports"| docker
    build -->|"extends"| ext

    %% Click Events
    click core "https://github.com/facebookresearch/detectron/tree/main/detectron/core"
    click model "https://github.com/facebookresearch/detectron/tree/main/detectron/modeling"
    click ops "https://github.com/facebookresearch/detectron/tree/main/detectron/ops"
    click dataset "https://github.com/facebookresearch/detectron/tree/main/detectron/datasets"
    click roi "https://github.com/facebookresearch/detectron/tree/main/detectron/roi_data"
    click config "https://github.com/facebookresearch/detectron/tree/main/configs"
    click tools "https://github.com/facebookresearch/detectron/tree/main/tools"
    click build "https://github.com/facebookresearch/detectron/blob/main/CMakeLists.txt"
    click build "https://github.com/facebookresearch/detectron/tree/main/Makefile"
    click build "https://github.com/facebookresearch/detectron/tree/main/cmake"
    click docker "https://github.com/facebookresearch/detectron/tree/main/docker/Dockerfile"
    click ext "https://github.com/facebookresearch/detectron/tree/main/projects/GN"

    %% Styles
    classDef datalayer fill:#f9f3,stroke:#333,stroke-width:2px
    classDef corelayer fill:#bbf3,stroke:#333,stroke-width:2px
    classDef toolslayer fill:#afa3,stroke:#333,stroke-width:2px
    classDef deploylayer fill:#fcc3,stroke:#333,stroke-width:2px

    class dataset,roi,config datalayer
    class core,model,ops corelayer
    class tools toolslayer
    class build,docker,ext deploylayer
    
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

