---
created: 2025-03-23 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExemN3aGhjeTBvN3NodTRzZG8wNWJ4ZHh2ZW9qMmh3cTF2cGpmeGhmNSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/nQdRDGKNgEmPK/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# OpenUSD-proposals
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
title: "Pixar Animation Studios - OpenUSD Proposals"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: default
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'lineColor': '#F8B229'
    }
  }
}%%
flowchart TD
    R["Repository Root"]:::repo
    D["Documentation (README.md)"]:::doc
    W["Workflow (.github)"]:::workflow
    P["Proposals Container"]:::proposal
    CON["Contributor"]:::contributor

    R -->|"contains"| D
    R -->|"contains"| W
    R -->|"contains"| P

    D -->|"guidelines"| P
    W -->|"guides"| P

    CON -->|"submits"| W
    CON -->|"creates"| P

    %% Proposal Nodes
    L["Proposal: LineStyle"]:::proposal
    PK["Proposal: PickAPI"]:::proposal
    ACC["Proposal: accessibility"]:::proposal
    AND["Proposal: android"]:::proposal
    BP["Proposal: boost_python_removal"]:::proposal
    HY["Proposal: hydra2"]:::proposal
    IP["Proposal: image-planes"]:::proposal
    LAN["Proposal: language"]:::proposal
    MX["Proposal: materialx-versioning"]:::proposal
    MA["Proposal: multiple-animations"]:::proposal
    NE["Proposal: namespace_editing"]:::proposal
    PCB["Proposal: pattern-based-collections"]:::proposal
    PRF["Proposal: profiles"]:::proposal
    RUM["Proposal: revise_use_of_layer_metadata"]:::proposal
    SAM["Proposal: selfAssemblingModelHierarchy"]:::proposal
    SS["Proposal: semantic_schema"]:::proposal
    SA["Proposal: spline-animation"]:::proposal
    SVE["Proposal: stage_variable_expressions"]:::proposal
    TX["Proposal: text"]:::proposal
    TFF["Proposal: tf_utf8_identifiers"]:::proposal
    TI["Proposal: transcoding_invalid_identifiers"]:::proposal
    UV["Proposal: usd-validation-framework"]:::proposal
    UST["Proposal: usdotio"]:::proposal
    VS["Proposal: variant_set_metadata"]:::proposal

    %% Connect Proposals Container to each Proposal Node
    P --> L
    P --> PK
    P --> ACC
    P --> AND
    P --> BP
    P --> HY
    P --> IP
    P --> LAN
    P --> MX
    P --> MA
    P --> NE
    P --> PCB
    P --> PRF
    P --> RUM
    P --> SAM
    P --> SS
    P --> SA
    P --> SVE
    P --> TX
    P --> TFF
    P --> TI
    P --> UV
    P --> UST
    P --> VS

    %% Click Events
    click D "https://github.com/pixaranimationstudios/openusd-proposals/blob/main/README.md"
    click W "https://github.com/pixaranimationstudios/openusd-proposals/blob/main/.github"
    click P "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals"
    click L "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/LineStyle"
    click PK "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/PickAPI"
    click ACC "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/accessibility"
    click AND "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/android"
    click BP "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/boost_python_removal"
    click HY "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/hydra2"
    click IP "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/image-planes"
    click LAN "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/language"
    click MX "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/materialx-versioning"
    click MA "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/multiple-animations"
    click NE "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/namespace_editing"
    click PCB "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/pattern-based-collections"
    click PRF "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/profiles"
    click RUM "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/revise_use_of_layer_metadata"
    click SAM "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/selfAssemblingModelHierarchy"
    click SS "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/semantic_schema"
    click SA "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/spline-animation"
    click SVE "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/stage_variable_expressions"
    click TX "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/text"
    click TFF "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/tf_utf8_identifiers"
    click TI "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/transcoding_invalid_identifiers"
    click UV "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/usd-validation-framework"
    click UST "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/usdotio"
    click VS "https://github.com/pixaranimationstudios/openusd-proposals/tree/main/proposals/variant_set_metadata"

    %% Styles
    classDef repo fill:#FAD,stroke:#333,stroke-width:2px;
    classDef doc fill:#BBF,stroke:#333,stroke-width:2px;
    classDef workflow fill:#BFB,stroke:#333,stroke-width:2px;
    classDef proposal fill:#FFDEAD,stroke:#333,stroke-width:2px;
    classDef contributor fill:#CDE,stroke:#333,stroke-width:2px

```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
