---
created: 2025-06-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/torproject/stem
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




# stem repo project
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
title: "stem repo project"
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
    %% External Consumers
    UserScripts["User Scripts / Apps<br/>(Nyx, examples)"]:::external
    subgraph "CLI & Interpreter"
        torPrompt["tor-prompt (ENTRYPOINT)"]:::cli
        Interpreter["stem.interpreter<br/>(REPL & Commands)"]:::cli
    end
    %% API Layer
    ClientAPI["stem.client<br/>(Client API Layer)"]:::api
    %% Transport Layer
    Socket["stem.socket<br/>(Abstract Socket)"]:::transport
    Connection["stem.connection<br/>(Connection Management)"]:::transport
    Control["stem.control<br/>(Control Protocol)"]:::transport
    %% External Tor Process
    TorProcess["Tor Process<br/>(ControlPort)"]:::external
    %% Parser Layers
    ResponseParser["stem.response<br/>(Response Parsing)"]:::parser
    subgraph "Descriptor Parsing"
        Descriptor["stem.descriptor/<br/>Descriptor Modules"]:::parser
        Directory["stem.directory<br/>(Directory Fetching)"]:::parser
        ExitPolicy["stem.exit_policy<br/>(Exit Policy Parsing)"]:::parser
    end
    %% Process Management
    Process["stem.process<br/>(Tor Process Control)"]:::parser
    Manual["stem.manual<br/>(Helper Scripts)"]:::parser
    %% Utility Layer
    Util["stem.util/<br/>Utilities"]:::util
    %% Version & Settings
    Version["stem.version<br/>(Package Version)"]:::util
    Settings["stem.settings.cfg<br/>(Default Settings)"]:::util
    %% Tests
    subgraph "Tests"
        UnitTests["test/unit/"]:::external
        IntegTests["test/integ/"]:::external
    end

    %% Main Flow
    UserScripts -->|"uses"| ClientAPI
    torPrompt -->|"launches"| Interpreter
    Interpreter -->|"calls API"| ClientAPI
    ClientAPI -->|"open socket"| Socket
    Socket -->|"establish connection"| Connection
    Connection -->|"send control commands"| Control
    Control -->|"connect to"| TorProcess
    TorProcess -->|"send responses"| Socket
    Socket -->|"deliver to"| ResponseParser
    ResponseParser -->|"parsed objects"| ClientAPI
    ClientAPI -->|"return results"| UserScripts

    %% Descriptor Flow
    ClientAPI -->|"fetch descriptors"| Descriptor
    Descriptor -->|"uses"| Directory
    Descriptor -->|"parses exit rules"| ExitPolicy

    %% Process Management Flow
    torPrompt -->|"manage process"| Process
    torPrompt -->|"helper"| Manual

    %% Utilities
    Util -.-> ClientAPI
    Util -.-> Socket
    Util -.-> Connection
    Util -.-> Control
    Util -.-> Descriptor
    Util -.-> ResponseParser
    Util -.-> Interpreter
    Util -.-> Process
    Util -.-> Manual

    %% Version & Settings usage
    Util -->|"load cfg"| Settings
    Util -->|"load version"| Version

    %% Styles
    classDef api fill:#add8e6,stroke:#000,stroke-width:1px
    classDef transport fill:#90ee90,stroke:#000,stroke-width:1px
    classDef parser fill:#ffa500,stroke:#000,stroke-width:1px
    classDef cli fill:#dda0dd,stroke:#000,stroke-width:1px
    classDef util fill:#d3d3d3,stroke:#000,stroke-width:1px
    classDef external fill:#ff7f7f,stroke:#000,stroke-width:1px

    %% Click Events
    click ClientAPI "https://github.com/torproject/stem/tree/master/stem/client/"
    click torPrompt "https://github.com/torproject/stem/tree/master/tor-prompt"
    click Interpreter "https://github.com/torproject/stem/tree/master/stem/interpreter/"
    click Socket "https://github.com/torproject/stem/blob/master/stem/socket.py"
    click Connection "https://github.com/torproject/stem/blob/master/stem/connection.py"
    click Control "https://github.com/torproject/stem/blob/master/stem/control.py"
    click ResponseParser "https://github.com/torproject/stem/tree/master/stem/response/"
    click Descriptor "https://github.com/torproject/stem/tree/master/stem/descriptor/"
    click Directory "https://github.com/torproject/stem/blob/master/stem/directory.py"
    click ExitPolicy "https://github.com/torproject/stem/blob/master/stem/exit_policy.py"
    click Process "https://github.com/torproject/stem/blob/master/stem/process.py"
    click Manual "https://github.com/torproject/stem/blob/master/stem/manual.py"
    click Util "https://github.com/torproject/stem/tree/master/stem/util/"
    click Version "https://github.com/torproject/stem/blob/master/stem/version.py"
    click Settings "https://github.com/torproject/stem/blob/master/stem/settings.cfg"
    click UnitTests "https://github.com/torproject/stem/tree/master/test/unit/"
    click IntegTests "https://github.com/torproject/stem/tree/master/test/integ/"
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