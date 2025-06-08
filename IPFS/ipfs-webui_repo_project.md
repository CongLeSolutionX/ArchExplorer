---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ipfs/ipfs-webui
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExd3VwcHgzZWxnbTc3eWUwd2NpdnEwem9wdWVxemZ1eDE1aHpmZmlhdSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/N35rW3vRNeaDC/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# ipfs-webui repo project
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
title: "ipfs-webui repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'linear' },
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#222B2B',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#2221',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '20px'
    }
  }
}%%
flowchart TB
    %% UI Layer
    subgraph "Browser / User Agent"
        User["User / Browser"]:::ui
        DevServer["Dev Server / Static Host (port 3000)"]:::infra
    end

    %% React Application
    subgraph "React SPA"
        ReactApp["React App"]:::ui

        subgraph "Entry Points"
            Index["src/index.js"]:::ui
            App["src/App.js"]:::ui
        end

        subgraph "Routes"
            FilesLoad["LoadableFilesPage"]
            FilesPage["FilesPage"]
            ExploreLoad["LoadableExplorePage"]
            ExplorePage["ExploreContainer"]
            PeersLoad["LoadablePeersPage"]
            PeersPage["PeersPage"]
            SettingsLoad["LoadableSettingsPage"]
            SettingsPage["SettingsPage"]
            StatusLoad["LoadableStatusPage"]
            StatusPage["StatusPage"]
            WelcomeLoad["LoadableWelcomePage"]
            WelcomePage["WelcomePage"]
        end

        ComponentsLib["Component Library"] 
    end

    %% State Management
    subgraph "State Bundles"
        FilesBundle["Files Bundle"]:::state
        PeersBundle["Peers Bundle"]:::state
        PinningBundle["Pinning Bundle"]:::state
        RepoStatsBundle["Repo Stats Bundle"]:::state
        IdleBundle["Idle Detection Bundle"]:::state
        AnalyticsBundle["Analytics Bundle"]:::state
        APIProvider["API Provider Bundle"]:::state
    end

    %% API Layer
    subgraph "API Layer"
        RPCClient["js-kubo-rpc-client"]:::api
        CorsConfig["CORS Config Script"]:::api
    end

    %% External Services
    subgraph "External Services"
        IPFS["IPFS Node (Kubo)"]:::external
        Transifex["Transifex"]:::external
    end

    %% Internationalization
    subgraph "Internationalization"
        I18nConfig["src/i18n.js"]:::state
        I18nHelper["src/helpers/i8n.js"]:::state
        Locales["public/locales"]:::state
    end

    %% Development Tools
    subgraph "Development Tools"
        Storybook["Storybook (port 9009)"]:::dev
        SBMain[".storybook/main.cjs"]:::dev
        Preview[".storybook/preview.js"]:::dev
        ComponentStories["Component Stories"]:::dev
        Jest["Jest Unit Tests"]:::dev
        E2ETests["Playwright E2E Tests"]:::dev
        PlayConfig["test/e2e/playwright.config.js"]:::dev
    end

    %% CI/CD
    CI["GitHub Actions CI/CD"]:::dev

    %% Connections
    User -->|loads| DevServer
    DevServer -->|serves| ReactApp
    ReactApp -->|renders| Index
    ReactApp -->|renders| App
    ReactApp -->|routes to| FilesLoad
    ReactApp -->|routes to| ExploreLoad
    ReactApp -->|routes to| PeersLoad
    ReactApp -->|routes to| SettingsLoad
    ReactApp -->|routes to| StatusLoad
    ReactApp -->|routes to| WelcomeLoad
    ReactApp -->|uses| ComponentsLib

    ReactApp -->|"dispatch actions"| FilesBundle
    ReactApp -->|"dispatch actions"| PeersBundle
    ReactApp -->|"dispatch actions"| PinningBundle
    ReactApp -->|"dispatch actions"| RepoStatsBundle
    ReactApp -->|"dispatch actions"| IdleBundle
    ReactApp -->|"dispatch actions"| AnalyticsBundle
    ReactApp -->|"dispatch actions"| APIProvider

    FilesBundle -->|"calls RPC"| RPCClient
    PeersBundle -->|"calls RPC"| RPCClient
    PinningBundle -->|"calls RPC"| RPCClient
    RepoStatsBundle -->|"calls RPC"| RPCClient
    APIProvider -->|"wraps RPC"| RPCClient

    RPCClient -->|HTTP RPC| IPFS
    RPCClient -->|requires CORS| CorsConfig

    ReactApp -->|loads translations| I18nConfig
    I18nConfig -->|uses| I18nHelper
    I18nConfig -->|loads| Locales
    I18nConfig -->|sync with| Transifex

    Storybook -->|serves components| ComponentsLib
    SBMain --> Storybook
    Preview --> Storybook
    ComponentStories -->|stories| Storybook

    Jest -->|tests| ReactApp
    Jest -->|tests| FilesBundle
    Jest -->|tests| PeersBundle

    E2ETests -->|drives| User
    E2ETests -->|spawns| IPFS
    E2ETests -->|serves| DevServer
    PlayConfig --> E2ETests

    CI -->|runs| Jest
    CI -->|runs| Storybook
    CI -->|runs| E2ETests

    %% Click Events
    click Index "https://github.com/ipfs/ipfs-webui/blob/main/src/index.js"
    click App "https://github.com/ipfs/ipfs-webui/blob/main/src/App.js"
    click FilesLoad "https://github.com/ipfs/ipfs-webui/blob/main/src/files/LoadableFilesPage.js"
    click FilesPage "https://github.com/ipfs/ipfs-webui/blob/main/src/files/FilesPage.js"
    click ExploreLoad "https://github.com/ipfs/ipfs-webui/blob/main/src/explore/LoadableExplorePage.js"
    click ExplorePage "https://github.com/ipfs/ipfs-webui/blob/main/src/explore/ExploreContainer.js"
    click PeersLoad "https://github.com/ipfs/ipfs-webui/blob/main/src/peers/LoadablePeersPage.js"
    click PeersPage "https://github.com/ipfs/ipfs-webui/blob/main/src/peers/PeersPage.js"
    click SettingsLoad "https://github.com/ipfs/ipfs-webui/blob/main/src/settings/LoadableSettingsPage.js"
    click SettingsPage "https://github.com/ipfs/ipfs-webui/blob/main/src/settings/SettingsPage.js"
    click StatusLoad "https://github.com/ipfs/ipfs-webui/blob/main/src/status/LoadableStatusPage.js"
    click StatusPage "https://github.com/ipfs/ipfs-webui/blob/main/src/status/StatusPage.js"
    click WelcomeLoad "https://github.com/ipfs/ipfs-webui/blob/main/src/welcome/LoadableWelcomePage.js"
    click WelcomePage "https://github.com/ipfs/ipfs-webui/blob/main/src/welcome/WelcomePage.js"
    click ComponentsLib "https://github.com/ipfs/ipfs-webui/tree/main/src/components/"
    click FilesBundle "https://github.com/ipfs/ipfs-webui/blob/main/src/bundles/files/index.js"
    click PeersBundle "https://github.com/ipfs/ipfs-webui/blob/main/src/bundles/peers.js"
    click PinningBundle "https://github.com/ipfs/ipfs-webui/blob/main/src/bundles/pinning.js"
    click RepoStatsBundle "https://github.com/ipfs/ipfs-webui/blob/main/src/bundles/repo-stats.js"
    click IdleBundle "https://github.com/ipfs/ipfs-webui/blob/main/src/bundles/app-idle.js"
    click AnalyticsBundle "https://github.com/ipfs/ipfs-webui/blob/main/src/bundles/analytics.js"
    click APIProvider "https://github.com/ipfs/ipfs-webui/blob/main/src/bundles/ipfs-provider.js"
    click CorsConfig "https://github.com/ipfs/ipfs-webui/blob/main/cors-config.sh"
    click I18nConfig "https://github.com/ipfs/ipfs-webui/blob/main/src/i18n.js"
    click I18nHelper "https://github.com/ipfs/ipfs-webui/blob/main/src/helpers/i8n.js"
    click Locales "https://github.com/ipfs/ipfs-webui/tree/main/public/locales/"
    click SBMain "https://github.com/ipfs/ipfs-webui/blob/main/.storybook/main.cjs"
    click Preview "https://github.com/ipfs/ipfs-webui/blob/main/.storybook/preview.js"
    click ComponentStories "https://github.com/ipfs/ipfs-webui/blob/main/src/components/button/button.stories.js"
    click PlayConfig "https://github.com/ipfs/ipfs-webui/blob/main/test/e2e/playwright.config.js"
    click CI "https://github.com/ipfs/ipfs-webui/tree/main/.github/workflows/"

    %% Styles
    classDef ui fill:#e0f7fa,stroke:#006064,color:#004d40;
    classDef state fill:#e8f5e9,stroke:#1b5e20,color:#2e7d32;
    classDef api fill:#fffde7,stroke:#f9a825,color:#f57f17;
    classDef external fill:#fff3e0,stroke:#e65100,color:#bf360c;
    classDef dev fill:#eceff1,stroke:#607d8b,color:#37474f;
    classDef infra fill:#cfd8dc,stroke:#455a64,color:#263238;
```


---

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
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

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