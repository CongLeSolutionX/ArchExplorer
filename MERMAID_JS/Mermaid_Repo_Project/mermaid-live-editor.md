---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is an ongoing document collecting notes for personal educational purposes and references. 
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExeHJ4YXdtYjJpMDl0MzEwYmU4ZzBobG0waGNiN3MzNzR0d2R2NnMwNSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/26gssNOlBJKjEM3yo/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----

# mermaid-live-editor
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## A Diagrammatic Guide 




```mermaid
---
title: "MERMAID-JS - mermaid-live-editor"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "flowchart": { "htmlLabels": true, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TB
    subgraph Client["Client"]
    style Client fill:#c222,stroke:#333,stroke-width:2px
        Browser["Web Browser"]
    end

    subgraph FrontendApp["Frontend Application"]
    style FrontendApp fill:#c222,stroke:#333,stroke-width:2px
        direction TB
        SvelteKit["SvelteKit Application"]:::frontend
        
        subgraph Components["Components"]
            direction TB
            Editor["Editor Component"]:::frontend
            Preview["Preview Component"]:::frontend
            Actions["Actions Component"]:::frontend
            History["History Component"]:::frontend
            Theme["Theme Management"]:::frontend
            View["View Component"]:::frontend
        end

        subgraph Routes["Routes"]
            direction TB
            EditRoute["Edit Route"]:::frontend
            ViewRoute["View Route"]:::frontend
        end

        subgraph Utilities["Utilities"]
            direction TB
            StateManagement["State Management"]:::frontend
            MermaidIntegration["Mermaid Integration"]:::frontend
            FileLoaders["File Loaders"]:::frontend
            ThemeUtils["Theme Utilities"]:::frontend
            Persistence["Persistence Layer"]:::frontend
            ErrorHandler["Error Handling"]:::frontend
        end
    end

    subgraph ExternalServices["External Services"]
    style ExternalServices fill:#c222,stroke:#333,stroke-width:2px
        direction TB
        RenderService["Rendering Service<br>(mermaid.ink)"]:::service
        KrokiService["Kroki Service"]:::service
        Analytics["Analytics Service<br>(Plausible)"]:::service
        MermaidChart["Mermaid Chart Service"]:::service
    end

    subgraph Infrastructure["Infrastructure"]
    style Infrastructure fill:#c222,stroke:#333,stroke-width:2px
        direction TB
        Docker["Docker Container"]:::infra
        Nginx["Nginx Server"]:::infra
        Netlify["Netlify Deployment"]:::infra
        Testing["Testing Infrastructure"]:::infra
    end

    %% Relationships
    Browser --> SvelteKit
    SvelteKit --> Components
    SvelteKit --> Routes
    Components --> Utilities
    FrontendApp --> ExternalServices
    ExternalServices --> Infrastructure

    %% Click Events
    click SvelteKit "https://github.com/mermaid-js/mermaid-live-editor/tree/develop/src"
    click Editor "https://github.com/mermaid-js/mermaid-live-editor/blob/develop/src/lib/components/Editor.svelte"
    click Actions "https://github.com/mermaid-js/mermaid-live-editor/blob/develop/src/lib/components/Actions.svelte"
    click History "https://github.com/mermaid-js/mermaid-live-editor/blob/develop/src/lib/components/History/History.svelte"
    click Theme "https://github.com/mermaid-js/mermaid-live-editor/blob/develop/src/lib/components/Theme.svelte"
    click View "https://github.com/mermaid-js/mermaid-live-editor/blob/develop/src/lib/components/View.svelte"
    click EditRoute "https://github.com/mermaid-js/mermaid-live-editor/blob/develop/src/routes/edit/+page.svelte"
    click ViewRoute "https://github.com/mermaid-js/mermaid-live-editor/blob/develop/src/routes/view/+page.svelte"
    click MermaidIntegration "https://github.com/mermaid-js/mermaid-live-editor/blob/develop/src/lib/util/mermaid.ts"
    click StateManagement "https://github.com/mermaid-js/mermaid-live-editor/blob/develop/src/lib/util/state.ts"
    click FileLoaders "https://github.com/mermaid-js/mermaid-live-editor/blob/develop/src/lib/util/fileLoaders/gist.ts"
    click Docker "https://github.com/mermaid-js/mermaid-live-editor/tree/develop/Dockerfile"
    click Nginx "https://github.com/mermaid-js/mermaid-live-editor/blob/develop/nginx.conf"
    click Netlify "https://github.com/mermaid-js/mermaid-live-editor/blob/develop/netlify.toml"
    click Testing "https://github.com/mermaid-js/mermaid-live-editor/tree/develop/cypress"
    click ThemeUtils "https://github.com/mermaid-js/mermaid-live-editor/blob/develop/src/lib/util/theme.ts"
    click Persistence "https://github.com/mermaid-js/mermaid-live-editor/blob/develop/src/lib/util/persist.ts"
    click ErrorHandler "https://github.com/mermaid-js/mermaid-live-editor/blob/develop/src/lib/util/errorHandling.ts"

    %% Styling
    classDef frontend fill:#3d32,stroke:#2980b9,color:white
    classDef service fill:#2ec4,stroke:#27ae60,color:white
    classDef infra fill:#f4f3,stroke:#f39c12,color:black
    classDef default fill:#95a3,stroke:#7f8c8d,color:white

    %% Legend
    subgraph Legend["Legend"]
    style Legend fill:#c222,stroke:#333,stroke-width:2px
        Frontend["Frontend Component"]:::frontend
        Service["External Service"]:::service
        Infrastructure["Infrastructure"]:::infra
    end
    
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

  Closing_quote ~~~ My_Meme
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }

```

---
> **Licenses:**
>
> - **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
> - **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).
> 
---

