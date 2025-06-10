---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExZ3RkZmw3bHh1cm1zOWltazhwZTN0NHhmenFpdWcycm1mdGY2Z212byZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/l3q2JguBw4fBXXVpm/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----



# segment-anything
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
title: "Meta Research - Segment Anything"
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
    "graph": {"htmlLabels": true, 'curve': 'natural'},
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
graph TB
    subgraph Input["Input"]
    style Input fill:#c2c3,stroke:#333,stroke-width:2px
        IMG[Image Input]:::input
        PROMPT[Prompt Input]:::input
        AUTO[Automatic Mode]:::input
    end

    subgraph Core["Core Model Architecture"]
    style Core fill:#c2f2,stroke:#333,stroke-width:2px
        IMENC["Image Encoder<br>(image_encoder.py)"]:::core
        PENC["Prompt Encoder<br>(prompt_encoder.py)"]:::core
        TRANS["Memory-efficient Transformer<br>(transformer.py)"]:::core
        MDEC["Mask Decoder<br>(mask_decoder.py)"]:::core
        SAM["SAM Model<br>(sam.py)"]:::core
    end

    subgraph Processing["Processing"]
    style Processing fill:#52f2,stroke:#333,stroke-width:2px
        AMG["Automatic Mask Generator<br>(automatic_mask_generator.py)"]:::process
        PRED["Predictor System<br>(predictor.py)"]:::process
        ONNX["ONNX Export Pipeline<br>(onnx.py)"]:::process
    end

    subgraph Output["Output"]
    style Output fill:#52f3,stroke:#333,stroke-width:2px
        MASK["Mask Predictions"]:::output
        IOU["IoU Predictions"]:::output
        STAB["Stability Scores"]:::output
    end

    subgraph Integration["Integration"]
    style Integration fill:#55f3,stroke:#333,stroke-width:2px
        DEMO["Web Demo Interface<br>(App.tsx)"]:::ui
        ONNXAPI["ONNX Model API<br>(onnxModelAPI.tsx)"]:::ui
        MASKUTIL["Mask Utilities<br>(maskUtils.tsx)"]:::ui
        NB["Example Notebooks"]:::ui
    end

    %% Relationships
    IMG --> IMENC
    PROMPT --> PENC
    AUTO --> AMG
    
    IMENC --> TRANS
    PENC --> TRANS
    TRANS --> MDEC
    
    IMENC & PENC & TRANS & MDEC --> SAM
    
    SAM --> AMG
    SAM --> PRED
    SAM --> ONNX
    
    AMG --> MASK
    AMG --> IOU
    AMG --> STAB
    
    ONNX --> ONNXAPI
    ONNXAPI --> DEMO
    MASKUTIL --> DEMO
    
    SAM --> NB

    %% Click Events
    click IMENC "https://github.com/facebookresearch/segment-anything/blob/main/segment_anything/modeling/image_encoder.py"
    click PENC "https://github.com/facebookresearch/segment-anything/blob/main/segment_anything/modeling/prompt_encoder.py"
    click MDEC "https://github.com/facebookresearch/segment-anything/blob/main/segment_anything/modeling/mask_decoder.py"
    click TRANS "https://github.com/facebookresearch/segment-anything/blob/main/segment_anything/modeling/transformer.py"
    click SAM "https://github.com/facebookresearch/segment-anything/blob/main/segment_anything/modeling/sam.py"
    click AMG "https://github.com/facebookresearch/segment-anything/blob/main/segment_anything/automatic_mask_generator.py"
    click ONNX "https://github.com/facebookresearch/segment-anything/blob/main/segment_anything/utils/onnx.py"
    click PRED "https://github.com/facebookresearch/segment-anything/blob/main/segment_anything/predictor.py"
    click DEMO "https://github.com/facebookresearch/segment-anything/blob/main/demo/src/App.tsx"
    click ONNXAPI "https://github.com/facebookresearch/segment-anything/blob/main/demo/src/components/helpers/onnxModelAPI.tsx"
    click MASKUTIL "https://github.com/facebookresearch/segment-anything/blob/main/demo/src/components/helpers/maskUtils.tsx"
    click NB "https://github.com/facebookresearch/segment-anything/tree/main/notebooks/"

    %% Styles
    classDef input fill:#9E95,stroke:#333,stroke-width:2px
    classDef core fill:#D8E6,stroke:#333,stroke-width:2px
    classDef process fill:#FB35,stroke:#333,stroke-width:2px
    classDef output fill:#98F8,stroke:#333,stroke-width:2px
    classDef ui fill:#DA33,stroke:#333,stroke-width:2px

    %% Legend
    subgraph Legend
        L1[Input Components]:::input
        L2[Core Components]:::core
        L3[Processing Components]:::process
        L4[Output Components]:::output
        L5[UI Components]:::ui
    end
    
```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
