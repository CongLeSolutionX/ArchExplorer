---
created: 2025-06-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/fbsamples/Canvas-Streaming-Example
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




# Canvas-Streaming-Example repo project
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
title: "Canvas-Streaming-Example repo project"
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
    %% Browser Client Layer
    subgraph "Browser Client"
        direction TB
        Index["index.html"]:::frontend
        CanvasJS["canvasFill.js"]:::frontend
        MediaRecorder["MediaRecorder API"]:::frontend
        WebSocketClient["WebSocket Client"]:::frontend
    end

    %% Proxy Server Layer
    subgraph "Proxy Server"
        direction TB
        ExpressServer["Express Static Server"]:::backend
        StaticAssets["www/"]:::backend
        WSServer["ws WebSocket Server"]:::backend
        FFmpegProcess["FFmpeg Process"]:::backend
        Dependencies["package.json"]:::backend
    end

    %% External Service Layer
    subgraph "Facebook Live API"
        direction TB
        ExternalFacebook["Facebook Live RTMP Endpoint"]:::external
    end

    %% Reference Diagram
    ReferenceDiagram["Reference Architecture Diagram"]:::external

    %% Connections - Browser Client
    CanvasJS -->|"initiates capture"| MediaRecorder
    MediaRecorder -->|"encoded WebM blobs"| WebSocketClient
    WebSocketClient -->|"WebSocket"| WSServer
    Index --> CanvasJS

    %% Connections - Proxy Server
    ExpressServer -->|"serves static"| StaticAssets
    StaticAssets --> Index
    StaticAssets --> CanvasJS
    Dependencies --> ExpressServer
    Dependencies --> WSServer
    WSServer -->|"spawn ffmpeg"| FFmpegProcess
    WSServer -->|"stdin stream"| FFmpegProcess

    %% Streaming to Facebook
    FFmpegProcess -->|"RTMP (FLV/AAC)"| ExternalFacebook

    %% Reference Diagram
    ReferenceDiagram

    %% Click Events
    click Index "https://github.com/fbsamples/canvas-streaming-example/blob/master/www/index.html"
    click CanvasJS "https://github.com/fbsamples/canvas-streaming-example/blob/master/www/js/canvasFill.js"
    click ExpressServer "https://github.com/fbsamples/canvas-streaming-example/blob/master/server.js"
    click WSServer "https://github.com/fbsamples/canvas-streaming-example/blob/master/server.js"
    click FFmpegProcess "https://github.com/fbsamples/canvas-streaming-example/blob/master/server.js"
    click Dependencies "https://github.com/fbsamples/canvas-streaming-example/blob/master/package.json"
    click StaticAssets "https://github.com/fbsamples/canvas-streaming-example/tree/master/www/"
    click ReferenceDiagram "https://github.com/fbsamples/canvas-streaming-example/blob/master/doc/architecture.png"

    %% Styles
    classDef frontend fill:#FFA500,stroke:#333,stroke-width:1px
    classDef backend fill:#FFFF00,stroke:#333,stroke-width:1px
    classDef external fill:#00FF00,stroke:#333,stroke-width:1px

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