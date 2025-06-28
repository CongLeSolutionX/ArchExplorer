---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/GPGTools/Libmacgpg
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExcGkzbzRzZWhmaTJmNHU0M3lmYXNnNmJmYnBkMHhueTJtZDd4MmR3ciZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/SGX16trfMg1fg5Ul3z/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# Libmacgpg repo project
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
title: "Libmacgpg repo project"
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
  %% Client Applications Layer
  subgraph "Client Applications" 
    direction TB
    LeakFinder["LeakFinder"]:::frontend
    SignatureViewApp["SignatureViewApp"]:::frontend
  end

  %% Framework Layer
  subgraph "Libmacgpg.framework" 
    direction TB
    LibmacgpgProj["Libmacgpg.xcodeproj"]:::framework
    PublicAPI["Libmacgpg.h"]:::framework
    subgraph "Process Management"
      direction TB
      GPGTask["GPGTask"]:::framework
      GPGTaskHelper["GPGTaskHelper"]:::framework
      GPGTaskHelperXPC["GPGTaskHelperXPC"]:::framework
    end
    subgraph "Streaming Abstractions"
      direction TB
      GPGStream["GPGStream"]:::framework
      GPGFileStream["GPGFileStream"]:::framework
      GPGMemoryStream["GPGMemoryStream"]:::framework
    end
    subgraph "Packet Parsing"
      direction TB
      GPGPacketParser["GPGPacket*"]:::framework
    end
    subgraph "Controllers & Managers"
      direction TB
      GPGController["GPGController"]:::framework
      GPGKeyManager["GPGKeyManager"]:::framework
      GPGUpdateController["GPGUpdateController"]:::framework
      GPGWatcher["GPGWatcher"]:::framework
    end
    subgraph "Settings & Config"
      direction TB
      GPGArraySetting["GPGArraySetting"]:::framework
      GPGDictSetting["GPGDictSetting"]:::framework
      GPGLinesSetting["GPGLinesSetting"]:::framework
      GPGStdSetting["GPGStdSetting"]:::framework
    end
    GPGException["GPGException"]:::framework
    GPGGlobals["GPGGlobals"]:::framework
    GPGOptions["GPGOptions"]:::framework
    subgraph "Utilities & Localization"
      direction TB
      GPGLocalization["NSBundle+GPGLocalization"]:::framework
      SandboxExt["NSBundle+Sandbox"]:::framework
      NoSigPipe["NSPipe+NoSigPipe"]:::framework
    end
  end

  %% XPC Service Layer
  subgraph "XPC Helper Service" 
    direction TB
    XPCService["org.gpgtools.Libmacgpg.xpc"]:::xpc
  end

  %% GnuPG Process
  subgraph "GnuPG Process" 
    direction TB
    GnuPG["GnuPG CLI"]:::process
  end

  %% External Resources
  Keyserver["Keyserver (HTTP/HTTPS)"]:::external
  FileSystem["Local File System"]:::fs

  %% Unit Test Harness
  UnitTests["UnitTests Harness"]:::test
  SocketTest["GPGSocketCloseTest"]:::test

  %% Connections
  LeakFinder -->|"Objective-C API"| PublicAPI
  SignatureViewApp -->|"Objective-C API"| PublicAPI
  PublicAPI -->|calls| GPGTask
  GPGTaskHelper -->|uses| GPGTask
  GPGTaskHelperXPC -->|XPC interface| XPCService
  GPGStream -->|streams| GPGTaskHelper
  GPGFileStream -->|streams| GPGTaskHelper
  GPGMemoryStream -->|streams| GPGTaskHelper
  GPGPacketParser -->|parses| GPGStream
  GPGController -->|orchestrates| GPGTaskHelper
  GPGController -->|manages| GPGKeyManager
  GPGUpdateController -->|updates| GPGGlobals
  GPGWatcher -->|watches| FileSystem
  GPGArraySetting -->|configures| GPGTaskHelper
  GPGDictSetting -->|configures| GPGTask
  GPGLinesSetting -->|configures| GPGTask
  GPGStdSetting -->|configures| GPGTask
  GPGException -->|handles| GPGTask
  GPGOptions -->|provides| PublicAPI
  GPGLocalization -->|extends| PublicAPI
  SandboxExt -->|extends| XPCService
  NoSigPipe -->|extends| GPGTask

  PublicAPI -->|"XPC pipe"| XPCService
  XPCService -->|"stdin/stdout"| GnuPG
  GnuPG -->|"reads/writes"| FileSystem
  GnuPG -->|"HTTP(S)"| Keyserver
  GnuPG -->|"stdout response"| XPCService
  XPCService -->|"XPC response"| PublicAPI
  PublicAPI -->|"callback"| LeakFinder
  PublicAPI -->|"callback"| SignatureViewApp

  UnitTests -->|direct call| GPGController
  UnitTests -->|direct call| GPGTask
  SocketTest -->|edge-case test| GPGTaskHelper

  %% Click Events
  click LeakFinder "https://github.com/gpgtools/libmacgpg/tree/dev/LeakFinder/"
  click SignatureViewApp "https://github.com/gpgtools/libmacgpg/tree/dev/SignatureViewApp/"
  click LibmacgpgProj "https://github.com/gpgtools/libmacgpg/tree/dev/Libmacgpg.xcodeproj/"
  click PublicAPI "https://github.com/gpgtools/libmacgpg/blob/dev/Source/Libmacgpg.h"
  click XPCService "https://github.com/gpgtools/libmacgpg/tree/dev/Source/org.gpgtools.Libmacgpg.xpc/"
  click GPGTask "https://github.com/gpgtools/libmacgpg/blob/dev/Source/GPGTask.h"
  click GPGTaskHelper "https://github.com/gpgtools/libmacgpg/blob/dev/Source/GPGTaskHelper.h"
  click GPGTaskHelperXPC "https://github.com/gpgtools/libmacgpg/blob/dev/Source/GPGTaskHelperXPC.h"
  click GPGStream "https://github.com/gpgtools/libmacgpg/blob/dev/Source/GPGStream.h"
  click GPGFileStream "https://github.com/gpgtools/libmacgpg/blob/dev/Source/GPGFileStream.h"
  click GPGMemoryStream "https://github.com/gpgtools/libmacgpg/blob/dev/Source/GPGMemoryStream.h"
  click GPGPacketParser "https://github.com/gpgtools/libmacgpg/tree/dev/Source/GPGPacket/"
  click GPGController "https://github.com/gpgtools/libmacgpg/blob/dev/Source/GPGController.h"
  click GPGKeyManager "https://github.com/gpgtools/libmacgpg/blob/dev/Source/GPGKeyManager.h"
  click GPGUpdateController "https://github.com/gpgtools/libmacgpg/blob/dev/Source/GPGUpdateController.h"
  click GPGWatcher "https://github.com/gpgtools/libmacgpg/blob/dev/Source/GPGWatcher.h"
  click GPGArraySetting "https://github.com/gpgtools/libmacgpg/blob/dev/Source/GPGArraySetting.h"
  click GPGDictSetting "https://github.com/gpgtools/libmacgpg/blob/dev/Source/GPGDictSetting.h"
  click GPGLinesSetting "https://github.com/gpgtools/libmacgpg/blob/dev/Source/GPGLinesSetting.h"
  click GPGStdSetting "https://github.com/gpgtools/libmacgpg/blob/dev/Source/GPGStdSetting.h"
  click GPGException "https://github.com/gpgtools/libmacgpg/blob/dev/Source/GPGException.h"
  click GPGGlobals "https://github.com/gpgtools/libmacgpg/blob/dev/Source/GPGGlobals.h"
  click GPGOptions "https://github.com/gpgtools/libmacgpg/blob/dev/Source/GPGOptions.h"
  click GPGLocalization "https://github.com/gpgtools/libmacgpg/blob/dev/Source/NSBundle+GPGLocalization.h"
  click SandboxExt "https://github.com/gpgtools/libmacgpg/blob/dev/Source/NSBundle+Sandbox.h"
  click NoSigPipe "https://github.com/gpgtools/libmacgpg/blob/dev/Source/NSPipe+NoSigPipe.h"
  click UnitTests "https://github.com/gpgtools/libmacgpg/tree/dev/UnitTests/"
  click SocketTest "https://github.com/gpgtools/libmacgpg/blob/dev/NewUnitTests/GPGSocketCloseTest.m"
  click FileSystem "https://github.com/gpgtools/libmacgpg/tree/dev/Resources/"
  click Keyserver "https://github.com/gpgtools/libmacgpg/blob/dev/Resources/Keyservers.plist"

  %% Styles
  classDef frontend fill:#cfc,stroke:#080
  classDef framework fill:#ccf,stroke:#00f
  classDef xpc fill:#fc8,stroke:#f60
  classDef process fill:#ccc,stroke:#666
  classDef external fill:#cff,stroke:#08f,shape:cloud
  classDef fs fill:#ffc,stroke:#f90,shape:cylinder
  classDef test stroke-dasharray: 3 3,fill:#fff,stroke:#f00

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
