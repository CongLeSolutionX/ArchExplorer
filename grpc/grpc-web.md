---
created: 2025-06-27 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/grpc/grpc-web
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExNWJ2N2N3bHFtaG53MWVtbWpldXgxZnp1N2d4dWdlMWdxdDE1a3UzcyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/j6NaTTkaqWS6RoV3qt/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# grpc-web repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for 👨‍🎓 <ins>educational purposes</ins> 👨‍🎓 (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), 📖 <ins> personal study </ins> 📖, and 🔖 <ins> reference </ins> 🔖.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>



---

```mermaid
---
title: "grpc-web repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
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
flowchart TB
    subgraph "Developer Environment"
        PROTO[".proto Definitions"]:::tools
        PROTO --> PROTOC["protoc"]:::tools
        subgraph "Code Generation Plugins"
            PGJS["protoc-gen-js"]:::plugin
            PGGW["protoc-gen-grpc-web"]:::plugin
        end
        PROTOC --> PGJS
        PROTOC --> PGGW
        PGJS --> STUBS["Generated JS/TS Stubs"]:::tools
        PGGW --> STUBS
    end

    subgraph "Build & Packaging"
        BAZEL["MODULE.bazel"]:::tools
        MAKEFILE["Makefile"]:::tools
        SCRIPTS["scripts/"]:::tools
        NPM["npm Packaging & Test Harness"]:::tools
        WEBPACK["Bundler (Webpack/Gulp)"]:::tools
        STUBS --> WEBPACK
        WEBPACK --> BUNDLE["Client Bundle"]:::tools
        BUNDLE --> RUNTIME["Runtime Library"]:::runtime
    end

    subgraph "Client Application"
        EXAMPLES["Demo Client Apps & Services"]:::examples
        BUNDLE --> EXAMPLES
        EXAMPLES --> BROWSER["Browser App"]:::client
    end

    subgraph "Network Flow"
        BROWSER --> PROXY["Envoy Proxy"]:::infra
        PROXY --> GRPC["Backend gRPC Server"]:::infra
        GRPC --> PROXY
        PROXY --> BROWSER
    end

    subgraph "Docker & Proxy"
        DOCKERCOMPOSE["docker-compose.yml"]:::infra
        DOCKERCOMPOSE --> PROXY
    end

    subgraph "CI / Test Harness"
        DOCKERCOMPOSECI["docker-compose.yml"]:::infra
        INTEROP["Interop Test Suite"]:::examples
        GH[".github/workflows"]:::tools
        KOKORO["kokoro"]:::tools
        DOCKERCOMPOSECI --> INTEROP
        DOCKERCOMPOSECI --> MAKEFILE
        DOCKERCOMPOSECI --> SCRIPTS
        DOCKERCOMPOSECI --> GH
        DOCKERCOMPOSECI --> KOKORO
    end

    classDef tools fill:#e0e0e0,stroke:#000;
    classDef plugin fill:#aed6f1,stroke:#000;
    classDef runtime fill:#a9dfbf,stroke:#000;
    classDef infra fill:#f5b7b1,stroke:#000;
    classDef examples fill:#f4ecf7,stroke:#8e44ad,stroke-dasharray: 5 5;
    classDef client fill:#d5f5e3,stroke:#27ae60;

    click RUNTIME "https://github.com/grpc/grpc-web/tree/master/javascript/net/grpc/web"
    click PGGW "https://github.com/grpc/grpc-web/tree/master/javascript/net/grpc/web/generator"
    click NPM "https://github.com/grpc/grpc-web/tree/master/packages/grpc-web"
    click EXAMPLES "https://github.com/grpc/grpc-web/tree/master/net/grpc/gateway/examples"
    click DOCKERCOMPOSE "https://github.com/grpc/grpc-web/blob/master/docker-compose.yml"
    click PROXY "https://github.com/grpc/grpc-web/tree/master/net/grpc/gateway/docker"
    click PROTO "https://github.com/grpc/grpc-web/tree/master/src/proto"
    click INTEROP "https://github.com/grpc/grpc-web/tree/master/test/interop"
    click MAKEFILE "https://github.com/grpc/grpc-web/tree/master/Makefile"
    click SCRIPTS "https://github.com/grpc/grpc-web/tree/master/scripts/"
    click BAZEL "https://github.com/grpc/grpc-web/blob/master/MODULE.bazel"
    click GH "https://github.com/grpc/grpc-web/tree/master/.github/workflows"
    click KOKORO "https://github.com/grpc/grpc-web/tree/master/kokoro"

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
    
  Closing_quote ~~~ My_Meme
    
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
