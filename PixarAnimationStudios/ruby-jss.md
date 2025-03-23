---
created: 2025-03-23 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Ruby JSS
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
title: "Pixar Animation Studios - Ruby JSS"
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
    Client("External Client"):::external
    JamfModule("Jamf Module (Public API)"):::module
    ConnectionLayer("API Connection Layer"):::connection
    subgraph "Classic API Objects"
        Classic("API Resources (Classic)"):::classic
    end
    subgraph "Jamf Pro API Objects"
        JamfPro("API Resources (Jamf Pro)"):::jamfpro
    end
    Config("Configuration & Utility"):::utility
    CLI("CLI/Utility Binaries"):::cli
    Testing("Testing Suite"):::test

    Client -->|"calls"| JamfModule
    JamfModule -->|"routes_request"| ConnectionLayer
    ConnectionLayer -->|"delegates_to_classic"| Classic
    ConnectionLayer -->|"delegates_to_jamfPro"| JamfPro
    JamfModule -->|"uses_configuration"| Config
    ConnectionLayer -->|"uses_configuration"| Config
    CLI -->|"invokes"| JamfModule
    Testing -->|"validates_classic"| Classic
    Testing -->|"validates_jamfPro"| JamfPro
    Testing -->|"validates_connection"| ConnectionLayer
    Testing -->|"validates_configuration"| Config

    classDef external fill:#f9f,stroke:#333,stroke-width:2px;
    classDef module fill:#bbf,stroke:#333,stroke-width:2px;
    classDef connection fill:#cfc,stroke:#333,stroke-width:2px;
    classDef classic fill:#fc9,stroke:#333,stroke-width:2px;
    classDef jamfpro fill:#ff9,stroke:#333,stroke-width:2px;
    classDef utility fill:#cff,stroke:#333,stroke-width:2px;
    classDef cli fill:#dcd,stroke:#333,stroke-width:2px;
    classDef test fill:#fdd,stroke:#333,stroke-width:2px;

    click JamfModule "https://github.com/pixaranimationstudios/ruby-jss/blob/master/lib/jamf.rb"
    click ConnectionLayer "https://github.com/pixaranimationstudios/ruby-jss/tree/master/lib/jamf/api/connection/"
    click Classic "https://github.com/pixaranimationstudios/ruby-jss/tree/master/lib/jamf/api/classic/api_objects/"
    click JamfPro "https://github.com/pixaranimationstudios/ruby-jss/tree/master/lib/jamf/api/jamf_pro/api_objects/"
    click Config "https://github.com/pixaranimationstudios/ruby-jss/blob/master/lib/jamf/configuration.rb"
    click CLI "https://github.com/pixaranimationstudios/ruby-jss/tree/master/bin/"
    click Testing "https://github.com/pixaranimationstudios/ruby-jss/tree/master/test/"

```





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---