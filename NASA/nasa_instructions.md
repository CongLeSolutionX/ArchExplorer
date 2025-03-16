---
created: 2025-03-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# NASA Instructions
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
    User("User"):::user

    subgraph Static_Website_Frontend["Static Website Frontend"]
        FS1("index.html"):::frontend
        FS2("index.css"):::frontend
        FS3("assets directory"):::frontend
    end

    subgraph Documentation_Module["Documentation Module"]
        DM1("docs directory"):::docs
        DM2("onboarding.md"):::docs
        subgraph "Docs Files"
            DM1a("INSTRUCTIONS.md"):::docs
            DM1b("about_section_instructions.md"):::docs
        end
    end

    subgraph Reports_Artifacts["Reports/Artifacts"]
        RA1("reports directory"):::reports
        subgraph "Reports Files"
            RA1a("Sema Code Health Check NASA.pdf"):::reports
            RA1b("Sema Open Source Demonstration DOD IC USG.pdf"):::reports
        end
    end

    subgraph Configuration_and_Metadata["Configuration & Metadata"]
        CM1("meta.json"):::config
        CM2(".gitignore"):::config
    end

    %% Relationships
    User -->|"accesses"| FS1
    FS1 -->|"navigates to"| DM1
    FS1 -->|"links to"| RA1
    DM1 -->|"references"| RA1
    CM1 ---|"supports build"| FS1
    CM2 ---|"supports build"| FS1

    %% Click Events
    click FS1 "https://github.com/nasa/instructions/blob/master/index.html"
    click FS2 "https://github.com/nasa/instructions/blob/master/index.css"
    click FS3 "https://github.com/nasa/instructions/tree/master/assets"
    click DM1 "https://github.com/nasa/instructions/tree/master/docs"
    click DM2 "https://github.com/nasa/instructions/blob/master/onboarding.md"
    click DM1a "https://github.com/nasa/instructions/blob/master/docs/INSTRUCTIONS.md"
    click DM1b "https://github.com/nasa/instructions/blob/master/docs/about_section_instructions.md"
    click RA1 "https://github.com/nasa/instructions/tree/master/reports"
    click RA1a "https://github.com/nasa/instructions/blob/master/reports/Sema Code Health Check NASA.pdf"
    click RA1b "https://github.com/nasa/instructions/blob/master/reports/Sema Open Source Demonstration DOD IC USG.pdf"
    click CM1 "https://github.com/nasa/instructions/blob/master/meta.json"
    click CM2 "https://github.com/nasa/instructions/blob/master/.gitignore"

    %% Styles
    classDef frontend fill:#CFC4,stroke:#333,stroke-width:2px
    classDef docs fill:#FCC4,stroke:#333,stroke-width:2px
    classDef reports fill:#CCF3,stroke:#333,stroke-width:2px
    classDef config fill:#FFC4,stroke:#333,stroke-width:2px
    classDef user fill:#FD75,stroke:#333,stroke-width:2px
    
```





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---