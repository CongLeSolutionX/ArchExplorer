---
created: 2025-06-012 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/openai-go
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExY2tvYWIyOGRpbWZodTQ2YTI2bjQ1eHpoaDY0YTZ3Mms2aWhneHNlYSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/fR6aYF0SUJAeoypyub/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# openai-go repo project
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
title: "openai-go repo project"
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

    A["Application (User)"]
    B["Client Initialization (NewClient)"]
    C["Functional Options & Middleware"]
    
    subgraph "Internal Utilities"
        D["JSON Serialization"]
        E["JSON Utilities"]
        F["API Query Encoding"]
        G["Optional Parameter Handling"]
    end
    subgraph "API Modules"
        H["Chat Completions"]
        I["Fine Tuning"]
        J["Audio Endpoints"]
        K["Image Generation"]
        L["Moderation"]
        M["Beta Features"]
        N["Azure Integration"]
    end
    O["HTTP Request Dispatch"]
    P["OpenAI REST API"]
    Q["Azure Service Endpoint"]
    R["Examples & Testing"]

    A --> B
    B --> C
    C --> D
    C --> H
    C --> I
    C --> J
    C --> K
    C --> L
    C --> M
    C --> N
    D --> O
    H --> O
    I --> O
    J --> O
    K --> O
    L --> O
    M --> O
    N --> O
    O --> P
    N --> Q
    P -- "error/retry" --> B
    R --- A

    click B "client.go"
    click C "option/requestoption.go"
    click H "chat.go"
    click I "finetuning.go"
    click J "audio.go"
    click K "image.go"
    click L "moderation.go"
    click M "beta.go"
    click N "azure/azure.go"
    click D "https://github.com/openai/openai-go/blob/main/internal/apijson/encoder.go"
    click E "https://github.com/openai/openai-go/blob/main/internal/encoding/json/encode.go"
    click F "https://github.com/openai/openai-go/blob/main/internal/apiquery/encoder.go"
    click G "https://github.com/openai/openai-go/tree/main/internal/param"
    click R "https://github.com/openai/openai-go/tree/main/examples/"

    class B,C clientStyle
    class D,E,F,G internalStyle
    class H,I,J,K,L,M,N apiStyle
    class O externalStyle
    class P externalStyle
    class Q externalStyle
    class R exampleStyle

    classDef clientStyle fill:#AED6F1,stroke:#1B4F72,stroke-width:2px;
    classDef internalStyle fill:#D7BDE2,stroke:#6C3483,stroke-width:2px;
    classDef apiStyle fill:#F9E79F,stroke:#B7950B,stroke-width:2px;
    classDef externalStyle fill:#F5B7B1,stroke:#943126,stroke-width:2px;
    classDef exampleStyle fill:#D5F5E3,stroke:#239B56,stroke-width:2px;
    
    linkStyle 0 stroke:#1B4F72,stroke-width:2px
    linkStyle 1 stroke:#1B4F72,stroke-width:2px
    linkStyle 2 stroke:#6C3483,stroke-width:2px
    linkStyle 3 stroke:#B7950B,stroke-width:2px
    linkStyle 4 stroke:#B7950B,stroke-width:2px
    linkStyle 5 stroke:#B7950B,stroke-width:2px
    linkStyle 6 stroke:#B7950B,stroke-width:2px
    linkStyle 7 stroke:#B7950B,stroke-width:2px
    linkStyle 8 stroke:#B7950B,stroke-width:2px
    linkStyle 9 stroke:#239B56,stroke-width:2px
    linkStyle 10 stroke:#943126,stroke-width:2px
    linkStyle 11 stroke:#943126,stroke-width:2px
    linkStyle 12 stroke:#1B4F72,stroke-dasharray: 5, 5, stroke-width:2px
    linkStyle 13 stroke:#239B56,stroke-dasharray: 2, 2, stroke-width:2px

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