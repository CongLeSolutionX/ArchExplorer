---
created: 2025-06-27 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/grpc/grpc-dotnet
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExY2tqeGd6Mms5ejMwbjIycDlrNGY4emV4aXN6dG0yb3FueWN5N2lzdyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/ZBVRlQamUaAMAOWDHB/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# grpc-dotnet repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for 👨‍🎓 <ins>educational purposes</ins> 👨‍🎓 (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), 📖 <ins> personal study </ins> 📖, and 🔖 <ins> reference </ins> 🔖.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>



----

```mermaid
---
title: "grpc-dotnet repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
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
    'flowchart': { 'htmlLabels': true, 'curve': 'linear'},
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#22BB',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#EEF2',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '15px'
    }
  }
}%%
flowchart LR
    %% Consumers
    subgraph "Consumers"  
        style Consumers stroke-dasharray: 5 5,stroke:#999
        Examples["Examples"]  
        Tests["Tests"]  
        Perf["Perf"]  
    end

    %% Client Stack
    subgraph "Client Stack"  
        direction TB
        Client["Grpc.Net.Client"]:::client
        ClientFactory["Grpc.Net.ClientFactory"]:::client
        ClientWeb["Grpc.Net.Client.Web"]:::client
    end

    %% Server Stack
    subgraph "Server Stack"  
        direction TB
        Server["Grpc.AspNetCore.Server"]:::server
        HealthChecks["Grpc.AspNetCore.HealthChecks"]:::server
        ServerClientFactory["Grpc.AspNetCore.Server.ClientFactory"]:::server
        ReflectionServer["Grpc.AspNetCore.Server.Reflection"]:::server
        WebServer["Grpc.AspNetCore.Web"]:::server
    end

    %% Ecosystem Packages
    subgraph "Ecosystem Packages"  
        direction TB
        Auth["Grpc.Auth"]:::server
        HealthService["Grpc.HealthCheck"]:::server
        ReflectionPkg["Grpc.Reflection"]:::server
        StatusProto["Grpc.StatusProto"]:::server
    end

    %% Core & Shared
    subgraph "Core Layer"  
        direction TB
        CoreApi["Grpc.Core.Api"]:::core
        Shared["Shared"]:::core
        CLI["dotnet-grpc CLI"]:::tool
    end

    %% Dependencies
    Client -->|"depends on"| CoreApi
    Client -->|"depends on"| Shared
    ClientFactory -->|"depends on"| Client
    ClientFactory -->|"depends on"| MicrosoftDI["IHttpClientFactory"]:::external
    ClientWeb -->|"depends on"| Client

    Server -->|"depends on"| CoreApi
    Server -->|"depends on"| Shared
    HealthChecks -->|"depends on"| Server
    ServerClientFactory -->|"depends on"| Server
    ReflectionServer -->|"depends on"| Server
    WebServer -->|"depends on"| Server

    Auth -->|"depends on"| Server
    HealthService -->|"depends on"| Server
    ReflectionPkg -->|"depends on"| Server
    StatusProto -->|"depends on"| Server

    CLI -->|"uses for code-gen"| CoreApi
    CLI -->|"uses for code-gen"| Shared

    %% Consumers usage
    Examples -->|"build-time & run-time"| Client
    Examples -->|"build-time & run-time"| Server
    Perf -->|"benchmarks"| Client
    Perf -->|"benchmarks"| Server
    Tests -->|"tests"| CoreApi
    Tests -->|"tests"| Client
    Tests -->|"tests"| Server

    %% Run-time Flow Inset
    subgraph "Run-Time Call Flow"
        direction TB
        App["Client App"]:::external
        Channel["GrpcChannel"]:::client
        HTTP2["HTTP/2 Transport"]:::transport
        Kestrel["Kestrel (ASP.NET Core)"]:::external
        Middleware["gRPC Middleware"]:::server
        Handler["Service Handler"]:::server

        App -->|"calls"| Channel
        Channel -->|"HTTP/2"| HTTP2
        HTTP2 --> Kestrel
        Kestrel --> Middleware
        Middleware --> Handler
        Handler --> Middleware
        Middleware --> Kestrel
        Kestrel --> HTTP2
        HTTP2 --> Channel
        Channel --> App
    end

    %% Click Events
    click CoreApi "https://github.com/grpc/grpc-dotnet/tree/master/src/Grpc.Core.Api/"
    click Shared "https://github.com/grpc/grpc-dotnet/tree/master/src/Shared/"
    click Client "https://github.com/grpc/grpc-dotnet/tree/master/src/Grpc.Net.Client/"
    click ClientFactory "https://github.com/grpc/grpc-dotnet/tree/master/src/Grpc.Net.ClientFactory/"
    click ClientWeb "https://github.com/grpc/grpc-dotnet/tree/master/src/Grpc.Net.Client.Web/"
    click Server "https://github.com/grpc/grpc-dotnet/tree/master/src/Grpc.AspNetCore.Server/"
    click HealthChecks "https://github.com/grpc/grpc-dotnet/tree/master/src/Grpc.AspNetCore.HealthChecks/"
    click ServerClientFactory "https://github.com/grpc/grpc-dotnet/tree/master/src/Grpc.AspNetCore.Server.ClientFactory/"
    click ReflectionServer "https://github.com/grpc/grpc-dotnet/tree/master/src/Grpc.AspNetCore.Server.Reflection/"
    click WebServer "https://github.com/grpc/grpc-dotnet/tree/master/src/Grpc.AspNetCore.Web/"
    click Auth "https://github.com/grpc/grpc-dotnet/tree/master/src/Grpc.Auth/"
    click HealthService "https://github.com/grpc/grpc-dotnet/tree/master/src/Grpc.HealthCheck/"
    click ReflectionPkg "https://github.com/grpc/grpc-dotnet/tree/master/src/Grpc.Reflection/"
    click StatusProto "https://github.com/grpc/grpc-dotnet/tree/master/src/Grpc.StatusProto/"
    click CLI "https://github.com/grpc/grpc-dotnet/tree/master/src/dotnet-grpc/"

    %% Styles
    classDef core fill:#dae8fc,stroke:#6c8ebf,color:#1f365d
    classDef client fill:#d5e8d4,stroke:#82b366,color:#264d23
    classDef server fill:#f8cecc,stroke:#b85450,color:#5c1412
    classDef tool fill:#e1e1e1,stroke:#888888,color:#333333
    classDef external fill:#f5f5f5,stroke:#aaaaaa,color:#555555
    classDef transport fill:#fff2cc,stroke:#d6b656,color:#665c03

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
