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
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExdDl3cXMwNWE1aXBzbXhsNndkcW9saTBjazFxeHVzeWk3cTBkd240MyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/0U7bWQK9s75PjRKcHz/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----



# DEPNotify-Starter
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
title: "JamF - DEPNotify Starter"
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
    %% Main Flow
    A("Enrollment Process"):::start
    C("User Provisioning Inputs"):::inputs
    B("DEPNotify Starter Script"):::bash
    D{"Check_TESTING_MODE"}:::decision
    E("Simulate_Deployment_(Sleep_Command)"):::bash
    F("Jamf_Pro_Policy_Trigger"):::jamf
    G("DEPNotify_App_Invocation"):::ui
    H{"FileVault_Check"}:::decision
    I("Perform_Logout"):::bash
    J("Quit_DEPNotify_(Normal_Termination)"):::bash

    %% Documentation & Assets Subgraph
    subgraph "Documentation & Assets"
        R("README.md"):::doc
        CH("CHANGELOG.md"):::doc
        CO("CONTRIBUTORS.md"):::doc
        RE("RELEASES.md"):::doc
        IMG("Visual_Assets:_example-img"):::doc
        VID("Visual_Assets:_example-video"):::doc
    end

    %% Connections
    A --> B
    C --> B
    B --> D
    D -- "true" --> E
    D -- "false" --> F
    B --> G
    B --> H
    H -- "yes" --> I
    H -- "no" --> J

    %% Click Events
    click B "https://github.com/jamf/depnotify-starter/blob/master/depNotify.sh"
    click R "https://github.com/jamf/depnotify-starter/blob/master/README.md"
    click CH "https://github.com/jamf/depnotify-starter/blob/master/CHANGELOG.md"
    click CO "https://github.com/jamf/depnotify-starter/blob/master/CONTRIBUTORS.md"
    click RE "https://github.com/jamf/depnotify-starter/blob/master/RELEASES.md"
    click IMG "https://github.com/jamf/depnotify-starter/tree/master/example-img"
    click VID "https://github.com/jamf/depnotify-starter/tree/master/example-video"

    %% Styles
    classDef start fill:#a2d9ff,stroke:#333,stroke-width:2px;
    classDef bash fill:#ffdd88,stroke:#333,stroke-width:2px;
    classDef jamf fill:#ffaaaa,stroke:#333,stroke-width:2px;
    classDef ui fill:#ccffcc,stroke:#333,stroke-width:2px;
    classDef decision fill:#ffeb3b,stroke:#333,stroke-width:2px,shape:diamond;
    classDef inputs fill:#d1c4e9,stroke:#333,stroke-width:2px;
    classDef doc fill:#e0e0e0,stroke:#333,stroke-width:2px

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

  Closing_quote ~~~ My_Meme
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }

```

---
> **Licenses:**
>
> - **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
> - **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).
> 
---
