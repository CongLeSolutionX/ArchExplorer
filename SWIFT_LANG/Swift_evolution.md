---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/swiftlang/swift-evolution
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExY2R6NW96ZW9hbDBib2dma25jdDMzd251MnN4ODdwcHRjcTZlY2pmMCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/o37e1VlwzOvFS/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# Swift evolution repo project
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
title: "Swift evolution repo project"
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
    subgraph "Swift Evolution System"
        Templates["Proposal Templates"]
        Proposals["Proposal Management"]
        Releases["Release Documentation"]
        Visions["Vision Documents"]
        Process["Process Controls"]

        subgraph "Template Types"
            SwiftTemp["Swift Template"]
            SwiftPMTemp["SwiftPM Template"]
        end

        subgraph "Proposal States"
            Active["Active Proposals"]
            Implemented["Implemented"]
            Rejected["Rejected"]
        end

        subgraph "Process Documentation"
            Contributing["Contributing Guide"]
            Guidelines["Process Guidelines"]
            Common["Common Proposals"]
        end

        subgraph "Vision Areas"
            Embedded["Embedded Swift"]
            Macros["Macros"]
            Testing["Testing"]
        end
    end

    Templates --> SwiftTemp
    Templates --> SwiftPMTemp
    SwiftTemp --> Proposals
    SwiftPMTemp --> Proposals
    
    Proposals --> Active
    Proposals --> Implemented
    Proposals --> Rejected
    
    Process --> Contributing
    Process --> Guidelines
    Process --> Common
    
    Visions --> Embedded
    Visions --> Macros
    Visions --> Testing
    
    Process --> Proposals
    Visions --> Proposals
    Proposals --> Releases
    Visions --> Releases

    %% Click events for component mapping
    click Proposals "https://github.com/swiftlang/swift-evolution/tree/main//proposals/"
    click Templates "https://github.com/swiftlang/swift-evolution/tree/main//proposal-templates/"
    click SwiftTemp "https://github.com/swiftlang/swift-evolution/blob/main//proposal-templates/0000-swift-template.md"
    click SwiftPMTemp "https://github.com/swiftlang/swift-evolution/blob/main//proposal-templates/0000-swiftpm-template.md"
    click Releases "https://github.com/swiftlang/swift-evolution/tree/main//releases/"
    click Visions "https://github.com/swiftlang/swift-evolution/tree/main//visions/"
    click Contributing "https://github.com/swiftlang/swift-evolution/blob/main//CONTRIBUTING.md"
    click Guidelines "https://github.com/swiftlang/swift-evolution/blob/main//process.md"
    click Common "https://github.com/swiftlang/swift-evolution/blob/main//commonly_proposed.md"

    %% Styling
    classDef default fill:#f9f9f9,stroke:#333,stroke-width:2px
    classDef template fill:#FFE873,stroke:#333
    classDef proposal fill:#9DC3E6,stroke:#333
    classDef vision fill:#D4A6E9,stroke:#333
    classDef process fill:#A8D08D,stroke:#333
    
    class Templates,SwiftTemp,SwiftPMTemp template
    class Proposals,Active,Implemented,Rejected proposal
    class Visions,Embedded,Macros,Testing vision
    class Process,Contributing,Guidelines,Common process
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
