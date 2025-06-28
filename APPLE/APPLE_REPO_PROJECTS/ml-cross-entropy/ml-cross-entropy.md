---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/apple/ml-cross-entropy
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is an ongoing document collecting notes for personal educational purposes and references. 
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExeHJ4YXdtYjJpMDl0MzEwYmU4ZzBobG0waGNiN3MzNzR0d2R2NnMwNSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/26gssNOlBJKjEM3yo/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# ml-cross-entropy repo project
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
title: "ml-cross-entropy repo project"
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
    'flowchart': { 'htmlLabels': true, 'curve': 'monotoneX'},
    'fontFamily': 'Monaco',
    'themeVariables': {
      'primaryColor': '#22BB',
      'primaryTextColor': '#F8B229',
      'lineColor': '#F8B229',
      'primaryBorderColor': '#27AE60',
      'secondaryColor': '#3483',
      'secondaryTextColor': '#6C3483',
      'secondaryBorderColor': '#A569BD',
      'fontSize': '15px'
    }
  }
}%%
flowchart LR
    %% User Application Layer
    subgraph User_Application_Layer["User Application Layer"]
    style User_Application_Layer fill:#F2F2,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        Scripts["scripts/train.sh"]:::user
        Training["training/train.py"]:::user
        Benchmark["benchmark/__main__.py"]:::user
        CustomLoop["Custom PyTorch Loop"]:::user
        TransformersClient["Transformers Training API"]:::user
    end

    %% CCE Library Core
    subgraph CCE_Library_Core["CCE Library Core"]
    style CCE_Library_Core fill:#22F2,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        CoreAPI["cce.py (Core API)"]:::core
        Dispatcher["torch_compile.py (Implementation Dispatcher)"]:::core

        subgraph Forward_Kernels["Forward Kernels"]
        style Forward_Kernels fill:#F2F2,stroke:#333,stroke-width:1px, color: #FFFF
        direction TB
            LSEForward["cce_lse_forward.py"]:::core
            LinearCE["linear_cross_entropy.py"]:::core
            IndexedDot["indexed_dot.py"]:::core
        end

        Backward["cce_backward.py"]:::core

        subgraph Constants_and_Utilities["Constants & Utilities"]
        style Constants_and_Utilities fill:#2BB5,stroke:#333,stroke-width:1px, color: #FFFF
        direction TB
            Constants["constants.py"]:::core
            CCEUtils["cce_utils.py"]:::core
            Utils["utils.py"]:::core
        end

        subgraph Autotuning_and_Triton_Helpers["Autotuning & Triton Helpers"]
        style Autotuning_and_Triton_Helpers fill:#B2B5,stroke:#333,stroke-width:1px, color: #FFFF
        direction TB
            Autotune["tl_autotune.py"]:::core
            TLUtils["tl_utils.py"]:::core
        end
    end

    subgraph Integration_Layer["Integration Layer"]
    style Integration_Layer fill:#115,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        subgraph Transformers_Adapters["Transformers Adapters"]
        style Transformers_Adapters fill:#B225,stroke:#333,stroke-width:1px, color: #FFFF
        direction TB
            Patch["patch.py"]:::core
            LlamaAdapter["llama.py"]:::core
            MistralAdapter["mistral.py"]:::core
            Gemma2Adapter["gemma2.py"]:::core
            Phi3Adapter["phi3.py"]:::core
            Qwen2Adapter["qwen2.py"]:::core
            TFUtils["utils.py"]:::core
        end
        subgraph Vocabulary_Parallelism["Vocabulary Parallelism"]
        style Vocabulary_Parallelism fill:#BB15,stroke:#333,stroke-width:1px, color: #FFFF
        direction TB
            VPUtils["utils.py (vocab_parallel)"]:::core
            VPTorchCompile["vocab_parallel_torch_compile.py"]:::core
        end
    end

    subgraph Auxiliary_Modules["Auxiliary Modules"]
    style Auxiliary_Modules fill:#B215,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        Tests["tests/... (unit tests)"]:::aux
    end

    subgraph External_Dependencies["External Dependencies"]
    style External_Dependencies fill:#D195,stroke:#333,stroke-width:1px, color: #FFFF
    direction TB
        PyTorch["PyTorch 2.4+"]:::external
        Triton["Triton 3.0+"]:::external
        CUDA["CUDA GPU"]:::external
        ProcessGroup["torch.distributed ProcessGroup"]:::external
        GPUMem["GPU Memory (flash + global)"]:::external
    end

    %% Connections
    Scripts -->|"runs benchmark/train"| CoreAPI
    Training -->|"invokes loss"| CoreAPI
    Benchmark -->|"calls loss"| CoreAPI
    CustomLoop -->|"calls linear_cross_entropy"| CoreAPI
    TransformersClient -->|"forward pass"| Patch
    Patch -->|"wraps loss call"| CoreAPI

    CoreAPI -->|"select impl"| Dispatcher
    Dispatcher -->|"Triton path"| LSEForward
    Dispatcher -->|"Triton path"| LinearCE
    Dispatcher -->|"Triton path"| IndexedDot
    Dispatcher -->|"Fallback"| DispatchTorchCompile --> TLCompile["torch_compile path"]:::core
    TLCompile -->|"compute via torch.compile"| GPUMem

    LSEForward -->|"embeddings, logits"| GPUMem
    LinearCE -->|"embeddings, logits"| GPUMem
    IndexedDot -->|"embeddings × weights"| GPUMem
    Backward -->|"gradients"| GPUMem

    CoreAPI -->|"constants & helpers"| Constants
    CoreAPI -->|"utils"| CCEUtils
    CoreAPI -->|"general utils"| Utils

    LSEForward --> Autotune
    LSEForward --> TLUtils

    CoreAPI -->|"adapter extension"| Patch
    CoreAPI -->|"vocab parallel options"| VPUtils
    VPUtils --> VPTorchCompile
    VPTorchCompile --> ProcessGroup
    ProcessGroup -->|"sharded weights"| GPUMem

    Tests --> CoreAPI
    Tests --> LSEForward
    Tests --> Backward
    Tests --> IndexedDot
    Tests --> VPUtils

    %% Click Events
    click CoreAPI "https://github.com/apple/ml-cross-entropy/blob/main/cut_cross_entropy/cce.py"
    click LSEForward "https://github.com/apple/ml-cross-entropy/blob/main/cut_cross_entropy/cce_lse_forward.py"
    click LinearCE "https://github.com/apple/ml-cross-entropy/blob/main/cut_cross_entropy/linear_cross_entropy.py"
    click IndexedDot "https://github.com/apple/ml-cross-entropy/blob/main/cut_cross_entropy/indexed_dot.py"
    click Backward "https://github.com/apple/ml-cross-entropy/blob/main/cut_cross_entropy/cce_backward.py"
    click Constants "https://github.com/apple/ml-cross-entropy/blob/main/cut_cross_entropy/constants.py"
    click CCEUtils "https://github.com/apple/ml-cross-entropy/blob/main/cut_cross_entropy/cce_utils.py"
    click Utils "https://github.com/apple/ml-cross-entropy/blob/main/cut_cross_entropy/utils.py"
    click Autotune "https://github.com/apple/ml-cross-entropy/blob/main/cut_cross_entropy/tl_autotune.py"
    click TLUtils "https://github.com/apple/ml-cross-entropy/blob/main/cut_cross_entropy/tl_utils.py"
    click TLCompile "https://github.com/apple/ml-cross-entropy/blob/main/cut_cross_entropy/torch_compile.py"
    click Patch "https://github.com/apple/ml-cross-entropy/blob/main/cut_cross_entropy/transformers/patch.py"
    click LlamaAdapter "https://github.com/apple/ml-cross-entropy/blob/main/cut_cross_entropy/transformers/llama.py"
    click MistralAdapter "https://github.com/apple/ml-cross-entropy/blob/main/cut_cross_entropy/transformers/mistral.py"
    click Gemma2Adapter "https://github.com/apple/ml-cross-entropy/blob/main/cut_cross_entropy/transformers/gemma2.py"
    click Phi3Adapter "https://github.com/apple/ml-cross-entropy/blob/main/cut_cross_entropy/transformers/phi3.py"
    click Qwen2Adapter "https://github.com/apple/ml-cross-entropy/blob/main/cut_cross_entropy/transformers/qwen2.py"
    click TFUtils "https://github.com/apple/ml-cross-entropy/blob/main/cut_cross_entropy/transformers/utils.py"
    click VPUtils "https://github.com/apple/ml-cross-entropy/blob/main/cut_cross_entropy/vocab_parallel/utils.py"
    click VPTorchCompile "https://github.com/apple/ml-cross-entropy/blob/main/cut_cross_entropy/vocab_parallel/vocab_parallel_torch_compile.py"
    click Benchmark "https://github.com/apple/ml-cross-entropy/blob/main/benchmark/__main__.py"
    click Scripts "https://github.com/apple/ml-cross-entropy/blob/main/scripts/train.sh"
    click Training "https://github.com/apple/ml-cross-entropy/blob/main/training/train.py"

    %% Styles
    classDef user fill:#fc82,stroke:#222
    classDef core fill:#324,stroke:#0b5394
    classDef external fill:#d35400,stroke:#d35400
    classDef aux fill:#8e44ad,stroke:#8e44ad

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
