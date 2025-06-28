---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/electron/build-tools
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExMG12d2t5Z3RjdGx2eGpibGZvNzFhajV0NnR6ZDNwMWFjd2FtdHlncSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/lyLRTrqRpW8YU/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# build-tools repo project
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
title: "build-tools repo project"
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
flowchart LR
    %% Layers
    subgraph "User Input"
        U["User: e <command> [args]"]
    end

    subgraph "CLI Frontend"
        direction TB
        E_UNIX["Entry: src/e"]:::internal
        E_WIN["Entry: src/e.bat"]:::internal
        E_WRAP["Wrappers: src/_e/"]:::internal
    end

    subgraph "Command Modules"
        direction TB
        INIT["e-init"]:::internal
        SYNC["e-sync"]:::internal
        BUILD["e-build"]:::internal
        TEST["e-test"]:::internal
        DEBUG["e-debug"]:::internal
        SHOW["e-show"]:::internal
        OPEN["e-open"]:::internal
        PATCHES["e-patches"]:::internal
        PR["e-pr"]:::internal
        GH_AUTH["e-gh-auth"]:::internal
        BACKPORT["e-backport"]:::internal
        CHERRY["e-cherry-pick"]:::internal
        RCV["e-rcv"]:::internal
        AUTO_UPDATE["e-auto-update"]:::internal
        DEPOT_TOOLS_CMD["e-depot-tools"]:::internal
    end

    subgraph "Configuration Manager"
        direction TB
        CONFIG_LOADER["evm-config.js"]:::config
        CONFIG_SCHEMA["evm-config.schema.json"]:::config
        EXAMPLES["example-configs/"]:::config
    end

    subgraph "Utility Layer"
        direction TB
        DL_CORE["download.js"]:::internal
        GIT_UTIL["git.js"]:::internal
        DEPOT_UTIL["depot-tools.js"]:::internal
        RECLIENT_UTIL["reclient.js"]:::internal
        PATHS["paths.js"]:::internal
        LOGGING["logging.js"]:::internal
        DL_AUX["utils/download.js"]:::internal
        GERRIT["gerrit.js"]:::internal
        GH_AUTH_UTIL["github-auth.js"]:::internal
        HEADERS["headers.js"]:::internal
        SDK["sdk.js"]:::internal
        RECLIENT_CHR["setup-reclient-chromium.js"]:::internal
        WHICH["which.js"]:::internal
        AUTO_FIX["maybe-auto-fix.js"]:::internal
        REFRESH_PATH["refresh-path.js"]:::internal
        SISO_UTIL["siso.js"]:::internal
    end

    subgraph "Shell Integration (siso)"
        SISO_DIR["src/siso/"]:::internal
        SISO_CONF["electron.star"]:::internal
    end

    subgraph "External Tools" 
        direction TB
        GIT_EXT["git"]:::external
        DEPOT_EXT["depot-tools (gclient, gn)"]:::external
        NINJA["ninja"]:::external
        PYTHON["Python"]:::external
        RECLIENT_EXT["reclient"]:::external
        DEBUGGER["gdb/lldb"]:::external
    end

    FS["Workspace\n(build root, out/, source tree)"]:::fs

    subgraph "CI & Tooling"
        WORKFLOWS[".github/workflows/"]:::internal
        VITEST["vitest.config.js"]:::internal
        TESTS["tests/"]:::internal
    end

    %% Connections
    U -->|"parse args"| E_UNIX
    U --> E_WIN
    U --> E_WRAP

    E_UNIX -->|"dispatch command"| INIT
    E_UNIX --> SYNC
    E_UNIX --> BUILD
    E_UNIX --> TEST
    E_UNIX --> DEBUG
    E_UNIX --> SHOW
    E_UNIX --> OPEN
    E_UNIX --> PATCHES
    E_UNIX --> PR
    E_UNIX --> GH_AUTH
    E_UNIX --> BACKPORT
    E_UNIX --> CHERRY
    E_UNIX --> RCV
    E_UNIX --> AUTO_UPDATE
    E_UNIX --> DEPOT_TOOLS_CMD

    INIT -->|"load config"| CONFIG_LOADER
    SYNC --> CONFIG_LOADER
    BUILD --> CONFIG_LOADER
    TEST --> CONFIG_LOADER
    DEBUG --> CONFIG_LOADER

    CONFIG_LOADER --> CONFIG_SCHEMA
    CONFIG_LOADER --> EXAMPLES

    INIT -->|"call utility"| DL_CORE
    INIT --> GIT_UTIL
    SYNC --> DEPOT_UTIL
    SYNC --> GIT_UTIL
    BUILD --> NINJA
    BUILD --> RECLIENT_UTIL
    DEBUG --> DEBUGGER
    TEST --> PYTHON

    DL_CORE --> FS
    GIT_UTIL --> GIT_EXT
    DEPOT_UTIL --> DEPOT_EXT
    RECLIENT_UTIL --> RECLIENT_EXT
    SISO_UTIL --> SISO_DIR
    SISO_UTIL --> SISO_CONF

    INIT --> FS
    SYNC --> FS
    BUILD --> FS

    WORKFLOWS -->|runs| INIT
    WORKFLOWS --> TEST
    WORKFLOWS --> SYNC

    VITEST --> TESTS

    %% Click Events
    click E_UNIX "https://github.com/electron/build-tools/tree/main/src/e"
    click E_WIN "https://github.com/electron/build-tools/blob/main/src/e.bat"
    click E_WRAP "https://github.com/electron/build-tools/tree/main/src/_e/"
    click INIT "https://github.com/electron/build-tools/blob/main/src/e-init.js"
    click SYNC "https://github.com/electron/build-tools/blob/main/src/e-sync.js"
    click BUILD "https://github.com/electron/build-tools/blob/main/src/e-build.js"
    click TEST "https://github.com/electron/build-tools/blob/main/src/e-test.js"
    click DEBUG "https://github.com/electron/build-tools/blob/main/src/e-debug.js"
    click SHOW "https://github.com/electron/build-tools/blob/main/src/e-show.js"
    click OPEN "https://github.com/electron/build-tools/blob/main/src/e-open.js"
    click PATCHES "https://github.com/electron/build-tools/blob/main/src/e-patches.js"
    click PR "https://github.com/electron/build-tools/blob/main/src/e-pr.js"
    click GH_AUTH "https://github.com/electron/build-tools/blob/main/src/e-gh-auth.js"
    click BACKPORT "https://github.com/electron/build-tools/blob/main/src/e-backport.js"
    click CHERRY "https://github.com/electron/build-tools/blob/main/src/e-cherry-pick.js"
    click RCV "https://github.com/electron/build-tools/blob/main/src/e-rcv.js"
    click AUTO_UPDATE "https://github.com/electron/build-tools/blob/main/src/e-auto-update.js"
    click DEPOT_TOOLS_CMD "https://github.com/electron/build-tools/blob/main/src/e-depot-tools.js"
    click CONFIG_LOADER "https://github.com/electron/build-tools/blob/main/src/evm-config.js"
    click CONFIG_SCHEMA "https://github.com/electron/build-tools/blob/main/evm-config.schema.json"
    click EXAMPLES "https://github.com/electron/build-tools/tree/main/example-configs/"
    click DL_CORE "https://github.com/electron/build-tools/blob/main/src/download.js"
    click GIT_UTIL "https://github.com/electron/build-tools/blob/main/src/utils/git.js"
    click DEPOT_UTIL "https://github.com/electron/build-tools/blob/main/src/utils/depot-tools.js"
    click RECLIENT_UTIL "https://github.com/electron/build-tools/blob/main/src/utils/reclient.js"
    click PATHS "https://github.com/electron/build-tools/blob/main/src/utils/paths.js"
    click LOGGING "https://github.com/electron/build-tools/blob/main/src/utils/logging.js"
    click DL_AUX "https://github.com/electron/build-tools/blob/main/src/utils/download.js"
    click GERRIT "https://github.com/electron/build-tools/blob/main/src/utils/gerrit.js"
    click GH_AUTH_UTIL "https://github.com/electron/build-tools/blob/main/src/utils/github-auth.js"
    click HEADERS "https://github.com/electron/build-tools/blob/main/src/utils/headers.js"
    click SDK "https://github.com/electron/build-tools/blob/main/src/utils/sdk.js"
    click RECLIENT_CHR "https://github.com/electron/build-tools/blob/main/src/utils/setup-reclient-chromium.js"
    click WHICH "https://github.com/electron/build-tools/blob/main/src/utils/which.js"
    click AUTO_FIX "https://github.com/electron/build-tools/blob/main/src/utils/maybe-auto-fix.js"
    click REFRESH_PATH "https://github.com/electron/build-tools/blob/main/src/utils/refresh-path.js"
    click SISO_UTIL "https://github.com/electron/build-tools/blob/main/src/utils/siso.js"
    click SISO_DIR "https://github.com/electron/build-tools/tree/main/src/siso/"
    click SISO_CONF "https://github.com/electron/build-tools/blob/main/src/siso/config/electron.star"
    click WORKFLOWS "https://github.com/electron/build-tools/tree/main/.github/workflows/"
    click VITEST "https://github.com/electron/build-tools/blob/main/vitest.config.js"
    click TESTS "https://github.com/electron/build-tools/tree/main/tests/"

    %% Styles
    classDef internal fill:#cfe2f3,stroke:#6fa8dc,color:#0b5394
    classDef external fill:#d9ead3,stroke:#93c47d,color:#38761d
    classDef config fill:#fce5cd,stroke:#f9cb9c,color:#b45f06
    classDef fs fill:#e7e6e6,stroke:#9d9d9d,color:#434343


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
