---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/dropbox/dropshots
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




# dropshots repo project
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
title: "dropshots repo project"
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
    %% Build-Time Layer
    subgraph "Build-Time Layer"
        direction TB
        Gradle["Gradle Build System\n(Kotlin DSL)"]:::buildtime
        Plugin["Dropshots Gradle Plugin"]:::buildtime
        subgraph "Plugin Tasks"
            direction TB
            Record["record<Variant>Screenshots\nTask"]:::buildtime
            Pull["pullScreenshots\nTask"]:::buildtime
            Clear["clearScreenshots\nTask"]:::buildtime
        end
    end

    %% Runtime Layer
    subgraph "Runtime Layer"
        direction TB
        Module["Android Module\n(Consumer/Sample App)"]:::runtime
        RuntimeLib["Dropshots Runtime Library"]:::runtime
        Device["Android Device/\nEmulator"]:::runtime
    end

    %% CI/CD & Artifact Repo
    subgraph "CI/CD & Artifact Repo"
        direction TB
        CI["CI Workflows"]:::ci
        Repo["Maven Central\n(Artifact Repository)"]:::ci
    end

    %% Connections
    Gradle -->|"apply plugin"| Plugin
    Plugin -->|"register tasks"| Record
    Plugin -->|"register tasks"| Pull
    Plugin -->|"register tasks"| Clear
    Plugin -->|"applies to modules"| Module
    Record -->|"adb push reference images"| Device
    Gradle -->|"connectedAndroidTest"| Device
    Device -->|"adb pull diff images & results"| Pull
    Module -->|"uses TestRule\nassertSnapshot"| RuntimeLib
    RuntimeLib -->|"captures & compares\nscreenshots"| Device
    CI -->|"publish artifacts"| Repo

    %% Click Events - Build System
    click Gradle "https://github.com/dropbox/dropshots/blob/main/build.gradle.kts"
    click Gradle "https://github.com/dropbox/dropshots/blob/main/settings.gradle.kts"
    click Gradle "https://github.com/dropbox/dropshots/blob/main/gradle/libs.versions.toml"
    click Gradle "https://github.com/dropbox/dropshots/blob/main/gradle.properties"

    %% Click Events - Plugin
    click Plugin "https://github.com/dropbox/dropshots/blob/main/dropshots-gradle-plugin/src/main/kotlin/com/dropbox/dropshots/DropshotsPlugin.kt"
    click Plugin "https://github.com/dropbox/dropshots/blob/main/dropshots-gradle-plugin/src/main/kotlin/com/dropbox/dropshots/DropshotsExtension.kt"
    click Record "https://github.com/dropbox/dropshots/blob/main/dropshots-gradle-plugin/src/main/kotlin/com/dropbox/dropshots/PushFileTask.kt"
    click Pull "https://github.com/dropbox/dropshots/blob/main/dropshots-gradle-plugin/src/main/kotlin/com/dropbox/dropshots/PullScreenshotsTask.kt"
    click Clear "https://github.com/dropbox/dropshots/blob/main/dropshots-gradle-plugin/src/main/kotlin/com/dropbox/dropshots/ClearScreenshotsTask.kt"
    click Plugin "https://github.com/dropbox/dropshots/blob/main/dropshots-gradle-plugin/build.gradle.kts"
    click Plugin "https://github.com/dropbox/dropshots/blob/main/dropshots-gradle-plugin/src/test/kotlin/com/dropbox/dropshots/DropshotsPluginTest.kt"

    %% Click Events - Runtime Library
    click RuntimeLib "https://github.com/dropbox/dropshots/blob/main/dropshots/src/main/java/com/dropbox/dropshots/Dropshots.kt"
    click RuntimeLib "https://github.com/dropbox/dropshots/blob/main/dropshots/src/main/java/com/dropbox/dropshots/BitmapImage.kt"
    click RuntimeLib "https://github.com/dropbox/dropshots/blob/main/dropshots/src/main/java/com/dropbox/dropshots/ResultValidator.kt"
    click RuntimeLib "https://github.com/dropbox/dropshots/blob/main/dropshots/src/androidTest/kotlin/com/dropbox/dropshots/DropshotsTest.kt"
    click RuntimeLib "https://github.com/dropbox/dropshots/blob/main/dropshots/src/androidTest/kotlin/com/dropbox/dropshots/BitmapImageTest.kt"
    click RuntimeLib "https://github.com/dropbox/dropshots/blob/main/dropshots/src/androidTest/kotlin/com/dropbox/dropshots/CustomImageComparatorTest.kt"
    click RuntimeLib "https://github.com/dropbox/dropshots/blob/main/dropshots/src/androidTest/kotlin/com/dropbox/dropshots/FakeResultValidator.kt"
    click RuntimeLib "https://github.com/dropbox/dropshots/blob/main/dropshots/src/androidTest/kotlin/com/dropbox/dropshots/ScreenshotTestFragment.kt"
    click RuntimeLib "https://github.com/dropbox/dropshots/blob/main/dropshots/src/debug/kotlin/com/dropbox/dropshots/TestActivity.kt"
    click RuntimeLib "https://github.com/dropbox/dropshots/tree/main/dropshots/src/androidTest/assets/static"

    %% Click Events - Sample App Module
    click Module "https://github.com/dropbox/dropshots/blob/main/sample/app/build.gradle.kts"
    click Module "https://github.com/dropbox/dropshots/blob/main/sample/app/src/main/java/com/dropbox/dropshots/sample/MainActivity.kt"
    click Module "https://github.com/dropbox/dropshots/blob/main/sample/app/src/androidTest/java/com/dropbox/dropshots/sample/ExampleInstrumentedTest.kt"
    click Module "https://github.com/dropbox/dropshots/tree/main/sample/app/src/androidTest/screenshots"
    click Module "https://github.com/dropbox/dropshots/tree/main/sample/app/src/androidTest/screenshots/views/colors"

    %% Click Events - CI/CD
    click CI "https://github.com/dropbox/dropshots/blob/main/.github/workflows/publish.yml"
    click CI "https://github.com/dropbox/dropshots/blob/main/.github/dependabot.yaml"
    click CI "https://github.com/dropbox/dropshots/blob/main/.github/scripts/checksum.sh"

    %% Styles
    classDef buildtime fill:#bbdefb,stroke:#0d47a1,color:#0d47a1
    classDef runtime fill:#c8e6c9,stroke:#1b5e20,color:#1b5e20
    classDef ci fill:#eceff1,stroke:#37474f,color:#37474f
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