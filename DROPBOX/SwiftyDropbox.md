---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/dropbox/SwiftyDropbox
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




# SwiftyDropbox repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes (<ins>sometimes, entertainment purposes</ins>), personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


---

```mermaid
---
title: "SwiftyDropbox repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright © 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'linear'},
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#22BB',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EEF2',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '15px'
    }
  }
}%%
flowchart TB
    %% Code Generation Pipeline
    subgraph "Code Generation Pipeline"
        spec["spec/"]:::codegen
        stone["stone/"]:::codegen
        gbc["generate_base_client.py"]:::codegen
        urc["update_repo_check.sh"]:::codegen
        uvs["update_version.sh"]:::codegen
        gdocs["Format/generate_docs.sh"]:::codegen
    end

    %% Generated Code
    subgraph "Generated Models & Routes"
        genSwift["Swift Generated (Source/SwiftyDropbox/Shared/Generated/)"]:::generated
        genObjC["ObjC Generated (Source/SwiftyDropboxObjC/Shared/Generated/)"]:::generated
    end

    %% Handwritten Core SDK
    subgraph "Core SDK Shared Logic"
        core["Handwritten Core (Source/SwiftyDropbox/Shared/Handwritten/)"]:::core
    end

    %% Platform Adapters
    subgraph "Platform Adapters"
        iosPlat["iOS Adapter (OAuthMobile, LoadingViewController)"]:::platform
        macPlat["macOS Adapter (OAuthDesktop)"]:::platform
    end

    %% Objective-C Layer
    subgraph "Objective-C Layer"
        objcPlat["ObjC Platform Adapters"]:::objc
        objcCore["ObjC Shared Handwritten"]:::objc
    end

    %% Network & OAuth
    subgraph "Network & OAuth Subsystem"
        network["NetworkSessionManager & Config"]:::network
        oauth["OAuthImpl & AuthSession"]:::oauth
    end

    %% Packaging & CI
    subgraph "Packaging & CI"
        pkgSwift["Package.swift"]:::packaging
        pod1["SwiftyDropbox.podspec"]:::packaging
        pod2["SwiftyDropboxObjc.podspec"]:::packaging
        ci[".github/workflows/ci.yml"]:::packaging
        jazzy[".jazzy.json"]:::packaging
        spm[".swiftpm/"]:::packaging
    end

    %% Tests & Samples
    subgraph "Tests & Sample Apps"
        unit["Unit Tests (Source/SwiftyDropboxUnitTests/)"]:::tests
        intg["Integration Tests (TestSwiftyDropbox/IntegrationTests/)"]:::tests
        sampIOS["Sample iOS (TestSwiftyDropbox/TestSwiftyDropbox_iOS/)"]:::tests
        sampMac["Sample macOS (TestSwiftyDropbox/TestSwiftyDropbox_macOS/)"]:::tests
        sampUI["Sample SwiftUI (TestSwiftyDropbox/TestSwiftyDropbox_SwiftUI/)"]:::tests
        sampExt["Sample Action Extension (TestSwiftyDropbox/TestSwiftyDropbox_ActionExtension/)"]:::tests
    end

    %% External API
    DropboxAPI["Dropbox HTTP API v2"]:::external

    %% Connections
    spec --> genSwift
    stone --> genSwift
    gbc --> genSwift
    genSwift --> core
    genObjC --> objcCore
    core --> iosPlat
    core --> macPlat
    iosPlat --> oauth
    macPlat --> oauth
    core --> network
    oauth --> network
    network --> DropboxAPI
    iosPlat --> DropboxAPI
    macPlat --> DropboxAPI
    core --> pkgSwift
    objcCore --> pod2
    pkgSwift --> ci
    pod1 --> ci
    pod2 --> ci
    ci --> jazzy
    ci --> spm
    core --> unit
    network --> intg
    oauth --> intg
    iosPlat --> sampIOS
    macPlat --> sampMac
    iosPlat --> sampUI
    iosPlat --> sampExt

    %% Click Events
    click spec "https://github.com/dropbox/swiftydropbox/tree/master/spec/"
    click stone "https://github.com/dropbox/swiftydropbox/tree/master/stone/"
    click gbc "https://github.com/dropbox/swiftydropbox/blob/master/generate_base_client.py"
    click urc "https://github.com/dropbox/swiftydropbox/blob/master/update_repo_check.sh"
    click uvs "https://github.com/dropbox/swiftydropbox/blob/master/update_version.sh"
    click gdocs "https://github.com/dropbox/swiftydropbox/blob/master/Format/generate_docs.sh"
    click genSwift "https://github.com/dropbox/swiftydropbox/tree/master/Source/SwiftyDropbox/Shared/Generated/"
    click genObjC "https://github.com/dropbox/swiftydropbox/tree/master/Source/SwiftyDropboxObjC/Shared/Generated/"
    click core "https://github.com/dropbox/swiftydropbox/tree/master/Source/SwiftyDropbox/Shared/Handwritten/"
    click network "https://github.com/dropbox/swiftydropbox/tree/master/Source/SwiftyDropbox/Shared/Handwritten/NetworkSession/"
    click oauth "https://github.com/dropbox/swiftydropbox/tree/master/Source/SwiftyDropbox/Shared/Handwritten/OAuth/"
    click iosPlat "https://github.com/dropbox/swiftydropbox/tree/master/Source/SwiftyDropbox/Platform/SwiftyDropbox_iOS/"
    click macPlat "https://github.com/dropbox/swiftydropbox/tree/master/Source/SwiftyDropbox/Platform/SwiftyDropbox_macOS/"
    click objcPlat "https://github.com/dropbox/swiftydropbox/tree/master/Source/SwiftyDropboxObjC/Platform/SwiftyDropbox_iOS/"
    click objcCore "https://github.com/dropbox/swiftydropbox/tree/master/Source/SwiftyDropboxObjC/Shared/Handwritten/"
    click pkgSwift "https://github.com/dropbox/swiftydropbox/blob/master/Package.swift"
    click pod1 "https://github.com/dropbox/swiftydropbox/blob/master/SwiftyDropbox.podspec"
    click pod2 "https://github.com/dropbox/swiftydropbox/blob/master/SwiftyDropboxObjc.podspec"
    click ci "https://github.com/dropbox/swiftydropbox/blob/master/.github/workflows/ci.yml"
    click jazzy "https://github.com/dropbox/swiftydropbox/blob/master/.jazzy.json"
    click spm "https://github.com/dropbox/swiftydropbox/tree/master/.swiftpm/"
    click unit "https://github.com/dropbox/swiftydropbox/tree/master/Source/SwiftyDropboxUnitTests/"
    click intg "https://github.com/dropbox/swiftydropbox/tree/master/TestSwiftyDropbox/IntegrationTests/"
    click sampIOS "https://github.com/dropbox/swiftydropbox/tree/master/TestSwiftyDropbox/TestSwiftyDropbox_iOS/"
    click sampMac "https://github.com/dropbox/swiftydropbox/tree/master/TestSwiftyDropbox/TestSwiftyDropbox_macOS/"
    click sampUI "https://github.com/dropbox/swiftydropbox/tree/master/TestSwiftyDropbox/TestSwiftyDropbox_SwiftUI/"
    click sampExt "https://github.com/dropbox/swiftydropbox/tree/master/TestSwiftyDropbox/TestSwiftyDropbox_ActionExtension/"

    %% Styles
    classDef codegen fill:#cce5ff,stroke:#004085,color:#004085
    classDef generated fill:#b8daff,stroke:#004085,color:#004085
    classDef core fill:#d4edda,stroke:#155724,color:#155724
    classDef platform fill:#ffe5b4,stroke:#c67605,color:#c67605
    classDef objc fill:#ffe5b4,stroke:#c67605,color:#c67605
    classDef network fill:#e2e3e5,stroke:#6c757d,color:#6c757d
    classDef oauth fill:#d6d8db,stroke:#6c757d,color:#6c757d
    classDef packaging fill:#f8f9fa,stroke:#6c757d,color:#6c757d
    classDef tests fill:#f1f1f1,stroke:#6c757d,color:#6c757d
    classDef external fill:#fff3cd,stroke:#856404,color:#856404

```

-----



<!-- 
```mermaid
%% Current Mermaid version
info
```  -->


```mermaid
---
title: "C<char>o&#770;</char>ngL<char>e&#770;</char>SolutionX"
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
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX/CongLeSolutionX' target='_blank'>Click here if you care about the profile of a tech guy seeking for job 🙏🏼</a>"}}

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