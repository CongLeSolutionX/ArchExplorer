---
created: 2025-06-12 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/openai-structured-outputs-samples
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




# structured-outputs-samples repo project
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
title: "structured-outputs-samples repo project"
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
    subgraph Legend
        L1[Frontend Component]:::frontend
        L2["/API Route"]:::api
        L3[Service/Logic]:::service
        L4[External Service]:::external
        L5[State Management]:::state
    end

    subgraph "Resume Extraction Application"
        FD[File Dropper]:::frontend
        EVD[Extracted Values Display]:::frontend
        RER["/api/extract_resume"]:::api
        RPS[Resume Processing Service]:::service
        
        FD --> RER
        RER --> RPS
        RPS --> EVD
    end

    subgraph "Generative UI Application"
        CI1[Chat Interface]:::frontend
        UID[Dynamic UI Display]:::frontend
        GUR["/api/generate_ui"]:::api
        UIGS[UI Generation Service]:::service
        CMS1[Component Mapping System]:::service
        
        CI1 --> GUR
        GUR --> UIGS
        UIGS --> CMS1
        CMS1 --> UID
    end

    subgraph "Conversational Assistant Application"
        CI2[Chat Interface]:::frontend
        AC[Assistant Component]:::frontend
        TCD[Tool Call Display]:::frontend
        TRR["/api/turn_response"]:::api
        TR["/api/tools/*"]:::api
        AS[Assistant Service]:::service
        TH[Tools Handler]:::service
        CMS2[Component Mapping]:::service
        SM[State Management]:::state
        
        CI2 --> TRR
        TRR --> AS
        AS --> TH
        TH --> TR
        TR --> CMS2
        CMS2 --> AC
        TH --> TCD
        SM --> CI2
        SM --> AC
        SM --> TCD
    end

    OAPI[OpenAI API]:::external
    
    RPS --> OAPI
    UIGS --> OAPI
    AS --> OAPI

    %% Click events for component mapping
    click FD "https://github.com/openai/openai-structured-outputs-samples/blob/main/resume-extraction/components/file-dropper.tsx"
    click EVD "https://github.com/openai/openai-structured-outputs-samples/blob/main/resume-extraction/components/extracted-values.tsx"
    click RER "https://github.com/openai/openai-structured-outputs-samples/blob/main/resume-extraction/app/api/extract_resume/route.ts"
    click RPS "https://github.com/openai/openai-structured-outputs-samples/blob/main/resume-extraction/lib/resume.ts"
    
    click CI1 "https://github.com/openai/openai-structured-outputs-samples/blob/main/generative-ui/components/chat.tsx"
    click UID "https://github.com/openai/openai-structured-outputs-samples/blob/main/generative-ui/components/ui-display.tsx"
    click GUR "https://github.com/openai/openai-structured-outputs-samples/blob/main/generative-ui/app/api/generate_ui/route.ts"
    click UIGS "https://github.com/openai/openai-structured-outputs-samples/blob/main/generative-ui/lib/generate-ui-tool.ts"
    click CMS1 "https://github.com/openai/openai-structured-outputs-samples/blob/main/generative-ui/lib/components-mapping.tsx"
    
    click CI2 "https://github.com/openai/openai-structured-outputs-samples/blob/main/conversational-assistant/components/chat.tsx"
    click AC "https://github.com/openai/openai-structured-outputs-samples/blob/main/conversational-assistant/components/assistant.tsx"
    click TCD "https://github.com/openai/openai-structured-outputs-samples/blob/main/conversational-assistant/components/tool-call.tsx"
    click TRR "https://github.com/openai/openai-structured-outputs-samples/blob/main/conversational-assistant/app/api/turn_response/route.ts"
    click TR "https://github.com/openai/openai-structured-outputs-samples/tree/main/conversational-assistant/app/api/tools"
    click AS "https://github.com/openai/openai-structured-outputs-samples/blob/main/conversational-assistant/lib/assistant.ts"
    click TH "https://github.com/openai/openai-structured-outputs-samples/blob/main/conversational-assistant/lib/tools/tools-handling.ts"
    click CMS2 "https://github.com/openai/openai-structured-outputs-samples/blob/main/conversational-assistant/lib/components-mapping.tsx"
    click SM "https://github.com/openai/openai-structured-outputs-samples/blob/main/conversational-assistant/stores/useConversationStore.ts"

    classDef frontend fill:#3b82f6,color:#fff
    classDef api fill:#22c55e,color:#fff
    classDef service fill:#f97316,color:#fff
    classDef external fill:#8b5cf6,color:#fff
    classDef state fill:#ec4899,color:#fff
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