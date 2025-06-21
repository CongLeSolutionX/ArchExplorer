---
created: 2025-06-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/fbsamples/f8app
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




# f8app repo project
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
----



```mermaid
---
title: "f8app repo project"
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
    subgraph "Mobile Clients"
        subgraph iOS
            iOSNative["ios/"]:::mobile
            iOSEntry["index.ios.js"]:::mobile
        end
        subgraph Android
            AndroidNative["android/"]:::mobile
            AndroidEntry["index.android.js"]:::mobile
        end
    end

    subgraph "React Native App"
        UIComponents["Presentation & UI Components\n(js/)"]:::frontend
        ReduxStore["Redux Store\n(js/store/, js/reducers/)"]:::frontend
        RelayClient["Relay Environment\n(js/relay-environment.js)"]:::frontend
        PushController["Push & Device Services\n(js/PushNotificationsController.js)"]:::frontend
        Analytics["Analytics Tracking\n(js/F8Analytics.js, js/store/analytics.js)"]:::frontend
    end

    subgraph "Backend Services"
        GraphQLService["GraphQL Service\n(server/graphql/)"]:::backend
        ParseServer["Parse Server\n(server/parse-server/)"]:::backend
        ParseDashboard["Parse Dashboard\n(server/parse-dashboard/)"]:::backend
        Mongo["MongoDB\n(server/mongorestore/)"]:::db
    end

    subgraph "External Services"
        PushGateways["Push Gateways\n(APNs, FCM)"]:::external
        AnalyticsEndpoints["Analytics Endpoints"]:::external
    end

    subgraph "DevOps & CI/CD"
        DockerCompose["docker-compose.yml"]:::ops
        Scripts["scripts/"]:::ops
        CICD[".circleci/config.yml"]:::ops
    end

    iOSNative --> iOSEntry
    AndroidNative --> AndroidEntry
    iOSEntry --> UIComponents
    AndroidEntry --> UIComponents
    UIComponents --> ReduxStore
    ReduxStore --> RelayClient
    RelayClient -->|GraphQL Queries/Mutations| GraphQLService
    GraphQLService -->|Resolve via SDK| ParseServer
    ParseServer -->|CRUD| Mongo
    RelayClient -->|Push Registration| ParseServer
    PushController -->|Push APIs| ParseServer
    ParseServer -->|Push Delivery| PushGateways
    Analytics -->|Track Events| AnalyticsEndpoints
    GraphQLService --> ParseServer
    DockerCompose --> GraphQLService
    DockerCompose --> ParseServer
    DockerCompose --> ParseDashboard
    DockerCompose --> Mongo
    CICD --> Scripts
    Scripts --> UIComponents
    Scripts --> GraphQLService
    Scripts --> ParseServer

    classDef mobile fill:#b7e4c7,stroke:#2b7a0b
    classDef frontend fill:#a0c4ff,stroke:#034078
    classDef backend fill:#ffd6a5,stroke:#bb3e03
    classDef db fill:#ffadad,stroke:#730000
    classDef ops fill:#eeeeee,stroke:#555555
    classDef external fill:#d3d3d3,stroke:#666666

    click AndroidNative "https://github.com/fbsamples/f8app/tree/main/android/"
    click iOSNative "https://github.com/fbsamples/f8app/tree/main/ios/"
    click iOSEntry "https://github.com/fbsamples/f8app/blob/main/index.ios.js"
    click AndroidEntry "https://github.com/fbsamples/f8app/blob/main/index.android.js"
    click UIComponents "https://github.com/fbsamples/f8app/tree/main/js/"
    click ReduxStore "https://github.com/fbsamples/f8app/tree/main/js/store/"
    click RelayClient "https://github.com/fbsamples/f8app/blob/main/js/relay-environment.js"
    click PushController "https://github.com/fbsamples/f8app/blob/main/js/PushNotificationsController.js"
    click Analytics "https://github.com/fbsamples/f8app/blob/main/js/F8Analytics.js"
    click AnalyticsEndpoints "https://github.com/fbsamples/f8app/blob/main/js/store/analytics.js"
    click Scripts "https://github.com/fbsamples/f8app/tree/main/scripts/"
    click DockerCompose "https://github.com/fbsamples/f8app/blob/main/docker-compose.yml"
    click CICD "https://github.com/fbsamples/f8app/blob/main/.circleci/config.yml"
    click GraphQLService "https://github.com/fbsamples/f8app/tree/main/server/graphql/"
    click ParseServer "https://github.com/fbsamples/f8app/tree/main/server/parse-server/"
    click ParseDashboard "https://github.com/fbsamples/f8app/tree/main/server/parse-dashboard/"
    click Mongo "https://github.com/fbsamples/f8app/tree/main/server/mongorestore/"
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