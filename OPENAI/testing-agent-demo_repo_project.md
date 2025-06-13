---
created: 2025-06-012 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/openai-testing-agent-demo
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExcXphbTlidzFscTJqZTBiOHFsMWNtaGFhYnM3aWNocjd6cWlmZGhvayZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/ecfn0jrPydL2M/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# openai-testing-agent-demo repo project
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
title: "openai-testing-agent-demo repo project"
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
    subgraph "User Layer"
        Browser(["🧑‍💻 Browser<br/>(port3000)"]):::user
    end

    subgraph "Client Layer"
        FrontendUI["Next.js Frontend<br/>(3000)"]:::frontend
        subgraph "FE Components"
            ConfigPanel["ConfigPanel"]:::frontend
            SidePanel["SidePanel"]:::frontend
            TaskSteps["TaskSteps"]:::frontend
            SocketIOManager["SocketIOManager"]:::frontend
            MainPageFE["page.tsx"]:::frontend
        end
    end

    subgraph "Orchestration Layer"
        CUAServer["CUA Server<br/>(WS 8080)"]:::orchestration
        subgraph "Handlers"
            HandlerInit["test-case-initiation-handler"]:::orchestration
            HandlerUpdate["test-case-update-handler"]:::orchestration
            HandlerUserMsgs["user-messages-handler"]:::orchestration
            HandlerLoop["cua-loop-handler"]:::orchestration
            HandlerAction["action-handler"]:::orchestration
        end
        subgraph "Agents"
            AgentTC["test-case-agent"]:::orchestration
            AgentReview["test-script-review-agent"]:::orchestration
        end
        subgraph "Services"
            ServiceOpenAI["openai-cua-client"]:::orchestration
            ServiceLogin["login-service"]:::orchestration
        end
        LibLoop["computer-use-loop"]:::orchestration
        IndexServer["index.ts"]:::orchestration
        Playwright["🎭 Headless Browser"]:::playwright
    end

    subgraph "Target Layer"
        SampleApp["Next.js Sample App<br/>(3005)"]:::target
        subgraph "API Routes"
            APIAuth["auth/login API"]:::target
            APIOrders["orders API"]:::target
            APIStyleID["store/styles/[id] API"]:::target
            APIStyle["store/styles API"]:::target
        end
        subgraph "UI Components"
            CartView["CartView"]:::target
            ItemCard["ItemCard"]:::target
            ShopContent["ShopPageContent"]:::target
            OrderSuccess["OrderSuccess"]:::target
        end
        LayoutTA["layout.tsx"]:::target
        PageTA["page.tsx"]:::target
    end

    subgraph "External"
        OpenAI["OpenAI API"]:::external
    end

    Browser -->|"HTTP GET /"| FrontendUI
    FrontendUI -->|"WebSocket: Start Test"| CUAServer
    CUAServer -->|"OpenAI API call"| OpenAI
    CUAServer -->|"Playwright commands"| Playwright
    Playwright -->|"HTTP actions"| SampleApp
    SampleApp -->|"HTTP responses"| Playwright
    CUAServer -->|"WebSocket events"| FrontendUI

    click FrontendUI "https://github.com/openai/openai-testing-agent-demo/tree/main/frontend/"
    click ConfigPanel "https://github.com/openai/openai-testing-agent-demo/blob/main/frontend/components/ConfigPanel.tsx"
    click SidePanel "https://github.com/openai/openai-testing-agent-demo/blob/main/frontend/components/SidePanel.tsx"
    click TaskSteps "https://github.com/openai/openai-testing-agent-demo/blob/main/frontend/components/TaskSteps.tsx"
    click SocketIOManager "https://github.com/openai/openai-testing-agent-demo/blob/main/frontend/components/SocketIOManager.tsx"
    click MainPageFE "https://github.com/openai/openai-testing-agent-demo/blob/main/frontend/app/page.tsx"

    click CUAServer "https://github.com/openai/openai-testing-agent-demo/blob/main/cua-server/src/index.ts"
    click HandlerInit "https://github.com/openai/openai-testing-agent-demo/blob/main/cua-server/src/handlers/test-case-initiation-handler.ts"
    click HandlerUpdate "https://github.com/openai/openai-testing-agent-demo/blob/main/cua-server/src/handlers/test-case-update-handler.ts"
    click HandlerUserMsgs "https://github.com/openai/openai-testing-agent-demo/blob/main/cua-server/src/handlers/user-messages-handler.ts"
    click HandlerLoop "https://github.com/openai/openai-testing-agent-demo/blob/main/cua-server/src/handlers/cua-loop-handler.ts"
    click HandlerAction "https://github.com/openai/openai-testing-agent-demo/blob/main/cua-server/src/handlers/action-handler.ts"
    click AgentTC "https://github.com/openai/openai-testing-agent-demo/blob/main/cua-server/src/agents/test-case-agent.ts"
    click AgentReview "https://github.com/openai/openai-testing-agent-demo/blob/main/cua-server/src/agents/test-script-review-agent.ts"
    click ServiceOpenAI "https://github.com/openai/openai-testing-agent-demo/blob/main/cua-server/src/services/openai-cua-client.ts"
    click ServiceLogin "https://github.com/openai/openai-testing-agent-demo/blob/main/cua-server/src/services/login-service.ts"
    click LibLoop "https://github.com/openai/openai-testing-agent-demo/blob/main/cua-server/src/lib/computer-use-loop.ts"

    click SampleApp "https://github.com/openai/openai-testing-agent-demo/tree/main/sample-test-app/"
    click APIAuth "https://github.com/openai/openai-testing-agent-demo/blob/main/sample-test-app/app/api/auth/login/route.ts"
    click APIOrders "https://github.com/openai/openai-testing-agent-demo/blob/main/sample-test-app/app/api/services/orders/route.ts"
    click APIStyleID "https://github.com/openai/openai-testing-agent-demo/blob/main/sample-test-app/app/api/store/styles/[id]/route.ts"
    click APIStyle "https://github.com/openai/openai-testing-agent-demo/blob/main/sample-test-app/app/api/store/styles/route.ts"
    click CartView "https://github.com/openai/openai-testing-agent-demo/blob/main/sample-test-app/components/CartView.tsx"
    click ItemCard "https://github.com/openai/openai-testing-agent-demo/blob/main/sample-test-app/components/ItemCard.tsx"
    click ShopContent "https://github.com/openai/openai-testing-agent-demo/blob/main/sample-test-app/components/ShopPageContent.tsx"
    click OrderSuccess "https://github.com/openai/openai-testing-agent-demo/blob/main/sample-test-app/components/OrderSuccess.tsx"
    click LayoutTA "https://github.com/openai/openai-testing-agent-demo/blob/main/sample-test-app/app/layout.tsx"
    click PageTA "https://github.com/openai/openai-testing-agent-demo/blob/main/sample-test-app/app/page.tsx"

    classDef user fill:#FFEB3B,stroke:#FBC02D,color:#000
    classDef frontend fill:#BBDEFB,stroke:#2196F3,color:#000
    classDef orchestration fill:#C8E6C9,stroke:#4CAF50,color:#000
    classDef playwright fill:#FFE0B2,stroke:#FF9800,color:#000
    classDef target fill:#D1C4E9,stroke:#7E57C2,color:#000
    classDef external fill:#C8E6C9,stroke:#388E3C,color:#000

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
