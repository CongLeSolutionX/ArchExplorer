---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/rca/GPGMail
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExZHAzM2xua2tid2JucnJwajY3amp4ZTVtdm9qYm9wMXgyY2drMTlxbyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/in7R7WASiy3rq/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----



# GPGMail repo project
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
title: "GPGMail repo project"
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
    %% Host Layer
    subgraph "Host Layer"
        MailApp["Mail.app"]:::host
    end

    %% Plugin Bundle
    subgraph "Plugin Bundle" 
        Bundle["GPGMailBundle (entry point)"]:::plugin
        Hooks["Category Hooks (Compose, Message, Mime, etc.)"]:::plugin
        subgraph "Crypto Core"
            Handler["GPGHandler"]:::plugin
            Task["GPGTask"]:::plugin
            Signature["GPGSignature"]:::plugin
            KeyDownload["GPGKeyDownload"]:::plugin
        end
        subgraph "Preferences & Keychain"
            Prefs["NSPreferences_GPGMail"]:::plugin
            Keychain["MessageKeychainManager+GPGMail"]:::plugin
        end
        subgraph "UI Resources"
            UINibs["UI NIBs & Localization"]:::plugin
        end
    end

    %% Frameworks & Dependencies
    subgraph "Frameworks"
        MacGPGME["MacGPGME.framework"]:::framework
        Sparkle["Sparkle.framework"]:::framework
    end

    %% External Services & Data
    subgraph "External"
        GPGBinary["GPG binary subprocess"]:::process
        Keyserver["External Keyservers"]:::data
        Appcast["appcast.xml"]:::data
    end

    %% Build & Release Tools
    subgraph "Build & Release"
        Build["Makefile & Scripts"]:::utility
        Signing["sign_update.rb / generate_keys.rb"]:::utility
    end

    %% Plugin loading and method hooks
    MailApp -->|"loads .bundle"| Bundle
    Bundle -->|"swizzles methods"| Hooks
    Hooks -->|"intercepts compose/view"| MailApp

    %% Crypto flows
    Bundle -->|"invokes crypto"| Handler
    Handler -->|"wraps API"| MacGPGME
    Handler -->|"spawns subprocess"| Task
    Task -->|"executes"| GPGBinary
    Bundle -->|"downloads keys"| KeyDownload
    KeyDownload -->|"fetches"| Keyserver

    %% Update flow
    Bundle -->|"uses update"| Sparkle
    Sparkle -->|"checks feed"| Appcast
    Sparkle -->|"triggers"| Signing

    %% Preferences integration
    Bundle --> Prefs
    Bundle --> Keychain

    %% UI resources
    Bundle --> UINibs

    %% Build pipeline
    Build --> Bundle
    Build --> MacGPGME
    Build --> Sparkle
    Signing --> Build

    %% Click events
    click Bundle "https://github.com/rca/gpgmail/blob/master/GPGMail/Source/GPGMailBundle.m"
    click Handler "https://github.com/rca/gpgmail/blob/master/GPGMail/Source/GPG.subproj/GPGHandler.m"
    click Task "https://github.com/rca/gpgmail/blob/master/GPGMail/Source/GPG.subproj/GPGTask.m"
    click Signature "https://github.com/rca/gpgmail/blob/master/GPGMail/Source/GPG.subproj/GPGSignature.m"
    click KeyDownload "https://github.com/rca/gpgmail/blob/master/GPGMail/Source/GPGKeyDownload.m"
    click Prefs "https://github.com/rca/gpgmail/blob/master/GPGMail/Source/NSPreferences_GPGMail.m"
    click Keychain "https://github.com/rca/gpgmail/blob/master/GPGMail/Source/MessageKeychainManager+GPGMail.m"
    click Sparkle "https://github.com/rca/gpgmail/blob/master/GPGMail/Frameworks/Sparkle.framework"
    click Keyserver "https://github.com/rca/gpgmail/blob/master/GPGMail/Plists/KeyServers.plist"
    click Build "https://github.com/rca/gpgmail/tree/master/GPGMail/Makefile"

    %% Styles
    classDef host fill:#FFDDAA,stroke:#333,stroke-width:1px
    classDef plugin fill:#DDEEFF,stroke:#333,stroke-width:1px
    classDef framework fill:#EEFFDD,stroke:#333,stroke-width:1px
    classDef process fill:#FFDDDD,stroke:#333,stroke-width:1px
    classDef data fill:#DDFFDD,stroke:#333,stroke-width:1px
    classDef utility fill:#F0E68C,stroke:#333,stroke-width:1px
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
