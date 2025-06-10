---
created: 2025-03-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExcmxhYzBobGw1NDd3YjlvaWcxMXMwbWVveG9vZXd3bzAyeDJudGZvYiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/RN8LABxDcleYvxC4go/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# SIL
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
title: "SIL"
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
    'flowchart': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#2ff9',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TD
    A["Simulink Model / Autocoding Environment"]:::input

    subgraph SIL_Code_Generation_Pipeline["SIL Code Generation Pipeline"]
        B1["MATLAB Packages<br>(+cfsPackage)"]:::module
        B2["TLC Files"]:::module
        B3["Additional TLC Files"]:::module
        B4["MEX TLC Files"]:::module
        B5["Utility Scripts"]:::module
        B6["MEX Functions"]:::module
    end

    BP["Pipeline Output"]:::junction

    subgraph cFS_ECI_Integration_Layer["cFS ECI Integration Layer"]
        C1["Wrapper & Interface Code"]:::integration
        C2["Integration Scripts"]:::integration
    end

    subgraph Testing_and_Validation_Framework["Testing & Validation Framework"]
        D1["ECI Compatibility Tests"]:::test
        D2["Unit & Code Parser Tests"]:::test
    end

    A -->|"generate"| B1
    A --> B2
    A --> B3
    A --> B4
    A --> B5
    A --> B6

    B1 --> BP
    B2 --> BP
    B3 --> BP
    B4 --> BP
    B5 --> BP
    B6 --> BP

    BP -->|"integrate"| C1
    C1 --> C2

    C1 -->|"validation"| D1
    C2 --> D2

    D2 -- "feedback" --> B1

    click A "https://github.com/nasa/sil/tree/master/tests/eci_compatibility/model"
    click B1 "https://github.com/nasa/sil/tree/master/src/+cfsPackage"
    click B2 "https://github.com/nasa/sil/tree/master/src/+cfsPackage/tlc"
    click B3 "https://github.com/nasa/sil/blob/master/src/cfs_ert.tlc"
    click B4 "https://github.com/nasa/sil/tree/master/src/mex/tlc_c"
    click B5 "https://github.com/nasa/sil/tree/master/src/util"
    click B6 "https://github.com/nasa/sil/tree/master/src/mex"
    click C1 "https://github.com/nasa/sil/blob/master/src/cfs_interface.tlc"
    click C2 "https://github.com/nasa/sil/blob/master/src/cfs_selectcallback.m"
    click D1 "https://github.com/nasa/sil/tree/master/tests/eci_compatibility"
    click D2 "https://github.com/nasa/sil/tree/master/tests/unit"

    classDef input fill:#f9c3,stroke:#333,stroke-width:2px
    classDef module fill:#bbf3,stroke:#333,stroke-width:2px
    classDef junction fill:#eee3,stroke:#333,stroke-dasharray: 5,5,stroke-width:2px
    classDef integration fill:#fc93,stroke:#333,stroke-width:2px
    classDef test fill:#cfc3,stroke:#333,stroke-width:2px
    
```





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
