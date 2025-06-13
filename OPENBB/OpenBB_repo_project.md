---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openbb-finance/openbb
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExNnllemVldmoyYm82cTc3cW5kbG04eWljYnAzY2dwcGdqam1pZ3ZobSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/gKVdeHpwce7TdHDyaK/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# OpenBB repo project
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
title: "OpenBB repo project"
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
    subgraph "User Interface Layer"
        CLI["CLI"]:::ui
        FE["Frontend Components"]:::ui
    end

    subgraph "Core Application Layer"
        Core["Core Engine"]:::core
        PR["Provider Registry"]:::core
        subgraph "Extensions and Plugins"
            Ext["Extensions"]:::ext
            OExt["Obbject Extensions"]:::ext
        end
    end

    subgraph "Data Providers Layer"
        DP["Data Providers"]:::dp
    end

    CLI -->|"user_command"| Core
    FE -->|"user_action"| Core
    Core -->|"load_extension"| Ext
    Core -->|"load_ob_extension"| OExt
    Core -->|"query"| PR
    PR -->|"fetch_data"| DP
    DP -->|"return_data"| PR
    PR -->|"provide_data"| Core
    Core -->|"render_results"| CLI
    Core -->|"render_results"| FE

    click CLI "https://github.com/openbb-finance/openbb/tree/develop/cli/openbb_cli"
    click FE "https://github.com/openbb-finance/openbb/tree/develop/frontend-components"
    click Core "https://github.com/openbb-finance/openbb/tree/develop/openbb_platform"
    click Ext "https://github.com/openbb-finance/openbb/tree/develop/openbb_platform/extensions"
    click OExt "https://github.com/openbb-finance/openbb/tree/develop/openbb_platform/obbject_extensions"
    click DP "https://github.com/openbb-finance/openbb/tree/develop/openbb_platform/providers"

    classDef ui fill:#f9e79f,stroke:#7d6608,stroke-width:2px;
    classDef core fill:#aed6f1,stroke:#1b4f72,stroke-width:2px;
    classDef ext fill:#d5f5e3,stroke:#186a3b,stroke-width:2px;
    classDef dp fill:#fadbd8,stroke:#922b21,stroke-width:2px;
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
