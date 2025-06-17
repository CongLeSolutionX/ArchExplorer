---
created: 2025-06-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: 
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




# audience-network repo project
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
title: "audience-network repo project"
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
    %% Left Column: Client Modules
    subgraph "Android Samples"
        direction TB
        subgraph "Java Sample"
            direction TB
            AJavaUI["UI Layer"]:::client
            AJavaSDK["SDK Integration Layer"]:::client
        end
        subgraph "Kotlin Sample"
            direction TB
            AKotlinUI["UI Layer"]:::client
            AKotlinSDK["SDK Integration Layer"]:::client
        end
    end

    subgraph "iOS Samples"
        direction TB
        subgraph "Objective-C Sample"
            direction TB
            iOSObjCUI["UI Layer"]:::client
            iOSObjCSDK["SDK Integration Layer"]:::client
        end
        subgraph "Swift Sample"
            direction TB
            iOSSwiftUI["UI Layer"]:::client
            iOSSwiftSDK["SDK Integration Layer"]:::client
        end
    end

    subgraph "Python Samples"
        direction TB
        PyScript["adnw_examples.py"]:::client
        PyHTTP["HTTP Client Utilities"]:::client
    end

    %% Middle Column: SDK & Libraries
    subgraph "SDK & Libraries"
        direction TB
        AARJava["AudienceNetwork.aar"]:::sdk
        DebugJava["DebugSettings.aar"]:::sdk
        AARKotlin["AudienceNetwork.aar"]:::sdk
        DebugKotlin["DebugSettings.aar"]:::sdk
        CocoaObjC["Podfile (Obj-C)"]:::sdk
        CocoaSwift["Podfile (Swift)"]:::sdk
        PyReq["adnw_requests.py"]:::sdk
        PyResp["adnw_response.py"]:::sdk
        PyUtils["adnw_utils.py"]:::sdk
    end

    %% Right Column: External Services
    subgraph "External Services"
        direction TB
        AdServer["Audience Network Ad Servers"]:::ext
        ReportingAPI["Audience Reporting API"]:::ext
    end

    %% Bottom: CI/CD
    CI["GitHub Actions CI Pipeline"]:::ci

    %% Relationships
    AJavaUI -->|"initializeSDK()"| AJavaSDK
    AJavaSDK -->|"loadAd(adUnitId)"| AARJava
    AARJava -->|"http request"| AdServer
    AdServer -->|"ad response"| AJavaSDK

    AKotlinUI -->|"initializeSDK()"| AKotlinSDK
    AKotlinSDK -->|"loadAd(adUnitId)"| AARKotlin
    AARKotlin -->|"http request"| AdServer
    AdServer -->|"ad response"| AKotlinSDK

    iOSObjCUI -->|"initializeSDK()"| iOSObjCSDK
    iOSObjCSDK -->|"loadAd(adUnitId)"| CocoaObjC
    CocoaObjC -->|"http request"| AdServer
    AdServer -->|"ad response"| iOSObjCSDK

    iOSSwiftUI -->|"initializeSDK()"| iOSSwiftSDK
    iOSSwiftSDK -->|"loadAd(adUnitId)"| CocoaSwift
    CocoaSwift -->|"http request"| AdServer
    AdServer -->|"ad response"| iOSSwiftSDK

    PyScript -->|"fetchReport(params)"| PyReq
    PyReq -->|"http request"| ReportingAPI
    ReportingAPI -->|"data response"| PyResp
    PyResp -->|"parsed data"| PyScript

    CI -->|"build/test"| AJavaUI
    CI -->|"build/test"| AKotlinUI
    CI -->|"build/test"| iOSObjCUI
    CI -->|"build/test"| iOSSwiftUI
    CI -->|"build/test"| PyScript

    %% Click Events
    click AJavaUI "https://github.com/fbsamples/audience-network/tree/main/samples/android/AdUnitsSample"
    click AJavaSDK "https://github.com/fbsamples/audience-network/blob/main/samples/android/AdUnitsSample/src/main/java/com/facebook/samples/AdUnitsSample/AudienceNetworkInitializeHelper.java"
    click AARJava "https://github.com/fbsamples/audience-network/blob/main/samples/android/AdUnitsSample/libs/AudienceNetwork.aar"
    click DebugJava "https://github.com/fbsamples/audience-network/blob/main/samples/android/AdUnitsSample/libs/DebugSettings.aar"

    click AKotlinUI "https://github.com/fbsamples/audience-network/tree/main/samples/android/KotlinAdUnitsSample"
    click AKotlinSDK "https://github.com/fbsamples/audience-network/blob/main/samples/android/KotlinAdUnitsSample/src/main/java/com/facebook/samples/adunitssamplekotlin/AudienceNetworkInitializeHelper.kt"
    click AARKotlin "https://github.com/fbsamples/audience-network/blob/main/samples/android/KotlinAdUnitsSample/libs/AudienceNetwork.aar"
    click DebugKotlin "https://github.com/fbsamples/audience-network/blob/main/samples/android/KotlinAdUnitsSample/libs/DebugSettings.aar"

    click iOSObjCUI "https://github.com/fbsamples/audience-network/tree/main/samples/ios/AdUnitsSample"
    click CocoaObjC "https://github.com/fbsamples/audience-network/tree/main/samples/ios/AdUnitsSample/Podfile"

    click iOSSwiftUI "https://github.com/fbsamples/audience-network/tree/main/samples/ios/FANSample"
    click CocoaSwift "https://github.com/fbsamples/audience-network/tree/main/samples/ios/FANSample/Podfile"

    click PyScript "https://github.com/fbsamples/audience-network/tree/main/samples/python/ReportingAPISamples"
    click PyReq "https://github.com/fbsamples/audience-network/blob/main/samples/python/ReportingAPISamples/adnw_requests.py"
    click PyResp "https://github.com/fbsamples/audience-network/blob/main/samples/python/ReportingAPISamples/adnw_response.py"
    click PyUtils "https://github.com/fbsamples/audience-network/blob/main/samples/python/ReportingAPISamples/adnw_utils.py"

    click CI "https://github.com/fbsamples/audience-network/blob/main/.github/workflows/main.yml"

    %% Styles
    classDef client fill:#D0E8FF,stroke:#1E90FF,stroke-width:1px
    classDef sdk fill:#E0FFE0,stroke:#28A745,stroke-width:1px
    classDef ext fill:#FFE4B5,stroke:#FF8C00,stroke-width:1px
    classDef ci fill:#F0F0F0,stroke:#A9A9A9,stroke-width:1px

```

------

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