---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/xiangechen/chili3d
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExZmdoYWhxb3c2NmR6OGZoMzN5NWxqNjJmbmVxd3U0NDFobjc4ZHdvNyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/xUA7bjPYcgAvwq5CKc/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# xiangechen - chili3d repo project
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


----

```mermaid
---
title: "chili3d repo project"
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
    %% Styles
    classDef ui fill:#3498db,stroke:#2980b9,color:white
    classDef core fill:#2ecc71,stroke:#27ae60,color:white
    classDef geometry fill:#e67e22,stroke:#d35400,color:white
    classDef rendering fill:#9b59b6,stroke:#8e44ad,color:white
    classDef external fill:#95a5a6,stroke:#7f8c8d,color:white
    
    %% Frontend Layer
    subgraph Frontend
        UI_Ribbon["Ribbon Interface"]:::ui
        UI_Property["Property Panels"]:::ui
        UI_Viewport["Viewport"]:::ui
        UI_Project["Project Tree"]:::ui
        UI_Status["Status Bar"]:::ui
        UI_Dialog["Dialog System"]:::ui
    end
    
    %% Core Layer
    subgraph Core
        App["Application Manager"]:::core
        Doc["Document Handler"]:::core
        Cmd["Command System"]:::core
        Select["Selection Manager"]:::core
        Prop["Property System"]:::core
        Event["Event Handler"]:::core
        I18N["i18n System"]:::core
    end
    
    %% Geometry Layer
    subgraph Geometry
        Shape["Shape Operations"]:::geometry
        Geom["Geometric Processing"]:::geometry
        Mesh["Meshing System"]:::geometry
        Factory["Shape Factory"]:::geometry
    end
    
    %% Rendering Layer
    subgraph Rendering
        ThreeView["Three.js View"]:::rendering
        Visual["Visual System"]:::rendering
        Camera["Camera Controller"]:::rendering
        Scene["Scene Manager"]:::rendering
    end
    
    %% External Dependencies
    OpenCascade["OpenCascade WASM"]:::external
    ThreeJS["Three.js"]:::external
    IndexedDB["Browser Storage"]:::external
    FileSystem["File System"]:::external
    
    %% Relationships
    Frontend --> Core
    Core --> Geometry
    Geometry --> Rendering
    Rendering --> Frontend
    
    Geometry --> OpenCascade
    Rendering --> ThreeJS
    Core --> IndexedDB
    Core --> FileSystem
    
    %% Click Events
    click UI_Ribbon "https://github.com/xiangechen/chili3d/tree/main/packages/chili-ui/src/ribbon"
    click UI_Property "https://github.com/xiangechen/chili3d/tree/main/packages/chili-ui/src/property"
    click UI_Viewport "https://github.com/xiangechen/chili3d/tree/main/packages/chili-ui/src/viewport"
    click UI_Project "https://github.com/xiangechen/chili3d/tree/main/packages/chili-ui/src/project"
    click UI_Status "https://github.com/xiangechen/chili3d/tree/main/packages/chili-ui/src/statusbar"
    
    click App "https://github.com/xiangechen/chili3d/blob/main/packages/chili-core/src/application.ts"
    click Doc "https://github.com/xiangechen/chili3d/blob/main/packages/chili-core/src/document.ts"
    click Cmd "https://github.com/xiangechen/chili3d/tree/main/packages/chili-core/src/command"
    click Select "https://github.com/xiangechen/chili3d/blob/main/packages/chili-core/src/selection.ts"
    click Prop "https://github.com/xiangechen/chili3d/blob/main/packages/chili-core/src/property.ts"
    click Event "https://github.com/xiangechen/chili3d/blob/main/packages/chili-core/src/visual/eventHandler.ts"
    click I18N "https://github.com/xiangechen/chili3d/tree/main/packages/chili-core/src/i18n"
    
    click Shape "https://github.com/xiangechen/chili3d/blob/main/packages/chili-wasm/src/shape.ts"
    click Geom "https://github.com/xiangechen/chili3d/blob/main/packages/chili-wasm/src/geometry.ts"
    click Mesh "https://github.com/xiangechen/chili3d/blob/main/packages/chili-wasm/src/mesher.ts"
    click Factory "https://github.com/xiangechen/chili3d/blob/main/packages/chili-wasm/src/factory.ts"
    
    click ThreeView "https://github.com/xiangechen/chili3d/blob/main/packages/chili-three/src/threeView.ts"
    click Visual "https://github.com/xiangechen/chili3d/blob/main/packages/chili-three/src/threeVisual.ts"
    click Camera "https://github.com/xiangechen/chili3d/blob/main/packages/chili-three/src/cameraController.ts"
    click Scene "https://github.com/xiangechen/chili3d/blob/main/packages/chili-three/src/threeRenderBuilder.ts"
    
    click IndexedDB "https://github.com/xiangechen/chili3d/blob/main/packages/chili-storage/src/indexedDBStorage.ts"

```

----


```mermaid
---
title: "❓...CongLeSolutionX....❓"
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

  Closing_quote ~~~ My_Meme
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }

```

---
><b>Licenses</b>:
>
>- <b>MIT License</b>:  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
>- <b>Creative Commons Attribution-ShareAlike 4.0 International</b>: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) [![CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/88x31.png)](https://creativecommons.org/licenses/by-sa/4.0/) - Legal details in [LICENSE-CC-BY-SA-4.0](THE_PAST/LICENSE-CC-BY-SA-4.0) and at [Creative Commons official site](https://creativecommons.org/licenses/by-sa/4.0/).
>
---
