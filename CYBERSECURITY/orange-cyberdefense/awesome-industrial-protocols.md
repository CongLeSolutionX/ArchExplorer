---
created: 2025-06-25 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/Orange-Cyberdefense/awesome-industrial-protocols
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




# awesome-industrial-protocols repo project
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
title: "awesome-industrial-protocols repo project"
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
    %% Content/Data Layer
    subgraph "Content/Data Layer"
        style DataLayer fill:none,stroke:none
        Links((db/links.json)):::data
        Packets((db/packets.json)):::data
        ProtocolsManifest((db/protocols.json)):::data
        ProtocolsFolder["protocols/ (Markdown)"]:::data
        ExampleProtocol["protocols/ads.md"]:::data
        Contrib["CONTRIBUTING.md"]:::repo
        Readme["README.md"]:::repo
        License["LICENSE"]:::repo
    end

    %% Build/Generation Layer
    subgraph "Build/Generation Layer"
        style BuildLayer fill:none,stroke:none
        GitHubRepo["GitHub Repository"]:::repo
        CI["GitHub Actions (CI/CD)"]:::process
        Generator["site-generator.js"]:::process
    end

    %% Hosting/Delivery Layer
    subgraph "Hosting/Delivery Layer"
        style HostLayer fill:none,stroke:none
        Pages("GitHub Pages"):::host
    end

    %% Client/User Layer
    subgraph "Client/User Layer"
        style ClientLayer fill:none,stroke:none
        Browser["Web Browser"]:::client
    end

    %% Relationships
    Dev[/"Developer"/]:::client -->|push| GitHubRepo
    GitHubRepo -->|triggers build| CI
    CI -->|runs| Generator
    Generator -->|reads| Links
    Generator -->|reads| Packets
    Generator -->|reads| ProtocolsManifest
    Generator -->|reads| ProtocolsFolder
    Generator -->|reads| ExampleProtocol
    Generator -->|reads| Readme
    Generator -->|reads| Contrib
    Generator -->|reads| License
    Generator -->|generates| SiteOutput["Generated Site"]:::process
    SiteOutput -->|deploy| Pages
    Browser -->|request| Pages
    Pages -->|serve| Browser

    %% Click Events
    click Links "https://github.com/orange-cyberdefense/awesome-industrial-protocols/blob/main/db/links.json"
    click Packets "https://github.com/orange-cyberdefense/awesome-industrial-protocols/blob/main/db/packets.json"
    click ProtocolsManifest "https://github.com/orange-cyberdefense/awesome-industrial-protocols/blob/main/db/protocols.json"
    click ProtocolsFolder "https://github.com/orange-cyberdefense/awesome-industrial-protocols/tree/main/protocols/"
    click ExampleProtocol "https://github.com/orange-cyberdefense/awesome-industrial-protocols/blob/main/protocols/ads.md"
    click Contrib "https://github.com/orange-cyberdefense/awesome-industrial-protocols/blob/main/CONTRIBUTING.md"
    click Readme "https://github.com/orange-cyberdefense/awesome-industrial-protocols/blob/main/README.md"
    click License "https://github.com/orange-cyberdefense/awesome-industrial-protocols/tree/main/LICENSE"

    %% Styles
    classDef data fill:#bbdefb,stroke:#1e88e5,color:#0d47a1
    classDef process fill:#c8e6c9,stroke:#2e7d32,color:#1b5e20
    classDef host fill:#ffcc80,stroke:#ef6c00,color:#e65100
    classDef client fill:#e0e0e0,stroke:#616161,color:#263238
    classDef repo fill:#d1c4e9,stroke:#6a1b9a,color:#4a148c

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