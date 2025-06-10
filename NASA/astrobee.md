---
created: 2025-03-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExbzZqcWo5bjJ1ZGxuanAybXZocHh0ejlpZWU3eWNtdjhmNzZid3k0YiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3ohzdU62e5iaTU4XJK/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Astrobee
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
title: "Astrobee"
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
graph TB
    subgraph "Onboard Flight Software"
        A["Flight Software Core"]
        B["Behavior Modules"]
        C["Navigation, Guidance & Control (GN&C)"]
        D["Hardware Drivers"]
    end

    subgraph "Perception & Localization"
        E["Localization"]
    end

    subgraph "Communications"
        F["Communications"]
    end

    subgraph "Mobility and Planning"
        G["Mobility and Planning"]
    end

    subgraph "Management and Monitoring"
        H["Management and System Monitoring"]
    end

    subgraph "Simulation Environment"
        I["Simulation"]
    end

    subgraph "Support Libraries"
        J["Shared / Support Libraries"]
    end

    subgraph "Development Tools"
        K["Tools and Scripts"]
    end

    %% Interactions and Data Flow
    A -->|"dispatches"| B
    B -->|"executes"| C
    C -->|"controls"| D
    D -->|"sends sensor data"| E
    E -->|"informs"| C
    A <-->|"ROS messaging"| F
    A -->|"mission status"| H
    A -->|"trajectory planning"| G
    G -->|"commands motion"| D
    I -->|"mimics hardware"| D
    D -->|"feedback"| I
    J -->|"provides services"| A
    K -->|"supports development"| A

    %% Click Events for Components
    click A "https://github.com/nasa/astrobee/tree/master//astrobee"
    click B "https://github.com/nasa/astrobee/tree/master//behaviors"
    click C "https://github.com/nasa/astrobee/tree/master//gnc"
    click D "https://github.com/nasa/astrobee/tree/master//hardware"
    click E "https://github.com/nasa/astrobee/tree/master//localization"
    click F "https://github.com/nasa/astrobee/tree/master//communications"
    click G "https://github.com/nasa/astrobee/tree/master//mobility"
    click H "https://github.com/nasa/astrobee/tree/master//management"
    click I "https://github.com/nasa/astrobee/tree/master//simulation"
    click J "https://github.com/nasa/astrobee/tree/master//shared"
    click K "https://github.com/nasa/astrobee/tree/master//scripts and /tools"

    %% Styling Classes
    classDef onboard fill:#FFCC00,stroke:#333,stroke-width:2px
    classDef localization fill:#66CC66,stroke:#333,stroke-width:2px
    classDef communications fill:#66CCCC,stroke:#333,stroke-width:2px
    classDef management fill:#FF9966,stroke:#333,stroke-width:2px
    classDef simulation fill:#CCCCFF,stroke:#333,stroke-width:2px
    classDef mobility fill:#99CC99,stroke:#333,stroke-width:2px
    classDef shared fill:#CCCCCC,stroke:#333,stroke-width:2px
    classDef tools fill:#FF99CC,stroke:#333,stroke-width:2px

    %% Assign classes to nodes
    class A,B,C,D onboard
    class E localization
    class F communications
    class H management
    class I simulation
    class G mobility
    class J shared
    class K tools

```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
