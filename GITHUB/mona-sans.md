---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/github/mona-sans
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExMXVjejV3dnVjc2o5MXd3eXBvcDR1cHlzbHQ1Z2R6YjY0ZHpmdjJ6OCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/hL9q5k9dk9l0wGd4e0/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# mona-sans repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>

---


```mermaid
---
title: "mona-sans repo project"
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
    subgraph "Sources"
        source_pkg["Glyphs Sources\n(.glyphspackage)"]:::sources
        metadata["fontinfo.plist"]:::sources
        order["order.plist"]:::sources
        config["config.yaml"]:::sources
    end

    subgraph "Build Pipeline"
        ci["GitHub Actions\n(.github)"]:::ci
        buildsh["build.sh"]:::ci
        requirements["requirements.txt"]:::ci
        python["Python Engine\n(fontmake + glyphsLib)"]:::ci
    end

    subgraph "Outputs"
        otf["Static OTF Fonts"]:::outputs
        ttf["Static TTF Fonts"]:::outputs
        varf["Variable Fonts"]:::outputs
        webf["Webfonts (WOFF2, etc)"]:::outputs
    end

    subgraph "Distribution"
        releases["GitHub Releases"]:::dist
        microsite["Microsite (docs)"]:::dist
        users["End Users\n(Web, Print)"]:::dist
    end

    source_pkg -->|includes metadata & order| metadata
    source_pkg -->|includes metadata & order| order
    source_pkg -->|drives build| config
    metadata -->|drives build| buildsh
    order -->|drives build| buildsh
    config -->|drives build| buildsh

    ci -->|triggers| buildsh
    buildsh -->|runs| python
    requirements -->|libraries| python

    python -->|generate| otf
    python -->|generate| ttf
    python -->|generate| varf
    python -->|generate| webf

    otf -->|publish| releases
    ttf -->|publish| releases
    varf -->|publish| releases
    webf -->|publish| releases

    releases -->|host fonts| users
    releases -->|host docs| microsite

    %% Click Events
    click source_pkg "https://github.com/github/mona-sans/tree/main/sources/MonaSans.glyphspackage/"
    click metadata "https://github.com/github/mona-sans/blob/main/sources/MonaSans.glyphspackage/fontinfo.plist"
    click order "https://github.com/github/mona-sans/blob/main/sources/MonaSans.glyphspackage/order.plist"
    click config "https://github.com/github/mona-sans/blob/main/sources/config.yaml"
    click buildsh "https://github.com/github/mona-sans/blob/main/sources/build.sh"
    click requirements "https://github.com/github/mona-sans/blob/main/requirements.txt"
    click ci "https://github.com/github/mona-sans/tree/main/.github/"
    click otf "https://github.com/github/mona-sans/tree/main/fonts/otf/"
    click ttf "https://github.com/github/mona-sans/tree/main/fonts/ttf/"
    click varf "https://github.com/github/mona-sans/tree/main/fonts/variable/"
    click webf "https://github.com/github/mona-sans/tree/main/fonts/webfonts/"

    classDef sources fill:#a8e6a3,stroke:#333,stroke-width:1px
    classDef ci fill:#9ec1f7,stroke:#333,stroke-width:1px
    classDef outputs fill:#f7c986,stroke:#333,stroke-width:1px
    classDef dist fill:#d3d3d3,stroke:#333,stroke-width:1px
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
 
  Closing_quote ~~~ My_Meme

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