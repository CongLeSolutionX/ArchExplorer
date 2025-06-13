---
created: 2025-06-012 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/whisper
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExdXZ4MGpmYmw1azl4ajBjaml2dXBob2NtYjA5a3BxY2xobzNmdWZnZCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/MMUJuyQBqvBuw/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# whisper repo project
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
title: "whisper repo project"
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
    %% CLI & API Layer
    subgraph "CLI & API"
        CLI["CLI Entry Point"]:::io
        API["Python API"]:::io
    end

    %% Audio Processing
    subgraph "Audio Processing" 
        AudioLoader["Audio Loader & Pad/Trim"]:::audio
        FeatureExt["Log-Mel Spectrogram"]:::audio
        MelFilters(("Mel Filters")):::audio
    end

    %% Model Inference
    subgraph "Model Inference"
        ModelLoader[(Model Loader & Weights)]:::ml
        Transformer["Transformer Model (PyTorch)"]:::ml
        Triton["Triton GPU Kernels"]:::ml
    end

    %% Text Processing
    subgraph "Text Processing"
        Decoder["Decoding Strategies"]:::text
        Tokenizer["Tokenizer (BPE)"]:::text
        TokenAssets(("Tokenizer Assets")):::text
        Normalizer["Text Normalizer"]:::text
    end

    %% Output
    Output["Transcription & Metadata"]:::io

    %% External Dependencies
    subgraph "External Dependencies"
        FFmpeg["ffmpeg"]:::ext
        PyTorch["PyTorch Backend"]:::ext
        Rust["Rust Toolchain"]:::ext
        Tiktoken["tiktoken"]:::ext
    end

    %% Data Flow
    CLI -->|invokes| AudioLoader
    API -->|calls| AudioLoader
    AudioLoader -->|produces audio| FeatureExt
    FeatureExt -->|uses| MelFilters
    FeatureExt -->|"mel spectrogram"| Transformer
    Transformer -->|loads weights from| ModelLoader
    Transformer -->|optional speedup| Triton
    Transformer -->|outputs logits| Decoder
    Decoder -->|uses| Tokenizer
    Tokenizer -->|loads vocab| TokenAssets
    Decoder -->|passes tokens| Normalizer
    Normalizer -->|outputs text| Output

    CLI -->|requires| FFmpeg
    FeatureExt -->|requires| FFmpeg
    Transformer -->|executes on| PyTorch
    Tokenizer -->|depends on| Tiktoken
    Tiktoken -->|built by| Rust

    %% Click Events
    click CLI "https://github.com/openai/whisper/blob/main/whisper/__main__.py"
    click API "https://github.com/openai/whisper/blob/main/whisper/transcribe.py"
    click AudioLoader "https://github.com/openai/whisper/blob/main/whisper/audio.py"
    click FeatureExt "https://github.com/openai/whisper/blob/main/whisper/audio.py"
    click MelFilters "https://github.com/openai/whisper/blob/main/whisper/assets/mel_filters.npz"
    click ModelLoader "https://github.com/openai/whisper/blob/main/whisper/model.py"
    click Triton "https://github.com/openai/whisper/blob/main/whisper/triton_ops.py"
    click Tokenizer "https://github.com/openai/whisper/blob/main/whisper/tokenizer.py"
    click TokenAssets "https://github.com/openai/whisper/blob/main/whisper/assets/gpt2.tiktoken"
    click TokenAssets "https://github.com/openai/whisper/blob/main/whisper/assets/multilingual.tiktoken"
    click Normalizer "https://github.com/openai/whisper/blob/main/whisper/normalizers/basic.py"
    click Normalizer "https://github.com/openai/whisper/blob/main/whisper/normalizers/english.py"
    click Normalizer "https://github.com/openai/whisper/blob/main/whisper/normalizers/english.json"
    click Decoder "https://github.com/openai/whisper/blob/main/whisper/decoding.py"
    click Timing "https://github.com/openai/whisper/blob/main/whisper/timing.py"

    %% Styles
    classDef io fill:#b3cde0,stroke:#333,stroke-width:1px
    classDef audio fill:#ccebc5,stroke:#333,stroke-width:1px
    classDef ml fill:#fbb4ae,stroke:#333,stroke-width:1px
    classDef text fill:#decbe4,stroke:#333,stroke-width:1px
    classDef ext fill:#f2f2f2,stroke:#333,stroke-width:1px
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
