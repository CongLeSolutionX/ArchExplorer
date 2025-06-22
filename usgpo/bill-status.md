---
created: 2025-06-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/usgpo/bill-status
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExNm1ubjFmbGlnNW9jOGphdHd2azA4ZzBpaDd5bDRkODlvNnh1a29xdCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/g5RsOpLxcPEpa/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# bill-status repo project
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
title: "bill-status repo project"
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
    %% Batch Pipeline
    subgraph "Batch Pipeline"
        Scheduler["Scheduler/Orchestrator<br/><i>every 4hrs (current) / daily (prior)</i>"]:::compute
        Ingestion["Ingestion Service<br/>(fetch GPO Bulk API)"]:::compute
        Processing["Processing & Organization<br/>(ETL & sample organization)"]:::compute
    end

    %% Storage Layer
    subgraph "Storage Layer"
        XMLStore(("XML File Store")):::storage
        RSSGen["RSS Feed Generator"]:::compute
        RSSStore(("RSS Feed Store")):::storage
        subgraph "Sample Data Organization"
            SamplesAC["actions-committees"]:::storage
            SamplesAV["amendment-votes"]:::storage
            SamplesFCc["formatChange/current"]:::storage
            SamplesFCf["formatChange/future"]:::storage
            SamplesLG["legacy"]:::storage
            SamplesTV["textVersions"]:::storage
        end
    end

    %% Publication Layer
    subgraph "Publication Layer"
        StaticSite["Static Site Hosting<br/>(GitHub Pages + GovInfo)"]:::delivery
        RSSFeed["RSS Feed Endpoint"]:::delivery
        Sitemap["Sitemap Index"]:::delivery
    end

    %% Documentation Artifacts
    subgraph "Documentation Artifacts"
        UserGuidePDF["BILLSTATUS-XML_User-Guide-v1.pdf"]:::docs
        UserGuideMD["BILLSTATUS-XML_User_User-Guide.md"]:::docs
        CHANGELOG["CHANGELOG.md"]:::docs
        Meetings["meetings/"]:::docs
        README["README.md"]:::docs
        CODEOWNERS["CODEOWNERS"]:::docs
    end

    EndUsers>End Users / RSS Clients / Browsers]:::external

    %% Data Flows
    Scheduler -->|triggers| Ingestion
    Ingestion -->|fetch XML bundles| Processing
    Processing -->|organize & enrich| XMLStore
    XMLStore -->|trigger site sync| StaticSite
    XMLStore -->|"generate RSS"| RSSGen
    RSSGen -->|write feed| RSSStore
    XMLStore -->|generate sitemap| Sitemap
    RSSStore -->|serve feed| RSSFeed
    StaticSite -->|serve static content| EndUsers
    RSSFeed -->|provide feed| EndUsers
    Sitemap -->|provide index| EndUsers

    %% Click Events
    click UserGuidePDF "https://github.com/usgpo/bill-status/blob/main/BILLSTATUS-XML_User-Guide-v1.pdf"
    click UserGuideMD "https://github.com/usgpo/bill-status/blob/main/BILLSTATUS-XML_User_User-Guide.md"
    click CHANGELOG "https://github.com/usgpo/bill-status/blob/main/CHANGELOG.md"
    click Meetings "https://github.com/usgpo/bill-status/tree/main/meetings/"
    click SamplesAC "https://github.com/usgpo/bill-status/tree/main/samples/actions-committees/"
    click SamplesAV "https://github.com/usgpo/bill-status/tree/main/samples/amendment-votes/"
    click SamplesFCc "https://github.com/usgpo/bill-status/tree/main/samples/formatChange/current/"
    click SamplesFCf "https://github.com/usgpo/bill-status/tree/main/samples/formatChange/future/"
    click SamplesLG "https://github.com/usgpo/bill-status/tree/main/samples/legacy/"
    click SamplesTV "https://github.com/usgpo/bill-status/tree/main/samples/textVersions/"
    click README "https://github.com/usgpo/bill-status/blob/main/README.md"
    click CODEOWNERS "https://github.com/usgpo/bill-status/tree/main/CODEOWNERS"

    %% Styles
    classDef compute fill:#D0E8FF,stroke:#0366d6,color:#0366d6,stroke-width:1px;
    classDef storage fill:#E8F5E9,stroke:#2E7D32,color:#2E7D32,stroke-width:1px;
    classDef delivery fill:#FFF3E0,stroke:#EF6C00,color:#EF6C00,stroke-width:1px;
    classDef docs fill:#F3E5F5,stroke:#6A1B9A,color:#6A1B9A,stroke-width:1px;
    classDef external fill:#ECEFF1,stroke:#546E7A,color:#546E7A,stroke-width:1px;

```

------

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
