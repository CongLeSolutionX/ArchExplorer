---
created: 2025-06-012 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/tiktoken
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExNnFxNnQ2amllaHdlNm5pZm5oanQ3MnE1aDc2cmlwZno3MGFkcDdvYSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/i7GXnfbuaqboyo93ld/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# openai-tiktoken repo project
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---

```mermaid
---
title: "openai-tiktoken repo project"
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
    subgraph Input
        Text[Text Input]
    end

    subgraph "Python Interface Layer"
        MainInterface["Main Package Interface"]
        PythonBindings["Python Bindings"]
        Registry["Encoding Registry"]
        LoadMech["Loading Mechanism"]
        ModelEnc["Model-specific Encodings"]
    end

    subgraph "Core Layer"
        RustCore["Rust Core Engine"]
        BPEImpl["BPE Implementation"]
        Cache["Caching System"]
    end

    subgraph "Extension Layer"
        ExtSystem["Extension System"]
        OpenAIExt["OpenAI Extensions"]
        CustomExt["Custom Extensions"]
    end

    subgraph "Educational & Testing"
        EduComp["Educational Components"]
        Benchmark["Performance Benchmarking"]
    end

    subgraph Output
        Tokens[Token Output]
        DecodedText[Decoded Text]
    end

    %% Relationships
    Text --> MainInterface
    MainInterface --> PythonBindings
    PythonBindings --> RustCore
    RustCore --> BPEImpl
    BPEImpl --> Cache
    Registry --> LoadMech
    LoadMech --> ModelEnc
    ModelEnc --> RustCore
    RustCore --> Tokens
    Tokens --> DecodedText
    
    ExtSystem --> Registry
    OpenAIExt --> ExtSystem
    CustomExt --> ExtSystem
    
    RustCore --> EduComp
    RustCore --> Benchmark

    %% Styling
    classDef core fill:#2374ab
    classDef python fill:#47b39d
    classDef extension fill:#ffc43d
    classDef educational fill:#615d6c
    classDef interface fill:#d4f2db
    classDef output fill:#f9f7f7

    class RustCore,BPEImpl,Cache core
    class MainInterface,PythonBindings,Registry,LoadMech,ModelEnc python
    class ExtSystem,OpenAIExt,CustomExt extension
    class EduComp,Benchmark educational
    class Text,Tokens,DecodedText interface

    %% Click Events
    click RustCore "https://github.com/openai/tiktoken/blob/main/src/lib.rs"
    click PythonBindings "https://github.com/openai/tiktoken/blob/main/tiktoken/core.py"
    click Registry "https://github.com/openai/tiktoken/blob/main/tiktoken/registry.py"
    click ExtSystem "https://github.com/openai/tiktoken/blob/main/tiktoken_ext/openai_public.py"
    click ModelEnc "https://github.com/openai/tiktoken/blob/main/tiktoken/model.py"
    click EduComp "https://github.com/openai/tiktoken/blob/main/tiktoken/_educational.py"
    click LoadMech "https://github.com/openai/tiktoken/blob/main/tiktoken/load.py"
    click MainInterface "https://github.com/openai/tiktoken/blob/main/tiktoken/__init__.py"
    click OpenAIExt "https://github.com/openai/tiktoken/blob/main/tiktoken_ext/openai_public.py"
    click Benchmark "https://github.com/openai/tiktoken/blob/main/scripts/benchmark.py"


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
    
  My_Meme ~~~ Closing_quote
    
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
