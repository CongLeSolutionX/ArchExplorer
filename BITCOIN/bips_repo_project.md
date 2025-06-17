---
created: 2025-06-11 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/bitcoin/bips
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnloOTFydDV5dTJpZWhzbnYwMGxiZHA5eWt5ZXgzb2wwYnd5Ym9ycCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/hK61m7SawMkqUcyLg1/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# bips repo project
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
title: "libblkmaker repo project"
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
    subgraph "Contribution & Process Guidelines"
        CG1["CONTRIBUTING.md"]
        CG2["README.mediawiki"]
    end

    subgraph "CI/CD Workflows"
        WORKFLOW["github-action-checks.yml"]
    end

    subgraph "Supporting Scripts & Tools"
        S1["buildtable.pl"]
        S2["diffcheck.sh"]
        S3["link-format-chk.sh"]
    end

    BIP["BIPs Repository"]

    subgraph "Repository Configuration & Meta Files"
        RC1[".gitattributes"]
        RC2[".gitignore"]
        RC3[".typos.toml"]
    end

    %% Flow Connections
    CG1 -->|"PR_triggers"| WORKFLOW
    CG2 -->|"PR_triggers"| WORKFLOW
    WORKFLOW -->|"executes"| S1
    WORKFLOW -->|"executes"| S2
    WORKFLOW -->|"executes"| S3
    S1 -->|"updates"| BIP
    S2 -->|"validates"| BIP
    S3 -->|"formats"| BIP

    %% Click Events
    click CG1 "https://github.com/bitcoin/bips/blob/master/CONTRIBUTING.md"
    click CG2 "https://github.com/bitcoin/bips/blob/master/README.mediawiki"
    click WORKFLOW "https://github.com/bitcoin/bips/blob/master/.github/workflows/github-action-checks.yml"
    click S1 "https://github.com/bitcoin/bips/blob/master/scripts/buildtable.pl"
    click S2 "https://github.com/bitcoin/bips/blob/master/scripts/diffcheck.sh"
    click S3 "https://github.com/bitcoin/bips/blob/master/scripts/link-format-chk.sh"
    click BIP "https://github.com/bitcoin/bips/tree/master/bip-xxxx"
    click RC1 "https://github.com/bitcoin/bips/blob/master/.gitattributes"
    click RC2 "https://github.com/bitcoin/bips/blob/master/.gitignore"
    click RC3 "https://github.com/bitcoin/bips/blob/master/.typos.toml"

    %% Styles
    classDef guideline fill:#FFA07A,stroke:#000,stroke-width:2px;
    classDef auto fill:#90EE90,stroke:#000,stroke-width:2px;
    classDef doc fill:#ADD8E6,stroke:#000,stroke-width:2px;
    classDef config fill:#FFD700,stroke:#000,stroke-width:2px;

    class CG1,CG2 guideline;
    class WORKFLOW,S1,S2,S3 auto;
    class BIP doc;
    class RC1,RC2,RC3 config;
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