---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Papers With Code Data
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
title: "Papers With Code - Data"
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
    External_Data_Sources["External Data Sources"]:::external
    SOTA_Extractor["SOTA Extractor"]:::processing
    Scheduler_for_Daily_Updates["Scheduler for Daily Updates"]:::scheduler
    JSON_Data_Repository["JSON Data Repository"]:::storage
    Data_Consumers["Data Consumers"]:::consumers
    CC_BY_SA_Licensing["CC-BY-SA Licensing"]:::policy

    External_Data_Sources -->|"loadRawData"| SOTA_Extractor
    SOTA_Extractor -->|"transformsData"| JSON_Data_Repository
    Scheduler_for_Daily_Updates -->|"triggersUpdate"| JSON_Data_Repository
    JSON_Data_Repository -->|"downloadData"| Data_Consumers
    JSON_Data_Repository -->|"governedBy"| CC_BY_SA_Licensing

    click External_Data_Sources "README.md"
    click SOTA_Extractor "README.md"
    click Scheduler_for_Daily_Updates "README.md"
    click JSON_Data_Repository "README.md"
    click Data_Consumers "README.md"
    click CC_BY_SA_Licensing "README.md"

    classDef external fill:#bbf3,stroke:#55f,stroke-width:2px
    classDef processing fill:#bfb3,stroke:#5a5,stroke-width:2px
    classDef storage fill:#ff93,stroke:#f80,stroke-width:2px
    classDef scheduler fill:#fbb3,stroke:#f55,stroke-width:2px
    classDef consumers fill:#cdf3,stroke:#9bf,stroke-width:2px
    classDef policy fill:#ddd3,stroke:#333,stroke-width:2px
    
```


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---