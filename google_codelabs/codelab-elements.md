---
created: 2025-06-19 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/googlecodelabs/codelab-elements
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




# codelab-elements repo project
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
title: "codelab-elements repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
	'flowchart': { 'htmlLabels': true, 'curve': 'linear' },
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#D5F5E3',
      'primaryTextColor': '#F8B229',
      'textColor': '#145A32',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EBDEF0',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD'
    }
  }
}%%
flowchart TB
  %% Source Packages
  subgraph "Source Packages"
    direction TB
    Core["google-codelab"]:::source
    Step["google-codelab-step"]:::source
    Index["google-codelab-index"]:::source
    Analytics["google-codelab-analytics"]:::source
    Survey["google-codelab-survey"]:::source
  end

  %% Third-Party
  subgraph "Third-Party Shims/Polyfills"
    direction TB
    ES6["ES6 Shim"]:::third
    Polyfill["Custom Elements Polyfill"]:::third
    Prettify["Prettify"]:::third
  end

  %% Build System
  subgraph "Build & Bundling" 
    direction TB
    BazelWorkspace["WORKSPACE & BUILD.bazel"]:::build
    Closure["Google Closure Compiler"]:::build
    Bundle["//:bundle → codelab-elements.js/css"]:::build
  end

  %% Demo Application
  subgraph "Demo Application"
    direction TB
    CodelabHTML["codelab.html/embed.html/hello.html"]:::demo
    HelloJS["hello.js & hello_test.js"]:::demo
    DemoImg["img/"]:::demo
  end

  %% CI/Test & Dev Server
  subgraph "CI & Dev Server"
    direction TB
    CIPresubmit["ci-presubmit.sh"]:::build
    CIContinuous["ci-continuous.sh"]:::build
    ServerGo["server.go"]:::build
    WebtestGo["webtest.go"]:::build
  end

  %% Runtime
  subgraph "Browser Runtime"
    direction TB
    Browser["Browser (HTML/CSS/JS)"]:::runtime
  end

  %% Build Flow
  Core -->|sources| BazelWorkspace
  Step -->|sources| BazelWorkspace
  Index -->|sources| BazelWorkspace
  Analytics -->|sources| BazelWorkspace
  Survey -->|sources| BazelWorkspace
  BazelWorkspace --> Closure
  Closure --> Bundle
  ES6 --> Bundle
  Polyfill --> Bundle
  Prettify --> Bundle

  %% Demo & Runtime Flow
  Bundle --> CodelabHTML
  CodelabHTML --> Browser
  ES6 --> Browser
  Polyfill --> Browser
  Prettify --> Browser

  %% User Interaction Flow
  Browser -->|"User clicks Next"| Core
  Core -->|"triggers step"| Step
  Step -->|"updates DOM"| Browser
  Browser -->|"survey popup"| Survey
  Survey -->|"event sent"| Analytics

  %% CI/Test Flow
  CIPresubmit -->|runs| BazelWorkspace
  CIContinuous -->|runs| BazelWorkspace
  BazelWorkspace -->|test| Core
  BazelWorkspace -->|test| Step
  BazelWorkspace -->|test| Index
  BazelWorkspace -->|test| Analytics
  BazelWorkspace -->|test| Survey
  WebtestGo -->|browser tests| Browser
  ServerGo -->|serves artifacts| Browser

  %% Click Events for component mapping
  click Core "https://github.com/googlecodelabs/codelab-elements/tree/master/google-codelab/"
  click Core "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab/BUILD.bazel"
  click Core "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab/google_codelab.js"
  click Core "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab/google_codelab_def.js"
  click Core "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab/google_codelab.scss"
  click Core "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab/_drawer.scss"
  click Core "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab/_steps.scss"
  click Core "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab/index.html"
  click Core "https://github.com/googlecodelabs/codelab-elements/tree/master/google-codelab/img/"
  click Step "https://github.com/googlecodelabs/codelab-elements/tree/master/google-codelab-step/"
  click Step "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-step/BUILD.bazel"
  click Step "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-step/google_codelab_step.js"
  click Step "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-step/google_codelab_step_def.js"
  click Step "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-step/google_codelab_step.scss"
  click Step "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-step/google-codelab-step.html"
  click Step "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-step/_syntax.scss"
  click Step "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-step/google_codelab_step_test.js"
  click Index "https://github.com/googlecodelabs/codelab-elements/tree/master/google-codelab-index/"
  click Index "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-index/BUILD.bazel"
  click Index "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-index/google_codelab_index.js"
  click Index "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-index/google_codelab_index_def.js"
  click Index "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-index/google_codelab_index_cards.js"
  click Index "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-index/google_codelab_index_cards_def.js"
  click Index "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-index/google_codelab_index.scss"
  click Index "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-index/_cards.scss"
  click Index "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-index/_categories.scss"
  click Index "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-index/index.html"
  click Analytics "https://github.com/googlecodelabs/codelab-elements/tree/master/google-codelab-analytics/"
  click Analytics "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-analytics/BUILD.bazel"
  click Analytics "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-analytics/google_codelab_analytics.js"
  click Analytics "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-analytics/google_codelab_analytics_def.js"
  click Analytics "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-analytics/google_codelab_analytics_test.js"
  click Survey "https://github.com/googlecodelabs/codelab-elements/tree/master/google-codelab-survey/"
  click Survey "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-survey/BUILD.bazel"
  click Survey "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-survey/google_codelab_survey.js"
  click Survey "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-survey/google_codelab_survey_def.js"
  click Survey "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-survey/google_codelab_survey.scss"
  click Survey "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-survey/google-codelab-survey.html"
  click Survey "https://github.com/googlecodelabs/codelab-elements/blob/master/google-codelab-survey/google_codelab_survey_test.js"
  click CodelabHTML "https://github.com/googlecodelabs/codelab-elements/blob/master/demo/codelab.html"
  click CodelabHTML "https://github.com/googlecodelabs/codelab-elements/blob/master/demo/embed.html"
  click CodelabHTML "https://github.com/googlecodelabs/codelab-elements/blob/master/demo/hello.html"
  click HelloJS "https://github.com/googlecodelabs/codelab-elements/blob/master/demo/hello.js"
  click HelloJS "https://github.com/googlecodelabs/codelab-elements/blob/master/demo/hello_test.js"
  click DemoImg "https://github.com/googlecodelabs/codelab-elements/tree/master/demo/img/"
  click ES6 "https://github.com/googlecodelabs/codelab-elements/blob/master/third_party/BUILD.es6shim"
  click Polyfill "https://github.com/googlecodelabs/codelab-elements/blob/master/third_party/BUILD.polyfill"
  click Prettify "https://github.com/googlecodelabs/codelab-elements/blob/master/third_party/BUILD.prettify"
  click BazelWorkspace "https://github.com/googlecodelabs/codelab-elements/tree/master/WORKSPACE"
  click BazelWorkspace "https://github.com/googlecodelabs/codelab-elements/blob/master/BUILD.bazel"
  click CIPresubmit "https://github.com/googlecodelabs/codelab-elements/blob/master/tools/ci-presubmit.sh"
  click CIContinuous "https://github.com/googlecodelabs/codelab-elements/blob/master/tools/ci-continuous.sh"
  click ServerGo "https://github.com/googlecodelabs/codelab-elements/blob/master/tools/server.go"
  click WebtestGo "https://github.com/googlecodelabs/codelab-elements/blob/master/tools/webtest.go"

  %% Styles
  classDef source fill:#9f6,stroke:#090,color:#000
  classDef build fill:#6cf,stroke:#039,color:#000
  classDef demo fill:#6cf,stroke:#036,color:#fff
  classDef third fill:#ccc,stroke:#888,color:#000
  classDef runtime fill:#fc6,stroke:#f80,color:#000

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