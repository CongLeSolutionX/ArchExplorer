---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/bluesky-social/statusphere-example-app
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




# statusphere-example-app repo project
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
title: "statusphere-example-app repo project"
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
    %% Styles and Classes
    classDef frontend fill:#a8d1f0,stroke:#333
    classDef application fill:#90EE90,stroke:#333
    classDef external fill:#D3D3D3,stroke:#333
    classDef database fill:#FFB6C1,stroke:#333
    classDef auth fill:#FFE4B5,stroke:#333
    classDef lexicon fill:#DDA0DD,stroke:#333

    %% Frontend Layer
    subgraph Frontend
        Home["Home Page"]:::frontend
        Login["Login Page"]:::frontend
        Shell["Shell Component"]:::frontend
        Styles["Styles"]:::frontend
    end

    %% Auth Layer
    subgraph Auth
        AuthClient["Auth Client"]:::auth
        AuthStorage["Auth Storage"]:::auth
    end

    %% Application Layer
    subgraph Core
        Ingester["Data Ingester"]:::application
        IDResolver["ID Resolver"]:::application
        DBInterface["Database Interface"]:::database
        ViewLib["View Library"]:::application
        EnvUtils["Environment Utils"]:::application
        MainEntry["Main Entry"]:::application
        Routes["Route Definitions"]:::application
    end

    %% Lexicon System
    subgraph LexiconSystem
        SchemaDefinitions["Schema Definitions"]:::lexicon
        TypeImplementations["Type Implementations"]:::lexicon
        subgraph Types
            BlueskyTypes["Bluesky Types"]:::lexicon
            ATProtoTypes["AT Protocol Types"]:::lexicon
            CustomStatusTypes["Custom Status Types"]:::lexicon
        end
        subgraph Schemas
            ProfileSchema["Profile Schema"]:::lexicon
            StatusSchema["Status Schema"]:::lexicon
            StrongRefSchema["Strong Ref Schema"]:::lexicon
            DefTypes["Definition Types"]:::lexicon
        end
    end

    %% External Services
    ATProtocol[("AT Protocol")]:::external
    OAuth[("OAuth Provider")]:::external

    %% Relationships
    Login --> AuthClient
    AuthClient --> OAuth
    OAuth --> ATProtocol
    ATProtocol --> Ingester
    Ingester --> DBInterface
    Home --> ViewLib
    Shell --> ViewLib
    AuthClient --> AuthStorage
    IDResolver --> ATProtocol
    MainEntry --> Routes
    Routes --> ViewLib
    LexiconSystem --> Ingester
    LexiconSystem --> IDResolver

    %% Click Events
    click Home "https://github.com/bluesky-social/statusphere-example-app/blob/main/src/pages/home.ts"
    click Login "https://github.com/bluesky-social/statusphere-example-app/blob/main/src/pages/login.ts"
    click Shell "https://github.com/bluesky-social/statusphere-example-app/blob/main/src/pages/shell.ts"
    click Styles "https://github.com/bluesky-social/statusphere-example-app/blob/main/src/pages/public/styles.css"
    click AuthClient "https://github.com/bluesky-social/statusphere-example-app/blob/main/src/auth/client.ts"
    click AuthStorage "https://github.com/bluesky-social/statusphere-example-app/blob/main/src/auth/storage.ts"
    click SchemaDefinitions "https://github.com/bluesky-social/statusphere-example-app/tree/main/lexicons/"
    click TypeImplementations "https://github.com/bluesky-social/statusphere-example-app/tree/main/src/lexicon/"
    click BlueskyTypes "https://github.com/bluesky-social/statusphere-example-app/tree/main/src/lexicon/types/app/bsky/"
    click ATProtoTypes "https://github.com/bluesky-social/statusphere-example-app/tree/main/src/lexicon/types/com/atproto/"
    click CustomStatusTypes "https://github.com/bluesky-social/statusphere-example-app/tree/main/src/lexicon/types/xyz/statusphere/"
    click Ingester "https://github.com/bluesky-social/statusphere-example-app/blob/main/src/ingester.ts"
    click IDResolver "https://github.com/bluesky-social/statusphere-example-app/blob/main/src/id-resolver.ts"
    click DBInterface "https://github.com/bluesky-social/statusphere-example-app/blob/main/src/db.ts"
    click ViewLib "https://github.com/bluesky-social/statusphere-example-app/blob/main/src/lib/view.ts"
    click EnvUtils "https://github.com/bluesky-social/statusphere-example-app/blob/main/src/lib/env.ts"
    click MainEntry "https://github.com/bluesky-social/statusphere-example-app/blob/main/src/index.ts"
    click Routes "https://github.com/bluesky-social/statusphere-example-app/blob/main/src/routes.ts"
    click ProfileSchema "https://github.com/bluesky-social/statusphere-example-app/blob/main/lexicons/profile.json"
    click StatusSchema "https://github.com/bluesky-social/statusphere-example-app/blob/main/lexicons/status.json"
    click StrongRefSchema "https://github.com/bluesky-social/statusphere-example-app/blob/main/lexicons/strongRef.json"
    click DefTypes "https://github.com/bluesky-social/statusphere-example-app/blob/main/lexicons/defs.json"
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