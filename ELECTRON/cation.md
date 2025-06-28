---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/electron/cation
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExbGhtNTh0NDlvcTlqd2I4c3BjZjExM3RlbmEzbHp1NmE2MWIxbXBxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/O6nT9DSoiUVYQ/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# cation repo project
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
title: "cation repo project"
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
    subgraph "Ingress"
        GitHub(("GitHub")):::external
        Receiver["Webhook Receiver / Probot\n(src/index.ts)"]:::app
        Dispatcher["Dispatcher\n(src/index.ts)"]:::app
    end

    subgraph "Business Logic"
        Semver["Semver Enforcement\n(src/enforce-semver-labels.ts)"]:::rule
        Rule24["24h PR Open-Time\n(src/24-hour-rule.ts)"]:::rule
        APIReview["API Review State\n(src/api-review-state.ts)"]:::rule
        DepRec["Deprecation Review\n(src/deprecation-review-state.ts)"]:::rule
        Triage["Triage Labels\n(src/add-triage-labels.ts)"]:::rule
    end

    subgraph "Utilities & Config"
        CheckUtils["Check Utils\n(src/utils/check-utils.ts)"]:::util
        EnvUtil["Env Util\n(src/utils/env-util.ts)"]:::util
        LabelUtils["Label Utils\n(src/utils/label-utils.ts)"]:::util
        LogUtil["Log Util\n(src/utils/log-util.ts)"]:::util
        Constants["Constants\n(src/constants.ts)"]:::util
        Enums["Enums\n(src/enums.ts)"]:::util
        Manifest["App Manifest\n(app.json)"]:::app
    end

    subgraph "External API"
        GitAPI(("GitHub REST & Checks API")):::external
    end

    subgraph "CI/CD"
        Lint["Lint Workflow\n(.github/workflows/lint.yml)"]:::ci
        TestWF["Test Workflow\n(.github/workflows/test.yml)"]:::ci
    end

    subgraph "Testing"
        Tests["Unit Tests\n(spec/*.spec.ts)"]:::test
        Fixtures["Fixtures\n(spec/fixtures/)"]:::test
    end

    GitHub -->|"webhook events\npull_request.opened, etc"| Receiver
    Receiver -->|"initialize & register handlers"| Dispatcher
    Dispatcher -->|"route events"| Semver
    Dispatcher --> Rule24
    Dispatcher --> APIReview
    Dispatcher --> DepRec
    Dispatcher --> Triage

    Semver -->|"uses utils"| CheckUtils
    Rule24 --> LabelUtils
    APIReview --> LabelUtils
    APIReview --> CheckUtils
    DepRec --> LabelUtils
    DepRec --> LogUtil
    Triage --> LabelUtils

    CheckUtils -->|"REST/Checks API calls"| GitAPI
    EnvUtil --> GitAPI
    LabelUtils --> GitAPI
    LogUtil --> GitAPI
    Constants --> Semver
    Enums --> Dispatcher

    Repo["Repository"]:::app
    Repo --> Lint
    Repo --> TestWF
    Lint -->|"runs on push/PR"| Repo
    TestWF --> Repo

    Tests --> Semver
    Tests --> Rule24
    Tests --> APIReview
    Tests --> DepRec
    Tests --> Triage
    Fixtures --> Tests

    classDef external fill:#D0E6F6,stroke:#000,stroke-width:1px
    classDef app fill:#E0E0E0,stroke:#000,stroke-width:1px
    classDef rule fill:#C6E2C6,stroke:#000,stroke-width:1px
    classDef util fill:#F9E79F,stroke:#000,stroke-width:1px
    classDef ci fill:#FAD7A0,stroke-dasharray:5 5
    classDef test fill:#E8DAEF,stroke:#000,stroke-width:1px

    click Receiver "https://github.com/electron/cation/blob/main/src/index.ts"
    click Dispatcher "https://github.com/electron/cation/blob/main/src/index.ts"
    click Semver "https://github.com/electron/cation/blob/main/src/enforce-semver-labels.ts"
    click Rule24 "https://github.com/electron/cation/blob/main/src/24-hour-rule.ts"
    click APIReview "https://github.com/electron/cation/blob/main/src/api-review-state.ts"
    click DepRec "https://github.com/electron/cation/blob/main/src/deprecation-review-state.ts"
    click Triage "https://github.com/electron/cation/blob/main/src/add-triage-labels.ts"
    click CheckUtils "https://github.com/electron/cation/blob/main/src/utils/check-utils.ts"
    click EnvUtil "https://github.com/electron/cation/blob/main/src/utils/env-util.ts"
    click LabelUtils "https://github.com/electron/cation/blob/main/src/utils/label-utils.ts"
    click LogUtil "https://github.com/electron/cation/blob/main/src/utils/log-util.ts"
    click Constants "https://github.com/electron/cation/blob/main/src/constants.ts"
    click Enums "https://github.com/electron/cation/blob/main/src/enums.ts"
    click Manifest "https://github.com/electron/cation/blob/main/app.json"
    click Lint "https://github.com/electron/cation/blob/main/.github/workflows/lint.yml"
    click TestWF "https://github.com/electron/cation/blob/main/.github/workflows/test.yml"
    click Tests "https://github.com/electron/cation/blob/main/spec/*.spec.ts"
    click Fixtures "https://github.com/electron/cation/tree/main/spec/fixtures/"
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
