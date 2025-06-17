---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/webcomponents/webcomponents.org
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


# webcomponents.org repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>



-----

```mermaid
---
title: "webcomponents.org repo project"
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
  subgraph "Tooling Layer"
    direction TB
    npmRegistry[(NPM Registry)]:::external
    cemt["custom-elements-manifest-tools"]:::tooling
  end
  npmRegistry -->|fetch packages| cemt
  cemt -->|ingest CEM JSON| catalogServer

  subgraph "Backend Layer"
    direction TB
    catalogAPI["catalog-api (GraphQL schema/types)"]:::tooling
    catalogServer["catalog-server: GraphQL API (port 6451)"]:::backend
    firestore[(Firestore)]:::database
  end
  cemt -->|bootstrap| catalogServer
  catalogServer -->|uses schema| catalogAPI
  catalogServer -->|read/write| firestore

  subgraph "Frontend Layer"
    direction TB
    siteContent["site-content (Eleventy SSG)"]:::tooling
    siteTemplates["site-templates (shared templates)"]:::tooling
    siteServer["site-server: static + proxy (ports 5450/5451)"]:::frontend
    siteClient["site-client SPA"]:::frontend
    browser[(Browser)]:::external
    documents[/Eleventy HTML/]:::frontend
  end
  siteContent -->|build with templates| documents
  documents -->|serve static| siteServer
  siteTemplates -->|shared| siteContent
  siteTemplates -->|shared| siteServer
  siteServer -->|hosts SPA| siteClient
  browser -->|HTTP/GraphQL| siteServer
  siteClient -->|GraphQL queries| siteServer
  siteServer -->|proxy GraphQL| catalogServer

  subgraph "Local Dev (Docker Compose)"
    direction TB
    dockerCompose["Docker Compose"]:::ci
    firestoreEmu["Firestore Emulator"]:::database
    dockerCatalog["catalog-server (container)"]:::backend
    dockerSite["site-server (container)"]:::frontend
  end
  dockerCompose -->|runs| firestoreEmu
  dockerCompose --> dockerCatalog
  dockerCompose --> dockerSite

  subgraph "CI/CD (Orange)"
    direction TB
    gha["GitHub Actions"]:::ci
    cloudBuild["cloud-build (GCP pipelines)"]:::ci
    gcp["GCP Deploy"]:::external
  end
  gha -->|on push| cloudBuild
  cloudBuild -->|deploy| gcp

  click cemt "https://github.com/webcomponents/webcomponents.org/tree/main/packages/custom-elements-manifest-tools"
  click catalogServer "https://github.com/webcomponents/webcomponents.org/tree/main/packages/catalog-server"
  click catalogAPI "https://github.com/webcomponents/webcomponents.org/tree/main/packages/catalog-api"
  click siteServer "https://github.com/webcomponents/webcomponents.org/tree/main/packages/site-server"
  click siteClient "https://github.com/webcomponents/webcomponents.org/tree/main/packages/site-client"
  click siteContent "https://github.com/webcomponents/webcomponents.org/tree/main/packages/site-content"
  click siteTemplates "https://github.com/webcomponents/webcomponents.org/tree/main/packages/site-templates"
  click dockerCompose "https://github.com/webcomponents/webcomponents.org/blob/main/docker/docker-compose.yml"
  click gha "https://github.com/webcomponents/webcomponents.org/blob/main/.github/workflows/*.yml"
  click cloudBuild "https://github.com/webcomponents/webcomponents.org/blob/main/cloud-build/deploy-main.yaml"
  click cloudBuild "https://github.com/webcomponents/webcomponents.org/blob/main/cloud-build/deploy-pr.yaml"

  classDef backend fill:#ADD8E6,stroke:#000;
  classDef frontend fill:#90EE90,stroke:#000;
  classDef tooling fill:#FFA500,stroke:#000;
  classDef database fill:#EEE8AA,stroke:#000;
  classDef external fill:#D3D3D3,stroke:#000;
  classDef ci fill:#FFD580,stroke:#000;
```

----

s

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