---
created: 2025-06-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/TheTorProject/stegotorus
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




# stegotorus repo project
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
title: "stegotorus repo project"
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
    subgraph Client_Layer["Client Layer"]
    style Client_Layer fill:#F2F2,stroke:#333,stroke-width:1px, color: #FFFF
        Client("Client Connection"):::client
    end

    subgraph Network_Communication_Layer["Network Communication Layer"]
    style Network_Communication_Layer fill:#22F2,stroke:#333,stroke-width:1px, color: #FFFF
        NetMgmt("Connection Management"):::network
        NetHandle("Network Handling"):::network
        TransProxy("Transparent Proxy"):::network
        Socks("SOCKS Handling"):::network
    end

    subgraph Chopper_Protocol_Layer["Chopper Protocol Layer"]
    style Chopper_Protocol_Layer fill:#BB52,stroke:#333,stroke-width:1px, color: #FFFF
        Chopper("Chopper Protocol"):::core
    end

    subgraph Steg_Modules_Layer["Steg Modules Layer"]
    style Steg_Modules_Layer fill:#FF52,stroke:#333,stroke-width:1px, color: #FFFF
        NoSteg("NoSteg Module"):::steg
        HTTPSteg("HTTP Steg Modules"):::steg
        ApachePayload("Apache Payload Server"):::steg
        PayloadServer("Payload Server"):::steg
        TracePayload("Trace Payload Server"):::steg
    end

    subgraph HTTP_Steg_SubModules["HTTP Steg SubModules"]
    style HTTP_Steg_SubModules fill:#DD52,stroke:#333,stroke-width:1px, color: #FFFF
        HttpGeneral("HTTP Steg General"):::steg
        FileSteg("File Steg"):::steg
        GifSteg("GIF Steg"):::steg
        HtmlSteg("HTML Steg"):::steg
        JpgSteg("JPG Steg"):::steg
        JsSteg("JS Steg"):::steg
        PdfSteg("PDF Steg"):::steg
        PngSteg("PNG Steg"):::steg
        SwfSteg("SWF Steg"):::steg
    end

    subgraph Configuration_and_Deployment["Configuration & Deployment"]
    style Configuration_and_Deployment fill:#F252,stroke:#333,stroke-width:1px, color: #FFFF
        Config("Configuration Files<br/>(conf.d)"):::config
        TestConfig("Test Config<br/>(src/test/test_conf.d)"):::config
    end

    subgraph External_Dependencies["External Dependencies"]
    style External_Dependencies fill:#BFF2,stroke:#333,stroke-width:1px, color: #FFFF
        OpenSSL("OpenSSL"):::external
        LibEvent("libevent"):::external
        LibCurl("libcurl"):::external
        YamlCpp("yaml-cpp"):::external
        Boost("Boost Libraries"):::external
        Zlib("zlib"):::external
    end

    subgraph Build_Tools["Build Tools"]
    style Build_Tools fill:#BAF2,stroke:#333,stroke-width:1px, color: #FFFF
        Autotools("GNU Autotools"):::build
        BuildScripts("Platform Build Scripts"):::build
    end

    %% Data Flow
    Client -->|"connection"| NetMgmt
    NetMgmt -->|"setup"| NetHandle
    NetMgmt -->|"manages"| Socks
    NetHandle -->|"routes"| Chopper
    Chopper -->|"chunks/encrypts"| NoSteg
    Chopper -->|"chunks/encrypts"| HTTPSteg
    HTTPSteg -->|"general encoding"| HttpGeneral
    HTTPSteg -->|"file encoding"| FileSteg
    HTTPSteg -->|"gif encoding"| GifSteg
    HTTPSteg -->|"html encoding"| HtmlSteg
    HTTPSteg -->|"jpg encoding"| JpgSteg
    HTTPSteg -->|"js encoding"| JsSteg
    HTTPSteg -->|"pdf encoding"| PdfSteg
    HTTPSteg -->|"png encoding"| PngSteg
    HTTPSteg -->|"swf encoding"| SwfSteg
    NoSteg -->|"sends data"| NetHandle
    HTTPSteg -->|"sends data"| NetHandle
    ApachePayload -->|"provides cover"| HTTPSteg
    PayloadServer -->|"provides cover"| HTTPSteg
    TracePayload -->|"provides cover"| HTTPSteg
    NetHandle -->|"utilizes"| TransProxy

    %% External Dependencies Integration
    Chopper -->|"encryption"| OpenSSL
    NetMgmt -->|"async events"| LibEvent
    NetHandle -->|"HTTP transport"| LibCurl

    %% Build Tools Relationship
    Autotools -->|"generates"| BuildScripts

    %% Styles
    classDef client fill:#f2f9,stroke:#333,stroke-width:2px;
    classDef network fill:#aff1,stroke:#333,stroke-width:2px;
    classDef core fill:#fbb1,stroke:#333,stroke-width:2px;
    classDef steg fill:#abc6,stroke:#333,stroke-width:2px;
    classDef config fill:#dbf2,stroke:#333,stroke-width:2px;
    classDef external fill:#f7f2,stroke:#333,stroke-width:2px;
    classDef build fill:#d4d2,stroke:#333,stroke-width:2px;

    %% Click Events for Chopper Protocol Components
    click Chopper "https://github.com/thetorproject/stegotorus/blob/master/src/protocol/chop.cc"
    click Chopper "https://github.com/thetorproject/stegotorus/blob/master/src/protocol/chop_blk.cc"
    click Chopper "https://github.com/thetorproject/stegotorus/blob/master/src/protocol/chop_blk.h"
    click Chopper "https://github.com/thetorproject/stegotorus/blob/master/src/protocol/chop_handshaker.h"

    %% Click Events for Steg Modules
    click NoSteg "https://github.com/thetorproject/stegotorus/blob/master/src/steg/nosteg.cc"
    click NoSteg "https://github.com/thetorproject/stegotorus/blob/master/src/steg/nosteg_rr.cc"
    click HTTPSteg "https://github.com/thetorproject/stegotorus/blob/master/src/steg/http.cc"
    click HTTPSteg "https://github.com/thetorproject/stegotorus/blob/master/src/steg/http_apache.cc"
    click FileSteg "https://github.com/thetorproject/stegotorus/blob/master/src/steg/http_steg_mods/file_steg.cc"
    click GifSteg "https://github.com/thetorproject/stegotorus/blob/master/src/steg/http_steg_mods/gifSteg.cc"
    click HtmlSteg "https://github.com/thetorproject/stegotorus/blob/master/src/steg/http_steg_mods/htmlSteg.cc"
    click JpgSteg "https://github.com/thetorproject/stegotorus/blob/master/src/steg/http_steg_mods/jpgSteg.cc"
    click JsSteg "https://github.com/thetorproject/stegotorus/blob/master/src/steg/http_steg_mods/jsSteg.cc"
    click PdfSteg "https://github.com/thetorproject/stegotorus/blob/master/src/steg/http_steg_mods/pdfSteg.cc"
    click PngSteg "https://github.com/thetorproject/stegotorus/blob/master/src/steg/http_steg_mods/pngSteg.cc"
    click SwfSteg "https://github.com/thetorproject/stegotorus/blob/master/src/steg/http_steg_mods/swfSteg.cc"
    click ApachePayload "https://github.com/thetorproject/stegotorus/blob/master/src/steg/apache_payload_server.cc"
    click PayloadServer "https://github.com/thetorproject/stegotorus/blob/master/src/steg/payload_server.cc"
    click TracePayload "https://github.com/thetorproject/stegotorus/blob/master/src/steg/trace_payload_server.cc"

    %% Click Events for Network Components
    click NetMgmt "https://github.com/thetorproject/stegotorus/blob/master/src/connections.cc"
    click NetHandle "https://github.com/thetorproject/stegotorus/blob/master/src/network.cc"
    click TransProxy "https://github.com/thetorproject/stegotorus/blob/master/src/transparent_proxy.cc"
    click Socks "https://github.com/thetorproject/stegotorus/blob/master/src/socks.cc"

    %% Click Events for Configuration
    click Config "https://github.com/thetorproject/stegotorus/blob/master/conf.d"
    click TestConfig "https://github.com/thetorproject/stegotorus/blob/master/src/test/test_conf.d"

    %% Click Events for Build Tools
    click BuildScripts "https://github.com/thetorproject/stegotorus/blob/master/scripts/build-linux.sh"
    click Autotools "https://github.com/thetorproject/stegotorus/blob/master/Makefile.am"

```

-----


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