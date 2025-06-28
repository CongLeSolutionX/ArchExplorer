---
created: 2025-06-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/nikdanilov/whisper-obsidian-plugin
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExeGQ2bmFidHMxeGJ5cmY2Zjhxcmkzcmh0MnBuOHBjcDBpMm12aTYwZCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/eg4t0mu8Bsp4N8sjrC/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# whisper obsidian-plugins repo project - nikdanilov
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
title: "whisper obsidian-plugin repo project - nikdanilov"
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
    subgraph UI_Layer["UI Layer"]
    style UI_Layer fill:#F2F2,stroke:#333,stroke-width:1px, color: #FFFF
        MAIN["Plugin Entry Point<br/>(main.ts)"]:::ui
        Controls["Controls<br/>(src/Controls.ts)"]:::ui
        SettingsManager["SettingsManager<br/>(src/SettingsManager.ts)"]:::ui
        WhisperSettingsTab["WhisperSettingsTab<br/>(src/WhisperSettingsTab.ts)"]:::ui
        StatusBar["StatusBar<br/>(src/StatusBar.ts)"]:::ui
        Timer["Timer<br/>(src/Timer.ts)"]:::ui
    end

    subgraph Audio_Capture_Layer["Audio Capture Layer"]
    style Audio_Capture_Layer fill:#2BF2,stroke:#333,stroke-width:1px, color: #FFFF
        AudioRecorder["AudioRecorder<br/> (src/AudioRecorder.ts)"]:::audio
    end

    subgraph API_Integration_Layer["API Integration Layer"]
    style API_Integration_Layer fill:#BBF2,stroke:#333,stroke-width:1px, color: #FFFF
        AudioHandler["AudioHandler<br/>(src/AudioHandler.ts)"]:::api
    end

    subgraph Persistence_Layer["Persistence Layer"]
    style Persistence_Layer fill:#BFF2,stroke:#333,stroke-width:1px, color: #FFFF
        Vault["Obsidian Vault Adapter"]:::persistence
        Utils["Utils<br/>(src/utils.ts)"]:::common
    end

    External["OpenAI Whisper API"]:::external

    subgraph Build_and_Config["Build & Config"]
    style Build_and_Config fill:#EEB2,stroke:#333,stroke-width:1px, color: #FFFF
        MANIFEST["manifest.json"]:::config
        ESG["esbuild.config.mjs"]:::config
        PKG["package.json & tsconfig.json"]:::config
        VERIFY["verify-and-update.mjs"]:::config
        VERSIONS["versions.json"]:::config
        STYLES["styles.css"]:::config
    end

    %% Connections
    MAIN --> Controls
    MAIN --> SettingsManager
    MAIN --> WhisperSettingsTab
    MAIN --> AudioRecorder
    MAIN --> AudioHandler
    MAIN --> Utils

    Controls -->|"startRecording()"| AudioRecorder
    Controls -->|invoke command| MAIN

    AudioRecorder -->|audio blob| AudioHandler
    AudioRecorder -->|update status| StatusBar
    AudioRecorder -->|update timer| Timer

    AudioHandler -->|POST audio blob| External
    External -->|transcription JSON| AudioHandler
    AudioHandler -->|save artifacts| Vault

    SettingsManager -->|"load/save settings"| MAIN
    WhisperSettingsTab -->|render settings UI| SettingsManager

    Utils -->|shared funcs| AudioRecorder
    Utils -->|shared funcs| AudioHandler
    Utils -->|shared funcs| Vault

    %% Click Events
    click MAIN "https://github.com/nikdanilov/whisper-obsidian-plugin/blob/main/main.ts"
    click Controls "https://github.com/nikdanilov/whisper-obsidian-plugin/blob/main/src/Controls.ts"
    click SettingsManager "https://github.com/nikdanilov/whisper-obsidian-plugin/blob/main/src/SettingsManager.ts"
    click WhisperSettingsTab "https://github.com/nikdanilov/whisper-obsidian-plugin/blob/main/src/WhisperSettingsTab.ts"
    click StatusBar "https://github.com/nikdanilov/whisper-obsidian-plugin/blob/main/src/StatusBar.ts"
    click Timer "https://github.com/nikdanilov/whisper-obsidian-plugin/blob/main/src/Timer.ts"
    click AudioRecorder "https://github.com/nikdanilov/whisper-obsidian-plugin/blob/main/src/AudioRecorder.ts"
    click AudioHandler "https://github.com/nikdanilov/whisper-obsidian-plugin/blob/main/src/AudioHandler.ts"
    click Utils "https://github.com/nikdanilov/whisper-obsidian-plugin/blob/main/src/utils.ts"
    click MANIFEST "https://github.com/nikdanilov/whisper-obsidian-plugin/blob/main/manifest.json"
    click ESG "https://github.com/nikdanilov/whisper-obsidian-plugin/blob/main/esbuild.config.mjs"
    click PKG "https://github.com/nikdanilov/whisper-obsidian-plugin/blob/main/package.json"
    click VERIFY "https://github.com/nikdanilov/whisper-obsidian-plugin/blob/main/verify-and-update.mjs"
    click VERSIONS "https://github.com/nikdanilov/whisper-obsidian-plugin/blob/main/versions.json"
    click STYLES "https://github.com/nikdanilov/whisper-obsidian-plugin/blob/main/styles.css"

    %% Styles
    classDef ui fill:#DEF2,stroke:#016392
    classDef audio fill:#DFF1,stroke:#4F8A10
    classDef api fill:#F2A2,stroke:#B45F06
    classDef persistence fill:#FDD2,stroke:#D8000C
    classDef common fill:#EEF3,stroke:#5A4EFB
    classDef external fill:#EEE5,stroke:#333333,stroke-dasharray:5 5
    classDef config fill:#FFF3,stroke:#999999,stroke-dasharray:2 2
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
