---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/DPGAlliance/publicgoods-candidates
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




# publicgoods-candidates repo project
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
title: "publicgoods-candidates repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright © 2025 Cong Le. All Rights Reserved."
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
flowchart TD
    %% Actors and Events
    Author(["Author"]):::external
    GitHubPush(["GitHub Push / PR"]):::ci

    %% Content Layer
    subgraph "Content Layer"
        Nominees["/nominees JSON Store"]:::data
        DigitalPublicGoods["/digitalpublicgoods JSON Store"]:::data
        Archive["/archive JSON Store"]:::data
        ExcludedNominees["/excluded-nominees JSON Store"]:::data
        Reviews["/reviews JSON Store"]:::data
        Schemas["nominee-schema.json<br/>screening-schema.json"]:::data
    end

    %% Processing Engine
    subgraph "Processing Engine"
        Scripts["Transformation Scripts<br/>(Node.js)"]:::process
        Dependencies["package.json<br/>package-lock.json"]:::process
    end

    %% CI/CD Layer
    subgraph "CI/CD (GitHub Actions)"
        Workflows[".github/workflows<br/>main.yml<br/>auto.yml"]:::ci
    end

    %% Documentation & Policies
    subgraph "Documentation & Policies"
        Docs["/docs"]:::doc
        HelpCenter["/help-center"]:::doc
        Governance["CONTRIBUTING.md<br/>CODE_OF_CONDUCT.md<br/>LICENSE"]:::doc
    end

    %% External Services
    subgraph "External Services"
        DPGWebsite["DigitalPublicGoods.net<br/>(Static Site/API)"]:::external
        BugReporter["bug-reporter.vercel.app"]:::external
    end

    %% Data Flows
    Author -->|commits JSON content| Nominees
    Author -->|commits JSON content| DigitalPublicGoods
    Author -->|commits JSON content| Archive
    Author -->|commits JSON content| ExcludedNominees
    Author -->|commits JSON content| Reviews
    Author -->|updates schemas| Schemas

    GitHubPush -.->|trigger| Workflows
    Workflows -->|invoke scripts| Scripts
    Scripts -->|read JSON & schemas| Nominees
    Scripts -->|read JSON & schemas| DigitalPublicGoods
    Scripts -->|read JSON & schemas| Archive
    Scripts -->|read JSON & schemas| ExcludedNominees
    Scripts -->|read JSON & schemas| Reviews
    Scripts -->|use schemas| Schemas
    Scripts -->|use dependencies| Dependencies
    Scripts -->|produce normalized JSON| Workflows
    Workflows -->|deploy artifacts| DPGWebsite
    Workflows -->|notify issues| BugReporter

    %% Documentation links
    Author --> Docs
    Author --> HelpCenter
    Author --> Governance

    %% Click Events for component mapping
    click Nominees "https://github.com/dpgalliance/publicgoods-candidates/tree/main/nominees/"
    click DigitalPublicGoods "https://github.com/dpgalliance/publicgoods-candidates/tree/main/digitalpublicgoods/"
    click Archive "https://github.com/dpgalliance/publicgoods-candidates/tree/main/archive/"
    click ExcludedNominees "https://github.com/dpgalliance/publicgoods-candidates/tree/main/excluded-nominees/"
    click Reviews "https://github.com/dpgalliance/publicgoods-candidates/tree/main/reviews/"
    click Schemas "https://github.com/dpgalliance/publicgoods-candidates/blob/main/nominee-schema.json"
    click Scripts "https://github.com/dpgalliance/publicgoods-candidates/tree/main/scripts/"
    click Dependencies "https://github.com/dpgalliance/publicgoods-candidates/blob/main/package.json"
    click Workflows "https://github.com/dpgalliance/publicgoods-candidates/blob/main/.github/workflows/main.yml"
    click Docs "https://github.com/dpgalliance/publicgoods-candidates/tree/main/docs/"
    click HelpCenter "https://github.com/dpgalliance/publicgoods-candidates/tree/main/help-center/"
    click Governance "https://github.com/dpgalliance/publicgoods-candidates/blob/main/CONTRIBUTING.md"

    %% Styling
    classDef data fill:#cce5ff,stroke:#004085,color:#004085;
    classDef process fill:#d4edda,stroke:#155724,color:#155724;
    classDef ci fill:#fff3cd,stroke:#856404,color:#856404;
    classDef external fill:#e2e3e5,stroke:#6c757d,color:#6c757d;
    classDef doc fill:#f8f9fa,stroke:#6c757d,color:#6c757d;
```

----

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