---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/GPGTools/GPGServices
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExa2RxaGR1ZDh0MTBubWxxb3FuaW9heHNxY3ltYTU2aWxyOHFnMWh1NiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/1xmhGbhGxJV0suEo6r/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# GPGServices repo project
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


```mermaid
---
title: "GPGServices repo project"
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
flowchart TD
    %% OS Integration Layer
    subgraph "OS Integration Layer"
        direction TB
        SW["ServiceWorker"]:::os
    end

    %% Core Service Layer
    subgraph "Core Service Layer"
        direction TB
        SWD["ServiceWorkerDelegate"]:::core
        SWO["ServiceWrappedOperation"]:::core
        ZO["ZipOperation"]:::core
        PSI["GKPasswordStrengthIndicator"]:::core
    end

    %% UI Layer
    subgraph "UI Layer"
        direction TB
        KC["KeyChooserWindowController"]:::ui
        RC["RecipientWindowController"]:::ui
        IP["InProgressWindowController"]:::ui
        VW["VerificationResultsWindow"]:::ui
        ST["SimpleTextWindow"]:::ui
        WP["WorkerProgressViewItem"]:::ui
    end

    %% External Dependencies
    subgraph "External Dependencies"
        direction TB
        ZX["Zxcvbn"]:::external
        ZP["ZipKit"]:::external
        GP["Libmacgpg/GnuPG"]:::external
    end

    %% Connections
    OS["macOS Services Menu"]:::os -->|"invoke via Services menu"| SW
    SW -->|"delegate events"| SWD
    SWD -->|"create operation"| SWO
    SWO -->|"compress/decompress"| ZO
    SWO -->|"score passphrase"| PSI
    SWO -->|"invoke crypto"| GP
    SWO -->|"report progress"| WP
    WP -->|"update UI"| IP
    SWO -->|"prompt key"| KC
    KC -->|"selected key"| SWO
    SWO -->|"prompt recipients"| RC
    RC -->|"selected recipients"| SWO
    SWO -->|"output text"| ST
    SWO -->|"verification results"| VW
    ZX -.-> PSI
    ZP -.-> ZO

    %% Click Events
    click SW "https://github.com/gpgtools/gpgservices/blob/dev/Source/ServiceWorker.h"
    click SW "https://github.com/gpgtools/gpgservices/blob/dev/Source/ServiceWorker.m"
    click SWD "https://github.com/gpgtools/gpgservices/blob/dev/Source/ServiceWorkerDelegate.h"
    click SWO "https://github.com/gpgtools/gpgservices/blob/dev/Source/ServiceWrappedOperation.h"
    click SWO "https://github.com/gpgtools/gpgservices/blob/dev/Source/ServiceWrappedOperation.m"
    click ZO "https://github.com/gpgtools/gpgservices/blob/dev/Source/ZipOperation.h"
    click ZO "https://github.com/gpgtools/gpgservices/blob/dev/Source/ZipOperation.m"
    click PSI "https://github.com/gpgtools/gpgservices/blob/dev/Source/GKPasswordStrengthIndicator.h"
    click PSI "https://github.com/gpgtools/gpgservices/blob/dev/Source/GKPasswordStrengthIndicator.m"
    click KC "https://github.com/gpgtools/gpgservices/blob/dev/Source/KeyChooserWindowController.h"
    click KC "https://github.com/gpgtools/gpgservices/blob/dev/Source/KeyChooserWindowController.m"
    click KC "https://github.com/gpgtools/gpgservices/blob/dev/Resources/Base.lproj/PrivateKeyChooserWindow.xib"
    click RC "https://github.com/gpgtools/gpgservices/blob/dev/Source/RecipientWindowController.h"
    click RC "https://github.com/gpgtools/gpgservices/blob/dev/Source/RecipientWindowController.m"
    click RC "https://github.com/gpgtools/gpgservices/blob/dev/Resources/Base.lproj/RecipientWindow.xib"
    click IP "https://github.com/gpgtools/gpgservices/blob/dev/Source/InProgressWindowController.h"
    click IP "https://github.com/gpgtools/gpgservices/blob/dev/Source/InProgressWindowController.m"
    click IP "https://github.com/gpgtools/gpgservices/blob/dev/Resources/InProgressWindow.xib"
    click VW "https://github.com/gpgtools/gpgservices/blob/dev/Source/VerificationResultsWindow.h"
    click VW "https://github.com/gpgtools/gpgservices/blob/dev/Source/VerificationResultsWindow.m"
    click VW "https://github.com/gpgtools/gpgservices/blob/dev/Resources/Base.lproj/VerificationResultsWindow.xib"
    click ST "https://github.com/gpgtools/gpgservices/blob/dev/Source/SimpleTextWindow.h"
    click ST "https://github.com/gpgtools/gpgservices/blob/dev/Source/SimpleTextWindow.m"
    click ST "https://github.com/gpgtools/gpgservices/blob/dev/Resources/SimpleTextWindow.xib"
    click WP "https://github.com/gpgtools/gpgservices/blob/dev/Source/WorkerProgressViewItem.h"
    click WP "https://github.com/gpgtools/gpgservices/blob/dev/Source/WorkerProgressViewItem.m"
    click ZX "https://github.com/gpgtools/gpgservices/tree/dev/Dependencies/Zxcvbn"
    click ZP "https://github.com/gpgtools/gpgservices/tree/dev/Dependencies/zipkit"

    %% Styles
    classDef os fill:#cccccc,stroke:#333,stroke-width:1px;
    classDef core fill:#c8e6c9,stroke:#2e7d32,stroke-width:1px;
    classDef ui fill:#bbdefb,stroke:#1565c0,stroke-width:1px;
    classDef external fill:#ffe0b2,stroke:#ef6c00,stroke-width:1px;
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