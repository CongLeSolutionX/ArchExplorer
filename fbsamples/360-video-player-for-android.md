---
created: 2025-06-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/fbsamples/360-video-player-for-android
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




# 360-video-player-for-android repo project
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
title: "360-video-player-for-android repo project"
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
    %% UI Layer
    subgraph "UI Layer"
        SPAct["SphericalPlayerActivity"]:::ui
        Touch["Touch Input"]:::ui
        TV["TextureView"]:::ui
    end

    %% Playback Pipeline
    subgraph "Playback Pipeline"
        SVP["SphericalVideoPlayer"]:::playback
        MP["MediaPlayer"]:::playback
    end

    %% Rendering Pipeline
    subgraph "Rendering Pipeline"
        SSR["SphericalSceneRenderer"]:::render
        Sphere["Sphere Mesh Geometry"]:::render
        SPP["ShaderProgram"]:::render
        GLH["GLHelpers"]:::render
        ERT["EGLRenderTarget"]:::render
    end

    %% Resources
    subgraph "Resources"
        Video[(sample360.mp4)]:::resource
        VS[(video_vertex_shader.glsl)]:::resource
        FS[(video_fragment_shader.glsl)]:::resource
    end

    %% OS / Hardware
    subgraph "OS / Hardware"
        Codec["MediaCodec"]:::system
        GPU["GPU"]:::system
    end

    %% Connections
    Touch -->|"touch events"| SPAct
    SPAct -->|"init(TextureView)"| TV
    SPAct -->|"start playback"| SVP
    SVP -->|"prepare(sample360.mp4)"| MP
    MP -->|"decode"| Codec
    MP -->|"output frames to SurfaceTexture"| TV
    SSR -->|"acquire texture from SurfaceTexture"| TV
    SSR -->|"render frame"| ERT
    ERT -->|"render to"| GPU
    GPU -->|"composite on screen"| TV
    Sphere -->|"geometry data"| SSR
    SPP -->|"apply shaders"| SSR
    VS -->|"vertex shader source"| SPP
    FS -->|"fragment shader source"| SPP
    SSR -->|"use helpers"| GLH

    %% Click Events
    click SPAct "https://github.com/fbsamples/360-video-player-for-android/blob/master/app/src/main/java/com/oculus/sample/SphericalPlayerActivity.java"
    click SVP "https://github.com/fbsamples/360-video-player-for-android/blob/master/app/src/main/java/com/oculus/sample/player/SphericalVideoPlayer.java"
    click SSR "https://github.com/fbsamples/360-video-player-for-android/blob/master/app/src/main/java/com/oculus/sample/gles/SphericalSceneRenderer.java"
    click Sphere "https://github.com/fbsamples/360-video-player-for-android/blob/master/app/src/main/java/com/oculus/sample/gles/Sphere.java"
    click SPP "https://github.com/fbsamples/360-video-player-for-android/blob/master/app/src/main/java/com/oculus/sample/gles/ShaderProgram.java"
    click GLH "https://github.com/fbsamples/360-video-player-for-android/blob/master/app/src/main/java/com/oculus/sample/gles/GLHelpers.java"
    click ERT "https://github.com/fbsamples/360-video-player-for-android/blob/master/app/src/main/java/com/oculus/sample/gles/EGLRenderTarget.java"
    click Video "https://github.com/fbsamples/360-video-player-for-android/blob/master/app/src/main/res/raw/sample360.mp4"
    click VS "https://github.com/fbsamples/360-video-player-for-android/blob/master/app/src/main/res/raw/video_vertex_shader.glsl"
    click FS "https://github.com/fbsamples/360-video-player-for-android/blob/master/app/src/main/res/raw/video_fragment_shader.glsl"
    click TV "https://github.com/fbsamples/360-video-player-for-android/blob/master/app/src/main/res/layout/activity_main.xml"
    click SPAct "https://github.com/fbsamples/360-video-player-for-android/blob/master/app/src/main/AndroidManifest.xml"

    %% Styles
    classDef ui fill:lightblue,stroke:#555,stroke-width:1px
    classDef playback fill:lightgreen,stroke:#555,stroke-width:1px
    classDef render fill:lightcoral,stroke:#555,stroke-width:1px
    classDef resource fill:lightyellow,stroke:#555,stroke-width:1px
    classDef system fill:lightgray,stroke:#555,stroke-width:1px

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