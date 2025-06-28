---
created: 2025-06-26 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/containerd/nerdctl
---

<div align="center">
  <p>⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷</p>
  <i>This is a working draft in progress.</i>
  <br/>
  <img alt="Loading…" src="https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExdGY1MW1qa3MybHVmYXdxNnZ1d2dra2lkM213NWY2N3RuNHRocjRlNSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/loqtlQxtRah1aSr9f3/giphy.gif"/>
  <br/>
  <blockquote>
	  <i>gif image is provided by <a href="https://giphy.com">Giphy</a></i>
  </blockquote>
  <p>⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷</p>

</div>


# nerdctl repo project
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
title: "nerdctl repo project"
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
    %% CLI Layer
    subgraph "CLI Layer"
        CLIInterface["CLI Interface"]:::cli
        ContainerModule["Container Module"]:::cli
        ImageModule["Image Module"]:::cli
        ComposeModule["Compose Module"]:::cli
        BuilderCLI["Builder CLI"]:::cli
        NetworkModule["Network Module"]:::cli
        SystemModule["System Module"]:::cli
        SecurityModule["Security Module"]:::cli
        IPFSModule["IPFS Module"]:::cli
    end

    %% Core Libraries Layer
    subgraph "Core Libraries"
        CoreBL["Core Business Logic (pkg)"]:::core
        BuildKitUtil["BuildKit Util (pkg/buildkitutil)"]:::core
        RootlessUtil["Rootless Utilities (pkg/rootlessutil)"]:::core
        CNIPlugin["CNI Plugin (pkg/netutil)"]:::core
    end

    %% External Systems Layer
    subgraph "External Systems"
        Containerd["Containerd Runtime"]:::external
        BuildKitDaemon["BuildKit Daemon"]:::external
        CNIPlugins["CNI Plugins"]:::external
        IPFSExternal["IPFS Network"]:::external
    end

    %% Connections from CLI Layer to Command Modules
    CLIInterface -->|"invokes"| ContainerModule
    CLIInterface -->|"invokes"| ImageModule
    CLIInterface -->|"invokes"| ComposeModule
    CLIInterface -->|"invokes"| BuilderCLI
    CLIInterface -->|"invokes"| NetworkModule
    CLIInterface -->|"invokes"| SystemModule
    CLIInterface -->|"invokes"| SecurityModule
    CLIInterface -->|"invokes"| IPFSModule

    %% Connections from Command Modules to Core Libraries
    ContainerModule -->|"calls"| CoreBL
    ImageModule -->|"calls"| CoreBL
    ComposeModule -->|"calls"| CoreBL
    BuilderCLI -->|"calls"| BuildKitUtil
    NetworkModule -->|"calls"| CNIPlugin
    SecurityModule -->|"calls"| CoreBL
    IPFSModule -->|"calls"| CoreBL
    SystemModule -->|"optional"| RootlessUtil

    %% Connections from Core Libraries to External Systems
    CoreBL -->|"executes on"| Containerd
    BuildKitUtil -->|"triggers"| BuildKitDaemon
    CNIPlugin -->|"interfaces with"| CNIPlugins
    IPFSModule -->|"utilizes"| IPFSExternal

    %% Styles
    classDef cli fill:#FAD7A0,stroke:#E67E22,stroke-width:2px;
    classDef core fill:#D5F5E3,stroke:#28B463,stroke-width:2px;
    classDef external fill:#AED6F1,stroke:#2471A3,stroke-width:2px;

    %% Click Events
    click CLIInterface "https://github.com/containerd/nerdctl/blob/main/cmd/nerdctl/main.go"
    click ContainerModule "https://github.com/containerd/nerdctl/tree/main/cmd/nerdctl/container"
    click ImageModule "https://github.com/containerd/nerdctl/tree/main/cmd/nerdctl/image"
    click ComposeModule "https://github.com/containerd/nerdctl/tree/main/cmd/nerdctl/compose"
    click BuilderCLI "https://github.com/containerd/nerdctl/tree/main/cmd/nerdctl/builder"
    click BuildKitUtil "https://github.com/containerd/nerdctl/tree/main/pkg/buildkitutil"
    click NetworkModule "https://github.com/containerd/nerdctl/tree/main/cmd/nerdctl/network"
    click SystemModule "https://github.com/containerd/nerdctl/tree/main/cmd/nerdctl/system"
    click SecurityModule "https://github.com/containerd/nerdctl/tree/main/cmd/nerdctl/apparmor"
    click IPFSModule "https://github.com/containerd/nerdctl/tree/main/cmd/nerdctl/ipfs"
    click CoreBL "https://github.com/containerd/nerdctl/tree/main/pkg"
    click RootlessUtil "https://github.com/containerd/nerdctl/tree/main/pkg/rootlessutil"
    click CNIPlugin "https://github.com/containerd/nerdctl/blob/main/pkg/netutil/cni_plugin.go"

```

------

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
