---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/feifeibear/long-context-attention
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


# feifeibear - long-context-attention repo project
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
title: "long-context-attention repo project"
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
    %% API Layer
    subgraph "API Layer"
        style API fill:#AEDFF7
        SPG["set_seq_parallel_pg()"]:::api
        EX["EXTRACT_FUNC_DICT"]:::api
        LCA["LongContextAttention"]:::api
        ACA["AsyncLongContextAttention"]:::api
    end

    %% Hybrid Controller
    subgraph "Hybrid Controller"
        style HC fill:#C8E6C9
        HC["HybridController\n(routing logic)"]:::core
    end

    %% Ulysses Module
    subgraph "Ulysses Module"
        style UM fill:#C8E6C9
        UA["UlyssesAttention"]:::core
    end

    %% Ring Module
    subgraph "Ring Module"
        style RM fill:#C8E6C9
        RPT["ring_pytorch_attn"]:::core
        RFA["ring_flash_attn"]:::core
        RFV["ring_flash_attn_varlen"]:::core
        SFA["stripe_flash_attn"]:::core
        ZFA["zigzag_ring_flash_attn"]:::core
        ZFV["zigzag_ring_flash_attn_varlen"]:::core
        RFI["ring_flashinfer_attn"]:::core
        TRU["triton_utils"]:::core
        RUN["utils"]:::core
    end

    %% Kernel Layer
    subgraph "Kernel Layer"
        style KL fill:#C8E6C9
        KA["FlashAttention / Torch fallback"]:::core
    end

    %% Communication Layer
    subgraph "Communication Layer"
        style CL fill:#C8E6C9
        AA["all_to_all"]:::core
        EL["extract_local"]:::core
    end

    %% External Dependencies
    subgraph "External Dependencies"
        style ED fill:#FFE0B2
        PT["PyTorch"]:::ext
        FA["flash-attn library"]:::ext
        TR["Triton"]:::ext
    end

    %% Peripheral Components
    subgraph "Peripheral Components"
        style PC fill:#FFCDD2
        SC["scripts/"]:::optional
        BM1["benchmark_longctx.py"]:::optional
        BM2["benchmark_longctx_qkvpacked.py"]:::optional
        T1["test_hybrid_attn.py"]:::optional
        T2["test_hybrid_qkvpacked_attn.py"]:::optional
        T3["test_ulysses_attn.py"]:::optional
        T4["test_utils.py"]:::optional
    end

    %% Data Flows
    SPG -->|"config PGs"| AA
    SPG -->|"config PGs"| EL
    EX -->|"shard QKV"| EL
    LCA -->|"call attn"| HC
    ACA -->|"call async attn"| HC
    HC -->|"heads→Ulysses"| UA
    HC -->|"heads→Ring"| RPT
    HC --> RFA
    HC --> RFV
    HC --> SFA
    HC --> ZFA
    HC --> ZFV
    HC --> RFI
    UA -->|"all-to-all"| AA
    RPT -->|"ring collect"| EL
    RFA -->|"ring collect"| EL
    RFV -->|"ring collect"| EL
    SFA -->|"ring collect"| EL
    ZFA -->|"ring collect"| EL
    ZFV -->|"ring collect"| EL
    RFI -->|"ring collect"| EL
    UA --> KA
    RPT --> KA
    RFA --> KA
    RFV --> KA
    SFA --> KA
    ZFA --> KA
    ZFV --> KA
    RFI --> KA
    KA -->|"compute attn"| PT
    KA -->|"compute attn"| FA
    KA -->|"kernels"| TR
    AA --> HC
    EL --> HC
    HC --> LCA
    LCA --> SPG

    %% Peripheral connections
    SC --> SPG
    BM1 --> LCA
    BM2 --> LCA
    T1 --> HC
    T2 --> HC
    T3 --> UA
    T4 --> HC

    %% Click Events
    click SPG "https://github.com/feifeibear/long-context-attention/blob/main/yunchang/comm/__init__.py"
    click EX "https://github.com/feifeibear/long-context-attention/blob/main/yunchang/comm/extract_local.py"
    click LCA "https://github.com/feifeibear/long-context-attention/blob/main/yunchang/hybrid/attn_layer.py"
    click ACA "https://github.com/feifeibear/long-context-attention/blob/main/yunchang/hybrid/async_attn_layer.py"
    click HC "https://github.com/feifeibear/long-context-attention/blob/main/yunchang/hybrid/utils.py"
    click UA "https://github.com/feifeibear/long-context-attention/blob/main/yunchang/ulysses/attn_layer.py"
    click RPT "https://github.com/feifeibear/long-context-attention/blob/main/yunchang/ring/ring_pytorch_attn.py"
    click RFA "https://github.com/feifeibear/long-context-attention/blob/main/yunchang/ring/ring_flash_attn.py"
    click RFV "https://github.com/feifeibear/long-context-attention/blob/main/yunchang/ring/ring_flash_attn_varlen.py"
    click SFA "https://github.com/feifeibear/long-context-attention/blob/main/yunchang/ring/stripe_flash_attn.py"
    click ZFA "https://github.com/feifeibear/long-context-attention/blob/main/yunchang/ring/zigzag_ring_flash_attn.py"
    click ZFV "https://github.com/feifeibear/long-context-attention/blob/main/yunchang/ring/zigzag_ring_flash_attn_varlen.py"
    click RFI "https://github.com/feifeibear/long-context-attention/blob/main/yunchang/ring/ring_flashinfer_attn.py"
    click TRU "https://github.com/feifeibear/long-context-attention/blob/main/yunchang/ring/triton_utils.py"
    click RUN "https://github.com/feifeibear/long-context-attention/blob/main/yunchang/ring/utils.py"
    click KA "https://github.com/feifeibear/long-context-attention/blob/main/yunchang/kernels/attention.py"
    click AA "https://github.com/feifeibear/long-context-attention/blob/main/yunchang/comm/all_to_all.py"
    click EL "https://github.com/feifeibear/long-context-attention/blob/main/yunchang/comm/extract_local.py"
    click PT "https://github.com/feifeibear/long-context-attention/tree/main/PyTorch"
    click FA "https://github.com/feifeibear/long-context-attention/tree/main/flash-attn"
    click TR "https://github.com/feifeibear/long-context-attention/tree/main/Triton"
    click SC "https://github.com/feifeibear/long-context-attention/tree/main/scripts/"
    click BM1 "https://github.com/feifeibear/long-context-attention/blob/main/benchmark/benchmark_longctx.py"
    click BM2 "https://github.com/feifeibear/long-context-attention/blob/main/benchmark/benchmark_longctx_qkvpacked.py"
    click T1 "https://github.com/feifeibear/long-context-attention/blob/main/test/test_hybrid_attn.py"
    click T2 "https://github.com/feifeibear/long-context-attention/blob/main/test/test_hybrid_qkvpacked_attn.py"
    click T3 "https://github.com/feifeibear/long-context-attention/blob/main/test/test_ulysses_attn.py"
    click T4 "https://github.com/feifeibear/long-context-attention/blob/main/test/test_utils.py"

    %% Styles
    classDef api fill:#AEDFF7,stroke:#333,stroke-width:1px
    classDef core fill:#C8E6C9,stroke:#333,stroke-width:1px
    classDef ext fill:#FFE0B2,stroke:#333,stroke-width:1px
    classDef optional fill:#FFCDD2,stroke:#333,stroke-width:1px
```

-----


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
