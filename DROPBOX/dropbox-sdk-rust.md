---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/dropbox/dropbox-sdk-rust
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




# dropbox-sdk-rust repo project
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
title: "dropbox-sdk-rust repo project"
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
    %% Build-Time Code Generation Pipeline
    subgraph "Build-Time Pipeline"
        direction TB
        dropbox_api_spec["dropbox-api-spec/*"]:::codegen
        stone["stone/*"]:::codegen
        gen_py["generate.py"]:::codegen
        update_spec_py["update_spec.py"]:::codegen
        update_manifest_py["update_manifest.py"]:::codegen
        subgraph "Generator Scripts & Templates"
            direction TB
            gen_rust_py["generator/rust.py"]:::codegen
            gen_rust_stone_py["generator/rust.stoneg.py"]:::codegen
            gen_test_stone_py["generator/test.stoneg.py"]:::codegen
        end
    end

    %% Generated Code Output
    subgraph "Generated Code" 
        direction TB
        sync_routes["src/generated/sync_routes/*"]:::generated
        async_routes["src/generated/async_routes/*"]:::generated
        types["src/generated/types/*"]:::generated
    end

    %% Tests
    subgraph "Integration & Serialization Tests"
        direction TB
        tests_dir["tests/*"]:::generated
    end

    %% Core SDK Runtime
    subgraph "Core SDK Runtime"
        direction TB
        client_trait["src/client_trait.rs"]:::core
        async_client_trait["src/async_client_trait.rs"]:::core
        client_helpers["src/client_helpers.rs & src/client_trait_common.rs"]:::core
        error_mod["src/error.rs"]:::core
        oauth2["src/oauth2.rs"]:::core
    end

    %% Default HTTP Clients
    subgraph "Default HTTP Clients"
        direction TB
        default_sync["src/default_client.rs & src/default_client_common.rs"]:::core
        default_async["src/default_async_client.rs"]:::core
    end

    %% User Application
    subgraph "User Code Examples"
        direction TB
        demo_sync["examples/demo.rs"]:::user
        demo_async["examples/demo-async.rs"]:::user
        demo_large["examples/large-file-upload.rs"]:::user
    end

    %% External Service
    dropbox_api["Dropbox API (HTTPS)"]:::external

    %% Build-Time Flow
    dropbox_api_spec -->|spec JSON| stone
    stone -->|uses templates| gen_py
    gen_py -->|generates code| sync_routes
    gen_py -->|generates code| async_routes
    gen_py -->|generates types| types
    gen_py -->|generates tests| tests_dir
    update_spec_py -->|updates spec| dropbox_api_spec
    update_manifest_py -->|updates generator manifest| gen_py
    gen_py --> gen_rust_py
    gen_py --> gen_rust_stone_py
    gen_py --> gen_test_stone_py

    %% Runtime Flow
    demo_sync -->|calls routes| sync_routes
    demo_async -->|calls routes| async_routes
    demo_large -->|calls routes| sync_routes
    sync_routes -->|serializes| client_trait
    async_routes -->|serializes| async_client_trait
    client_trait -->|uses| default_sync
    async_client_trait -->|uses| default_async
    client_helpers --> client_trait
    client_helpers --> async_client_trait
    error_mod --> sync_routes
    error_mod --> async_routes
    oauth2 --> demo_sync
    oauth2 --> demo_async
    default_sync -->|JSON over HTTPS| dropbox_api
    default_async -->|JSON over HTTPS| dropbox_api

    %% Click Events
    click dropbox_api_spec "https://github.com/dropbox/dropbox-sdk-rust/tree/master/dropbox-api-spec/"
    click stone "https://github.com/dropbox/dropbox-sdk-rust/tree/master/stone/"
    click gen_py "https://github.com/dropbox/dropbox-sdk-rust/blob/master/generate.py"
    click update_spec_py "https://github.com/dropbox/dropbox-sdk-rust/blob/master/update_spec.py"
    click update_manifest_py "https://github.com/dropbox/dropbox-sdk-rust/blob/master/update_manifest.py"
    click gen_rust_py "https://github.com/dropbox/dropbox-sdk-rust/blob/master/generator/rust.py"
    click gen_rust_stone_py "https://github.com/dropbox/dropbox-sdk-rust/blob/master/generator/rust.stoneg.py"
    click gen_test_stone_py "https://github.com/dropbox/dropbox-sdk-rust/blob/master/generator/test.stoneg.py"
    click client_trait "https://github.com/dropbox/dropbox-sdk-rust/blob/master/src/client_trait.rs"
    click async_client_trait "https://github.com/dropbox/dropbox-sdk-rust/blob/master/src/async_client_trait.rs"
    click client_helpers "https://github.com/dropbox/dropbox-sdk-rust/blob/master/src/client_helpers.rs"
    click client_helpers "https://github.com/dropbox/dropbox-sdk-rust/blob/master/src/client_trait_common.rs"
    click error_mod "https://github.com/dropbox/dropbox-sdk-rust/blob/master/src/error.rs"
    click oauth2 "https://github.com/dropbox/dropbox-sdk-rust/blob/master/src/oauth2.rs"
    click default_sync "https://github.com/dropbox/dropbox-sdk-rust/blob/master/src/default_client.rs"
    click default_sync "https://github.com/dropbox/dropbox-sdk-rust/blob/master/src/default_client_common.rs"
    click default_async "https://github.com/dropbox/dropbox-sdk-rust/blob/master/src/default_async_client.rs"
    click sync_routes "https://github.com/dropbox/dropbox-sdk-rust/tree/master/src/generated/sync_routes/"
    click async_routes "https://github.com/dropbox/dropbox-sdk-rust/tree/master/src/generated/async_routes/"
    click types "https://github.com/dropbox/dropbox-sdk-rust/tree/master/src/generated/types/"
    click demo_sync "https://github.com/dropbox/dropbox-sdk-rust/blob/master/examples/demo.rs"
    click demo_async "https://github.com/dropbox/dropbox-sdk-rust/blob/master/examples/demo-async.rs"
    click demo_large "https://github.com/dropbox/dropbox-sdk-rust/blob/master/examples/large-file-upload.rs"
    click tests_dir "https://github.com/dropbox/dropbox-sdk-rust/tree/master/tests/"

    %% Styles
    classDef codegen fill:#FFA500,stroke:#333,stroke-width:1px
    classDef generated fill:#ADD8E6,stroke:#333,stroke-width:1px
    classDef core fill:#90EE90,stroke:#333,stroke-width:1px
    classDef user fill:#D3D3D3,stroke:#333,stroke-width:1px
    classDef external fill:#DDA0DD,stroke:#333,stroke-width:1px

```

---


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