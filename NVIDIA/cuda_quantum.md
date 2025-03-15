---
created: 2025-03-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Cuda Quantum
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
title: "Cuda Quantum"
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
    "flowchart": { "htmlLabels": false, 'curve': 'linear' },
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
flowchart TD
    A["User Quantum Algorithm<br>(C++/Python Input)"]:::user 
    B["nvq++ Frontend/Compiler"]:::frontend 
    C["Python Bindings/Interfaces"]:::python 
    D["Optimizer/Transformation Engine"]:::optimizer 
    E["CUDA-Q Runtime Engine"]:::runtime 
    F["Backend Platforms<br>(GPU/CPU/QPU)"]:::backend 
    G["Results/Output"]:::result 
    H["Supporting Tools<br>(CMake, Docker, CI/CD, Testing)"]:::supporting

    A -->|"compiles to"| B
    A -->|"via API"| C
    B -->|"generates IR"| D
    D -->|"optimized IR"| E
    C -->|"calls"| E
    E -->|"dispatches"| F
    F -->|"execution results"| G

    H --- B
    H --- D
    H--- E

    %% Click Events
    click B "include/cudaq/Frontend/nvqpp"
    click B "lib/Frontend/nvqpp"
    
    click D "include/cudaq/Optimizer"
    click D "lib/Optimizer"
    click D "cmake/Modules"
    
    click E "runtime/"
    click E "python/runtime"
    
    click F "runtime/cudaq/platform"
    click F "python/runtime/cudaq/platform"
    
    click C "python/cudaq"
    click C "python/extension"

    %% %% Styles
    %% classDef user fill:#d3d3d3,stroke:#333,stroke-width:2px;
    %% classDef frontend fill:#add8e6,stroke:#333,stroke-width:2px;
    %% classDef optimizer fill:#90ee90,stroke:#333,stroke-width:2px;
    %% classDef runtime fill:#ffffcc,stroke:#333,stroke-width:2px;
    %% classDef backend fill:#f08080,stroke:#333,stroke-width:2px;
    %% classDef python fill:#ffb6c1,stroke:#333,stroke-width:2px;
    %% classDef result fill:#f5deb3,stroke:#333,stroke-width:2px;
    %% classDef supporting fill:#e0ffff,stroke:#333,stroke-width:2px;

```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---