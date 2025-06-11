---
created: 2025-03-23 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExZDJxZWZzZjF4aXkzNnkxMzlyZ21tdnZ0eDJhcjluNm1lZ2VweHU3ciZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/VX7yEoXAFf8as/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# JamF Connect
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
title: "JamF - JamF Connect"
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
    %% Core Application
    JC["Jamf Connect (macOS Client)"]:::core

    %% External Systems
    JP["Jamf Pro Inventory/Reporting"]:::external

    subgraph "Identity Providers"
        AD["Azure AD"]:::idp
        G["Google"]:::idp
        O["Okta"]:::idp
    end

    subgraph "Cloud Storage Services"
        AW["AWS S3"]:::cloud
        AZ["Azure Files"]:::cloud
        GC["Google Cloud Storage"]:::cloud
    end

    %% Repository Resources
    CP["Configuration Profiles"]:::config
    EA1["Extension Attributes (Built-in)"]:::ext
    EA2["Extension Attributes (Additional)"]:::ext
    JCS["Jamf Connect Scripts"]:::script
    HT["Helper Tools"]:::helper
    UL["Unified Logging"]:::logging
    ZTNA["ZTNA Configuration"]:::ztna

    %% Data flows and relationships
    CP -->|"applyConfig"| JC
    JCS -->|"executeActions"| JC
    ZTNA -->|"configureAccess"| JC

    %% Jamf Connect interacts with Identity Providers
    JC -->|"integrates"| AD
    JC -->|"integrates"| G
    JC -->|"integrates"| O

    %% Extension Attributes reporting to Jamf Pro Inventory
    EA1 -->|"reportInventory"| JP
    EA2 -->|"reportInventory"| JP

    %% Helper Tools assisting logging and cloud integrations
    HT -->|"collectLogs"| UL
    HT ---|"sendLogs"| AW
    HT ---|"sendLogs"| AZ
    HT ---|"sendLogs"| GC

    %% Unified Logging supports debugging and reporting
    UL -->|"provideLogs"| JP

    %% Click Events
    click CP "https://github.com/jamf/jamfconnect/tree/main/configurations"
    click EA1 "https://github.com/jamf/jamfconnect/tree/main/built_in_extension_attributes"
    click EA2 "https://github.com/jamf/jamfconnect/tree/main/additional_extension_attributes"
    click JCS "https://github.com/jamf/jamfconnect/tree/main/scripts"
    click HT "https://github.com/jamf/jamfconnect/tree/main/helper_tools"
    click UL "https://github.com/jamf/jamfconnect/tree/main/unified_logging"
    click ZTNA "https://github.com/jamf/jamfconnect/tree/main/ztna"

    %% Styles
    classDef config fill:#ffdb99,stroke:#b58900,stroke-width:2px;
    classDef ext fill:#cce5ff,stroke:#2a7f62,stroke-width:2px;
    classDef script fill:#d6d6f5,stroke:#4e148c,stroke-width:2px;
    classDef helper fill:#e6ffe6,stroke:#3c763d,stroke-width:2px;
    classDef logging fill:#ffe6e6,stroke:#d43f3a,stroke-width:2px;
    classDef ztna fill:#fce8b2,stroke:#d58512,stroke-width:2px;
    classDef core fill:#fff2cc,stroke:#af7817,stroke-width:2px;
    classDef external fill:#e6ccff,stroke:#6a0dad,stroke-width:2px;
    classDef idp fill:#d0e9c6,stroke:#3c763d,stroke-width:2px;
    classDef cloud fill:#c6e2ff,stroke:#1f78b4,stroke-width:2px

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
