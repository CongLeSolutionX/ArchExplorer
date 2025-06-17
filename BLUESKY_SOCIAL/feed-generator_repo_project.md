---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/bluesky-social/feed-generator
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




# feed-generator repo project
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
title: "feed-generator repo project"
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
  subgraph "External Systems"
    PDS["PDS (Personal Data Server)"]:::external
    FIREHOSE["AT Protocol Firehose WS"]:::external
    ADMINAPI["AT Protocol Admin API"]:::external
  end

  subgraph "FeedGen Service"
    subgraph "API Layer"
      SERVER["XRPC Endpoint\nsrc/server.ts\nsrc/index.ts"]:::api
    end
    AUTH["Auth Middleware\nsrc/auth.ts"]:::auth
    subgraph "Controllers"
      DESC["Describe Generator Handler\nmethods/describe-generator.ts"]:::api
      FEEDGEN["Feed Generation Handler\nmethods/feed-generation.ts"]:::api
    end
    subgraph "Business Layer"
      SUB["Subscription Service\nsrc/subscription.ts"]:::business
      UTIL["Subscription Utils\nsrc/util/subscription.ts"]:::business
      ALGOINDEX["Algo Loader\nsrc/algos/index.ts"]:::business
      ALGO["Example Algorithm\nsrc/algos/whats-alf.ts"]:::business
    end
    subgraph "Data Layer"
      DBINDEX["DB Init & Migrations\nsrc/db/index.ts\nsrc/db/migrations.ts"]:::db
      SCHEMA["Schema Definitions\nsrc/db/schema.ts"]:::db
    end
    CONFIG["Configuration & DID Setup\nsrc/config.ts\nsrc/well-known.ts"]:::config
    LEXICON["Lexicon Types\nsrc/lexicon/index.ts\nsrc/lexicon/lexicons.ts\nsrc/lexicon/types/**"]:::data
  end

  subgraph "CLI Scripts"
    PUBLISH["Publish FeedGen Metadata\nscripts/publishFeedGen.ts"]:::scripts
    UNPUBLISH["Unpublish FeedGen Metadata\nscripts/unpublishFeedGen.ts"]:::scripts
  end

  PDS -->|"getFeedSkeleton (HTTPS + JWT)"| SERVER
  SERVER -->|"route request"| DESC
  SERVER -->|"route request"| FEEDGEN
  SERVER -->|"validate JWT"| AUTH
  AUTH -->|" "| FEEDGEN

  FEEDGEN -->|"load algorithm"| ALGOINDEX
  ALGOINDEX -->|"execute"| ALGO
  FEEDGEN -->|"query index"| DBINDEX
  ALGO -->|"read/write index"| DBINDEX

  SUB -->|"write events"| DBINDEX
  FIREHOSE -->|"subscribeRepos WS"| SUB
  CONFIG -->|"initialize"| DBINDEX
  CONFIG -->|"load config"| SERVER
  CONFIG -->|"load config"| SUB

  PUBLISH -->|"publish feed metadata"| ADMINAPI
  UNPUBLISH -->|"unpublish feed metadata"| ADMINAPI

  classDef external fill:#f2f2f2,stroke:#ccc;
  classDef api fill:#d0e8ff,stroke:#5b9bd5;
  classDef auth fill:#cfe2f3,stroke:#6fa8dc;
  classDef business fill:#e2f0d9,stroke:#82b366;
  classDef db fill:#d9ead3,stroke:#6aa84f,stroke-width:2px;
  classDef data fill:#d9ead3,stroke:#6aa84f;
  classDef config fill:#fff2cc,stroke:#e69138;
  classDef scripts fill:#fde9d9,stroke:#e06666;

  click SERVER "https://github.com/bluesky-social/feed-generator/blob/main/src/server.ts"
  click SERVER "https://github.com/bluesky-social/feed-generator/blob/main/src/index.ts"
  click AUTH "https://github.com/bluesky-social/feed-generator/blob/main/src/auth.ts"
  click DESC "https://github.com/bluesky-social/feed-generator/blob/main/src/methods/describe-generator.ts"
  click FEEDGEN "https://github.com/bluesky-social/feed-generator/blob/main/src/methods/feed-generation.ts"
  click ALGOINDEX "https://github.com/bluesky-social/feed-generator/blob/main/src/algos/index.ts"
  click ALGO "https://github.com/bluesky-social/feed-generator/blob/main/src/algos/whats-alf.ts"
  click SUB "https://github.com/bluesky-social/feed-generator/blob/main/src/subscription.ts"
  click UTIL "https://github.com/bluesky-social/feed-generator/blob/main/src/util/subscription.ts"
  click DBINDEX "https://github.com/bluesky-social/feed-generator/blob/main/src/db/index.ts"
  click DBINDEX "https://github.com/bluesky-social/feed-generator/blob/main/src/db/migrations.ts"
  click SCHEMA "https://github.com/bluesky-social/feed-generator/blob/main/src/db/schema.ts"
  click CONFIG "https://github.com/bluesky-social/feed-generator/blob/main/src/config.ts"
  click CONFIG "https://github.com/bluesky-social/feed-generator/blob/main/src/well-known.ts"
  click LEXICON "https://github.com/bluesky-social/feed-generator/blob/main/src/lexicon/index.ts"
  click LEXICON "https://github.com/bluesky-social/feed-generator/blob/main/src/lexicon/lexicons.ts"
  click LEXICON "https://github.com/bluesky-social/feed-generator/tree/main/src/lexicon/types"
  click PUBLISH "https://github.com/bluesky-social/feed-generator/blob/main/scripts/publishFeedGen.ts"
  click UNPUBLISH "https://github.com/bluesky-social/feed-generator/blob/main/scripts/unpublishFeedGen.ts"
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