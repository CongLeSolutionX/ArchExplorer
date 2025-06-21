---
created: 2025-06-19 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/googlecodelabs/monolith-to-microservices
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




# monolith-to-microservices repo project
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


----

```mermaid
---
title: "monolith-to-microservices repo project"
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
    Client["Client (Browser)\nReact SPA"]:::ui

    subgraph "Monolith Architecture"
        direction TB
        MonolithServer["Monolith API + UI\n(Node.js Server)\nPort 8080"]:::api
        MonolithPublic["Monolith Static Assets"]:::ui
        MonolithOrdersData["monolith/data/orders.json"]:::data
        MonolithProductsData["monolith/data/products.json"]:::data
    end

    subgraph "Microservices Architecture"
    direction TB
        subgraph "Kubernetes Cluster"
        %% :::platform
        direction TB
            FrontendMS["Frontend MS\n(UI Gateway)\nPort 8080"]:::api
            OrdersMS["Orders MS\nREST API\nPort 8081"]:::api
            ProductsMS["Products MS\nREST API\nPort 8082"]:::api
            OrdersData["microservices/src/orders/data/orders.json"]:::data
            ProductsData["microservices/src/products/data/products.json"]:::data
        end
    end

    Client -->|"HTTP GET"| MonolithServer
    MonolithServer -->|serves| MonolithPublic
    MonolithServer -->|reads| MonolithOrdersData
    MonolithServer -->|reads| MonolithProductsData

    Client -->|"HTTP GET"| FrontendMS
    FrontendMS -->|calls API| OrdersMS
    FrontendMS -->|calls API| ProductsMS
    OrdersMS -->|reads| OrdersData
    ProductsMS -->|reads| ProductsData

    %% Click Events
    click Client "https://github.com/googlecodelabs/monolith-to-microservices/tree/master/react-app/"
    click MonolithServer "https://github.com/googlecodelabs/monolith-to-microservices/blob/master/monolith/src/server.js"
    click MonolithPublic "https://github.com/googlecodelabs/monolith-to-microservices/tree/master/monolith/public/"
    click MonolithOrdersData "https://github.com/googlecodelabs/monolith-to-microservices/blob/master/monolith/data/orders.json"
    click MonolithProductsData "https://github.com/googlecodelabs/monolith-to-microservices/blob/master/monolith/data/products.json"
    click FrontendMS "https://github.com/googlecodelabs/monolith-to-microservices/tree/master/microservices/src/frontend/"
    click OrdersMS "https://github.com/googlecodelabs/monolith-to-microservices/tree/master/microservices/src/orders/"
    click ProductsMS "https://github.com/googlecodelabs/monolith-to-microservices/tree/master/microservices/src/products/"

    %% Styles
    classDef ui fill:#D6E9FF,stroke:#4A90E2,stroke-width:1px
    classDef api fill:#E6FFEA,stroke:#34A853,stroke-width:1px
    classDef data fill:#FFEFD6,stroke:#F4B400,stroke-width:1px
    classDef platform fill:#F0F0F0,stroke:#AAA,stroke-dasharray: 5 5


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