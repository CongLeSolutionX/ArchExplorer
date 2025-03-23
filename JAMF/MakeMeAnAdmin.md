---
created: 2025-03-23 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# MakeMeAnAdmin
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
title: "JamF - Make Me An Admin"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: default
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
    %% User Interaction
    U["User Trigger"]:::user

    %% Utility Script Execution
    S["Privilege Escalation Script (MakeMeAnAdmin.sh)"]:::script

    %% System Operations
    P["OS Privilege Management"]:::os
    L["OS Log Capture (Last 30 Min)"]:::os
    D["Launch Daemon (Scheduled Task)"]:::daemon
    R["Admin Revocation"]:::revocation

    %% Documentation Node
    Doc["Project Documentation (ReadMe.md)"]:::doc

    %% Flow Connections (vertical layout)
    U -->|"executes"| S
    S -->|"grants_temp_admin"| P
    S -->|"configures_daemon"| D
    S -->|"initiates_log_capture"| L
    D -->|"triggers_after_30_min"| R
    R -->|"revokes_admin"| P
    U -->|"references"| Doc

    %% Click Events
    click S "https://github.com/jamf/makemeanadmin/blob/master/MakeMeAnAdmin.sh"
    click Doc "https://github.com/jamf/makemeanadmin/blob/master/ReadMe.md"

    %% Styles
    classDef user fill:#8ecae6,stroke:#219ebc,stroke-width:2px;
    classDef script fill:#ffb703,stroke:#fb8500,stroke-width:2px;
    classDef os fill:#219ebc,stroke:#023047,stroke-width:2px;
    classDef daemon fill:#ff006e,stroke:#d62828,stroke-width:2px;
    classDef revocation fill:#00b4d8,stroke:#0077b6,stroke-width:2px;
    classDef doc fill:#90be6d,stroke:#43aa8b,stroke-width:2px
    
```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---