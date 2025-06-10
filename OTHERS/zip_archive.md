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
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExNGZiMnVrZTZ2amc4d2lmanAzZHV5bmM5YzY4eWxkbjZ2azduc2x3biZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/9hSsOshicxQHe/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Zip Archive
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
title: "Zip Archive"
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
    %% Core Library Subgraph
    subgraph "Core Library"
        A["SSZipArchive Core Library"]:::library
        B["Minizip Module"]:::module
    end

    %% Client Applications Subgraph
    subgraph "Client Applications"
        C["Client Applications (Objective-C Example)"]:::client
        D["Client Applications (Swift Example)"]:::client
    end

    %% Testing Subgraph
    subgraph "Testing"
        E["Tests & Fixtures"]:::test
    end

    %% External Dependencies Subgraph
    subgraph "External Dependencies"
        F["zlib"]:::external
        G["libiconv"]:::external
        H["Security Framework"]:::external
    end

    %% Build/CI Infrastructure Subgraph
    subgraph "Build/CI Infrastructure"
        I["CI/Build Infrastructure"]:::ci
        J["ZipArchive.xcodeproj"]:::ci
        K["Example/ZipArchiveExample.xcodeproj"]:::ci
    end

    %% Relationships
    C -->|"calls"| A
    D -->|"calls"| A
    E -->|"exercises"| A
    A -->|"utilizes"| B
    A -->|"depends"| F
    A -->|"depends"| G
    A -->|"depends"| H
    I -->|"triggers"| J
    I -->|"triggers"| K

    %% Click Events
    click A "https://github.com/ziparchive/ziparchive/tree/main/SSZipArchive"
    click B "https://github.com/ziparchive/ziparchive/tree/main/SSZipArchive/minizip"
    click C "https://github.com/ziparchive/ziparchive/tree/main/Example/ObjectiveCExample"
    click D "https://github.com/ziparchive/ziparchive/tree/main/Example/SwiftExample"
    click E "https://github.com/ziparchive/ziparchive/tree/main/Example/ObjectiveCExampleTests"
    click I "https://github.com/ziparchive/ziparchive/tree/main/.github/workflows"
    click J "https://github.com/ziparchive/ziparchive/blob/main/ZipArchive.xcodeproj"
    click K "https://github.com/ziparchive/ziparchive/blob/main/Example/ZipArchiveExample.xcodeproj"

    %% Styles
    classDef library fill:#AEDFF7,stroke:#333,stroke-width:2px;
    classDef module fill:#CDE6C7,stroke:#333,stroke-width:2px;
    classDef client fill:#FFC2C2,stroke:#333,stroke-width:2px;
    classDef test fill:#FFF79A,stroke:#333,stroke-width:2px;
    classDef external fill:#D0E6A5,stroke:#333,stroke-width:2px;
    classDef ci fill:#E0BBE4,stroke:#333,stroke-width:2px;

```


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
