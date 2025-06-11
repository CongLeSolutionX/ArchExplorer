---
created: 2025-06-11 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/luke-jr/libbase58
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExZDJ0amFhaDRvN2R3cjgxczd2MHJ4MW1oczJ1ZjZsMGkwcDZ0b3pxcyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/trN9ht5RlE3Dcwavg2/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# luke-jr_libbase58 repo project
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
title: "luke-jr_libbase58 repo project"
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
    %% External Integrating Application
    subgraph "Integrating Application"
        App["Integrating App"]:::external
    end

    %% Core Library
    subgraph "libbase58 Core Library"
        Base58C["base58.c"]:::core
        LibHdr["libbase58.h"]:::core
    end

    %% SHA256 Plugin
    subgraph "SHA256 Plugin"
        SHA256["User SHA256 Implementation"]:::plugin
    end

    %% CLI Tool
    subgraph "CLI Tool"
        CLI["clitool.c"]:::tool
    end

    %% Test Suite
    subgraph "Test Suite"
        Tests["tests/"]:::test
    end

    %% Build System and Packaging
    subgraph "Build System & Packaging"
        Autogen["autogen.sh"]:::build
        Configure["configure.ac"]:::build
        Makefile["Makefile.am"]:::build
        Pkg["libbase58.pc.in"]:::build
        Travis[".travis.yml"]:::build
        subgraph "Project Metadata"
            README["README.md"]:::build
            Authors["AUTHORS"]:::build
            Copy["COPYING"]:::build
            Install["INSTALL"]:::build
        end
    end

    %% Relationships
    App -->|"b58tobin(), b58enc(), b58check() calls"| Base58C
    Base58C -.->|"b58_sha256_impl() hook"| SHA256
    CLI -->|"links & invokes libbase58 API"| Base58C
    Tests -->|"./clitool encode/decode"| CLI
    Autogen --> Configure --> Makefile
    Makefile -->|"build & install artifacts"| Base58C
    Makefile -->|"build & install artifacts"| CLI
    Makefile -->|"generate pkg-config"| Pkg
    Travis -->|"runs tests"| Tests

    %% Click Events
    click Base58C "https://github.com/luke-jr/libbase58/blob/master/base58.c"
    click LibHdr "https://github.com/luke-jr/libbase58/blob/master/libbase58.h"
    click CLI "https://github.com/luke-jr/libbase58/blob/master/clitool.c"
    click Tests "https://github.com/luke-jr/libbase58/tree/master/tests/"
    click Autogen "https://github.com/luke-jr/libbase58/blob/master/autogen.sh"
    click Configure "https://github.com/luke-jr/libbase58/blob/master/configure.ac"
    click Makefile "https://github.com/luke-jr/libbase58/blob/master/Makefile.am"
    click Pkg "https://github.com/luke-jr/libbase58/blob/master/libbase58.pc.in"
    click Travis "https://github.com/luke-jr/libbase58/blob/master/.travis.yml"
    click README "https://github.com/luke-jr/libbase58/blob/master/README.md"
    click Authors "https://github.com/luke-jr/libbase58/tree/master/AUTHORS"
    click Copy "https://github.com/luke-jr/libbase58/tree/master/COPYING"
    click Install "https://github.com/luke-jr/libbase58/tree/master/INSTALL"

    %% Styles
    classDef core fill:#cce5ff,stroke:#004085;
    classDef plugin fill:#d4edda,stroke:#155724;
    classDef build fill:#e2e3e5,stroke:#6c757d;
    classDef tool fill:#ffe5b4,stroke:#cc8400;
    classDef test fill:#fff3cd,stroke:#856404;
    classDef external fill:#f5f5f5,stroke:#333;
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