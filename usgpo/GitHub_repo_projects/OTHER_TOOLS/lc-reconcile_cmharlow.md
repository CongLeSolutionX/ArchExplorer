---
created: 2025-06-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/cmharlow/lc-reconcile
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExYzRwc2Uxdmh3MTh1NDRsb3NsdXRyN3ZlamUxdGN5MndnbzJpdWwycCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3o6Mvn3uHSZA3AnCA8/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# cmharlow - lc-reconcile repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


----

```mermaid
---
title: "cmharlow - lc-reconcile repo project"
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
    %% Client Layer
    subgraph "Client Layer"
        direction TB
        Client["OpenRefine Client"]:::client
    end

    %% Service Layer
    subgraph "Service Layer"
        direction TB
        HTTP["HTTP Server\n(reconcile.py)"]:::service
        Normalizer["Text Normalizer\n(text.py)"]:::service
        Orchestrator["Suggest & DidYouMean Orchestrator"]:::service
        Ranking["Ranking Module\n(fuzzywuzzy)"]:::service
        Formatter["Response Formatter"]:::service
        Debug["Debug Logger Flag"]:::service
    end

    %% Project Artifacts
    subgraph "Project Artifacts"
        direction TB
        Req["requirements.txt"]:::docs
        Readme["README.md"]:::docs
    end

    %% External API Layer
    subgraph "External API Layer"
        direction TB
        SuggestAPI["LC Suggest API"]:::external
        DidYouMeanAPI["LC DidYouMean API"]:::external
    end

    %% Flows
    Client -->|"User query request"| HTTP
    HTTP -->|"normalize(query)"| Normalizer
    HTTP -->|"GET /suggest?q=..."| SuggestAPI
    HTTP -->|"GET /didyoumean?label=..."| DidYouMeanAPI
    HTTP -->|"score & sort"| Ranking
    HTTP -->|"format JSON"| Formatter
    Formatter -->|"JSON top 3 candidates"| Client
    HTTP --- Debug

    %% Click Events
    click HTTP "https://github.com/cmharlow/lc-reconcile/blob/master/reconcile.py"
    click Normalizer "https://github.com/cmharlow/lc-reconcile/blob/master/text.py"
    click Req "https://github.com/cmharlow/lc-reconcile/blob/master/requirements.txt"
    click Readme "https://github.com/cmharlow/lc-reconcile/blob/master/README.md"

    %% Styles
    classDef client fill:#ADD8E6,stroke:#000,stroke-width:1px
    classDef service fill:#90EE90,stroke:#000,stroke-width:1px
    classDef external fill:#FFA500,stroke:#000,stroke-width:1px
    classDef docs fill:#E0E0E0,stroke:#000,stroke-width:1px
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
