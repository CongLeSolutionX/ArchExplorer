---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/mokeyish/obsidian-code-emitter
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




# code-emitter repo project - mokeyish
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
title: "code-emitter repo project - mokeyish"
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
    %% Obsidian Host Layer
    subgraph "Obsidian Host Layer"
        direction TB
        Manifest["manifest.json"] 
        MainTS["main.tsx"]
        HMR["hmr.ts"]
        Solidify["solidify.ts"]
        HostSetting["setting.ts"]
    end

    %% Plugin Frontend Layer
    subgraph "Plugin Frontend Layer"
        direction TB
        CodeBlock["CodeBlock.tsx"]:::ui
        PlayBtn["Play.tsx"]:::ui
        TermComp["Term.tsx"]:::ui
        SpinComp["Spin.tsx"]:::ui
        SettingTabUI["SettingTab.tsx"]:::ui
        IconComp["Icon.tsx"]:::ui
        UIStyle["style.css"]:::ui
    end

    %% Plugin Core Layer
    subgraph "Plugin Core Layer"
        direction TB
        CoreIndex["backend/index.ts"]:::core
        Store["backend/store.ts"]:::storage
        LangIndex["languages/index.ts"]:::core
    end

    %% Execution Layer: Local Sandbox
    subgraph "Local Sandbox Execution Engines"
        direction TB
        SandboxIndex["sandbox/index.ts"]:::exec
        ProxySandbox["proxySandbox.ts"]:::exec
        CommonSandbox["common.ts"]:::exec
        UtilsSandbox["utils.ts"]:::exec
        Interfaces["interfaces.ts"]:::exec
    end

    %% Execution Layer: Remote Providers
    subgraph "Remote Providers"
        direction TB
        SoloLearn["sololearn.ts"]:::exec
    end

    %% Network Layer
    subgraph "Network Layer"
        direction TB
        URLImport["url_import.ts"]:::core
        ExternalService[(Third-Party HTTP Endpoints)]:::external
    end

    %% Data Store
    subgraph "Obsidian Data Store"
        direction TB
        Store
        HostSetting
    end

    %% Connections
    CodeBlock -->|"runCode(lang, source)"| CoreIndex
    PlayBtn --> CoreIndex
    CoreIndex -->|"load strategy"| LangIndex
    LangIndex -->|"js/ts/python"| SandboxIndex
    SandboxIndex --> ProxySandbox
    SandboxIndex --> CommonSandbox
    CommonSandbox --> Interfaces
    CommonSandbox --> UtilsSandbox
    LangIndex -->|"others"| SoloLearn
    SoloLearn -->|"fetch POST"| ExternalService
    ExternalService -->|"response"| SoloLearn
    ProxySandbox -->|"result"| CoreIndex
    CommonSandbox -->|"result"| CoreIndex
    SoloLearn -->|"result"| CoreIndex
    CoreIndex -->|"stdout/stderr"| TermComp

    %% Click Events
    click Manifest "https://github.com/mokeyish/obsidian-code-emitter/blob/main/manifest.json"
    click MainTS "https://github.com/mokeyish/obsidian-code-emitter/blob/main/src/main.tsx"
    click HMR "https://github.com/mokeyish/obsidian-code-emitter/blob/main/src/hmr.ts"
    click Solidify "https://github.com/mokeyish/obsidian-code-emitter/blob/main/src/solidify.ts"
    click HostSetting "https://github.com/mokeyish/obsidian-code-emitter/blob/main/src/setting.ts"

    click CodeBlock "https://github.com/mokeyish/obsidian-code-emitter/blob/main/src/components/CodeBlock.tsx"
    click PlayBtn "https://github.com/mokeyish/obsidian-code-emitter/blob/main/src/components/Play.tsx"
    click TermComp "https://github.com/mokeyish/obsidian-code-emitter/blob/main/src/components/Term.tsx"
    click SpinComp "https://github.com/mokeyish/obsidian-code-emitter/blob/main/src/components/Spin.tsx"
    click SettingTabUI "https://github.com/mokeyish/obsidian-code-emitter/blob/main/src/components/SettingTab.tsx"
    click IconComp "https://github.com/mokeyish/obsidian-code-emitter/blob/main/src/components/Icon.tsx"
    click UIStyle "https://github.com/mokeyish/obsidian-code-emitter/blob/main/src/style.css"

    click CoreIndex "https://github.com/mokeyish/obsidian-code-emitter/blob/main/src/backend/index.ts"
    click Store "https://github.com/mokeyish/obsidian-code-emitter/blob/main/src/backend/store.ts"

    click LangIndex "https://github.com/mokeyish/obsidian-code-emitter/blob/main/src/backend/languages/index.ts"
    click ProxySandbox "https://github.com/mokeyish/obsidian-code-emitter/blob/main/src/lib/sandbox/proxySandbox.ts"
    click CommonSandbox "https://github.com/mokeyish/obsidian-code-emitter/blob/main/src/lib/sandbox/common.ts"
    click SandboxIndex "https://github.com/mokeyish/obsidian-code-emitter/blob/main/src/lib/sandbox/index.ts"
    click UtilsSandbox "https://github.com/mokeyish/obsidian-code-emitter/blob/main/src/lib/sandbox/utils.ts"
    click Interfaces "https://github.com/mokeyish/obsidian-code-emitter/blob/main/src/lib/sandbox/interfaces.ts"

    click SoloLearn "https://github.com/mokeyish/obsidian-code-emitter/blob/main/src/backend/providers/sololearn.ts"
    click URLImport "https://github.com/mokeyish/obsidian-code-emitter/blob/main/src/lib/url_import.ts"

    %% Styles
    classDef ui fill:#D0E8FF,stroke:#0366D6,color:#000
    classDef core fill:#E8F5D0,stroke:#2E8B57,color:#000
    classDef exec fill:#DFF0D8,stroke:#4CAF50,color:#000
    classDef storage fill:#FFF4D0,stroke:#DAA520,color:#000
    classDef external fill:#F0F0F0,stroke-dasharray: 5 5,stroke:#888,color:#000
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