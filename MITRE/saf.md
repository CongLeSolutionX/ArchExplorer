---
created: 2025-06-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/mitre/saf
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExMXVjejV3dnVjc2o5MXd3eXBvcDR1cHlzbHQ1Z2R6YjY0ZHpmdjJ6OCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/hL9q5k9dk9l0wGd4e0/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# saf repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>

---


```mermaid
---
title: "saf repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
  look: handDrawn
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'American Typewriter, monospace',
    'logLevel': 'fatal',
    'themeVariables': {
      'primaryColor': '#22BB',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#E2F1',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '20px'
    }
  }
}%%
flowchart TB
    %% User invokes CLI
    User(("User")):::external
    CLI["CLI Frontend"]:::cli
    User -->|"saf <command>"| CLI

    %% Command Handlers Layer
    subgraph "Command Handlers"
    direction TB
        Attest["Attest Service"]:::handlers
        Convert["Converter Plugins"]:::handlers
        Emasser["eMASSer API Client"]:::handlers
        Generate["Generate Service"]:::handlers
        View["View Service"]:::handlers
        Validate["Validate Service"]:::handlers
        Supplement["Supplement Service"]:::handlers
        ScanHarden["Scan & Harden"]:::handlers
    end

    CLI --> Attest
    CLI --> Convert
    CLI --> Emasser
    CLI --> Generate
    CLI --> View
    CLI --> Validate
    CLI --> Supplement
    CLI --> ScanHarden

    %% Core Libraries Layer
    subgraph "Core Libraries"
    direction TB
        OHDF["OHDF Processing"]:::core
        EMASSUtils["eMASS Utilities"]:::core
        Global["Global Utilities"]:::core
        OclifHelpers["Oclif Helpers"]:::core
    end

    Attest --> OHDF
    Convert --> OHDF
    Emasser --> EMASSUtils
    Generate --> Global
    View --> Global
    Validate --> Global
    Supplement --> Global
    ScanHarden --> Global

    %% Data Store
    FileSystem(["Filesystem<br/>(HDF JSON, outputs)"]):::datastore
    OHDF --> FileSystem
    Global --> FileSystem

    %% External Services
    subgraph "External Services"
    direction TB
        AWS["AWS<br/>(Security Hub, Config, S3)"]:::external
        Splunk["Splunk"]:::external
        EMASAPI["eMASS REST API"]:::external
        Heimdall["Heimdall Lite"]:::external
    end

    Convert -->|dash: async| AWS
    Convert -->|dash: async| Splunk
    Emasser -->|dash: HTTP| EMASAPI
    View -->|spawn process| Heimdall

    %% CI/CD & Packaging
    subgraph "CI/CD & Packaging"
        direction TB
        CI["GitHub Actions"]:::pipeline
        Docker["Docker Image Build"]:::pipeline
        NPM["NPM / Homebrew Publish"]:::pipeline
    end

    CI --> Docker
    CI --> NPM

    %% Click Events
    click CLI "https://github.com/mitre/saf/blob/main/src/index.ts"
    click Attest "https://github.com/mitre/saf/tree/main/src/commands/attest"
    click Convert "https://github.com/mitre/saf/tree/main/src/commands/convert"
    click Emasser "https://github.com/mitre/saf/tree/main/src/commands/emasser"
    click Generate "https://github.com/mitre/saf/tree/main/src/commands/generate"
    click View "https://github.com/mitre/saf/tree/main/src/commands/view"
    click Validate "https://github.com/mitre/saf/tree/main/src/commands/validate"
    click Supplement "https://github.com/mitre/saf/tree/main/src/commands/supplement"
    click ScanHarden "https://github.com/mitre/saf/tree/main/src/commands/scan"
    click OHDF "https://github.com/mitre/saf/tree/main/src/utils/ohdf"
    click EMASSUtils "https://github.com/mitre/saf/tree/main/src/utils/emasser"
    click Global "https://github.com/mitre/saf/blob/main/src/utils/global.ts"
    click OclifHelpers "https://github.com/mitre/saf/tree/main/src/utils/oclif"
    click FileSystem "https://github.com/mitre/saf/tree/main/bin/run"
    click CI "https://github.com/mitre/saf/tree/main/.github/workflows"
    click Docker "https://github.com/mitre/saf/tree/main/Dockerfile"
    click NPM "https://github.com/mitre/saf/blob/main/pack-hdf-converters.sh"

    %% Styles
    classDef cli fill:#c58af9,stroke:#a052c1,color:#fff,stroke-width:2px;
    classDef handlers fill:#8ab4f8,stroke:#3778c2,color:#000;
    classDef core fill:#8af89a,stroke:#3c8d40,color:#000;
    classDef datastore fill:#cccccc,stroke:#999,color:#000,stroke-dasharray: 5 5;
    classDef external fill:#f8b48a,stroke:#d2691e,color:#000,stroke-dasharray: 5 5;
    classDef pipeline fill:#f8e38a,stroke:#d2b55b,color:#000,stroke-width:1px;

```

----

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
    
  My_Meme ~~~ Closing_quote
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }



```

---
>**Licenses:**
>
>- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
>- **Creative Commons Attribution-ShareAlike 4.0 International**: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) [![CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/88x31.png)](https://creativecommons.org/licenses/by-sa/4.0/) - Legal details in [LICENSE-CC-BY-SA-4.0](THE_PAST/LICENSE-CC-BY-SA-4.0) and at [Creative Commons official site](https://creativecommons.org/licenses/by-sa/4.0/).
>
---