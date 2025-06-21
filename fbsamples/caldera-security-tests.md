---
created: 2025-06-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/fbsamples/caldera-security-tests
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




# caldera-security-tests repo project
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
title: "caldera-security-tests repo project"
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
    subgraph "Build & Release Pipeline"
        MG["Magefiles"]:::config
        GR[".goreleaser.yml"]:::config
        HC[".hooks/"]:::config
        MG --> GR
        MG --> HC
    end

    subgraph "CI/CD"
        GH["GitHub Actions Workflows"]:::service
    end

    GH -->|"runs build"| MG
    GH -->|"runs tests & lint"| HC
    GH -->|"invokes CLI"| CLI

    subgraph "CLI Application"
        CLI["Go CLI (caldera-security-tests)"]:::compute
        CLI --> RC["Root Cobra Command"]:::compute
        RC --> CP["CLI Entrypoint (caldera.go)"]:::compute
        CP --> TE["testEnv"]:::compute
        CP --> SX1["storedXSSUno"]:::compute
        CP --> SX2["storedXSSDos"]:::compute
        CP --> SX3["storedXSSTres"]:::compute
        CP --> CFG["Config Loader"]:::config
        CP --> LOG["Logging Module"]:::compute
    end

    CFG -->|"reads"| CFGF["config.yaml"]:::config

    TE -->|"provisions"| DO["Docker Env"]:::compute
    DO -->|"runs"| CAL["CALDERA Instance"]:::service

    SX1 -->|"calls API"| CAL
    SX2 -->|"calls API"| CAL
    SX3 -->|"calls API"| CAL

    CAL -->|"response"| CP
    CP -->|"exit code"| GH

    subgraph "Documentation"
        DOC["docs/dev.md"]:::config
        IMG["images/"]:::config
    end

    click CLI "https://github.com/fbsamples/caldera-security-tests/blob/main/main.go"
    click RC "https://github.com/fbsamples/caldera-security-tests/blob/main/cmd/root.go"
    click CP "https://github.com/fbsamples/caldera-security-tests/blob/main/cmd/caldera.go"
    click TE "https://github.com/fbsamples/caldera-security-tests/blob/main/cmd/testEnv.go"
    click SX1 "https://github.com/fbsamples/caldera-security-tests/blob/main/cmd/storedXSSUno.go"
    click SX2 "https://github.com/fbsamples/caldera-security-tests/blob/main/cmd/storedXSSDos.go"
    click SX3 "https://github.com/fbsamples/caldera-security-tests/blob/main/cmd/storedXSSTres.go"
    click CFGF "https://github.com/fbsamples/caldera-security-tests/blob/main/cmd/config/config.yaml"
    click LOG "https://github.com/fbsamples/caldera-security-tests/blob/main/cmd/logging.go"
    click GH "https://github.com/fbsamples/caldera-security-tests/blob/main/.github/workflows/srp.yaml"
    click MG "https://github.com/fbsamples/caldera-security-tests/tree/main/magefiles/"
    click GR "https://github.com/fbsamples/caldera-security-tests/blob/main/.goreleaser.yml"
    click HC "https://github.com/fbsamples/caldera-security-tests/tree/main/.hooks/"
    click DOC "https://github.com/fbsamples/caldera-security-tests/blob/main/docs/dev.md"
    click IMG "https://github.com/fbsamples/caldera-security-tests/tree/main/images/"

    classDef compute fill:#ADD8E6,stroke:#000
    classDef config fill:#90EE90,stroke:#000
    classDef service fill:#FFA500,stroke:#000

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