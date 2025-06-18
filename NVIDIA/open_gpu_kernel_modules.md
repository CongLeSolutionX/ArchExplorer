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
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExZXp6ejJ4eDh0dDl4Y3R5cDcwdzBnMjdhYjI5aWRpdXJqcG42N2ZwMyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/SmaYvew52UlC9MmB6l/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Open GPU Kernel Modules
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
title: "NVIDIA - Open GPU Kernel Modules"
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
flowchart TD
    %% Build Environment & Tools
    subgraph Build_Environment_and_Tools["Build Environment & Tools"]
        BE1("Makefile"):::build
        BE2("nv-compiler.sh"):::build
    end

    %% OS-Agnostic / Shared GPU Driver Code (src)
    subgraph OS_Agnostic_GPU_Driver_Code["OS-Agnostic GPU Driver Code<br>(src)"]
        OS1("GPU Core<br>(src/nvidia)"):::os
        OS2("Modeset Library<br>(src/nvidia-modeset)"):::os
        OS3("Common Utilities<br>(src/common)"):::os
    end

    %% Kernel Interface Layer (kernel-open)
    subgraph Kernel_Interface_Layer["Kernel Interface Layer<br>(kernel-open)"]
        K1("NVIDIA Kernel Module<br>(nvidia)"):::kernel
        K2("NVIDIA-DRM Module<br>(nvidia-drm)"):::kernel
        K3("NVIDIA-Modeset Module<br>(nvidia-modeset)"):::kernel
        K4("NVIDIA-UVM Module<br>(nvidia-uvm)"):::kernel
    end

    %% Nouveau Integration Tools
    subgraph Nouveau_Integration_Tools["Nouveau Integration Tools"]
        N1("Firmware Extraction Tools"):::nouveau
    end

    %% Build Pipeline Connections - orchestrated by Build Environment
    BE1 -->|"orchestrates"| OS1
    BE1 -->|"orchestrates"| OS2
    BE1 -->|"orchestrates"| OS3
    BE1 -->|"orchestrates"| K1
    BE1 -->|"orchestrates"| K2
    BE1 -->|"orchestrates"| K3
    BE1 -->|"orchestrates"| K4

    %% Integration of OS-Agnostic binaries into Kernel Interface Layer
    OS1 -->|"integrated into"| K1
    OS2 -->|"integrated into"| K3
    OS3 -->|"shared utilities"| K2
    OS3 -->|"shared utilities"| K4

    %% Nouveau Firmware Extraction: tools extract firmware from OS-Agnostic code
    N1 -->|"extracts firmware"| OS1

    %% Styles
    classDef build fill:#e0f7f,stroke:#006064,stroke-width:2px
    classDef kernel fill:#e8f5e,stroke:#2e7d32,stroke-width:2px
    classDef os fill:#ff22,stroke:#f9a825,stroke-width:2px
    classDef nouveau fill:#febee,stroke:#c62828,stroke-width:2px

    %% Click Events
    click BE1 "https://github.com/nvidia/open-gpu-kernel-modules/tree/main/Makefile"
    click BE2 "https://github.com/nvidia/open-gpu-kernel-modules/blob/main/nv-compiler.sh"
    click K1 "https://github.com/nvidia/open-gpu-kernel-modules/tree/main/kernel-open/nvidia"
    click K2 "https://github.com/nvidia/open-gpu-kernel-modules/tree/main/kernel-open/nvidia-drm"
    click K3 "https://github.com/nvidia/open-gpu-kernel-modules/tree/main/kernel-open/nvidia-modeset"
    click K4 "https://github.com/nvidia/open-gpu-kernel-modules/tree/main/kernel-open/nvidia-uvm"
    click OS1 "https://github.com/nvidia/open-gpu-kernel-modules/tree/main/src/nvidia"
    click OS2 "https://github.com/nvidia/open-gpu-kernel-modules/tree/main/src/nvidia-modeset"
    click OS3 "https://github.com/nvidia/open-gpu-kernel-modules/tree/main/src/common"
    click N1 "https://github.com/nvidia/open-gpu-kernel-modules/tree/main/nouveau/"

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
