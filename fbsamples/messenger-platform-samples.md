---
created: 2025-06-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/fbsamples/messenger-platform-samples
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




# messenger-platform-samples repo project
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
title: "messenger-platform-samples repo project"
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
    %% External User and Platform
    User[/"User"/]:::external
    MessengerPlatform(("Facebook Messenger Platform")):::external
    Postman[/"Postman Collections"/]:::postman

    User -->|"Sends Message"| MessengerPlatform
    Postman -->|"Simulates Webhook/API"| MessengerPlatform

    %% Quick-start Service
    subgraph "Quick-start Express Service" 
        QSApp["Express Bot /quick-start/app.js"]:::node
        QSPkg["package.json"]:::util
    end
    MessengerPlatform -->|"/webhook"| QSApp
    QSApp -->|"Calls Graph API"| MessengerPlatform
    click QSApp "https://github.com/fbsamples/messenger-platform-samples/blob/main/quick-start/app.js"
    click QSPkg "https://github.com/fbsamples/messenger-platform-samples/blob/main/quick-start/package.json"

    %% Node.js Sample Service
    subgraph "Node.js Sample Service" 
        NodeApp["Express Bot /node/app.js"]:::node
        NodeConfig["config/default.json"]:::util
        NodeView["authorize.ejs"]:::util
        NodeAssets["public/ (assets & index.html)"]:::util
        NodePkg["package.json"]:::util
    end
    MessengerPlatform -->|"/webhook"| NodeApp
    NodeApp -->|"Calls Graph API"| MessengerPlatform
    click NodeApp "https://github.com/fbsamples/messenger-platform-samples/blob/main/node/app.js"
    click NodeConfig "https://github.com/fbsamples/messenger-platform-samples/blob/main/node/config/default.json"
    click NodeView "https://github.com/fbsamples/messenger-platform-samples/blob/main/node/views/authorize.ejs"
    click NodeAssets "https://github.com/fbsamples/messenger-platform-samples/tree/main/node/public/"
    click NodePkg "https://github.com/fbsamples/messenger-platform-samples/blob/main/node/package.json"

    %% Handover Protocol Demo
    subgraph "Handover Protocol Demo"
        HPApp["Bot App /handover_protocol/index.js"]:::node
        HPPkg["package.json"]:::util
        subgraph "Utils"
            APIUtil["api.js"]:::util
            HPUtil["handover-protocol.js"]:::util
            QRUtil["quick-reply.js"]:::util
        end
    end
    MessengerPlatform -->|"/webhook"| HPApp
    HPApp -->|"Uses Utilities"| APIUtil
    HPApp -->|"Uses Utilities"| HPUtil
    HPApp -->|"Uses Utilities"| QRUtil
    HPApp -->|"Graph API: Handover"| MessengerPlatform
    click HPApp "https://github.com/fbsamples/messenger-platform-samples/blob/main/handover_protocol/index.js"
    click HPPkg "https://github.com/fbsamples/messenger-platform-samples/blob/main/handover_protocol/package.json"
    click APIUtil "https://github.com/fbsamples/messenger-platform-samples/blob/main/handover_protocol/utils/api.js"
    click HPUtil "https://github.com/fbsamples/messenger-platform-samples/blob/main/handover_protocol/utils/handover-protocol.js"
    click QRUtil "https://github.com/fbsamples/messenger-platform-samples/blob/main/handover_protocol/utils/quick-reply.js"

    %% Inter-page Bots
    subgraph "Inter-page Bots"
        subgraph Marketing
            MApp["marketing-bot/app.js"]:::node
            MPkg["package.json"]:::util
        end
        subgraph Support
            SApp["support-bot/app.js"]:::node
            SPkg["package.json"]:::util
        end
    end
    MessengerPlatform -->|"/webhook"| MApp
    MessengerPlatform -->|"/webhook"| SApp
    MApp -->|"Thread Control Handover"| SApp
    MApp -->|"Calls Graph API"| MessengerPlatform
    SApp -->|"Calls Graph API"| MessengerPlatform
    click MApp "https://github.com/fbsamples/messenger-platform-samples/blob/main/inter-page/marketing-bot/app.js"
    click MPkg "https://github.com/fbsamples/messenger-platform-samples/blob/main/inter-page/marketing-bot/package.json"
    click SApp "https://github.com/fbsamples/messenger-platform-samples/blob/main/inter-page/support-bot/app.js"
    click SPkg "https://github.com/fbsamples/messenger-platform-samples/blob/main/inter-page/support-bot/package.json"

    %% Messenger-API Demos
    subgraph "Messenger-API Demos"
        %% Python
        subgraph "Python Flask Demo" 
            PyApp["app.py"]:::python
            PyLib["messenger_platform.py"]:::python
        end
        %% Node.js JS
        subgraph "Node.js JavaScript Version"
            JSIndex["index.js"]:::node
            JSLib["messenger.js"]:::node
            JSPkg["package.json"]:::util
        end
        %% Node.js TS
        subgraph "Node.js TypeScript Version"
            TSIndex["index.ts"]:::node
            TSLib["messenger.ts"]:::node
            TSConfig["tsconfig.json"]:::util
            TSPkg["package.json"]:::util
        end
        %% Java
        subgraph "Java Service"
            JavaMain["Main.java"]:::java
            JavaSend["MessageSender.java"]:::java
            JavaPom["pom.xml"]:::util
        end
    end
    MessengerPlatform -->|"/webhook"| PyApp
    MessengerPlatform -->|"/webhook"| JSIndex
    MessengerPlatform -->|"/webhook"| TSIndex
    MessengerPlatform -->|"/webhook"| JavaMain
    PyApp -->|"Calls Graph API"| MessengerPlatform
    JSIndex -->|"Calls Graph API"| MessengerPlatform
    TSIndex -->|"Calls Graph API"| MessengerPlatform
    JavaMain -->|"Calls Graph API"| MessengerPlatform
    click PyApp "https://github.com/fbsamples/messenger-platform-samples/blob/main/messenger-api/messenger-api-and-webhooks/app.py"
    click PyLib "https://github.com/fbsamples/messenger-platform-samples/blob/main/messenger-api/messenger-api-with-python/messenger_platform.py"
    click JSIndex "https://github.com/fbsamples/messenger-platform-samples/blob/main/messenger-api/messenger-api-with-nodejs/javascript-version/index.js"
    click JSLib "https://github.com/fbsamples/messenger-platform-samples/blob/main/messenger-api/messenger-api-with-nodejs/javascript-version/messenger.js"
    click JSPkg "https://github.com/fbsamples/messenger-platform-samples/blob/main/messenger-api/messenger-api-with-nodejs/javascript-version/package.json"
    click TSIndex "https://github.com/fbsamples/messenger-platform-samples/blob/main/messenger-api/messenger-api-with-nodejs/typescript-version/src/index.ts"
    click TSLib "https://github.com/fbsamples/messenger-platform-samples/blob/main/messenger-api/messenger-api-with-nodejs/typescript-version/src/messenger.ts"
    click TSConfig "https://github.com/fbsamples/messenger-platform-samples/blob/main/messenger-api/messenger-api-with-nodejs/typescript-version/tsconfig.json"
    click TSPkg "https://github.com/fbsamples/messenger-platform-samples/blob/main/messenger-api/messenger-api-with-nodejs/typescript-version/package.json"
    click JavaMain "https://github.com/fbsamples/messenger-platform-samples/blob/main/messenger-api/messenger-api-with-java/src/main/java/org/example/Main.java"
    click JavaSend "https://github.com/fbsamples/messenger-platform-samples/blob/main/messenger-api/messenger-api-with-java/src/main/java/org/example/MessageSender.java"
    click JavaPom "https://github.com/fbsamples/messenger-platform-samples/blob/main/messenger-api/messenger-api-with-java/pom.xml"

    %% Webview Host Service
    subgraph "Webview Host Service"
        WVApp["app.js"]:::node
        WVPkg["package.json"]:::util
        WVDotEnv[".env"]:::util
        WVPage["options.html"]:::util
    end
    MessengerPlatform -->|"/webview"| WVApp
    WVApp -->|"Serves Page"| WVPage
    click WVApp "https://github.com/fbsamples/messenger-platform-samples/blob/main/webview/app.js"
    click WVPkg "https://github.com/fbsamples/messenger-platform-samples/blob/main/webview/package.json"
    click WVDotEnv "https://github.com/fbsamples/messenger-platform-samples/blob/main/webview/.env"
    click WVPage "https://github.com/fbsamples/messenger-platform-samples/blob/main/webview/public/options.html"

    %% CI/CD & API Testing
    subgraph "CI/CD & API Testing"
        GHAction["postman-sync.yaml"]:::util
        PM1["messenger-platform-api.postman_collection.json"]:::postman
        PM2["instagram-platform-api.postman_collection.json"]:::postman
    end
    GHAction -->|"Triggers Sync"| PM1
    GHAction -->|"Triggers Sync"| PM2
    click GHAction "https://github.com/fbsamples/messenger-platform-samples/blob/main/.github/workflows/postman-sync.yaml"
    click PM1 "https://github.com/fbsamples/messenger-platform-samples/blob/main/postman/messenger-platform-api.postman_collection.json"
    click PM2 "https://github.com/fbsamples/messenger-platform-samples/blob/main/postman/instagram-platform-api.postman_collection.json"

    %% Styles
    classDef node fill:#d5f5e3,stroke:#27ae60,stroke-width:2px
    classDef python fill:#aed6f1,stroke:#2e86c1,stroke-width:2px
    classDef java fill:#f5b7b1,stroke:#c0392b,stroke-width:2px
    classDef util fill:#d5d8dc,stroke:#7f8c8d,stroke-width:1px
    classDef external fill:#f4f6f7,stroke:#95a5a6,stroke-width:1px
    classDef postman fill:#f9e79f,stroke:#b7950b,stroke-width:1px

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