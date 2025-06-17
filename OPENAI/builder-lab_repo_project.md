---
created: 2025-06-12 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/openai-builder-lab
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




# builder-lab repo project
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
title: "builder-lab repo project"
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
    %% Frontend Layer
    subgraph "Frontend (Next.js App)" 
        direction TB
        UI["ChatWindow Component"]:::frontend
        MSG["MessageRendering Component"]:::frontend
        BTN1["AssistantButton Component"]:::frontend
        BTN2["ToolCallButton Component"]:::frontend
        STORE["useConversationStore"]:::frontend
        CLIENT["assistant.ts (API Client)"]:::frontend
        TOOLS["tools.ts (Core Tools Module)"]:::frontend
        CONST["constants.ts"]:::frontend
        UTILS["utils.ts"]:::frontend
        STYLES["globals.css"]:::config
        TAILWIND["tailwind.config.ts"]:::config
        NEXTCFG["next.config.mjs"]:::config
        PKG["package.json"]:::config
    end

    %% Backend Layer
    subgraph "Backend Layer" 
        direction TB
        API["Next.js API Route (/api/get_response)"]:::backend
        PY["Python Service (Flask app.py)"]:::backend
    end

    %% External Service
    OPENAI["OpenAI API"]:::external

    %% Config Layer
    ENV[".env (OPENAI_API_KEY)"]:::config

    %% Interactions
    UI -->|user input| CLIENT
    MSG -->|renders state| STORE
    BTN1 -->|triggers| CLIENT
    BTN2 -->|triggers| CLIENT
    CLIENT -->|POST /api/get_response| API
    CLIENT -->|POST Python endpoint| PY
    API -->|reads ENV & forwards| OPENAI
    PY -->|reads ENV & forwards| OPENAI
    OPENAI -->|response JSON| API
    OPENAI -->|response JSON| PY
    API -->|JSON response| CLIENT
    PY -->|JSON response| CLIENT
    CLIENT -->|updates| STORE
    STORE -->|state update| UI
    STORE -->|state update| MSG

    %% Click Events - Frontend
    click UI "https://github.com/openai/openai-builder-lab/blob/main/starting_point/frontend/components/chat.tsx"
    click MSG "https://github.com/openai/openai-builder-lab/blob/main/starting_point/frontend/components/message.tsx"
    click BTN1 "https://github.com/openai/openai-builder-lab/blob/main/starting_point/frontend/components/assistant.tsx"
    click BTN2 "https://github.com/openai/openai-builder-lab/blob/main/starting_point/frontend/components/tool-call.tsx"
    click STORE "https://github.com/openai/openai-builder-lab/blob/main/starting_point/frontend/stores/useConversationStore.ts"
    click CLIENT "https://github.com/openai/openai-builder-lab/blob/main/starting_point/frontend/lib/assistant.ts"
    click TOOLS "https://github.com/openai/openai-builder-lab/blob/main/starting_point/frontend/lib/tools.ts"
    click CONST "https://github.com/openai/openai-builder-lab/blob/main/starting_point/frontend/lib/constants.ts"
    click UTILS "https://github.com/openai/openai-builder-lab/blob/main/starting_point/frontend/lib/utils.ts"
    click API "https://github.com/openai/openai-builder-lab/blob/main/starting_point/frontend/app/api/get_response/route.ts"
    click STYLES "https://github.com/openai/openai-builder-lab/blob/main/starting_point/frontend/app/globals.css"
    click TAILWIND "https://github.com/openai/openai-builder-lab/blob/main/starting_point/frontend/tailwind.config.ts"
    click NEXTCFG "https://github.com/openai/openai-builder-lab/blob/main/starting_point/frontend/next.config.mjs"
    click PKG "https://github.com/openai/openai-builder-lab/blob/main/starting_point/frontend/package.json"

    %% Click Events - Backend
    click PY "https://github.com/openai/openai-builder-lab/blob/main/starting_point/python-backend/app.py"
    click ENV "https://github.com/openai/openai-builder-lab/blob/main/starting_point/python-backend/.env.example"

    %% Styles
    classDef frontend fill:#e0f7fa,stroke:#0288d1,stroke-width:1px
    classDef backend fill:#e0f2f1,stroke:#388e3c,stroke-width:1px
    classDef external fill:#ffebee,stroke:#c62828,stroke-width:1px
    classDef config fill:#f3e5f5,stroke:#6a1b9a,stroke-width:1px

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