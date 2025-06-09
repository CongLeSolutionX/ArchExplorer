---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/filecoin-project/rust-fil-proofs
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExMnF2dWN0czd0djAwaHhrMGFpbTB2cnFtdTgwaGNlZWJjY2I3aXhrYyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/b4R6VJ3y942mHySNta/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# rust-fil-proofs repo project
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
title: "rust-fil-proofs repo project"
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
    %% CI/CD and External Storage
    CIWorkflows["CI/CD Workflows"]:::gray
    ExternalStorage["Artifact Storage (IPFS/GitHub)"]:::gray

    CIWorkflows -->|triggers tests & param tasks| CoreCrypto
    CIWorkflows --> CircuitModules
    CIWorkflows --> FilecoinProofs
    CIWorkflows --> FilProofsParam
    CIWorkflows --> FilProofsTooling
    CIWorkflows -->|uploads/downloads artifacts| ExternalStorage

    ExternalStorage -->|provides parameters| FilProofsParam

    %% Low-Level Crypto Libraries
    subgraph "Low-Level Crypto Libraries"
        direction TB
        CoreCrypto["storage-proofs-core"]:::lowblue
        FilecoinHashers["filecoin-hashers"]:::lowblue
        Sha2Raw["sha2raw"]:::lowblue
        FR32["fr32"]:::lowblue
    end

    CoreCrypto -->|uses hashing| FilecoinHashers
    CoreCrypto --> Sha2Raw
    CoreCrypto --> FR32

    %% Circuit Modules
    subgraph "Circuit Modules"
        direction TB
        PoRep["storage-proofs-porep"]:::green
        PoSt["storage-proofs-post"]:::green
        Update["storage-proofs-update"]:::green
    end

    CoreCrypto -->|provides gadgets| PoRep
    CoreCrypto --> PoSt
    CoreCrypto --> Update

    %% High-Level API
    FilecoinProofs["filecoin-proofs"]:::orange

    PoRep -->|wraps in API| FilecoinProofs
    PoSt --> FilecoinProofs
    Update --> FilecoinProofs

    %% Parameter Management
    FilProofsParam["fil-proofs-param"]:::orange
    FilProofsParam -->|feeds parameters| PoRep
    FilProofsParam --> PoSt
    FilProofsParam --> Update
    FilProofsParam --> FilecoinProofs

    %% Tooling & Benchmarks
    FilProofsTooling["fil-proofs-tooling"]:::orange

    FilProofsTooling -->|benchmarks & checks| Engineers[Engineers/CI Consumers]:::gray

    %% Click Events
    click CoreCrypto "https://github.com/filecoin-project/rust-fil-proofs/tree/master/storage-proofs-core/"
    click FilecoinHashers "https://github.com/filecoin-project/rust-fil-proofs/tree/master/filecoin-hashers/"
    click Sha2Raw "https://github.com/filecoin-project/rust-fil-proofs/tree/master/sha2raw/"
    click FR32 "https://github.com/filecoin-project/rust-fil-proofs/tree/master/fr32/"
    click PoRep "https://github.com/filecoin-project/rust-fil-proofs/tree/master/storage-proofs-porep/"
    click PoSt "https://github.com/filecoin-project/rust-fil-proofs/tree/master/storage-proofs-post/"
    click Update "https://github.com/filecoin-project/rust-fil-proofs/tree/master/storage-proofs-update/"
    click FilecoinProofs "https://github.com/filecoin-project/rust-fil-proofs/tree/master/filecoin-proofs/"
    click FilProofsParam "https://github.com/filecoin-project/rust-fil-proofs/tree/master/fil-proofs-param/"
    click FilProofsTooling "https://github.com/filecoin-project/rust-fil-proofs/tree/master/fil-proofs-tooling/"
    click CIWorkflows "https://github.com/filecoin-project/rust-fil-proofs/tree/master/.github/workflows/"

    %% Styles
    classDef lowblue fill:#E0F7FA,stroke:#006064,color:#004D40;
    classDef green fill:#E8F5E9,stroke:#1B5E20,color:#1B5E20;
    classDef orange fill:#FFF3E0,stroke:#E65100,color:#E65100;
    classDef gray fill:#ECEFF1,stroke:#607D8B,color:#37474F;
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