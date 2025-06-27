---
created: 2025-06-26 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/WebKit/MotionMark
---

<div align="center">
  <p>⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷</p>
  <i>This is a working draft in progress.</i>
  <br/>
  <img alt="Loading…" src="https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExeHJ4YXdtYjJpMDl0MzEwYmU4ZzBobG0waGNiN3MzNzR0d2R2NnMwNSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/26gssNOlBJKjEM3yo/giphy.gif"/>
  <br/>
  <blockquote>
	  <i>gif image is provided by <a href="https://giphy.com">Giphy</a></i>
  </blockquote>
  <p>⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷</p>

</div>


# MotionMark repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for 👨‍🎓 <ins>educational purposes</ins> 👨‍🎓 (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), 📖 <ins> personal study </ins> 📖, and 🔖 <ins> reference </ins> 🔖.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


---

```mermaid
---
title: "MotionMark repo project"
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
flowchart TB
    subgraph "User Interface Layer"
        Index["index.html"]:::frontend
        About["about.html"]:::frontend
        Developer["developer.html"]:::frontend
        UI_CSS["motionmark.css"]:::frontend
        MotionMarkJS["motionmark.js"]:::frontend
        ResultsJS["results.js"]:::frontend
    end

    subgraph "Core Benchmark Engine"
        CORE_RUNNER["benchmark-runner.js"]:::core
        DEBUG_RUNNER["debug-runner.js"]:::core
        GraphJS["graph.js"]:::core
        TestsJS["tests.js"]:::core
    end

    subgraph "Test Suites"
        direction TB
        TS_ALL["3D, Bouncing, Core, DOM, Simple, SVG, Template, Text Tests"]:::tests
    end

    subgraph "Results Processor & Extensions"
        RES_STATS["statistics.js"]:::util
        RES_STRINGS["strings.js"]:::util
        EXTENSIONS["extensions.js"]:::util
    end

    subgraph "Unit-Test Harness"
        UT_HARNESS["run-unit-tests.html"]:::unit
        UT_SCRIPTS["test-data-import.js, test-random.js, test-statistics.js"]:::unit
        UT_DATA["two-suite-single-iteration-test-data.json"]:::unit
    end

    Index -->|"loads"| CORE_RUNNER
    About -->|"loads"| CORE_RUNNER
    Developer -->|"loads"| CORE_RUNNER
    Index -->|"loads"| DEBUG_RUNNER

    CORE_RUNNER -->|"loads test suites"| TS_ALL
    DEBUG_RUNNER -->|"verbose run"| TS_ALL

    TS_ALL -->|"timing data"| RES_STATS
    RES_STATS -->|"metrics"| ResultsJS
    ResultsJS -->|"render charts"| Index

    ResultsJS -->|"hook calls"| EXTENSIONS

    UT_HARNESS -->|"load tests"| UT_SCRIPTS
    UT_SCRIPTS -->|"uses data"| UT_DATA

    click Index "https://github.com/webkit/motionmark/blob/main/MotionMark/index.html"
    click About "https://github.com/webkit/motionmark/blob/main/MotionMark/about.html"
    click Developer "https://github.com/webkit/motionmark/blob/main/MotionMark/developer.html"
    click UI_CSS "https://github.com/webkit/motionmark/blob/main/MotionMark/resources/runner/motionmark.css"
    click MotionMarkJS "https://github.com/webkit/motionmark/blob/main/MotionMark/resources/runner/motionmark.js"
    click ResultsJS "https://github.com/webkit/motionmark/blob/main/MotionMark/resources/runner/results.js"
    click CORE_RUNNER "https://github.com/webkit/motionmark/blob/main/MotionMark/resources/runner/benchmark-runner.js"
    click DEBUG_RUNNER "https://github.com/webkit/motionmark/blob/main/MotionMark/resources/debug-runner/debug-runner.js"
    click GraphJS "https://github.com/webkit/motionmark/blob/main/MotionMark/resources/debug-runner/graph.js"
    click TestsJS "https://github.com/webkit/motionmark/blob/main/MotionMark/resources/debug-runner/tests.js"
    click RES_STATS "https://github.com/webkit/motionmark/blob/main/MotionMark/resources/statistics.js"
    click RES_STRINGS "https://github.com/webkit/motionmark/blob/main/MotionMark/resources/strings.js"
    click EXTENSIONS "https://github.com/webkit/motionmark/blob/main/MotionMark/resources/extensions.js"
    click UT_HARNESS "https://github.com/webkit/motionmark/blob/main/MotionMark/unit-tests/run-unit-tests.html"
    click UT_SCRIPTS "https://github.com/webkit/motionmark/blob/main/MotionMark/unit-tests/tests/test-data-import.js"
    click UT_DATA "https://github.com/webkit/motionmark/blob/main/MotionMark/unit-tests/data/two-suite-single-iteration-test-data.json"

    classDef frontend fill:#bbdefb,stroke:#0d47a1,color:#0d47a1
    classDef core fill:#c8e6c9,stroke:#1b5e20,color:#1b5e20
    classDef tests fill:#ffe0b2,stroke:#e65100,color:#e65100
    classDef util fill:#e1bee7,stroke:#4a148c,color:#4a148c
    classDef unit fill:#eceff1,stroke:#37474f,color:#37474f

```

----

```mermaid
---
title: "❓...CongLeSolutionX....❓"
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