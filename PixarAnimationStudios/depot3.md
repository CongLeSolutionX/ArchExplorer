---
created: 2025-03-23 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExcHdnZ3VkcDEydmlia2VyNTk3ZHZqNzhycTVoNzV6amVjYWIxZ2czdyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/jPsObTEowtqZW/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# depot3
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
title: "Pixar Animation Studios - Depot3"
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
      'textColor': '#F8B229',
      'lineColor': '#F8B229'
    }
  }
}%%
flowchart TD
    %% Command-line Tools Subgraph
    subgraph "Command-line Tools"
        d3["d3 (CLI)"]:::cli
        d3admin["d3admin (CLI)"]:::cli
        d3helper["d3helper (CLI)"]:::cli
        d3sync["d3sync (CLI)"]:::cli
        phi["phi (CLI)"]:::cli
        puppytimeCLI["puppytime (CLI)"]:::cli
    end

    %% Core Library Subgraph
    subgraph "Core Library"
        core["Ruby Core Library"]:::core
        client["d3 Client Module"]:::client
        admin["d3 Admin Module"]:::admin
        package["Package Management Module"]:::package
    end

    %% External Integrations Subgraph
    subgraph "External Integrations"
        jamf["Jamf Pro API Connector"]:::external
        db["Database Access"]:::external
    end

    %% Data/Configuration Subgraph
    subgraph "Data/Configuration"
        config["Configuration Files"]:::data
    end

    %% GUI/UX Resources Subgraph
    subgraph "GUI/UX Resources"
        xcode["Xcode Project (d3RepoMan)"]:::gui
        macos["MacOS App (d3RepoMan.app)"]:::gui
    end

    %% Connections from CLI Tools to Core Library
    d3 --> core
    d3admin --> core
    d3helper --> core
    d3sync --> core
    phi --> core
    puppytimeCLI --> core

    %% Internal Core Library Connections
    core --> client
    core --> admin
    core --> package
    client <--> admin

    %% Core Library to External Integrations
    core --> jamf
    core --> db

    %% Data/Configuration Feeding into Core Library
    config --> core

    %% Core Library to GUI/UX Resources (Graphical Administration Interface)
    core --> xcode
    core --> macos

    %% Click Events for Command-line Tools
    click d3 "https://github.com/pixaranimationstudios/depot3/tree/github-master/bin/d3"
    click d3admin "https://github.com/pixaranimationstudios/depot3/tree/github-master/bin/d3admin"
    click d3helper "https://github.com/pixaranimationstudios/depot3/tree/github-master/bin/d3helper"
    click d3sync "https://github.com/pixaranimationstudios/depot3/tree/github-master/bin/d3sync"
    click phi "https://github.com/pixaranimationstudios/depot3/tree/github-master/bin/phi"
    click puppytimeCLI "https://github.com/pixaranimationstudios/depot3/tree/github-master/bin/puppytime"

    %% Click Events for Core Library and Modules
    click core "https://github.com/pixaranimationstudios/depot3/blob/github-master/lib/d3.rb"
    click client "https://github.com/pixaranimationstudios/depot3/tree/github-master/lib/d3/client"
    click admin "https://github.com/pixaranimationstudios/depot3/tree/github-master/lib/d3/admin"
    click package "https://github.com/pixaranimationstudios/depot3/tree/github-master/lib/d3/package"

    %% Click Event for External Integrations
    click db "https://github.com/pixaranimationstudios/depot3/blob/github-master/lib/d3/database.rb"

    %% Click Events for GUI/UX Resources
    click xcode "https://github.com/pixaranimationstudios/depot3/tree/github-master/d3RepoMan"
    click macos "https://github.com/pixaranimationstudios/depot3/blob/github-master/data/d3/d3RepoMan.app"

    %% Click Event for Data/Configuration
    click config "https://github.com/pixaranimationstudios/depot3/blob/github-master/data/d3/d3.conf.example"

    %% Styles
    classDef cli fill:#d1f2eb,stroke:#16a085,stroke-width:2px;
    classDef core fill:#d6eaf8,stroke:#2e86c1,stroke-width:2px;
    classDef client fill:#fad7a0,stroke:#d35400,stroke-width:2px;
    classDef admin fill:#f9e79f,stroke:#f1c40f,stroke-width:2px;
    classDef package fill:#f5b7b1,stroke:#e74c3c,stroke-width:2px;
    classDef external fill:#f6ddcc,stroke:#e67e22,stroke-width:2px;
    classDef data fill:#fcf3cf,stroke:#f39c12,stroke-width:2px;
    classDef gui fill:#d5f5e3,stroke:#27ae60,stroke-width:2px
    
```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
