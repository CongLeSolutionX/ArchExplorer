---
created: 2025-06-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/fbsamples/messenger-bot-samples
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




# messenger-bot-samples repo project
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
title: "messenger-bot-samples repo project"
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
    %% External Service
    FB["Facebook Messenger Platform"]:::external

    %% Account-Linking Sample
    subgraph "Account-Linking Sample"
        direction TB
        AL_Server["Express Server (app.js)"]:::transport
        AL_Webhook["Webhook Controller"]:::transport
        AL_Biz["Business Logic (models & stores)"]:::business
        AL_Integration["Messenger-API-Helpers"]:::integration
        AL_Data["In-Memory Store"]:::data
        AL_UI["Frontend/UI (public & views)"]:::frontend

        AL_Server -->|“POST /webhook”| AL_Webhook
        AL_Webhook -->|invokes| AL_Biz
        AL_Biz -->|reads/writes| AL_Data
        AL_Biz -->|calls| AL_Integration
        AL_Integration -->|Graph API calls| FB
        AL_Server -->|serves| AL_UI
    end

    %% Chat-Extensions Sample
    subgraph "Chat-Extensions Sample"
        direction TB
        CE_Server["Express Server (app.js & bin/www)"]:::transport
        CE_Webhook["Webhook Controller"]:::transport
        CE_Biz["Business Logic (models)"]:::business
        CE_Data["Knex DB"]:::data
        CE_Integration["Messenger-API-Helpers"]:::integration
        CE_WS["WebSocket Layer"]:::transport
        CE_UI["Client React & Views"]:::frontend

        CE_Server -->|“POST /webhook”| CE_Webhook
        CE_Webhook -->|invokes| CE_Biz
        CE_Biz -->|reads/writes| CE_Data
        CE_Biz -->|calls| CE_Integration
        CE_Integration -->|Graph API calls| FB
        CE_Server -->|serves| CE_UI
        CE_WS <-->|real-time updates| CE_UI
        CE_Biz -->|emits| CE_WS
    end

    %% Chat-Plugin-Autodetect Sample
    subgraph "Chat-Plugin-Autodetect Sample"
        direction TB
        CP_Server["Express Server (app.js)"]:::transport
        CP_Router["Routing Layer"]:::transport
        CP_UI["Static UI & Views"]:::frontend

        FB -->|loads plugin| CP_Server
        CP_Server -->|routes| CP_Router
        CP_Router -->|serves| CP_UI
    end

    %% Customer-Care-CSAT Sample
    subgraph "Customer-Care-CSAT Sample"
        direction TB
        CC_Server["Express Server (index.js)"]:::transport
        CC_Biz["Business Logic (bot & payloads)"]:::business
        CC_Integration["Messenger-API-Helpers"]:::integration
        CC_Config["Config (sample.config.js)"]:::data

        FB -->|“POST /webhook”| CC_Server
        CC_Server -->|invokes| CC_Biz
        CC_Biz -->|uses| CC_Config
        CC_Biz -->|calls| CC_Integration
        CC_Integration -->|Graph API calls| FB
    end

    %% GUI-Webview Sample
    subgraph "GUI-Webview Sample"
        direction TB
        GUI_Server["Express Server (app.js & bin/www)"]:::transport
        GUI_Webhook["Webhook Controller"]:::transport
        GUI_Biz["Business Logic (models & stores)"]:::business
        GUI_Integration["Messenger-API-Helpers"]:::integration
        GUI_UI["React SPA & Views"]:::frontend
        GUI_Data["Stores (data)"]:::data
        GUI_Util["Utils & Build Config"]:::data

        FB -->|“POST /webhook”| GUI_Server
        GUI_Server -->|routes| GUI_Webhook
        GUI_Webhook -->|invokes| GUI_Biz
        GUI_Biz -->|reads/writes| GUI_Data
        GUI_Biz -->|calls| GUI_Integration
        GUI_Integration -->|Graph API calls| FB
        GUI_Server -->|serves| GUI_UI
        GUI_Util -.-> GUI_UI

    end

    %% Click Events Account-Linking
    click AL_Server "https://github.com/fbsamples/messenger-bot-samples/blob/master/account-linking/app.js"
    click AL_Webhook "https://github.com/fbsamples/messenger-bot-samples/blob/master/account-linking/routes/webhooks.js"
    click AL_Integration "https://github.com/fbsamples/messenger-bot-samples/tree/master/account-linking/messenger-api-helpers/"
    click AL_Biz "https://github.com/fbsamples/messenger-bot-samples/blob/master/account-linking/models/user.js"
    click AL_Data "https://github.com/fbsamples/messenger-bot-samples/blob/master/account-linking/stores/store.js"
    click AL_UI "https://github.com/fbsamples/messenger-bot-samples/tree/master/account-linking/public/"
    click AL_UI "https://github.com/fbsamples/messenger-bot-samples/tree/master/account-linking/views/"

    %% Click Events Chat-Extensions
    click CE_Server "https://github.com/fbsamples/messenger-bot-samples/blob/master/chat-extensions/app.js"
    click CE_Server "https://github.com/fbsamples/messenger-bot-samples/tree/master/chat-extensions/bin/www"
    click CE_Webhook "https://github.com/fbsamples/messenger-bot-samples/blob/master/chat-extensions/routes/webhooks.js"
    click CE_Integration "https://github.com/fbsamples/messenger-bot-samples/tree/master/chat-extensions/messenger-api-helpers/"
    click CE_Data "https://github.com/fbsamples/messenger-bot-samples/blob/master/chat-extensions/db/knex.js"
    click CE_Server "https://github.com/fbsamples/messenger-bot-samples/blob/master/chat-extensions/knexfile.js"
    click CE_WS "https://github.com/fbsamples/messenger-bot-samples/blob/master/chat-extensions/sockets/index.js"
    click CE_UI "https://github.com/fbsamples/messenger-bot-samples/blob/master/chat-extensions/client/index.js"
    click CE_UI "https://github.com/fbsamples/messenger-bot-samples/blob/master/chat-extensions/public/style.css"
    click CE_UI "https://github.com/fbsamples/messenger-bot-samples/blob/master/chat-extensions/views/index.ejs"

    %% Click Events Chat-Plugin-Autodetect
    click CP_Server "https://github.com/fbsamples/messenger-bot-samples/blob/master/chat_plugin_autodetect/app.js"
    click CP_Router "https://github.com/fbsamples/messenger-bot-samples/blob/master/chat_plugin_autodetect/router.js"
    click CP_UI "https://github.com/fbsamples/messenger-bot-samples/blob/master/chat_plugin_autodetect/public/style.css"
    click CP_UI "https://github.com/fbsamples/messenger-bot-samples/blob/master/chat_plugin_autodetect/views/index.ejs"

    %% Click Events Customer-Care-CSAT
    click CC_Server "https://github.com/fbsamples/messenger-bot-samples/blob/master/customer-care-csat/index.js"
    click CC_Biz "https://github.com/fbsamples/messenger-bot-samples/blob/master/customer-care-csat/app/bot.js"
    click CC_Config "https://github.com/fbsamples/messenger-bot-samples/blob/master/customer-care-csat/config/sample.config.js"

    %% Click Events GUI-Webview
    click GUI_Server "https://github.com/fbsamples/messenger-bot-samples/blob/master/gui-webview/app.js"
    click GUI_Server "https://github.com/fbsamples/messenger-bot-samples/tree/master/gui-webview/bin/www"
    click GUI_Webhook "https://github.com/fbsamples/messenger-bot-samples/blob/master/gui-webview/routes/webhooks.js"
    click GUI_Integration "https://github.com/fbsamples/messenger-bot-samples/tree/master/gui-webview/messenger-api-helpers/"
    click GUI_Biz "https://github.com/fbsamples/messenger-bot-samples/blob/master/gui-webview/models/user.js"
    click GUI_Data "https://github.com/fbsamples/messenger-bot-samples/blob/master/gui-webview/stores/store.js"
    click GUI_UI "https://github.com/fbsamples/messenger-bot-samples/blob/master/gui-webview/client/index.js"
    click GUI_UI "https://github.com/fbsamples/messenger-bot-samples/blob/master/gui-webview/public/bundle.js"
    click GUI_Util "https://github.com/fbsamples/messenger-bot-samples/blob/master/gui-webview/utils/date-string-format.js"
    click GUI_Util "https://github.com/fbsamples/messenger-bot-samples/blob/master/gui-webview/webpack.config.js"

    %% Styles
    classDef transport fill:#cce5ff,stroke:#0066cc,color:#000;
    classDef business fill:#d4edda,stroke:#28a745,color:#000;
    classDef integration fill:#ffe5b4,stroke:#ff8c00,color:#000;
    classDef data fill:#fff3cd,stroke:#ffcd39,color:#000;
    classDef frontend fill:#e2d4f0,stroke:#800080,color:#000;
    classDef external fill:#f0f0f0,stroke:#999,color:#000;

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