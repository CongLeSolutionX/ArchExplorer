---
created: 2025-04-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# WhisperKit - Project Overview
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---

```mermaid
---
title: "WhisperKit"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': {'htmlLabels': true, 'curve': 'step' },
    'fontFamily': 'Monospace',
    'themeVariables': {
      'lineColor': '#F8B229'
    }
  }
}%%
flowchart TD
    IA["Input Audio"]:::input
    subgraph WhisperKit_Core["WhisperKit Core"]
        CoreAudio["Audio Processing"]:::core
        CoreText["Text Processing"]:::core
        CoreUtils["Utility Functions"]:::core
        CoreConfig["Configuration & Model Management"]:::core
    end
    TT["Transcribed Text"]:::output

    CLI["CLI Wrapper"]:::cli
    EX["Example Apps"]:::example

    ExtHF["HuggingFace Model Repo"]:::external
    ExtHB["Homebrew"]:::external

    subgraph CI_CD_Deployment_Automation["CI/CD & Deployment Automation"]
        GH["GitHub Workflows"]:::ci
        FL["fastlane"]:::ci
    end

    TEST["Testing & Benchmarks"]:::test

    IA -->|"Stream"| CoreAudio
    CoreAudio -->|"Extract Features"| CoreText
    CoreText -->|"Generate Text"| TT

    CLI -->|"Uses API"| CoreAudio
    EX -->|"Integrates Via SPM"| CoreAudio

    CoreConfig -->|"Downloads Models"| ExtHF
    CLI -->|"Distributed Via CLI"| ExtHB

    GH -->|"Triggers"| TEST
    FL -->|"Releases"| CLI

    TEST -->|"Validates"| CoreAudio
    GH -->|"Build Test"| CoreAudio

    %% Click Events
    click CoreAudio "https://github.com/argmaxinc/whisperkit/tree/main/Sources/WhisperKit/Core/Audio"
    click CoreText "https://github.com/argmaxinc/whisperkit/tree/main/Sources/WhisperKit/Core/Text"
    click CoreUtils "https://github.com/argmaxinc/whisperkit/tree/main/Sources/WhisperKit/Core/Utils"
    click CoreConfig "https://github.com/argmaxinc/whisperkit/blob/main/Sources/WhisperKit/Core/Configurations.swift"
    click CLI "https://github.com/argmaxinc/whisperkit/tree/main/Sources/WhisperKitCLI"
    click EX "https://github.com/argmaxinc/whisperkit/tree/main/Examples/WhisperAX"
    click GH "https://github.com/argmaxinc/whisperkit/tree/main/.github/workflows"
    click FL "https://github.com/argmaxinc/whisperkit/tree/main/fastlane"
    click TEST "https://github.com/argmaxinc/whisperkit/tree/main/Tests"

    %% Styles
    classDef core fill:#f6e58d,stroke:#b71540,stroke-width:2px
    classDef cli fill:#badc58,stroke:#130f40,stroke-width:2px
    classDef example fill:#f9ca24,stroke:#130f40,stroke-width:2px
    classDef external fill:#ff7979,stroke:#130f40,stroke-width:2px
    classDef ci fill:#7ed6df,stroke:#130f40,stroke-width:2px
    classDef test fill:#e056fd,stroke:#130f40,stroke-width:2px
    classDef input fill:#dff9fb,stroke:#130f40,stroke-width:2px
    classDef output fill:#95a5a6,stroke:#130f40,stroke-width:2px

```


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---