---
created: 2025-03-23 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# NetSUS
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---



```mermaid
---
title: "JamF - NetSUS"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: default
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'lineColor': '#F8B229'
    }
  }
}%%
flowchart TD
    %% User Interaction
    Admin("Administrator/User"):::external

    %% Management Console
    Webadmin("Webadmin – Management Console"):::frontend

    %% Backend Services
    SUS("Software Update Server (SUS)"):::backend
    NetBoot("NetBoot Server"):::backend
    LDAP("LDAP Proxy"):::backend
    FileShare("File Sharing Service"):::backend

    %% Setup & Configuration
    Installer("Installer/Appliance Setup Scripts"):::scripts
    Docs("Documentation & Configuration"):::docs

    %% External Clients
    Clients("Client Systems"):::external

    %% Relationships
    Admin -->|"uses"| Webadmin

    Webadmin -->|"manages"| SUS
    Webadmin -->|"manages"| NetBoot
    Webadmin -->|"manages"| LDAP
    Webadmin -->|"configures"| FileShare

    Installer -->|"bootstraps"| Webadmin
    Installer -->|"deploys"| SUS
    Installer -->|"deploys"| NetBoot
    Installer -->|"deploys"| LDAP
    Installer -->|"deploys"| FileShare

    SUS -->|"provides_updates_to"| Clients
    NetBoot -->|"provides_boot_images_to"| Clients
    LDAP -->|"provides_directory_info_to"| Clients
    FileShare -->|"provides_file_shares_to"| Clients

    %% Click Events
    click Webadmin "https://github.com/jamf/netsus/tree/master/webadmin/var/www/webadmin"
    click SUS "https://github.com/jamf/netsus/tree/master/SUS"
    click NetBoot "https://github.com/jamf/netsus/tree/master/NetBoot"
    click LDAP "https://github.com/jamf/netsus/tree/master/LDAPProxy"
    click Installer "https://github.com/jamf/netsus/tree/master/appliance"
    click Installer "https://github.com/jamf/netsus/tree/master/base"
    click Installer "https://github.com/jamf/netsus/tree/master/includes"
    click Installer "https://github.com/jamf/netsus/tree/master/makeself"
    click Docs "https://github.com/jamf/netsus/tree/master/docs"
    click Docs "https://github.com/jamf/netsus/blob/master/README.md"

    %% Styles
    classDef external fill:#f9c,stroke:#333,stroke-width:2px;
    classDef frontend fill:#bbf,stroke:#333,stroke-width:2px;
    classDef backend fill:#bfb,stroke:#333,stroke-width:2px;
    classDef scripts fill:#ffebcd,stroke:#333,stroke-width:2px;
    classDef docs fill:#eef,stroke:#333,stroke-width:2px

```





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---