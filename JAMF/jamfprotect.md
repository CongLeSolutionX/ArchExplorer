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


# Jamfprotect
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
title: "JamF - Jamfprotect"
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
      'textColor': '#F8B229',
      'lineColor': '#F8B229'
    }
  }
}%%
flowchart TD
    %% Nodes
    JamfProtect["Jamf Protect Core Integration"]:::core
    JamfPro["Jamf Pro"]:::core
    ExternalSIEM["SIEM/External Systems"]:::integration

    CustomAnalytics["Custom Analytic Detections (YAML rules)"]:::config
    DeviceControls["Device Controls (Endpoint Configurations)"]:::config
    HelperTools["Helper Tools (Diagnostics & Utilities)"]:::script
    JamfProExt["Jamf Pro Extension Attributes (Custom Reporting)"]:::script
    JamfProtectAPIScripts["Jamf Protect API Scripts (Automated Tasks)"]:::script
    JSONSamples["JSON Samples & Schemas (Data Contracts)"]:::config
    SOARPlaybooks["SOAR Playbooks (Automation & Orchestration)"]:::automation
    Telemetry["Telemetry (Log & Telemetry Collection)"]:::script
    ThirdParty["Third Party Integrations (External Connectors)"]:::integration
    UnifiedLogFilters["Unified Log Filters (Log Standardization)"]:::config

    %% Relationships to Jamf Protect Core Integration
    CustomAnalytics -->|"rules"| JamfProtect
    DeviceControls -->|"configs"| JamfProtect
    JamfProtectAPIScripts -->|"APIcalls"| JamfProtect
    Telemetry -->|"telemetry"| JamfProtect
    HelperTools -->|"support"| JamfProtect

    %% Relationships involving Jamf Pro
    JamfProExt -->|"inventory"| JamfPro
    SOARPlaybooks -->|"remediation"| JamfProtect
    SOARPlaybooks -->|"remediation"| JamfPro

    %% External integration paths
    UnifiedLogFilters -->|"filters"| ExternalSIEM
    ThirdParty -->|"externalAPIs"| ExternalSIEM

    %% Data contract flows
    JSONSamples -->|"standards"| Telemetry
    JSONSamples -->|"standards"| UnifiedLogFilters
    JSONSamples -->|"schemas"| JamfProtectAPIScripts
    HelperTools -->|"testing"| JamfProtectAPIScripts

    %% Styles
    classDef core fill:#FFD700,stroke:#333,stroke-width:2px;
    classDef config fill:#ADD8E6,stroke:#333,stroke-width:1px;
    classDef script fill:#90EE90,stroke:#333,stroke-width:1px;
    classDef automation fill:#FFB6C1,stroke:#333,stroke-width:1px;
    classDef integration fill:#DDA0DD,stroke:#333,stroke-width:1px;

    %% Click Events
    click CustomAnalytics "https://github.com/jamf/jamfprotect/tree/main/custom_analytic_detections"
    click DeviceControls "https://github.com/jamf/jamfprotect/tree/main/device_controls"
    click HelperTools "https://github.com/jamf/jamfprotect/tree/main/helper_tools"
    click JamfProExt "https://github.com/jamf/jamfprotect/tree/main/jamf_pro_extension_attributes"
    click JamfProtectAPIScripts "https://github.com/jamf/jamfprotect/tree/main/jamf_protect_api"
    click JSONSamples "https://github.com/jamf/jamfprotect/tree/main/json_samples_and_schemas"
    click SOARPlaybooks "https://github.com/jamf/jamfprotect/tree/main/soar_playbooks"
    click Telemetry "https://github.com/jamf/jamfprotect/tree/main/telemetry"
    click ThirdParty "https://github.com/jamf/jamfprotect/tree/main/third_party_integrations"
    click UnifiedLogFilters "https://github.com/jamf/jamfprotect/tree/main/unified_log_filters"


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
