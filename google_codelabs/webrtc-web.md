---
created: 2025-06-19 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/googlecodelabs/webrtc-web
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




# webrtc-web repo project
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


---

```mermaid
---
title: "webrtc-web repo project"
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
flowchart TD
    %% Browser Clients
    subgraph "Browser Client (Sample Step-06)"
    direction TB
        S06_UI["UI (HTML/CSS)"]:::static
        S06_CSS["Stylesheet (main.css)"]:::static
        S06_JS["WebRTC Logic (main.js)"]:::static
    end

    subgraph "Browser Client (Work Final)"
    direction TB
        W_UI["UI (HTML/CSS)"]:::static
        W_CSS["Stylesheet (main.css)"]:::static
        W_SHIM["Shim (adapter.js)"]:::static
        W_JS["WebRTC Logic (main.js)"]:::static
    end

    %% Signaling Server
    subgraph "Signaling Server (Node.js Stub)" 
    direction TB
        SIG_IDX["index.js"]:::external
        SIG_PKG["package.json"]:::external
    end

    %% External Services
    STUN["STUN/TURN Server"]:::external

    %% Peer Client
    Peer2["Peer Browser Client #2"]:::static

    %% Connections
    S06_UI -->|"loads logic"| S06_JS
    S06_JS -->|"uses shim"| Shim["Shim<br/>(adapter.js)"]:::static
    S06_JS -->|HTTP GET/WS Signaling| SIG_IDX
    W_UI -->|"loads logic"| W_JS
    W_JS -->|"uses shim"| W_SHIM
    W_JS -->|"HTTP GET/WS Signaling"| SIG_IDX

    %% P2P Media & Data
    S06_JS -->|"Media<br/>(RTP)"| Peer2
    S06_JS -.->|DataChannel| Peer2
    W_JS -->|"Media<br/>(RTP)"| Peer2
    W_JS -.->|"DataChannel"| Peer2

    %% ICE via STUN/TURN
    S06_JS -.->|"ICE Binding"| STUN
    W_JS -.->|"ICE Binding"| STUN

    %% Legend
    subgraph Legend
    direction TB
        A["Solid = media<br/>Dashed = data/control"]
    end

    %% Click Events
    click S06_UI "https://github.com/googlecodelabs/webrtc-web/blob/master/step-06/index.html"
    click S06_CSS "https://github.com/googlecodelabs/webrtc-web/blob/master/step-06/css/main.css"
    click S06_JS "https://github.com/googlecodelabs/webrtc-web/blob/master/step-06/js/main.js"
    click Shim "https://github.com/googlecodelabs/webrtc-web/blob/master/js/lib/adapter.js"
    click W_UI "https://github.com/googlecodelabs/webrtc-web/blob/master/work/index.html"
    click W_CSS "https://github.com/googlecodelabs/webrtc-web/blob/master/work/css/main.css"
    click W_SHIM "https://github.com/googlecodelabs/webrtc-web/blob/master/work/js/lib/adapter.js"
    click W_JS "https://github.com/googlecodelabs/webrtc-web/blob/master/work/js/main.js"
    click SIG_IDX "https://github.com/googlecodelabs/webrtc-web/blob/master/step-06/index.js"
    click SIG_PKG "https://github.com/googlecodelabs/webrtc-web/blob/master/step-06/package.json"

    %% Styles
    classDef static fill:#ADD8E6,stroke:#333,stroke-width:1px;
    classDef external fill:#FFA500,stroke:#333,stroke-width:1px;
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