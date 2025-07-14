---
created: 2025-07-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/dropbox/zxcvbn
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




# zxcvbn repo project
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
title: "zxcvbn repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright © 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': { 'htmlLabels': true, 'curve': 'linear'},
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#22BB',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EEF2',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '15px'
    }
  }
}%%
flowchart TD
    subgraph "Offline Data Generation"
        rawData(("Raw Data")):::datastore
        dataScripts["Data Generation Scripts"]:::datascripts
        rawData --> dataScripts
        dataScripts --> genData["Generated Data Modules"]:::datastore
    end

    subgraph "Core Algorithm Modules"
        adjacency["Adjacency Graphs Module"]:::algorithm
        frequency["Frequency Data Module"]:::algorithm
        matching["Pattern Matching Module"]:::algorithm
        scoring["Scoring Engine Module"]:::algorithm
        timeEst["Time Estimation Module"]:::algorithm
        feedback["Feedback Generator Module"]:::algorithm
        orchestrator["Core Orchestrator (main.coffee)"]:::algorithm
    end

    genData --> adjacency
    genData --> frequency
    adjacency --> orchestrator
    frequency --> orchestrator
    orchestrator --> matching
    matching --> scoring
    scoring --> timeEst
    timeEst --> feedback

    subgraph "Build Pipeline"
        csComp["CoffeeScript Compiler"]:::build
        browserify["Browserify"]:::build
        uglify["Uglifyify"]:::build
        exorcist["Exorcist"]:::build
        csComp --> browserify --> uglify --> exorcist --> bundle
    end

    subgraph "Distribution"
        bundle["zxcvbn.js (bundle)"]:::output
        map["zxcvbn.js.map"]:::output
    end

    feedback --> csComp
    orchestrator --> csComp
    exorcist --> bundle
    bundle --> map

    subgraph "Consumers"
        node["Node/CommonJS"]:::consumer
        amd["AMD/RequireJS"]:::consumer
        global["Global window.zxcvbn"]:::consumer
    end

    bundle --> node
    bundle --> amd
    bundle --> global

    subgraph "Demo & Tests"
        demo["Demo Application"]:::demo
        tests["Automated Tests"]:::tests
    end

    global --> demo
    bundle --> tests

    click adjacency "https://github.com/dropbox/zxcvbn/blob/master/src/adjacency_graphs.coffee"
    click frequency "https://github.com/dropbox/zxcvbn/blob/master/src/frequency_lists.coffee"
    click matching "https://github.com/dropbox/zxcvbn/blob/master/src/matching.coffee"
    click scoring "https://github.com/dropbox/zxcvbn/blob/master/src/scoring.coffee"
    click timeEst "https://github.com/dropbox/zxcvbn/blob/master/src/time_estimates.coffee"
    click feedback "https://github.com/dropbox/zxcvbn/blob/master/src/feedback.coffee"
    click orchestrator "https://github.com/dropbox/zxcvbn/blob/master/src/main.coffee"
    click dataScripts "https://github.com/dropbox/zxcvbn/tree/master/data-scripts/"
    click rawData "https://github.com/dropbox/zxcvbn/tree/master/data/"
    click bundle "https://github.com/dropbox/zxcvbn/blob/master/dist/zxcvbn.js"
    click map "https://github.com/dropbox/zxcvbn/blob/master/dist/zxcvbn.js.map"
    click tests "https://github.com/dropbox/zxcvbn/blob/master/test/test-matching.coffee"

    classDef algorithm fill:#cfe2ff,stroke:#084298
    classDef datastore fill:#d1e7dd,stroke:#0f5132
    classDef datascripts fill:#d1e7dd,stroke:#0f5132
    classDef build fill:#ffe5d9,stroke:#d9480f
    classDef output fill:#fff3cd,stroke:#856404
    classDef consumer fill:#e2e3e5,stroke:#6c757d
    classDef demo fill:#f5e1ff,stroke:#6f42c1
    classDef tests fill:#f8d7da,stroke:#842029
```

----

<!-- 
```mermaid
%% Current Mermaid version
info
```  -->


```mermaid
---
title: "C<char>o&#770;</char>ngL<char>e&#770;</char>SolutionX"
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
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX/CongLeSolutionX' target='_blank'>Click here if you care about the profile of a tech guy seeking for job 🙏🏼</a>"}}

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