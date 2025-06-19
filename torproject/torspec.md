---
created: 2025-06-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/torproject/torspec
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




# torspec repo project
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


----

```mermaid
---
title: "torspec repo project"
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
    subgraph "Version Control"
        GitLabRepo["GitLab Repo"]:::config
        GitIgnore[".gitignore"]:::config
        README["README.md"]:::config
        GitLabRepo -->|contains| GitIgnore
        GitLabRepo -->|contains| README
    end

    subgraph "Proposals (Drafts)" 
        ProposalsDir["Proposals Directory"]:::docs
        ReindexScript["reindex.py"]:::config
        ProposalsDir -->|uses| ReindexScript
    end

    subgraph "Specification Modules" 
        subgraph "General Interest" 
            TorSpec["tor-spec.txt"]:::docs
            CertSpec["cert-spec.txt"]:::docs
            DirSpec["dir-spec.txt"]:::docs
            VersionSpec["version-spec.txt"]:::docs
        end
        subgraph "Client Operations"
            AddressSpec["address-spec.txt"]:::docs
            PathSpec["path-spec.txt"]:::docs
            SocksSpec["socks-extensions.txt"]:::docs
            ExtOrportSpec["ext-orport-spec.txt"]:::docs
        end
        subgraph "Onion Services"
            RendV3["rend-spec-v3.txt"]:::docs
            AtticRendV2["rend-spec-v2.txt"]:::docs
        end
        subgraph "Censorship Resistance"
            BridgeSpec["bridgedb-spec.txt"]:::docs
            PtSpec["pt-spec.txt"]:::docs
            GettorSpec["gettor-spec.txt"]:::docs
        end
        subgraph "Directory Authorities"
            BandwidthSpec["bandwidth-file-spec.txt"]:::docs
            SrvSpec["srv-spec.txt"]:::docs
        end
        subgraph "Controller Protocol"
            ControlSpec["control-spec.txt"]:::docs
        end
        subgraph "Miscellaneous & Historical"
            DirListSpec["dir-list-spec.txt"]:::docs
            Attic["attic/"]:::docs
        end
    end

    subgraph "Automation"
        CI["CI Pipeline"]:::automation
        CIGitlab[".gitlab-ci.yml"]:::config
        CI -->|configured by| CIGitlab
    end

    Implementers["Implementer/Client & Relay Codebases"]:::external

    GitLabRepo -->|push triggers| CI
    CI -->|validates| ProposalsDir
    CI -->|validates| SpecificationModules
    ProposalsDir -->|propose→review→merge| SpecificationModules
    SpecificationModules -->|consumed by| Implementers

    click TorSpec "https://github.com/torproject/torspec/blob/main/tor-spec.txt"
    click CertSpec "https://github.com/torproject/torspec/blob/main/cert-spec.txt"
    click DirSpec "https://github.com/torproject/torspec/blob/main/dir-spec.txt"
    click VersionSpec "https://github.com/torproject/torspec/blob/main/version-spec.txt"
    click AddressSpec "https://github.com/torproject/torspec/blob/main/address-spec.txt"
    click PathSpec "https://github.com/torproject/torspec/blob/main/path-spec.txt"
    click SocksSpec "https://github.com/torproject/torspec/blob/main/socks-extensions.txt"
    click ExtOrportSpec "https://github.com/torproject/torspec/blob/main/ext-orport-spec.txt"
    click RendV3 "https://github.com/torproject/torspec/blob/main/rend-spec-v3.txt"
    click AtticRendV2 "https://github.com/torproject/torspec/blob/main/attic/rend-spec-v2.txt"
    click BridgeSpec "https://github.com/torproject/torspec/blob/main/bridgedb-spec.txt"
    click PtSpec "https://github.com/torproject/torspec/blob/main/pt-spec.txt"
    click GettorSpec "https://github.com/torproject/torspec/blob/main/gettor-spec.txt"
    click BandwidthSpec "https://github.com/torproject/torspec/blob/main/bandwidth-file-spec.txt"
    click SrvSpec "https://github.com/torproject/torspec/blob/main/srv-spec.txt"
    click ControlSpec "https://github.com/torproject/torspec/blob/main/control-spec.txt"
    click DirListSpec "https://github.com/torproject/torspec/blob/main/dir-list-spec.txt"
    click Attic "https://github.com/torproject/torspec/tree/main/attic/"
    click ProposalsDir "https://github.com/torproject/torspec/tree/main/proposals/"
    click ReindexScript "https://github.com/torproject/torspec/blob/main/proposals/reindex.py"
    click CIGitlab "https://github.com/torproject/torspec/blob/main/.gitlab-ci.yml"
    click GitIgnore "https://github.com/torproject/torspec/blob/main/.gitignore"
    click README "https://github.com/torproject/torspec/blob/main/README.md"

    classDef docs fill:#D0E6FF,stroke:#0366d6
    classDef automation fill:#DFFFE0,stroke:#28a745
    classDef external fill:#FFE8CC,stroke:#d15704
    classDef config fill:#F0F0F0,stroke:#888888
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