---
created: 2025-06-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/github/scientist
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


# scientist repo project
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


----

```mermaid
---
title: "scientist repo project"
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
    subgraph User_Application["User Application"]
        UA["App Code"]:::app
    end

    subgraph Scientist_Gem_Core["Scientist Gem Core"]
        API["Scientist Public API<br/>(include Scientist, Scientist.run)"]:::core
        Factory["Experiment Factory<br/>(Default or Custom)"]:::core
        Default["Scientist::Default"]:::core
        Experiment["Scientist::Experiment Mixin"]:::core
        Observation["Scientist::Observation"]:::core
        Result["Scientist::Result"]:::core
        Errors["Scientist::Errors"]:::core
        Version["Scientist::VERSION"]:::core
        GemSpec["Gem Specification<br/>(scientist.gemspec)"]:::core
    end

    subgraph External_Publishers["External Publishers"]
        Publisher["Publisher Hook"]:::core
        StatsD["StatsD"]:::extsvc
        Redis["Redis"]:::extsvc
        CustomSink["Custom Sink"]:::extsvc
    end
    
    subgraph Test_and_CI["Test & CI"]
        Test["Test Harness<br/><b>test/scientist/</b>"]:::infra
        Scripts["Helper Scripts<br/><b>script/</b>"]:::infra
        CI["CI Config<br/><b>.github/workflows/ci.yml</b>"]:::infra
    end

    %% Data Flows
    UA -->|"science(name){…}"| API
    API -->|"select Experiment impl."| Factory
    Factory --> Default
    Factory -->|"or custom" | Experiment
    Default --> Experiment
    Experiment -->|"wrap blocks"| Observation
    Observation -->|"collect data"| Result
    Result -->|"publish(result)"| Publisher
    Publisher --> StatsD
    Publisher --> Redis
    Publisher --> CustomSink
    Test -->|"raise_on_mismatches" | Experiment
    CI --> Scripts

    %% Click Events
    click API "https://github.com/github/scientist/blob/main/lib/scientist.rb"
    click Default "https://github.com/github/scientist/blob/main/lib/scientist/default.rb"
    click Experiment "https://github.com/github/scientist/blob/main/lib/scientist/experiment.rb"
    click Observation "https://github.com/github/scientist/blob/main/lib/scientist/observation.rb"
    click Result "https://github.com/github/scientist/blob/main/lib/scientist/result.rb"
    click Errors "https://github.com/github/scientist/blob/main/lib/scientist/errors.rb"
    click Version "https://github.com/github/scientist/blob/main/lib/scientist/version.rb"
    click GemSpec "https://github.com/github/scientist/blob/main/scientist.gemspec"
    click Test "https://github.com/github/scientist/tree/main/test/scientist/"
    click Scripts "https://github.com/github/scientist/tree/main/script/"
    click CI "https://github.com/github/scientist/blob/main/.github/workflows/ci.yml"

    %% Styles
    classDef core fill:#D0E8FF,stroke:#0366D6,color:#0366D6;
    classDef app fill:#E6FFEA,stroke:#28A745,color:#28A745;
    classDef extsvc fill:#FFE8D6,stroke:#D25D00,color:#D25D00;
    classDef infra fill:#F2F2F2,stroke:#6A737D,color:#6A737D;
    classDef ext stroke-dasharray: 5 5,fill:#FFF,stroke:#8B0000,color:#8B0000;
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