---
created: 2025-07-01 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/cloudflare/foundations
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




# foundations repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for 👨‍🎓 <ins>educational purposes</ins> 👨‍🎓 (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), 📖 <ins> personal study </ins> 📖, and 🔖 <ins> technical reference </ins> 🔖.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


----

```mermaid
---
title: "foundations repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright © 2025 Cong Le. All Rights Reserved."
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
    %% Application Layer
    UA["Example Application"]:::application
    UA -->|"(1) use macros"| Macros

    %% Macro Layer
    Macros["foundations-macros"]:::macros
    Macros -->|"generates"| API["foundations API Surface"]:::api

    %% Core Library Layer
    subgraph "foundations Core Library"
        direction TB
        API --> TelemetryCore
        API --> ConfigCore
        API --> SecurityCore
        API --> CLIHelper
        API --> TelemetryServer

        subgraph "Telemetry Sub-system"
            direction TB
            TelemetryCore["Telemetry Module"]:::telemetry
            TelemetryCore --> LoggingMod
            TelemetryCore --> MetricsMod
            TelemetryCore --> TracingMod
            TelemetryCore --> MemProf
            TelemetryCore --> OTLPConv
            TelemetryCore --> TokioMetrics
        end

        subgraph "Configuration Sub-system"
            direction TB
            ConfigCore["Config Module"]:::config
        end

        subgraph "Security Sub-system"
            direction TB
            SecurityCore["Security Module"]:::security
        end

        subgraph "CLI Helper"
            direction TB
            CLIHelper["CLI Helper"]:::api
        end

        subgraph "Telemetry Server"
            direction TB
            TelemetryServer["OTLP-gRPC Server"]:::telemetry
        end
    end

    %% Telemetry Modules
    LoggingMod["Logging Module"]:::telemetry
    MetricsMod["Metrics Module"]:::telemetry
    TracingMod["Tracing Module"]:::telemetry
    MemProf["Memory Profiler"]:::telemetry
    OTLPConv["OTLP Conversion"]:::telemetry
    TokioMetrics["Tokio Runtime Metrics"]:::telemetry

    %% External Systems
    subgraph "External Integrations"
        direction TB
        Logsinks["Log Sinks"]:::external
        MetricsBackends["Metrics Backends"]:::external
        TraceCollectors["Tracing Collectors"]:::external
        Jemalloc["jemalloc Profiler"]:::external
        SeccompSandbox["OS seccomp Sandbox"]:::external
    end

    LoggingMod -->|"routes logs"| Logsinks
    MetricsMod -->|"exports metrics"| MetricsBackends
    TracingMod -->|"exports spans"| TraceCollectors
    MemProf -->|"profiling data"| Jemalloc
    SecurityCore -->|"seccomp profiles"| SeccompSandbox

    %% Click Events - Macro Layer
    click Macros "https://github.com/cloudflare/foundations/tree/main/foundations-macros/"
    click Macros "https://github.com/cloudflare/foundations/blob/main/foundations-macros/src/lib.rs"
    click Macros "https://github.com/cloudflare/foundations/tree/main/foundations-macros/src/metrics/"
    click Macros "https://github.com/cloudflare/foundations/tree/main/foundations-macros/src/info_metric/"
    click Macros "https://github.com/cloudflare/foundations/blob/main/foundations-macros/src/settings.rs"
    click Macros "https://github.com/cloudflare/foundations/blob/main/foundations-macros/src/span_fn.rs"

    %% Click Events - Core Library
    click API "https://github.com/cloudflare/foundations/blob/main/foundations/src/lib.rs"
    click CLIHelper "https://github.com/cloudflare/foundations/blob/main/foundations/src/cli.rs"

    click TelemetryCore "https://github.com/cloudflare/foundations/tree/main/foundations/src/telemetry/"
    click TelemetryCore "https://github.com/cloudflare/foundations/blob/main/foundations/src/telemetry/driver.rs"
    click LoggingMod "https://github.com/cloudflare/foundations/tree/main/foundations/src/telemetry/log/"
    click MetricsMod "https://github.com/cloudflare/foundations/tree/main/foundations/src/telemetry/metrics/"
    click TracingMod "https://github.com/cloudflare/foundations/tree/main/foundations/src/telemetry/tracing/"
    click MemProf "https://github.com/cloudflare/foundations/blob/main/foundations/src/telemetry/memory_profiler.rs"
    click OTLPConv "https://github.com/cloudflare/foundations/tree/main/foundations/src/telemetry/otlp_conversion/"
    click TokioMetrics "https://github.com/cloudflare/foundations/tree/main/foundations/src/telemetry/tokio_runtime_metrics/"
    click TelemetryServer "https://github.com/cloudflare/foundations/tree/main/foundations/src/telemetry/server/"
    click TelemetryCore "https://github.com/cloudflare/foundations/tree/main/foundations/src/telemetry/settings/"
    click TelemetryCore "https://github.com/cloudflare/foundations/blob/main/foundations/src/telemetry/telemetry_context.rs"

    click SecurityCore "https://github.com/cloudflare/foundations/blob/main/foundations/src/security/mod.rs"
    click SecurityCore "https://github.com/cloudflare/foundations/blob/main/foundations/src/security/internal.rs"
    click SecurityCore "https://github.com/cloudflare/foundations/blob/main/foundations/src/security/common_syscall_allow_lists.rs"
    click SecurityCore "https://github.com/cloudflare/foundations/tree/main/foundations/src/security/libseccomp/"
    click SecurityCore "https://github.com/cloudflare/foundations/tree/main/foundations/src/security/syscalls/"

    click ConfigCore "https://github.com/cloudflare/foundations/blob/main/foundations/src/settings/mod.rs"
    click ConfigCore "https://github.com/cloudflare/foundations/blob/main/foundations/src/settings/basic_impls.rs"
    click ConfigCore "https://github.com/cloudflare/foundations/blob/main/foundations/src/settings/collections.rs"
    click ConfigCore "https://github.com/cloudflare/foundations/blob/main/foundations/src/settings/net.rs"
    click ConfigCore "https://github.com/cloudflare/foundations/tree/main/foundations/src/settings/"

    click UA "https://github.com/cloudflare/foundations/tree/main/examples/http_server/"
    click UA "https://github.com/cloudflare/foundations/blob/main/examples/http_server/main.rs"
    click UA "https://github.com/cloudflare/foundations/blob/main/examples/http_server/metrics.rs"
    click UA "https://github.com/cloudflare/foundations/blob/main/examples/http_server/settings.rs"
    click UA "https://github.com/cloudflare/foundations/blob/main/examples/http_server/example_conf.yaml"

    %% Styles
    classDef application fill:#EFEFFF,stroke:#0000CC,color:#0000CC;
    classDef macros fill:#FFF0E0,stroke:#CC6600,color:#CC6600;
    classDef api fill:#E0FFE0,stroke:#00AA00,color:#00AA00;
    classDef telemetry fill:#E0F0FF,stroke:#3366CC,color:#3366CC;
    classDef config fill:#E0FFE0,stroke:#33AA33,color:#33AA33;
    classDef security fill:#FFE0E0,stroke:#CC3333,color:#CC3333;
    classDef external fill:#EEEEEE,stroke:#888888,color:#555555;

```

-----

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
copyright: "Copyright © 2025 Cong Le. All Rights Reserved."
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