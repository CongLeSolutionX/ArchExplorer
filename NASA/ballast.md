---
created: 2025-03-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# ballast
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## A Diagrammatic Guide 


```mermaid
---
title: "Ballast"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: dark
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
      'primaryColor': '#ffff',
      'primaryTextColor': '#2ff9',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TD
    %% Ballast Components Subgraph
    subgraph "Ballast Components"
        A["Ballast Agent (Perl)"]:::agent
        S["Ballast Server (Perl/C)"]:::server
        C["Ballast Client (Perl)"]:::client
        P["Performance Component (C)"]:::performance
    end

    %% External Components Subgraph
    subgraph "External Components"
        T["TCP Relay/Netcat"]:::external
        BH["Balanced Host"]:::external
    end

    %% Deployment & Configuration Subgraph
    subgraph "Deployment & Configuration"
        Config["Configuration (ballastrc)"]:::config
        Debian["Debian Packaging"]:::config
        SysdA1["Systemd: ballast-agent.service"]:::config
        SysdA2["Systemd: ballast-agent.timer"]:::config
        SysdS["Systemd: ballast.service"]:::config
        DocA["Documentation: ballast-agent.1"]:::config
        DocS["Documentation: ballastd.1"]:::config
        DocC["Documentation: ballast.1"]:::config
    end

    %% Data Flows
    A -->|"LoadData"| S
    C -->|"AliasRequest"| S
    S -->|"HostSelection"| C
    C -->|"TCPRelay"| T
    T -->|"Connect"| BH

    %% Associations with Deployment & Configuration
    A --- DocA
    A --- SysdA1
    A --- SysdA2
    S --- DocS
    S --- SysdS
    C --- DocC
    Config --- A
    Config --- S
    Config --- C
    P --- S
    Debian --- Config

    %% Click Events for Ballast Agent
    click A "https://github.com/pkolano/ballast/tree/master/perl/ballast-agent"
    click DocA "https://github.com/pkolano/ballast/blob/master/doc/ballast-agent.1"
    click SysdA1 "https://github.com/pkolano/ballast/blob/master/etc/systemd/system/ballast-agent.service"
    click SysdA2 "https://github.com/pkolano/ballast/blob/master/etc/systemd/system/ballast-agent.timer"

    %% Click Events for Ballast Server
    click S "https://github.com/pkolano/ballast/tree/master/perl/ballastd"
    click DocS "https://github.com/pkolano/ballast/blob/master/doc/ballastd.1"
    click SysdS "https://github.com/pkolano/ballast/blob/master/etc/systemd/system/ballast.service"

    %% Click Events for Ballast Client
    click C "https://github.com/pkolano/ballast/tree/master/perl/ballast"
    click DocC "https://github.com/pkolano/ballast/blob/master/doc/ballast.1"

    %% Click Events for Configuration & Packaging
    click Config "https://github.com/pkolano/ballast/tree/master/etc/ballastrc"
    click Debian "https://github.com/pkolano/ballast/tree/master/debian/"

    %% Click Event for Performance Component
    click P "https://github.com/pkolano/ballast/blob/master/c/ballast.c"

    %% Styles
    classDef agent fill:#fd33,stroke:#cc0000,stroke-width:2px
    classDef server fill:#df22,stroke:#009900,stroke-width:2px
    classDef client fill:#df33,stroke:#0000cc,stroke-width:2px
    classDef performance fill:#fd22,stroke:#cc6600,stroke-width:2px
    classDef external fill:#fc33,stroke:#cccc00,stroke-width:2px
    classDef config fill:#df33,stroke:#009999,stroke-width:2px

```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---