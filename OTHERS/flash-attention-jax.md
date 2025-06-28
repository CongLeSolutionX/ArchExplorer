---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/lucidrains/flash-attention-jax
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExZmdoYWhxb3c2NmR6OGZoMzN5NWxqNjJmbmVxd3U0NDFobjc4ZHdvNyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/xUA7bjPYcgAvwq5CKc/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# lucidrains - flash-attention-jax repo project
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
title: "flash-attention-jax repo project"
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
    %% User Layer
    UserApp["User Application/Notebook"]:::blue

    %% Library Layer
    subgraph "flash_attention_jax Library"
        API["flash_attention_jax API Layer"]:::green
        Core["attention.py"]:::green
        FlashKernel["flash_attention.py"]:::green
        Causal["causal_flash_attention.py"]:::green
        Cosine["cosine_sim_flash_attention.py"]:::green
        Rabe["rabe_attention.py"]:::green
        Utils["utils.py"]:::green
    end

    %% Compilation Layer
    Compiler["JAX/XLA Compiler"]:::orange

    %% Hardware Layer
    Hardware["Hardware Backend (CPU/GPU)"]:::purple

    %% Packaging & CI/CD
    subgraph "Packaging & CI/CD"
        Setup["setup.py (Packaging Metadata)"]:::gray
        CI["GitHub Actions Workflow"]:::gray
        PyPI(("PyPI Registry")):::gray
    end

    %% Connections
    UserApp -->|"import & calls (q, k, v arrays)"| API
    API -->|"delegates to core logic"| Core
    API -->|"invokes flash kernel"| FlashKernel
    API -->|"invokes causal variant"| Causal
    API -->|"invokes cosine sim variant"| Cosine
    API -->|"invokes rabe variant"| Rabe
    API -->|"uses utilities"| Utils

    Core & FlashKernel & Causal & Cosine & Rabe & Utils -->|"JAX tracer"| Compiler
    Compiler -->|"compiled HLO"| Hardware
    Hardware -->|"results (tensor)"| UserApp

    Setup -->|"defines packaging"| CI
    CI -->|"publishes package"| PyPI

    %% Click Events
    click API "https://github.com/lucidrains/flash-attention-jax/blob/main/flash_attention_jax/__init__.py"
    click Core "https://github.com/lucidrains/flash-attention-jax/blob/main/flash_attention_jax/attention.py"
    click FlashKernel "https://github.com/lucidrains/flash-attention-jax/blob/main/flash_attention_jax/flash_attention.py"
    click Causal "https://github.com/lucidrains/flash-attention-jax/blob/main/flash_attention_jax/causal_flash_attention.py"
    click Cosine "https://github.com/lucidrains/flash-attention-jax/blob/main/flash_attention_jax/cosine_sim_flash_attention.py"
    click Rabe "https://github.com/lucidrains/flash-attention-jax/blob/main/flash_attention_jax/rabe_attention.py"
    click Utils "https://github.com/lucidrains/flash-attention-jax/blob/main/flash_attention_jax/utils.py"
    click Setup "https://github.com/lucidrains/flash-attention-jax/blob/main/setup.py"
    click CI "https://github.com/lucidrains/flash-attention-jax/blob/main/.github/workflows/python-publish.yml"

    %% Styles
    classDef blue fill:#CCF2,stroke:#888,stroke-width:1px
    classDef green fill:#CFC2,stroke:#888,stroke-width:1px
    classDef orange fill:#FC92,stroke:#888,stroke-width:1px
    classDef purple fill:#C9C2,stroke:#888,stroke-width:1px
    classDef gray fill:#DDD2,stroke:#888,stroke-width:1px

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
><b>Licenses</b>:
>
>- <b>MIT License</b>:  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
>- <b>Creative Commons Attribution-ShareAlike 4.0 International</b>: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) [![CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/88x31.png)](https://creativecommons.org/licenses/by-sa/4.0/) - Legal details in [LICENSE-CC-BY-SA-4.0](THE_PAST/LICENSE-CC-BY-SA-4.0) and at [Creative Commons official site](https://creativecommons.org/licenses/by-sa/4.0/).
>
---
