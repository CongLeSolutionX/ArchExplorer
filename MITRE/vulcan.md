---
created: 2025-06-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/mitre/vulcan
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

# vulcan repo project
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

---

```mermaid
---
title: "vulcan repo project"
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
  subgraph "Presentation Layer"
    direction TB
    Browser["Browser<br/>(Vue.js Front End)"]:::front
    VueComp["Vue.js Front End Components"]:::front
    Webpack["Vue.js Entry Points<br/>(Webpack packs)"]:::front
    Channels["WebSocket (ActionCable) Channels"]:::front
  end

  subgraph "Application Layer"
    direction TB
    Puma["Puma Rails Web Server"]:::app
    Controllers["Rails MVC<br/>Controllers"]:::app
    Models["Rails MVC<br/>Models"]:::app
    Views["Rails MVC<br/>Views"]:::app
    ActionCableServer["ActionCable Server"]:::app
    RakePull["Rake Task<br/>STIG/SRG Puller"]:::app
    RakeCCI["Rake Task<br/>CCI Mapping"]:::app
    XCCDF["XCCDF Parsing Library"]:::app
    DeviseInit["Devise Authentication<br/>Initializer"]:::app
    LDAPView["Devise Views &<br/>LDAP Support"]:::app
    OCIDHelper["OIDC Auto-Discovery Helper"]:::app
    OmniauthCB["OmniAuth Callbacks<br/>Controller"]:::app
    SlackInit["Slack API<br/>Integration Initializer"]:::app
    SlackHelper["Slack Notification<br/>Helpers"]:::app
    SMTPInit["SMTP Settings<br/>Initializer"]:::app
    UserMailer["User Mailer"]:::app
  end

  subgraph "Data Layer"
direction TB
    Postgres["PostgreSQL DB"]:::data
    Redis["Redis<br/>(ActionCable)"]:::data
    Storage["ActiveStorage"]:::data
  end

  subgraph "External Systems"
direction TB
    OIDC["OIDC/OKTA/Auth0 Provider"]:::ext
    LDAP["LDAP Server"]:::ext
    GitHub["GitHub OAuth"]:::ext
    SlackAPI["Slack API"]:::ext
    SMTP["SMTP Server"]:::ext
    PublicSTIG["public.cyber.mil STIG/SRG Endpoint"]:::ext
  end

  %% Connections
  Browser -->|"HTTP(S) requests"| Puma
  Browser -->|WebSocket| ActionCableServer
  VueComp --> Browser
  Webpack --> Browser
  Channels --> Browser

  Puma -->|routes to| Controllers
  Controllers -->|accesses| Models
  Controllers -->|renders| Views
  Puma -->|serves assets| Webpack
  ActionCableServer -->|pub/sub| Redis
  Puma -->|pub/sub| Redis
  Controllers -->|reads/writes| Postgres

  RakePull -->|pulls data from| PublicSTIG
  RakePull -->|stores data in| Postgres
  RakePull -->|uses| XCCDF

  RakeCCI -->|stores mappings in| Postgres

  Controllers -->|auth via| OIDC
  OCIDHelper -->|discovers endpoints| OIDC
  Controllers -->|auth via| LDAP
  Controllers -->|oauth via| GitHub
  Controllers -->|sends notifications to| SlackAPI
  SlackHelper -->|posts messages to| SlackAPI
  Controllers -->|sends emails via| SMTP
  UserMailer -->|delivers via| SMTP

  Controllers -->|stores files in| Storage
  Storage -->|backing store| Postgres

  %% Click Events
  click Controllers "https://github.com/mitre/vulcan/tree/master/app/controllers/"
  click Models "https://github.com/mitre/vulcan/tree/master/app/models/"
  click Views "https://github.com/mitre/vulcan/tree/master/app/views/"
  click VueComp "https://github.com/mitre/vulcan/tree/master/app/javascript/components/"
  click Webpack "https://github.com/mitre/vulcan/tree/master/app/javascript/packs/"
  click Channels "https://github.com/mitre/vulcan/tree/master/app/javascript/channels/"
  click Channels "https://github.com/mitre/vulcan/blob/master/config/cable.yml"
  click Puma "https://github.com/mitre/vulcan/blob/master/config/puma.rb"
  click Postgres "https://github.com/mitre/vulcan/blob/master/config/database.yml"
  click Postgres "https://github.com/mitre/vulcan/tree/master/db/migrate/"
  click Storage "https://github.com/mitre/vulcan/blob/master/config/storage.yml"
  click Redis "https://github.com/mitre/vulcan/blob/master/config/cable.yml"
  click RakePull "https://github.com/mitre/vulcan/blob/master/lib/tasks/stig_and_srg_puller.rake"
  click RakeCCI "https://github.com/mitre/vulcan/blob/master/lib/tasks/cci_tasks.rake"
  click XCCDF "https://github.com/mitre/vulcan/tree/master/lib/xccdf/"
  click DeviseInit "https://github.com/mitre/vulcan/blob/master/config/initializers/devise.rb"
  click LDAPView "https://github.com/mitre/vulcan/blob/master/app/views/devise/sessions/_ldap.html.haml"
  click OCIDHelper "https://github.com/mitre/vulcan/blob/master/app/controllers/concerns/oidc_discovery_helper.rb"
  click OCIDHelper "https://github.com/mitre/vulcan/blob/master/config/initializers/oidc_startup_validation.rb"
  click OmniauthCB "https://github.com/mitre/vulcan/blob/master/app/controllers/users/omniauth_callbacks_controller.rb"
  click SlackInit "https://github.com/mitre/vulcan/blob/master/config/initializers/slack.rb"
  click SlackHelper "https://github.com/mitre/vulcan/blob/master/app/helpers/slack_notifications_helper.rb"
  click SMTPInit "https://github.com/mitre/vulcan/blob/master/config/initializers/smtp_settings.rb"
  click UserMailer "https://github.com/mitre/vulcan/blob/master/app/mailers/user_mailer.rb"
  click Dockerfile "https://github.com/mitre/vulcan/tree/master/Dockerfile"
  click DockerCompose "https://github.com/mitre/vulcan/blob/master/docker-compose.yml"
  click DockerComposeDev "https://github.com/mitre/vulcan/blob/master/docker-compose.dev.yml"
  click Kubernetes "https://github.com/mitre/vulcan/tree/master/docs/k8s/"

  %% Styles
  classDef front fill:#D0E6FF,stroke:#0366D6,color:#0366D6,stroke-width:1px
  classDef app fill:#E6FFEA,stroke:#28A745,color:#28A745,stroke-width:1px
  classDef data fill:#FFF4E6,stroke:#D69E31,color:#D69E31,stroke-width:1px
  classDef ext fill:#EDEDED,stroke:#6A737D,color:#6A737D,stroke-width:1px

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