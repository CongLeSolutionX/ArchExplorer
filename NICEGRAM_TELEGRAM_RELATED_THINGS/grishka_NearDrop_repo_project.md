---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/grishka/NearDrop
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


# grishka_NearDrop repo project
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
title: "grishka_NearDrop repo project"
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
    subgraph "Menu Bar App (NearDrop)"
        AppDelegate("AppDelegate"):::mainApp
        MainMenu("MainMenu.xib"):::mainApp
        Assets("Assets.xcassets"):::mainApp
        Localization("Localized Strings"):::mainApp
    end

    subgraph "NearbyShare Module"
        Inbound("InboundNearbyConnection"):::network
        Outbound("OutboundNearbyConnection"):::network
        ConnectionManager("NearbyConnectionManager"):::network
        DataExtensions("Data+Extensions"):::network
        ProtobufHandling("Protobuf Handling"):::network
        ProtobufSource("Protobuf Source"):::network
        GenerateProtobuf("GenerateProtobuf.sh"):::network
    end

    subgraph "Share Extension"
        ShareView("ShareViewController"):::shareExt
        DeviceCell("DeviceListCell"):::shareExt
        ShareViewUI("ShareViewController.xib"):::shareExt
        DeviceCellUI("DeviceListCell.xib"):::shareExt
        ShareAssets("Assets (ShareExtension)"):::shareExt
        SELocalization("Localized Resources"):::shareExt
    end

    subgraph "Protocol & Documentation"
        ProtocolDoc("PROTOCOL.md"):::protocol
    end

    AndroidDevice("External: Android Device"):::external

    %% Connections between components
    ShareView -->|"FileShareRequest"| AppDelegate
    ShareView -->|"InvokeNearbyShare"| ConnectionManager
    AppDelegate -->|"InitiateConnection"| ConnectionManager
    ConnectionManager -->|"Control_Inbound"| Inbound
    ConnectionManager -->|"Control_Outbound"| Outbound
    Inbound -->|"SendsStatus"| AppDelegate
    Outbound -->|"ReceivesData"| AppDelegate
    ConnectionManager -->|"DataExchange"| AndroidDevice
    ConnectionManager -->|"HandlesProtobuf"| ProtobufHandling
    ProtobufHandling -->|"UsesProtocol"| ProtocolDoc

    %% Styles
    classDef mainApp fill:#f9e79f,stroke:#d4ac0d,stroke-width:2px;
    classDef network fill:#aed6f1,stroke:#2471a3,stroke-width:2px;
    classDef shareExt fill:#d5f5e3,stroke:#27ae60,stroke-width:2px;
    classDef external fill:#fadbd8,stroke:#c0392b,stroke-width:2px;
    classDef protocol fill:#f5cba7,stroke:#af601a,stroke-width:2px;

    %% Click Events for Main Application nodes
    click AppDelegate "https://github.com/grishka/neardrop/blob/master/NearDrop/AppDelegate.swift"
    click MainMenu "https://github.com/grishka/neardrop/blob/master/NearDrop/MainMenu.xib"
    click Assets "https://github.com/grishka/neardrop/blob/master/NearDrop/Assets.xcassets"
    click Localization "https://github.com/grishka/neardrop/blob/master/NearDrop/Base.lproj"

    %% Click Events for NearbyShare module nodes
    click Inbound "https://github.com/grishka/neardrop/blob/master/NearbyShare/InboundNearbyConnection.swift"
    click Outbound "https://github.com/grishka/neardrop/blob/master/NearbyShare/OutboundNearbyConnection.swift"
    click ConnectionManager "https://github.com/grishka/neardrop/blob/master/NearbyShare/NearbyConnectionManager.swift"
    click DataExtensions "https://github.com/grishka/neardrop/blob/master/NearbyShare/Data+Extensions.swift"
    click ProtobufHandling "https://github.com/grishka/neardrop/tree/master/NearbyShare/Protobuf"
    click ProtobufSource "https://github.com/grishka/neardrop/tree/master/NearbyShare/ProtobufSource"
    click GenerateProtobuf "https://github.com/grishka/neardrop/blob/master/NearbyShare/GenerateProtobuf.sh"

    %% Click Events for Share Extension nodes
    click ShareView "https://github.com/grishka/neardrop/blob/master/ShareExtension/ShareViewController.swift"
    click DeviceCell "https://github.com/grishka/neardrop/blob/master/ShareExtension/DeviceListCell.swift"
    click ShareViewUI "https://github.com/grishka/neardrop/blob/master/ShareExtension/Base.lproj/ShareViewController.xib"
    click DeviceCellUI "https://github.com/grishka/neardrop/blob/master/ShareExtension/DeviceListCell.xib"
    click ShareAssets "https://github.com/grishka/neardrop/blob/master/ShareExtension/Assets.xcassets"
    click SELocalization "https://github.com/grishka/neardrop/blob/master/ShareExtension/Base.lproj"

    %% Click Event for Protocol & Documentation
    click ProtocolDoc "https://github.com/grishka/neardrop/blob/master/PROTOCOL.md"
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