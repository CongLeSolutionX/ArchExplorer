---
created: 2025-03-23 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Homebrew Tap
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
title: "JamF - Homebrew Tap"
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
    U("User: brew_install_jamf-pro"):::user
    U -->|"invokes"| A

    subgraph "Homebrew Tap Repository"
        A("README.md"):::doc
    end

    subgraph "Formula Definitions"
        F1("hermes.rb"):::formula
        F2("jamf-pro.rb"):::formula
        F3("rendr-sdk-groovy.rb"):::formula
        F4("rendr.rb"):::formula
    end

    subgraph "Shared Libraries"
        S1("artifactory.rb"):::shared
        S2("private.rb"):::shared
    end

    subgraph "Release Configurations"
        R1("hermes/release.json"):::config
        R2("jamf-pro/release.json"):::config
        R3("jamf-pro/beta.json"):::config
    end

    subgraph "Metadata Information"
        M1("express.yaml"):::metadata
        M2("rendr-sdk-groovy.yaml"):::metadata
        M3("rendr.yaml"):::metadata
    end

    A -->|"accesses"| F1
    A -->|"accesses"| F2
    A -->|"accesses"| F3
    A -->|"accesses"| F4

    F1 -->|"loads_shared_logic"| S1
    F1 -->|"loads_shared_logic"| S2
    F2 -->|"loads_shared_logic"| S1
    F2 -->|"loads_shared_logic"| S2
    F3 -->|"loads_shared_logic"| S1
    F3 -->|"loads_shared_logic"| S2
    F4 -->|"loads_shared_logic"| S1
    F4 -->|"loads_shared_logic"| S2

    F1 -->|"references"| R1
    F2 -->|"references"| R2
    F2 -->|"references"| R3

    F1 -->|"uses_metadata"| M1
    F3 -->|"uses_metadata"| M2
    F4 -->|"uses_metadata"| M3

    click A "https://github.com/jamf/homebrew-tap/blob/master/README.md"
    click F1 "https://github.com/jamf/homebrew-tap/blob/master/Formula/hermes.rb"
    click F2 "https://github.com/jamf/homebrew-tap/blob/master/Formula/jamf-pro.rb"
    click F3 "https://github.com/jamf/homebrew-tap/blob/master/Formula/rendr-sdk-groovy.rb"
    click F4 "https://github.com/jamf/homebrew-tap/blob/master/Formula/rendr.rb"
    click S1 "https://github.com/jamf/homebrew-tap/blob/master/Formula/lib/artifactory.rb"
    click S2 "https://github.com/jamf/homebrew-tap/blob/master/Formula/lib/private.rb"
    click R1 "https://github.com/jamf/homebrew-tap/blob/master/hermes/release.json"
    click R2 "https://github.com/jamf/homebrew-tap/blob/master/jamf-pro/release.json"
    click R3 "https://github.com/jamf/homebrew-tap/blob/master/jamf-pro/beta.json"
    click M1 "https://github.com/jamf/homebrew-tap/blob/master/metadata/express.yaml"
    click M2 "https://github.com/jamf/homebrew-tap/blob/master/metadata/rendr-sdk-groovy.yaml"
    click M3 "https://github.com/jamf/homebrew-tap/blob/master/metadata/rendr.yaml"

    classDef user fill:#ffefc1,stroke:#333,stroke-width:2px;
    classDef doc fill:#c1dfff,stroke:#333,stroke-width:2px;
    classDef formula fill:#c1ffde,stroke:#333,stroke-width:2px;
    classDef shared fill:#ffc1f7,stroke:#333,stroke-width:2px;
    classDef config fill:#f7c1ff,stroke:#333,stroke-width:2px;
    classDef metadata fill:#d1ffc1,stroke:#333,stroke-width:2px
    
```





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---