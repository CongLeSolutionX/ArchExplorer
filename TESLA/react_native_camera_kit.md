---
created: 2025-03-17 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExM2Y4MGZybmJhcTNnMXJzOXdpdDM5ejk0dWtvcWR4dzdjejR0bTQ5dyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/K5DhLPHVVRrNW7nhfy/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----




# React Native Camera Kit
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## A Diagrammatic Guide 


```mermaid
---
title: "TESLA - React Native Camera Kit"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: default
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'graph': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'textColor': '#F8B229',
      'lineColor': '#F8B229'
    }
  }
}%%
graph TD
    %% React Native Layer
    subgraph "React Native Layer"
        RN["React Native Camera Component"]:::react
        SrcLib["Core Library (src)"]:::react
    end

    %% Native Bridge Layer
    subgraph "Native Bridge Layer"
        Bridge1["CameraNativeComponent"]:::bridge
        Bridge2["NativeCameraKitModule"]:::bridge
    end

    %% Native Modules
    subgraph "Native Modules"
        subgraph "Android Native Module"
            AndroidCore["Android Core Implementation\n(CKCamera.kt, CKCameraManager.kt)"]:::android
            Barcode["Barcode/QR Scanning\n(BarcodeFrame.kt)"]:::android
            AndroidEvents["Android Event Handling\n(PictureTakenEvent.kt, ReadCodeEvent.kt, ZoomEvent.kt)"]:::android
            AndroidPaper["Android Paper Components"]:::android
        end
        subgraph "iOS Native Module"
            iOSMain["iOS Implementation\n(CameraManager.swift, CKCameraViewComponentView)"]:::ios
        end
    end

    %% Example / Demo Application
    subgraph "Example / Demo Application"
        ExampleApp["Example App"]:::example
    end

    %% Testing & Configuration
    subgraph "Testing & Configuration"
        Tests["Unit Tests"]:::test
        Config["CI/CD & Build & Config Files"]:::config
    end

    %% Relationships and Data Flow
    RN -->|"executes"| SrcLib
    RN -->|"calls"| Bridge1
    RN -->|"calls"| Bridge2
    Bridge1 -->|"invokes"| AndroidCore
    Bridge1 -->|"invokes"| iOSMain
    Bridge2 -->|"invokes"| AndroidCore
    Bridge2 -->|"invokes"| iOSMain
    AndroidEvents -->|"sendsEvent"| Bridge1
    iOSMain -->|"sendsEvent"| Bridge2
    Bridge1 -->|"propagatesEvent"| RN
    Bridge2 -->|"propagatesEvent"| RN
    ExampleApp -->|"uses"| RN
    Tests -->|"validates"| SrcLib
    Config -->|"configures"| SrcLib

    %% Click Events
    click SrcLib "https://github.com/teslamotors/react-native-camera-kit/blob/master/src/Camera.tsx"
    click ExampleApp "https://github.com/teslamotors/react-native-camera-kit/blob/master/example/src/App.tsx"
    click Bridge1 "https://github.com/teslamotors/react-native-camera-kit/blob/master/src/specs/CameraNativeComponent.ts"
    click Bridge2 "https://github.com/teslamotors/react-native-camera-kit/blob/master/src/specs/NativeCameraKitModule.ts"
    click AndroidCore "https://github.com/teslamotors/react-native-camera-kit/tree/master/android/src/main/java/com/rncamerakit"
    click Barcode "https://github.com/teslamotors/react-native-camera-kit/blob/master/android/src/main/java/com/rncamerakit/barcode/BarcodeFrame.kt"
    click AndroidEvents "https://github.com/teslamotors/react-native-camera-kit/tree/master/android/src/main/java/com/rncamerakit/events"
    click AndroidPaper "https://github.com/teslamotors/react-native-camera-kit/tree/master/android/src/paper/java"
    click iOSMain "https://github.com/teslamotors/react-native-camera-kit/tree/master/ios/ReactNativeCameraKit"
    click Tests "https://github.com/teslamotors/react-native-camera-kit/blob/master/src/__tests__/index.test.tsx"
    click Config "https://github.com/teslamotors/react-native-camera-kit/blob/master/babel.config.js"

    %% Styles
    classDef react fill:#ADD8E6,stroke:#000,stroke-width:1px;
    classDef bridge fill:#FFD700,stroke:#000,stroke-width:1px;
    classDef android fill:#90EE90,stroke:#000,stroke-width:1px;
    classDef ios fill:#FFB6C1,stroke:#000,stroke-width:1px;
    classDef example fill:#D3D3D3,stroke:#000,stroke-width:1px;
    classDef test fill:#FFA07A,stroke:#000,stroke-width:1px;
    classDef config fill:#E6E6FA,stroke:#000,stroke-width:1px
    
```



---

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

  Closing_quote ~~~ My_Meme
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }

```

---
> **Licenses:**
>
> - **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
> - **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).
> 
---


