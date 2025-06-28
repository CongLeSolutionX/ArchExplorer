---
created: 2025-06-26 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/containerd
---

<div align="center">
  <p>⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷</p>
  <i>This is a working draft in progress.</i>
  <br/>
  <img alt="Loading…" src="https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExdm1hdjd2MzBoZ2d4dnVuYWhnankyYmN6dmZxbXVucTEybzYzcXgzZSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/SL3OBH0jvefvjDizsl/giphy.gif"/>
  <br/>
  <blockquote>
	  <i>gif image is provided by <a href="https://giphy.com">Giphy</a></i>
  </blockquote>
  <p>⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷</p>

</div>


# containerd repo project
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
title: "containerd repo project"
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
    %% Define styles
    classDef core fill:#2374ab,color:#fff,stroke:#333
    classDef plugin fill:#7dba97,color:#333,stroke:#333
    classDef external fill:#f7d794,color:#333,stroke:#333
    classDef storage fill:#95afc0,color:#333,stroke:#333
    classDef api fill:#c56cf0,color:#fff,stroke:#333

    %% Client Layer
    subgraph ClientLayer
        Clients["Client Interface"]
        K8s["Kubernetes"]
        Docker["Docker Engine"]
    end

    %% API Layer
    subgraph APILayer
        API["GRPC API"]:::api
    end

    %% Core Services Layer
    subgraph CoreServices
        ContentMgmt["Content Management"]:::core
        ImageMgmt["Image Management"]:::core
        ContainerRuntime["Container Runtime"]:::core
        SnapshotMgmt["Snapshot Management"]:::core
        TaskExec["Task Execution"]:::core
        MetadataStore["Metadata Store"]:::core
        EventSystem["Events System"]:::core
        Metrics["Metrics"]:::core
    end

    %% Plugin Layer
    subgraph PluginLayer
        ContentPlugin["Content Store Plugin"]:::plugin
        SnapshotPlugin["Snapshot Plugins"]:::plugin
        RuntimePlugin["Runtime Plugins"]:::plugin
        ServicePlugin["Service Plugins"]:::plugin
        MetricsPlugin["Metrics Plugin"]:::plugin
        CRIPlugin["CRI Plugin"]:::plugin
    end

    %% Runtime Layer
    subgraph RuntimeLayer
        ContainerdShim["Containerd Shim"]
        OCIRuntime["OCI Runtime (runc)"]:::external
        Container["Containers"]
    end

    %% Connections
    Clients --> API
    K8s --> API
    Docker --> API
    
    API --> CoreServices
    
    ContentMgmt --> ContentPlugin
    ImageMgmt --> ContentPlugin
    SnapshotMgmt --> SnapshotPlugin
    ContainerRuntime --> RuntimePlugin
    TaskExec --> RuntimePlugin
    Metrics --> MetricsPlugin
    
    RuntimePlugin --> ContainerdShim
    ContainerdShim --> OCIRuntime
    OCIRuntime --> Container
    
    CRIPlugin --> K8s
    
    EventSystem --> CoreServices
    MetadataStore --> CoreServices

    %% Click events for component mapping
    click ContentMgmt "https://github.com/containerd/containerd/tree/main//core/content"
    click ImageMgmt "https://github.com/containerd/containerd/tree/main//core/images"
    click ContainerRuntime "https://github.com/containerd/containerd/tree/main//core/runtime"
    click SnapshotMgmt "https://github.com/containerd/containerd/tree/main//core/snapshots"
    click TaskExec "https://github.com/containerd/containerd/tree/main//core/runtime/v2/task"
    click MetadataStore "https://github.com/containerd/containerd/tree/main//core/metadata"
    click EventSystem "https://github.com/containerd/containerd/tree/main//core/events"
    click CRIPlugin "https://github.com/containerd/containerd/tree/main//internal/cri"
    click ServicePlugin "https://github.com/containerd/containerd/tree/main//plugins/services"
    click Metrics "https://github.com/containerd/containerd/tree/main//core/metrics"
    click API "https://github.com/containerd/containerd/tree/main//api/services"
    click Clients "https://github.com/containerd/containerd/tree/main//client"
    click ContainerdShim "https://github.com/containerd/containerd/tree/main//cmd/containerd-shim-runc-v2"
    click OCIRuntime "https://github.com/containerd/containerd/tree/main//pkg/oci"

    %% Legend
    subgraph Legend
        CoreComp["Core Component"]:::core
        PluginComp["Plugin"]:::plugin
        ExtComp["External Component"]:::external
        APIComp["API Component"]:::api
    end

```

----

```mermaid
---
title: "❓...CongLeSolutionX....❓"
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
>**Licenses:**
>
>- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
>- **Creative Commons Attribution-ShareAlike 4.0 International**: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) [![CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/88x31.png)](https://creativecommons.org/licenses/by-sa/4.0/) - Legal details in [LICENSE-CC-BY-SA-4.0](THE_PAST/LICENSE-CC-BY-SA-4.0) and at [Creative Commons official site](https://creativecommons.org/licenses/by-sa/4.0/).
>
---
