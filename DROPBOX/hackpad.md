---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/dropbox/hackpad
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




# hackpad repo project
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



---

```mermaid
---
title: "hackpad repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright © 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
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
flowchart LR
    subgraph "Public Internet"
        Browser["Web Browser"]:::client
        IOS["iOS App"]:::client
        Mac["macOS App"]:::client
    end

    LB["Load Balancer / Proxy"]:::server

    subgraph "Application Layer"
        NodeCluster["Etherpad Node.js Cluster"]:::server
        OOService["OpenOffice Conversion Service"]:::server
    end

    StaticCDN["Static CDN / Asset Server"]:::server

    subgraph "Data Layer"
        MySQL[(MySQL<br/>3306)]:::database
        Solr[(Solr<br/>9001)]:::database
        Memcached[(Memcached)]:::database
    end

    subgraph "Background Jobs"
        Cron["Cron Scripts"]:::server
        Runit["Runit Wrappers"]:::server
        RunSh["Shell Wrapper"]:::server
    end

    subgraph "External Services"
        OAuth["OAuth2 Providers"]:::external
        Dropbox["Dropbox Sync"]:::external
        APNs["APNs Service"]:::external
        Stripe["Stripe Billing"]:::external
        Email["Email Gateway"]:::external
        Analytics["Analytics"]:::external
    end

    Browser -->|HTTPS| LB
    IOS -->|HTTPS| LB
    Mac -->|HTTPS| LB

    LB -->|routes traffic| NodeCluster
    LB -->|serves static| StaticCDN

    NodeCluster -->|read/write| MySQL
    NodeCluster -->|index/search| Solr
    NodeCluster -->|cache| Memcached
    NodeCluster -->|RPC/HTTP| OOService
    NodeCluster -->|trigger jobs| Cron
    NodeCluster -->|trigger jobs| Runit
    NodeCluster -->|trigger jobs| RunSh
    NodeCluster -->|OAuth2 auth| OAuth
    NodeCluster -->|sync| Dropbox
    NodeCluster -->|push| APNs
    NodeCluster -->|billing| Stripe
    NodeCluster -->|send emails| Email
    NodeCluster -->|track events| Analytics

    click Browser "https://github.com/dropbox/hackpad/tree/master/etherpad/src/static"
    click IOS "https://github.com/dropbox/hackpad/tree/master/client/ios/Hackpad"
    click Mac "https://github.com/dropbox/hackpad/tree/master/client/osx/Hackpad"
    click LB "https://github.com/dropbox/hackpad/blob/master/contrib/nginx.conf"
    click LB "https://github.com/dropbox/hackpad/blob/master/bin/docker-entrypoint.sh"
    click NodeCluster "https://github.com/dropbox/hackpad/blob/master/etherpad/src/main.js"
    click OOService "https://github.com/dropbox/hackpad/blob/master/infrastructure/com.etherpad.openofficeservice"
    click MySQL "https://github.com/dropbox/hackpad/tree/master/etherpad/src/etherpad/db_migrations"
    click Solr "https://github.com/dropbox/hackpad/tree/master/etherpad/solr/collection1"
    click Memcached "https://github.com/dropbox/hackpad/blob/master/infrastructure/lib/memcached-2.6rc1.jar"
    click Cron "https://github.com/dropbox/hackpad/tree/master/contrib/cron/cron.daily/etherpad-remove-ooconvert"
    click Runit "https://github.com/dropbox/hackpad/tree/master/contrib/runit/run"
    click RunSh "https://github.com/dropbox/hackpad/blob/master/bin/run.sh"
    click OAuth "https://github.com/dropbox/hackpad/blob/master/infrastructure/framework-src/modules/oauth.js"
    click Dropbox "https://github.com/dropbox/hackpad/blob/master/etherpad/src/etherpad/importexport/dropbox.js"
    click APNs "https://github.com/dropbox/hackpad/blob/master/etherpad/src/etherpad/pro/pro_apns.js"
    click Stripe "https://github.com/dropbox/hackpad/blob/master/etherpad/src/etherpad/db_migrations/m0058_add_stripeJson.js"
    click Email "https://github.com/dropbox/hackpad/blob/master/infrastructure/framework-src/modules/email.js"
    click Analytics "https://github.com/dropbox/hackpad/tree/master/etherpad/src/etherpad/statistics"

    classDef client fill:#add8e6,stroke:#000,stroke-width:1px
    classDef server fill:#90ee90,stroke:#000,stroke-width:1px
    classDef database fill:#ffa500,stroke:#000,stroke-width:1px
    classDef external fill:#dda0dd,stroke:#000,stroke-width:1px

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