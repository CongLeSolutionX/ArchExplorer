---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# ml-stable-diffusion
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
title: "Apple - ML Stable Diffusion"
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
    "flowchart": {"htmlLabels": true, 'curve': 'natural'},
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#f231',
      'primaryTextColor': '#239',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TD
    A["PyTorch Model Source"]:::external
    B["Python Conversion & Optimization<br>(torch2coreml, activation_quantization, mixed_bit_compression, ControlNet)"]:::conversion
    C["Core ML Model Assets & Resources"]:::asset

    subgraph Swift_Inference_Integration["Swift Inference / Integration"]
        D1["Swift Package"]:::swift
        D2["Tokenizer"]:::swift
        D3["CLI"]:::swift
        D4["Test Modules"]:::swift
    end

    subgraph Python_Inference_Pipeline["Python Inference Pipeline"]
        E1["Diffusers-like Interface"]:::python
        E2["Pipeline Module"]:::python
    end

    A -->|"downloads+transforms"| B
    B -->|"outputs"| C
    C -->|"loaded by"| D1
    C -->|"loaded by"| D2
    C -->|"loaded by"| D3
    C -->|"loaded by"| D4
    C -->|"loaded by"| E1
    C -->|"loaded by"| E2
    D1 -->|"feedback"| B
    E1 -->|"feedback"| B

    click B "https://github.com/apple/ml-stable-diffusion/tree/main/python_coreml_stable_diffusion"
    click C "https://github.com/apple/ml-stable-diffusion/tree/main/assets"
    click D1 "https://github.com/apple/ml-stable-diffusion/tree/main/swift/StableDiffusion"
    click D3 "https://github.com/apple/ml-stable-diffusion/tree/main/swift/StableDiffusionCLI"
    click E1 "https://github.com/apple/ml-stable-diffusion/tree/main/tests"
    click E2 "https://github.com/apple/ml-stable-diffusion/blob/main/python_coreml_stable_diffusion/pipeline.py"

    classDef external fill:#F464,stroke:#000,stroke-width:2px
    classDef conversion fill:#ADE3,stroke:#000,stroke-width:2px
    classDef asset fill:#D3D3,stroke:#000,stroke-width:2px
    classDef swift fill:#9E92,stroke:#000,stroke-width:2px
    classDef python fill:#FDB2,stroke:#000,stroke-width:2px
    
```







---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---