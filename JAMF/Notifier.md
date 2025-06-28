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
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExeGNsOXdrYjc0ZWFteWI4eGx5anAzaW5iZjRmd3F4NGpueTVudHFjNSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/ZO9b1ntYVJmjZlsWlm/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----



# Notifier
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
title: "JamF - Notifier"
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
    A("User/Command Input"):::input
    B("Main Notifier App"):::internal
    C("Notifier - Alerts Helper"):::internal
    D("Notifier - Notifications Helper"):::internal
    E("macOS Notification Center"):::external
    F("Rebranding Script"):::deployment
    G("PPPC Profile"):::deployment
    H("CI/CD Integration"):::cicd

    A --> B
    F --> B
    G --> B
    H --> B
    B -->|"alerts"| C
    B -->|"banners"| D
    C --> E
    D --> E

    click B "https://github.com/jamf/notifier/blob/main/Notifier/Notifier (including AppDelegate.swift, ArgParser.swift, Functions.swift, Structures.swift, UserNotifications.swift)"
    click C "https://github.com/jamf/notifier/blob/main/Notifier/Notifier - Alerts (including AppDelegate.swift, Functions.swift, Structures.swift, UserNotifications.swift, Assets.xcassets)"
    click D "https://github.com/jamf/notifier/blob/main/Notifier/Notifier - Notifications (including AppDelegate.swift, Functions.swift, Structures.swift, UserNotifications.swift, Assets.xcassets)"
    click F "https://github.com/jamf/notifier/blob/main/package/make-notifier-pkg.sh"
    click G "https://github.com/jamf/notifier/blob/main/profile/Allow Notifier Notifications.mobileconfig"
    click H "https://github.com/jamf/notifier/tree/main/.ci/Jenkinsfile"

    classDef input fill:#F5CBA7,stroke:#A04000,stroke-width:2px;
    classDef internal fill:#AED6F1,stroke:#1B4F72,stroke-width:2px;
    classDef external fill:#F9E79F,stroke:#B7950B,stroke-width:2px;
    classDef deployment fill:#FAD7A0,stroke:#D35400,stroke-width:2px;
    classDef cicd fill:#D5F5E3,stroke:#27AE60,stroke-width:2px
    
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
