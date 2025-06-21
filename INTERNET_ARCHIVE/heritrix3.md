---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/internetarchive/heritrix3
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExZGMyaDVxbWJydWp6YzFvNnFhdGVvNXlxNTJyODV5dXdqNWF4aWFnNyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/hLZohDcjflptK/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# heritrix3 repo project
> <ins>📢 **Disclaimer** 🚨</ins>
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
title: "heritrix3 repo project"
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
    UI_REST["Web UI / REST API"]:::ui
    Engine_Core["Engine Core\n(CrawlController, Engine, ToePool, CheckpointService)"]:::core
    Frontier["Frontier\n(WorkQueue & BDBJE)"]:::pipeline
    Prefetch["Prefetch & Quota Enforcement"]:::pipeline
    Processing["Processing Pipeline\n(Canonicalize → Deciderules → Extractors → Postprocessors)"]:::pipeline
    Writers["Writers & Storage\n(ARC/WARC, Mirror)"]:::pipeline
    Commons["Commons & Shared Utilities"]:::util
    Modules["Modules\n(Fetchers, Extractors, Deciderules, Writers, Seeds, Net)"]:::modules
    Contrib["Contrib Extensions\n(AMQP/Kafka, Reporting)"]:::modules
    Config["Configuration\n(Spring Beans, XML/Groovy)"]:::config
    Packaging["Packaging & Deployment\n(Docker & Distribution Scripts)"]:::packaging
    Docs["Documentation"]:::packaging

    UI_REST -->|submits jobs, queries status| Engine_Core
    Engine_Core -->|enqueue seeds| Frontier
    Frontier -->|dispatch URIs| Prefetch
    Prefetch -->|fetch responses| Processing
    Processing -->|write records| Writers
    Processing -->|new URIs| Frontier
    Processing -->|emit events| Contrib
    Contrib -->|publish/subscribe| Frontier
    Contrib -->|publish/subscribe| Processing
    Engine_Core --> Commons
    Frontier --> Commons
    Prefetch --> Commons
    Modules --> Prefetch
    Modules --> Processing
    Engine_Core --> Modules
    Engine_Core --> Config
    Config --> Engine_Core
    Packaging -->|contains| Docs

    click UI_REST "https://github.com/internetarchive/heritrix3/tree/master/engine/src/main/java/org/archive/crawler/restlet"
    click UI_REST "https://github.com/internetarchive/heritrix3/tree/master/engine/src/main/resources/org/archive/crawler/restlet"
    click Engine_Core "https://github.com/internetarchive/heritrix3/tree/master/engine/src/main/java/org/archive/crawler/framework"
    click Frontier "https://github.com/internetarchive/heritrix3/tree/master/engine/src/main/java/org/archive/crawler/frontier"
    click Prefetch "https://github.com/internetarchive/heritrix3/tree/master/engine/src/main/java/org/archive/crawler/prefetch"
    click Processing "https://github.com/internetarchive/heritrix3/tree/master/engine/src/main/java/org/archive/crawler/processor"
    click Processing "https://github.com/internetarchive/heritrix3/tree/master/engine/src/main/java/org/archive/crawler/postprocessor"
    click Commons "https://github.com/internetarchive/heritrix3/tree/master/commons/src/main/java/org/archive"
    click Commons "https://github.com/internetarchive/heritrix3/tree/master/commons/src/main/java/org/archive/bdb"
    click Commons "https://github.com/internetarchive/heritrix3/tree/master/commons/src/main/java/org/archive/checkpointing"
    click Commons "https://github.com/internetarchive/heritrix3/tree/master/commons/src/main/java/org/archive/io"
    click Modules "https://github.com/internetarchive/heritrix3/tree/master/modules/src/main/java/org/archive/modules"
    click Modules "https://github.com/internetarchive/heritrix3/tree/master/modules/src/main/java/org/archive/modules/fetcher"
    click Modules "https://github.com/internetarchive/heritrix3/tree/master/modules/src/main/java/org/archive/modules/extractor"
    click Modules "https://github.com/internetarchive/heritrix3/tree/master/modules/src/main/java/org/archive/modules/canonicalize"
    click Modules "https://github.com/internetarchive/heritrix3/tree/master/modules/src/main/java/org/archive/modules/deciderules"
    click Modules "https://github.com/internetarchive/heritrix3/tree/master/modules/src/main/java/org/archive/modules/writer"
    click Modules "https://github.com/internetarchive/heritrix3/tree/master/modules/src/main/java/org/archive/modules/recrawl"
    click Modules "https://github.com/internetarchive/heritrix3/tree/master/modules/src/main/java/org/archive/modules/revisit"
    click Modules "https://github.com/internetarchive/heritrix3/tree/master/modules/src/main/java/org/archive/modules/seeds"
    click Modules "https://github.com/internetarchive/heritrix3/tree/master/modules/src/main/java/org/archive/modules/net"
    click Contrib "https://github.com/internetarchive/heritrix3/tree/master/contrib/src/main/java/org/archive"
    click Contrib "https://github.com/internetarchive/heritrix3/tree/master/contrib/src/main/java/org/archive/crawler/event"
    click Contrib "https://github.com/internetarchive/heritrix3/tree/master/contrib/src/main/java/org/archive/crawler/frontier"
    click Contrib "https://github.com/internetarchive/heritrix3/tree/master/contrib/src/main/java/org/archive/crawler/prefetch"
    click Contrib "https://github.com/internetarchive/heritrix3/tree/master/contrib/src/main/java/org/archive/crawler/reporting"
    click Config "https://github.com/internetarchive/heritrix3/tree/master/engine/src/main/java/org/archive/crawler/spring"
    click Packaging "https://github.com/internetarchive/heritrix3/tree/master/docker/Dockerfile"
    click Packaging "https://github.com/internetarchive/heritrix3/blob/master/docker/docker-compose.yml"
    click Packaging "https://github.com/internetarchive/heritrix3/blob/master/docker/entrypoint.sh"
    click Packaging "https://github.com/internetarchive/heritrix3/tree/master/dist/src/main/bin"
    click Packaging "https://github.com/internetarchive/heritrix3/tree/master/dist/src/main/conf"
    click Docs "https://github.com/internetarchive/heritrix3/tree/master/docs/"
    click Docs "https://github.com/internetarchive/heritrix3/blob/master/docs/_ext/beandoc.py"

    classDef ui fill:#AED6F1,stroke:#217DBB;
    classDef core fill:#ABEBC6,stroke:#28B463;
    classDef pipeline fill:#FCF3CF,stroke:#F4D03F;
    classDef modules fill:#FAD7A0,stroke:#E67E22;
    classDef util fill:#D5D8DC,stroke:#808B96;
    classDef config fill:#F5B7B1,stroke:#C0392B;
    classDef packaging fill:#D6EAF8,stroke:#5DADE2;
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
