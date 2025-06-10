---
created: 2025-03-14 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExd3EwbGJ6cmphOGFjMjNybzM3eHF5M3psamZmdjh5ZmR5ZGR2eHh0aiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/4NjjHHXoHbb6AmJHSu/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# NVIDIA Container Toolkit
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
title: "NVIDIA Container Toolkit"
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
    "graph": { "htmlLabels": false, 'curve': 'linear' },
    'themeVariables': {
        'fontFamily': 'Fantasy',
        'fontSize': '20px',
        'primaryColor': '#ffff',
        'primaryTextColor': '#55ff',
        'primaryBorderColor': '#7c2',
        'lineColor': '#F8B229',
        'secondaryColor': '#006100',
        'tertiaryColor': '#fff'
    }
  }
}%%
graph TD
    H["Host Environment<br>(NVIDIA Drivers)"]:::host
    L["libnvidia-container"]:::external

    subgraph NVIDIA_Container_Toolkit["NVIDIA Container Toolkit"]
        subgraph Command_Line_Utilities["Command-Line Utilities"]
        style Command_Line_Utilities fill:#fcc3,stroke:#cc0000,stroke-width:2px
            A["nvidia-cdi-hook"]:::cli
            B["nvidia-container-runtime-hook"]:::cli
            C["nvidia-ctk-installer"]:::cli
            D["nvidia-ctk"]:::cli
            E["nvidia-container-runtime"]:::cli
        end
        subgraph Internal_Libraries["Internal Libraries"]
        style Internal_Libraries fill:#c335,stroke:#cc0000,stroke-width:2px
            F["Internal Modules<br>(config, discover, cuda, logger, system, modifier)"]:::internal
            G["Pkg Modules<br>(config, nvcdi)"]:::internal
        end
        subgraph OCI_Hooks_Integration["OCI Hooks Integration"]
        style OCI_Hooks_Integration fill:#c535,stroke:#cc0000,stroke-width:2px
            H1["OCI Hooks"]:::oci
        end
    end

    subgraph Container_Runtime_Integration["Container Runtime Integration"]
    style Container_Runtime_Integration fill:#cff5,stroke:#cc0000,stroke-width:2px
        I["Docker"]:::runtimes
        J["containerd"]:::runtimes
        K["CRI-O"]:::runtimes
    end

    subgraph Support_Services["Support Services"]
    style Support_Services fill:#cf52,stroke:#cc0000,stroke-width:2px
        L1["Packaging & Deployment"]:::packaging
        M["CI/CD & Testing"]:::cicd
    end

    H -->|"requires"| A
    L -->|"dependency"| A

    E -->|"configures"| H1
    B -->|"enables"| H1
    F -->|"discovers/modifies"| H1
    G -->|"CDI logic"| H1

    H1 -->|"injects"| I
    H1 -->|"injects"| J
    H1 -->|"injects"| K

    L1 -->|"builds"| F
    M -->|"tests"| F

    click A "https://github.com/nvidia/nvidia-container-toolkit/tree/main/cmd/nvidia-cdi-hook"
    click B "https://github.com/nvidia/nvidia-container-toolkit/tree/main/cmd/nvidia-container-runtime-hook"
    click C "https://github.com/nvidia/nvidia-container-toolkit/tree/main/cmd/nvidia-ctk-installer"
    click D "https://github.com/nvidia/nvidia-container-toolkit/tree/main/cmd/nvidia-ctk"
    click E "https://github.com/nvidia/nvidia-container-toolkit/tree/main/cmd/nvidia-container-runtime"
    click F "https://github.com/nvidia/nvidia-container-toolkit/tree/main/internal"
    click G "https://github.com/nvidia/nvidia-container-toolkit/tree/main/pkg"
    click H1 "https://github.com/nvidia/nvidia-container-toolkit/tree/main/pkg/config/ocihook"
    click L1 "https://github.com/nvidia/nvidia-container-toolkit/tree/main/packaging"
    click M "https://github.com/nvidia/nvidia-container-toolkit/tree/main/.github/workflows"
    click L "https://github.com/nvidia/nvidia-container-toolkit/tree/main/third_party/libnvidia-container"

    classDef host fill:#ffccc,stroke:#cc0000,stroke-width:2px;
    classDef external fill:#2c35,stroke:#009900,stroke-width:2px;
    classDef cli fill:#cce5f,stroke:#004085,stroke-width:2px;
    classDef internal fill:#d4edd,stroke:#155724,stroke-width:2px;
    classDef oci fill:#f8d7a,stroke:#721c24,stroke-width:2px;
    classDef runtimes fill:#fff3c,stroke:#856404,stroke-width:2px;
    classDef packaging fill:#d1ecf,stroke:#0c5460,stroke-width:2px;
    classDef cicd fill:#e2e3e,stroke:#6c757d,stroke-width:2px;


```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
