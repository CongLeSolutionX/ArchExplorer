---
created: 2025-06-29 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/jupyter/jupyter_client
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




# jupyter_client repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for 👨‍🎓 <ins>educational purposes</ins> 👨‍🎓 (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), 📖 <ins> personal study </ins> 📖, and 🔖 <ins> technical reference </ins> 🔖.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>




---

```mermaid
---
title: "jupyter_client repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright © 2025 Cong Le. All Rights Reserved."
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
    %% Layers arranged vertically
    subgraph "Frontend" 
        style Frontend fill:#f0f0f0,stroke:#333,stroke-width:1px
        Notebook["Jupyter Notebook/Lab"]:::external
    end

    subgraph Client_API_Layer["Client API Layer"]
        style Client_API_Layer fill:#ffffff,stroke:#666,stroke-width:1px
        subgraph "Sync API"
            BlockingClient["jupyter_client.blocking.client BlockingClient"]:::core
        end
        subgraph "Async API"
            AsyncClient["jupyter_client.asynchronous.client AsyncClient"]:::core
        end
        AbstractClient["jupyter_client.clientabc ClientABC"]:::core
        Adapter["jupyter_client.adapter Adapter"]:::core
    end

    subgraph "Session Layer"
        Session["jupyter_client.session.Session"]:::core
    end

    subgraph "Channels Layer"
        ChannelsAbc["jupyter_client.channelsabc ZMQChannelABC"]:::core
        Channels["jupyter_client.channels Channels"]:::core
    end

    subgraph "I/O Loop Managers"
        LoopManager["jupyter_client.ioloop.manager LoopManager"]:::core
        Restarter["jupyter_client.ioloop.restarter Restarter"]:::core
    end

    subgraph "Provisioning & Management"
        Factory["jupyter_client.provisioning.factory ProvisioningFactory"]:::core
        ProvBase["jupyter_client.provisioning.provisioner_base ProvisionerBase"]:::core
        LocalProv["jupyter_client.provisioning.local_provisioner LocalProvisioner"]:::core
        subgraph "SSH Tunnel" 
            style SSH\ Tunnel stroke-dasharray: 5 5
            Forward["jupyter_client.ssh.forward Forward"]:::optional
            Tunnel["jupyter_client.ssh.tunnel Tunnel"]:::optional
        end
        KM["jupyter_client.manager KernelManager"]:::core
        MultiKM["jupyter_client.multikernelmanager MultiKernelManager"]:::core
    end

    subgraph CLI_Entry_Points["CLI Entry Points"]
        style CLI_Entry_Points fill:#ffffff,stroke:#666,stroke-width:1px
        ConsoleApp["jupyter_client.consoleapp ConsoleApp"]:::core
        KernelApp["jupyter_client.kernelapp KernelApp"]:::core
        KernSpecApp["jupyter_client.kernelspecapp KernelspecApp"]:::core
        KernSpec["jupyter_client.kernelspec KernelSpec"]:::core
    end

    KernelProc["Kernel Process"]:::external

    %% Connections
    Notebook -->|"execute_request"| AsyncClient
    Notebook -->|"execute_request"| BlockingClient

    AsyncClient --> Session
    BlockingClient --> Session

    Session --> Channels
    Channels -->|"ZMQ"| KernelProc
    KernelProc -->|"iopub"| Channels

    Channels --> Session
    Session --> AsyncClient
    Session --> BlockingClient

    AsyncClient --> LoopManager
    BlockingClient --> LoopManager
    LoopManager --> Channels
    LoopManager --> AsyncClient
    LoopManager --> BlockingClient

    BlockingClient --> KM
    AsyncClient --> KM
    KM --> Factory
    Factory --> ProvBase
    ProvBase --> LocalProv
    ProvBase --> Forward
    ProvBase --> Tunnel
    LocalProv --> KM

    MultiKM --> KM

    ConsoleApp --> BlockingClient
    KernelApp --> BlockingClient
    KernSpecApp --> KernSpec

    %% Click Events
    click AsyncClient "https://github.com/jupyter/jupyter_client/blob/main/jupyter_client/asynchronous/client.py"
    click BlockingClient "https://github.com/jupyter/jupyter_client/blob/main/jupyter_client/blocking/client.py"
    click Session "https://github.com/jupyter/jupyter_client/blob/main/jupyter_client/session.py"
    click Channels "https://github.com/jupyter/jupyter_client/blob/main/jupyter_client/channels.py"
    click ChannelsAbc "https://github.com/jupyter/jupyter_client/blob/main/jupyter_client/channelsabc.py"
    click KM "https://github.com/jupyter/jupyter_client/blob/main/jupyter_client/manager.py"
    click MultiKM "https://github.com/jupyter/jupyter_client/blob/main/jupyter_client/multikernelmanager.py"
    click Factory "https://github.com/jupyter/jupyter_client/blob/main/jupyter_client/provisioning/factory.py"
    click ProvBase "https://github.com/jupyter/jupyter_client/blob/main/jupyter_client/provisioning/provisioner_base.py"
    click LocalProv "https://github.com/jupyter/jupyter_client/blob/main/jupyter_client/provisioning/local_provisioner.py"
    click Forward "https://github.com/jupyter/jupyter_client/blob/main/jupyter_client/ssh/forward.py"
    click Tunnel "https://github.com/jupyter/jupyter_client/blob/main/jupyter_client/ssh/tunnel.py"
    click LoopManager "https://github.com/jupyter/jupyter_client/blob/main/jupyter_client/ioloop/manager.py"
    click Restarter "https://github.com/jupyter/jupyter_client/blob/main/jupyter_client/ioloop/restarter.py"
    click ConsoleApp "https://github.com/jupyter/jupyter_client/blob/main/jupyter_client/consoleapp.py"
    click KernelApp "https://github.com/jupyter/jupyter_client/blob/main/jupyter_client/kernelapp.py"
    click KernSpecApp "https://github.com/jupyter/jupyter_client/blob/main/jupyter_client/kernelspecapp.py"
    click KernSpec "https://github.com/jupyter/jupyter_client/blob/main/jupyter_client/kernelspec.py"
    click AbstractClient "https://github.com/jupyter/jupyter_client/blob/main/jupyter_client/clientabc.py"
    click Adapter "https://github.com/jupyter/jupyter_client/blob/main/jupyter_client/adapter.py"

    %% Styles
    classDef core fill:#add8e6,stroke:#0177b5,stroke-width:1px
    classDef external fill:#cccccc,stroke:#666666,stroke-width:1px
    classDef optional stroke-dasharray: 5 5,fill:#fff8dc,stroke:#d2691e,stroke-width:1px
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
    

  Closing_quote ~~~ My_Meme
    
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