---
created: 2025-06-26 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/containerd/imgcrypt
---

<div align="center">
  <p>⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷</p>
  <i>This is a working draft in progress.</i>
  <br/>
  <img alt="Loading…" src="https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExNjN1Nnk0bXIyNjhvd3ZxYWNpMXlhbWE5OXJlODlnZWQydWRrZjZpYSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/6jnuP7BZPv3uAAtAFs/giphy.gif"/>
  <br/>
  <blockquote>
	  <i>gif image is provided by <a href="https://giphy.com">Giphy</a></i>
  </blockquote>
  <p>⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷</p>

</div>


# imgcrypt repo project
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


----

```mermaid
---
title: "imgcrypt repo project"
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
    %% Consumers
    Consumer["Kubernetes/CRI<br/>End-user Apps"]:::consumer

    subgraph "CLI Tools Layer"
    direction TB
        ctr_enc["ctr-enc<br/>(enhanced ctr CLI)"]:::cli
        ctd_decoder["ctd-decoder<br/>(stream-processor plugin)"]:::cli
    end

    subgraph "imgcrypt Library Layer"
    direction TB
        imgcrypt_lib["images/encryption<br/>(core encryption logic)"]:::library
        parsehelpers["JWE Parse Helpers<br/>parsehelpers.go"]:::library
        payload["Shared Payload Structures<br/>payload.go"]:::library
    end

    %% External Dependencies
    subgraph "External Crypto Engine"
    direction TB
        ocicrypt["ocicrypt<br/>(JWE/AES-GCM)"]:::external
    end

    %% Containerd Daemon & Plugin
    subgraph "Containerd"
    direction TB
        cd_daemon["containerd Daemon<br/>(stream_processor plugin)"]:::daemon
    end

    %% OCI Registry
    Registry["OCI Registry<br/>(Docker/Registry)"]:::registry

    %% Key Management
    Keystore["Key Store<br/>(PEM files / HSM)"]:::keystore

    %% Flows
    Consumer -->|"invoke encrypt<br/>ctr-enc images encrypt"| ctr_enc
    ctr_enc -->|"calls imgcrypt<br/>EncryptLayer"| imgcrypt_lib
    imgcrypt_lib -->|"Wrap Layer"| ocicrypt
    ocicrypt -->|"Encrypted Layer<br/>& Index"| ctr_enc
    ctr_enc -->|"Push (HTTP Push)"| Registry

    Consumer -->|"pull/run<br/>using ctr-enc"| ctr_enc
    ctr_enc -->|"HTTP Pull"| Registry
    Registry -->|"Registry Data"| cd_daemon
    cd_daemon -->|"gRPC StreamProcessor<br/>invokes Decoder"| ctd_decoder
    ctd_decoder -->|"calls imgcrypt<br/>DecryptStream"| imgcrypt_lib
    imgcrypt_lib -->|"Decrypt Layer"| ocicrypt
    ocicrypt -->|"Plain Layer Stream"| cd_daemon

    ctr_enc -->|"--recipient embeds JWE"| payload
    ctd_decoder -->|"reads private key"| Keystore

    %% Click Events for component mapping
    click ctr_enc "https://github.com/containerd/imgcrypt/tree/main/cmd/ctr"
    click ctd_decoder "https://github.com/containerd/imgcrypt/tree/main/cmd/ctd-decoder"
    click imgcrypt_lib "https://github.com/containerd/imgcrypt/tree/main/images/encryption"
    click parsehelpers "https://github.com/containerd/imgcrypt/blob/main/images/encryption/parsehelpers/parsehelpers.go"
    click payload "https://github.com/containerd/imgcrypt/blob/main/payload.go"
    click encrypt_cmd "https://github.com/containerd/imgcrypt/blob/main/cmd/ctr/commands/images/encrypt.go"
    click decrypt_cmd "https://github.com/containerd/imgcrypt/blob/main/cmd/ctr/commands/images/decrypt.go"
    click run_cmd "https://github.com/containerd/imgcrypt/blob/main/cmd/ctr/commands/run/run.go"
    click ctr_app_main "https://github.com/containerd/imgcrypt/blob/main/cmd/ctr/app/main.go"
    click ctr_app_unix "https://github.com/containerd/imgcrypt/blob/main/cmd/ctr/app/main_unix.go"
    click ctd_main "https://github.com/containerd/imgcrypt/blob/main/cmd/ctd-decoder/main.go"
    click ctd_main_unix "https://github.com/containerd/imgcrypt/blob/main/cmd/ctd-decoder/main_unix.go"
    click ctd_main_win "https://github.com/containerd/imgcrypt/blob/main/cmd/ctd-decoder/main_windows.go"
    click ctd_helpers "https://github.com/containerd/imgcrypt/blob/main/cmd/ctd-decoder/enc_helpers.go"
    click softhsm "https://github.com/containerd/imgcrypt/tree/main/script/tests/softhsm_setup"
    click checkfmt "https://github.com/containerd/imgcrypt/blob/main/script/check_format.sh"
    click ci "https://github.com/containerd/imgcrypt/blob/main/ .github/workflows/ci.yml"
    click makefile "https://github.com/containerd/imgcrypt/tree/main/Makefile"
    click go_mod "https://github.com/containerd/imgcrypt/blob/main/go.mod"

    %% Styles
    classDef cli fill:#cce5ff,stroke:#00529B,color:#00529B;
    classDef library fill:#d4edda,stroke:#40754C,color:#40754C;
    classDef external fill:#fff3cd,stroke:#9F6000,color:#9F6000;
    classDef daemon fill:#f8d7da,stroke:#D8000C,color:#D8000C;
    classDef registry fill:#e2e3e5,stroke:#6C757D,color:#6C757D;
    classDef keystore fill:#ffeeba,stroke:#9F6000,color:#9F6000;
    classDef consumer fill:#f5c6cb,stroke:#721c24,color:#721c24;

```

-----

```mermaid
---
title: "❓...CongLeSolutionX....❓"
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
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

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
