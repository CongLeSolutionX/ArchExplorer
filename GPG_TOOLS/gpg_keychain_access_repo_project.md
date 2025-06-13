---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/gpgtools/gpgkeychainaccess
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




# gpg keychain access repo project
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
title: "gpg keychain access repo project"
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
    %% UI Layer
    subgraph "UI Layer"
        direction TB
        MainMenu["MainMenu.xib"]:::ui
        PreferencesUI["Preferences.xib"]:::ui
        ModalSheets["ModalSheets.xib"]:::ui
        PhotoPopover["PhotoPopover.xib"]:::ui
        GKImageView["GKImageView"]:::ui
        GKTableView["GKTableView"]:::ui
        GKMenuButton["GKMenuButton"]:::ui
        GKPasswordIndicator["GKPasswordStrengthIndicator"]:::ui
        GKDateCell["GKDateCell"]:::ui
        GKFieldEditor["GKFieldEditor"]:::ui
        GKVolumeView["GKVolumeCollectionView"]:::ui
        GPGToolbarItem["GPGToolbarItem"]:::ui
    end

    %% Controller Layer
    subgraph "Controller Layer"
        direction TB
        AppDelegate["AppDelegate"]:::controller
        ActionController["ActionController"]:::controller
        KeychainController["KeychainController"]:::controller
        PreferencesController["PreferencesController"]:::controller
        SignaturesController["GKSignaturesController"]:::controller
        SheetController["SheetController"]:::controller
        PhotoPopoverController["GKPhotoPopoverController"]:::controller
    end

    %% Business Logic / Services
    subgraph "Business Logic / Services"
        direction TB
        GKScripting["GKScripting"]:::service
        PasswordIndicator["GKPasswordStrengthIndicator (Wrapper)"]:::service
        ZxcvbnLib["Zxcvbn (DBZxcvbn)"]:::service
        Globals["Globales (Preferences Storage)"]:::service
    end

    %% External Dependencies
    subgraph "External Dependencies"
        direction TB
        MacGPG2["MacGPG2 / libmacgpg"]:::external
        ZxcvbnCore["Zxcvbn Core"]:::external
    end

    %% Data / Persistence
    subgraph "Data / Persistence"
        direction TB
        KeychainAPI["macOS Keychain API"]:::data
        GPGKeyring["GPG Keyring Files"]:::data
    end

    %% Resources & Localization
    subgraph "Resources & Localization"
        direction TB
        Localization["Localization Bundles"]:::resource
        Icons["Icon Assets"]:::resource
        SDef["gka.sdef"]:::resource
        InfoPlist["Info.plist"]:::resource
    end

    %% Build Layer
    subgraph "Build"
        direction TB
        MainEntry["main.m"]:::build
        XcodeProj["GPGKeychain.xcodeproj"]:::build
        Makefile["Makefile"]:::build
    end

    %% Connections
    MainMenu -->|"events"| AppDelegate
    PreferencesUI -->|"events"| PreferencesController
    ModalSheets -->|"events"| SheetController
    PhotoPopover -->|"events"| PhotoPopoverController

    GKImageView -->|display| AppDelegate
    GKTableView -->|display| KeychainController
    GKMenuButton -->|actions| ActionController
    GKPasswordIndicator -->|display| PreferencesController

    AppDelegate -->|"invoke"| ActionController
    ActionController -->|"manage keys"| KeychainController
    PreferencesController -->|"load/save"| Globals
    SignaturesController -->|"invoke"| GKScripting
    PhotoPopoverController -->|"invoke"| GKScripting

    AppDelegate -->|"trigger"| GKScripting
    ActionController -->|"compute score"| PasswordIndicator
    PasswordIndicator -->|"wrapper calls"| ZxcvbnLib

    KeychainController -->|"invoke GPG"| MacGPG2
    GKScripting -->|"script GPG"| MacGPG2

    KeychainController <-->|"read/write"| KeychainAPI
    
    KeychainController -->|"access"| GPGKeyring
    PreferencesController <-->|"load/save"| Globals

     
    Localization -->|"localize"| MainMenu
      
    Localization -->|"localize"| PreferencesUI
    
    Localization -->|"localize"| ModalSheets 

    MainEntry -->|"start app"| AppDelegate
    XcodeProj -->|"build"| MainEntry
    Makefile -->|"build"| MainEntry

    %% Click Events
    click MainMenu "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/Resources/Base.lproj/MainMenu.xib"
    click PreferencesUI "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/Resources/Base.lproj/Preferences.xib"
    click ModalSheets "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/Resources/Base.lproj/ModalSheets.xib"
    click PhotoPopover "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/Resources/PhotoPopover.xib"
    click GKImageView "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/Source/GKImageView.h"
    click GKTableView "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/Source/GKTableView.h"
    click GKMenuButton "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/Source/GKMenuButton.h"
    click GKPasswordIndicator "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/Source/GKPasswordStrengthIndicator.h"
    click GKDateCell "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/Source/GKDateCell.h"
    click GKFieldEditor "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/Source/GKFieldEditor.h"
    click GKVolumeView "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/Source/GKVolumeCollectionView.h"
    click GPGToolbarItem "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/Source/GPGToolbarItem.h"
    click AppDelegate "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/Source/AppDelegate.h"
    click ActionController "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/Source/ActionController.h"
    click KeychainController "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/Source/KeychainController.h"
    click PreferencesController "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/Source/PreferencesController.h"
    click SignaturesController "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/Source/GKSignaturesController.h"
    click SheetController "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/Source/SheetController.h"
    click PhotoPopoverController "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/Source/GKPhotoPopoverController.h"
    click GKScripting "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/Source/GKScripting.h"
    click ZxcvbnLib "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/Dependencies/Zxcvbn/DBZxcvbn.h"
    click Globals "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/Source/Globales.h"
    click MainEntry "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/Source/main.m"
    click XcodeProj "https://github.com/gpgtools/gpgkeychainaccess/blob/dev/GPGKeychain.xcodeproj"
    click Makefile "https://github.com/gpgtools/gpgkeychainaccess/tree/dev/Makefile"

    %% Styles
    classDef ui fill:#87CEFA,stroke:#1E90FF,color:#000
    classDef controller fill:#98FB98,stroke:#228B22,color:#000
    classDef service fill:#FFE4B5,stroke:#FF8C00,color:#000
    classDef external fill:#FFDAB9,stroke:#FF4500,color:#000
    classDef data fill:#E6E6FA,stroke:#9370DB,color:#000
    classDef resource fill:#F5DEB3,stroke:#DEB887,color:#000
    classDef build fill:#D3D3D3,stroke:#A9A9A9,color:#000
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