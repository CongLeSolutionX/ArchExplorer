---
created: 2025-06-012 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/sample-deep-research-mcp
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExcmNrdmhnMDAxMGNiMjdrcGdnbnc4YTFrNGxpajhrZTdvYWNkdnFxMiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/NZe7YqL8yvlxRpnnUk/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# sample-deep-research-mcp repo project
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
title: "sample-deep-research-mcp repo project"
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
    subgraph "Client Side"
        Client["Client (Consumer)"]:::client
    end

    subgraph "MCP Server (Python 3.x)"
        SSE["SSE Transport Layer\nHTTP SSE Endpoint"]:::server
        Logic["MCP Server Logic"]:::server
        Dependencies["Dependencies\n(requirements.txt)"]:::server
    end

    Data["Data Store\n(records.json)"]:::datastore

    subgraph "Repository Files"
        README["README.md"]:::docs
        LICENSE["LICENSE"]:::docs
        GITIGNORE[".gitignore"]:::docs
    end

    Client -->|"MCP query over HTTP"| SSE
    SSE -->|"Invoke query()"| Logic
    Logic -->|"Read JSON"| Data
    Logic -->|"SSE event stream"| Client

    click SSE "https://github.com/openai/sample-deep-research-mcp/blob/main/sample_mcp.py"
    click Logic "https://github.com/openai/sample-deep-research-mcp/blob/main/sample_mcp.py"
    click Data "https://github.com/openai/sample-deep-research-mcp/blob/main/records.json"
    click Dependencies "https://github.com/openai/sample-deep-research-mcp/blob/main/requirements.txt"
    click README "https://github.com/openai/sample-deep-research-mcp/blob/main/README.md"
    click LICENSE "https://github.com/openai/sample-deep-research-mcp/tree/main/LICENSE"
    click GITIGNORE "https://github.com/openai/sample-deep-research-mcp/blob/main/.gitignore"

    classDef client fill:#C6E5FF,stroke:#0366D6,stroke-width:1px
    classDef server fill:#D6F5D6,stroke:#2E8B57,stroke-width:1px
    classDef datastore fill:#FFE5B4,stroke:#CC5500,stroke-width:1px
    classDef docs fill:#F5F5F5,stroke:#666,stroke-width:1px

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
