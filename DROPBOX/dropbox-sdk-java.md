---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/dropbox/dropbox-sdk-java
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




# dropbox-sdk-java repo project
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
title: "dropbox-sdk-java repo project"
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
flowchart TD
    subgraph "GitHub Repo"
        subgraph "Gradle Modules"
            stonePlugin["Stone Plugin"]:::plugin
            generatedModel["Generated Model"]:::generated
            coreModule["Core Module"]:::module
            androidModule["Android Module"]:::module
            examplesAndroid["Examples - Android"]:::example
            examplesCW["Examples - Console/Web"]:::example
            examplesJava["Examples - Java"]:::example
        end
        buildSystem["Gradle Build System"]:::build
    end

    stonePlugin -->|"generates code"| generatedModel
    generatedModel -->|"compiled into"| coreModule
    coreModule -->|"uses at runtime"| StandardReq
    coreModule -->|"uses at runtime"| OkHttpReq
    coreModule -->|"uses at runtime"| OkHttp3Req
    coreModule -->|"makes API calls"| dropboxAPI
    androidModule -->|"depends on"| coreModule
    examplesAndroid -->|"depends on"| androidModule
    examplesAndroid -->|"depends on"| coreModule
    examplesCW -->|"depends on"| coreModule
    examplesJava -->|"depends on"| coreModule
    buildSystem -->|"build/test/publish"| stonePlugin
    buildSystem -->|"build/test/publish"| coreModule
    buildSystem -->|"build/test/publish"| androidModule
    buildSystem -->|"build/test/publish"| examplesAndroid
    buildSystem -->|"build/test/publish"| examplesCW
    buildSystem -->|"build/test/publish"| examplesJava

    subgraph "Pluggable HTTP Engines"
        StandardReq["StandardHttpRequestor"]:::extension
        OkHttpReq["OkHttpRequestor"]:::extension
        OkHttp3Req["OkHttp3Requestor"]:::extension
    end

    dropboxAPI["Dropbox API Servers"]:::external

    %% Click Events
    click coreModule "https://github.com/dropbox/dropbox-sdk-java/blob/main/core/build.gradle"
    click generatedModel "https://github.com/dropbox/dropbox-sdk-java/tree/main/core/build/generated_stone_source"
    click androidModule "https://github.com/dropbox/dropbox-sdk-java/blob/main/android/build.gradle"
    click stonePlugin "https://github.com/dropbox/dropbox-sdk-java/blob/main/stone-java-gradle-plugin/build.gradle.kts"
    click examplesAndroid "https://github.com/dropbox/dropbox-sdk-java/blob/main/examples/android/build.gradle"
    click examplesCW "https://github.com/dropbox/dropbox-sdk-java/blob/main/examples/examples/build.gradle"
    click examplesJava "https://github.com/dropbox/dropbox-sdk-java/blob/main/examples/java/build.gradle"
    click StandardReq "https://github.com/dropbox/dropbox-sdk-java/blob/main/core/src/main/java/com/dropbox/core/http/StandardHttpRequestor.java"
    click OkHttpReq "https://github.com/dropbox/dropbox-sdk-java/blob/main/core/src/main/java/com/dropbox/core/http/OkHttpRequestor.java"
    click OkHttp3Req "https://github.com/dropbox/dropbox-sdk-java/blob/main/core/src/main/java/com/dropbox/core/http/OkHttp3Requestor.java"
    click buildSystem "https://github.com/dropbox/dropbox-sdk-java/blob/main/settings.gradle"

    classDef plugin fill:#f9f3,stroke:#333,stroke-width:1px
    classDef generated fill:#ccf3,stroke:#333,stroke-width:1px
    classDef module fill:#cfc3,stroke:#333,stroke-width:1px
    classDef extension fill:#ffc3,stroke:#333,stroke-width:1px
    classDef external fill:#eef3,stroke:#333,stroke-width:1px,stroke-dasharray: 5 5
    classDef build fill:#fcf3,stroke:#333,stroke-width:1px
    classDef example fill:#fee3,stroke:#333,stroke-width:1px
```

----

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