---
created: 2025-06-26 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/webkit/speedometer
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


# speedometer repo project
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
title: "speedometer repo project"
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
    %% Static Host Layer
    subgraph "Static Asset Host"
        direction TB
        Config["netlify.toml"]:::fs
        HomePage["index.html"]:::fs
        AboutPage["about.html"]:::fs
        Instructions["instructions.html"]:::fs
    end

    %% Browser Runtime
    Browser["Browser Environment\n(Chrome/Firefox)"]:::browser

    %% Benchmark Harness
    subgraph "Benchmark Harness" 
        direction TB
        Runner["benchmark-runner.mjs"]:::fs
        Suite["suite-runner.mjs"]:::fs
        MainMod["main.mjs"]:::fs
        SharedBM["shared/benchmark.mjs"]:::fs
        SharedHP["shared/helpers.mjs"]:::fs
        SharedPM["shared/params.mjs"]:::fs
        SharedTR["shared/test-runner.mjs"]:::fs
        SharedTI["shared/test-invoker.mjs"]:::fs
    end

    %% Workload Modules
    subgraph "Workload Modules" 
        direction TB
        Charts["resources/charts/"]:::workload
        Editors["resources/editors/"]:::workload
        NewsSite["resources/newssite/"]:::workload
        PerfWebkit["resources/perf.webkit.org/"]:::workload
        StockCharts["resources/react-stockcharts/"]:::workload
        TodoMVC["resources/todomvc/"]:::workload
        BigDOM["resources/big-dom-generator/"]:::workload
        TodoMVCCSS["resources/todomvc-css/"]:::workload
        VanillaEx["resources/vanilla-examples/"]:::workload
        ExpTodoMVC["experimental/todomvc-localstorage/"]:::workload
    end

    %% Measurement Engine
    subgraph "Measurement Engine"
        direction TB
        MetricCore["metric.mjs"]:::fs
        MetricUI["metric-ui.mjs"]:::fs
        Stats["statistics.mjs"]:::fs
        Translations["translations.mjs"]:::fs
    end

    %% Reporting UI
    subgraph "Reporting UI"
        direction TB
        DevReport["resources/charts/developer.html"]:::fs
        EdReport["resources/editors/index.html"]:::fs
        Style["resources/main.css"]:::fs
        UIHome["index.html"]:::fs
    end

    %% Node.js Automation
    subgraph "Node.js Automation" 
        direction TB
        End2End["tests/run-end2end.mjs"]:::automation
        UnitTests["tests/run-unittests.mjs"]:::automation
        Server["tests/server.mjs"]:::automation
        HelperTest["tests/helper.mjs"]:::automation
        UT_Bench["tests/unittests/benchmark-runner.mjs"]:::automation
        UT_Params["tests/unittests/params.mjs"]:::automation
    end

    %% CI Pipeline
    subgraph "CI Pipeline"
        direction TB
        Workflow[".github/workflows/test.yml"]:::ci
        Scripts["package.json scripts"]:::ci
    end

    %% Connections
    Config -->|HTTP GET| Browser
    HomePage -->|loads| Browser
    AboutPage -->|loads| Browser
    Instructions -->|loads| Browser

    Browser -->|bootstraps| Runner
    Runner -->|imports| Suite
    Suite -->|uses| MainMod

    Runner -->|dynamically loads| Charts
    Runner -->|dynamically loads| Editors
    Runner -->|dynamically loads| NewsSite
    Runner -->|dynamically loads| PerfWebkit
    Runner -->|dynamically loads| StockCharts
    Runner -->|dynamically loads| TodoMVC
    Runner -->|dynamically loads| BigDOM
    Runner -->|dynamically loads| TodoMVCCSS
    Runner -->|dynamically loads| VanillaEx
    Runner -->|dynamically loads| ExpTodoMVC

    Charts <-->|executes workloads| MetricCore
    Editors <-->|executes workloads| MetricCore
    NewsSite <-->|executes workloads| MetricCore
    PerfWebkit <-->|executes workloads| MetricCore
    StockCharts <-->|executes workloads| MetricCore
    TodoMVC <-->|executes workloads| MetricCore
    BigDOM <-->|executes workloads| MetricCore
    TodoMVCCSS <-->|executes workloads| MetricCore
    VanillaEx <-->|executes workloads| MetricCore
    ExpTodoMVC <-->|executes workloads| MetricCore

    MetricCore -->|collects data| MetricUI
    MetricCore -->|calculates stats| Stats
    MetricCore -->|loads translations| Translations

    Stats -->|aggregates metrics| DevReport
    Stats -->|aggregates metrics| EdReport
    Style -->|styles| DevReport
    Style -->|styles| EdReport
    UIHome -->|bootstraps UI| DevReport

    Workflow -->|triggers| End2End
    Workflow -->|triggers| UnitTests
    Scripts -->|invoke| End2End
    Scripts -->|invoke| UnitTests

    End2End -->|launches headless| Browser
    End2End -->|runs| Runner
    UnitTests -->|tests modules| Runner

    End2End -->|outputs| Server
    Server -->|serves| UIHome

    %% Click Events
    click Config "https://github.com/webkit/speedometer/blob/main/netlify.toml"
    click HomePage "https://github.com/webkit/speedometer/blob/main/index.html"
    click AboutPage "https://github.com/webkit/speedometer/blob/main/about.html"
    click Instructions "https://github.com/webkit/speedometer/blob/main/instructions.html"

    click Runner "https://github.com/webkit/speedometer/blob/main/resources/benchmark-runner.mjs"
    click Suite "https://github.com/webkit/speedometer/blob/main/resources/suite-runner.mjs"
    click MainMod "https://github.com/webkit/speedometer/blob/main/resources/main.mjs"
    click SharedBM "https://github.com/webkit/speedometer/blob/main/resources/shared/benchmark.mjs"
    click SharedHP "https://github.com/webkit/speedometer/blob/main/resources/shared/helpers.mjs"
    click SharedPM "https://github.com/webkit/speedometer/blob/main/resources/shared/params.mjs"
    click SharedTR "https://github.com/webkit/speedometer/blob/main/resources/shared/test-runner.mjs"
    click SharedTI "https://github.com/webkit/speedometer/blob/main/resources/shared/test-invoker.mjs"

    click Charts "https://github.com/webkit/speedometer/tree/main/resources/charts/"
    click Editors "https://github.com/webkit/speedometer/tree/main/resources/editors/"
    click NewsSite "https://github.com/webkit/speedometer/tree/main/resources/newssite/"
    click PerfWebkit "https://github.com/webkit/speedometer/tree/main/resources/perf.webkit.org/"
    click StockCharts "https://github.com/webkit/speedometer/tree/main/resources/react-stockcharts/"
    click TodoMVC "https://github.com/webkit/speedometer/tree/main/resources/todomvc/"
    click BigDOM "https://github.com/webkit/speedometer/tree/main/resources/big-dom-generator/"
    click TodoMVCCSS "https://github.com/webkit/speedometer/tree/main/resources/todomvc-css/"
    click VanillaEx "https://github.com/webkit/speedometer/tree/main/resources/vanilla-examples/"
    click ExpTodoMVC "https://github.com/webkit/speedometer/tree/main/experimental/todomvc-localstorage/"

    click MetricCore "https://github.com/webkit/speedometer/blob/main/resources/metric.mjs"
    click MetricUI "https://github.com/webkit/speedometer/blob/main/resources/metric-ui.mjs"
    click Stats "https://github.com/webkit/speedometer/blob/main/resources/statistics.mjs"
    click Translations "https://github.com/webkit/speedometer/blob/main/resources/translations.mjs"

    click DevReport "https://github.com/webkit/speedometer/blob/main/resources/charts/developer.html"
    click EdReport "https://github.com/webkit/speedometer/blob/main/resources/editors/index.html"
    click Style "https://github.com/webkit/speedometer/blob/main/resources/main.css"
    click UIHome "https://github.com/webkit/speedometer/blob/main/index.html"

    click End2End "https://github.com/webkit/speedometer/blob/main/tests/run-end2end.mjs"
    click UnitTests "https://github.com/webkit/speedometer/blob/main/tests/run-unittests.mjs"
    click Server "https://github.com/webkit/speedometer/blob/main/tests/server.mjs"
    click HelperTest "https://github.com/webkit/speedometer/blob/main/tests/helper.mjs"
    click UT_Bench "https://github.com/webkit/speedometer/blob/main/tests/unittests/benchmark-runner.mjs"
    click UT_Params "https://github.com/webkit/speedometer/blob/main/tests/unittests/params.mjs"

    click Workflow "https://github.com/webkit/speedometer/blob/main/.github/workflows/test.yml"
    click Scripts "https://github.com/webkit/speedometer/blob/main/package.json"

    %% Styles
    classDef browser fill:#BBDEFB,stroke:#1E88E5,color:#0D47A1;
    classDef workload fill:#C8E6C9,stroke:#2E7D32,color:#1B5E20;
    classDef fs fill:#F1F8E9,stroke:#4CAF50,color:#2E7D32;
    classDef automation fill:#FFE0B2,stroke:#FB8C00,color:#E65100;
    classDef ci fill:#E1BEE7,stroke:#8E24AA,color:#4A148C;
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