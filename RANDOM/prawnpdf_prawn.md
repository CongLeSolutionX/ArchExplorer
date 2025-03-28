---
created: 2025-03-28 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# PrawnPDF - Prawn
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
title: "Prawn PDF - Prawn"
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
    'flowchart': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'lineColor': '#F8B229'
    }
  }
}%%
flowchart TD
    A["API Entry (require 'prawn')"]:::entry
    B["Prawn::Document"]:::core

    subgraph "Core Engine"
        B
        C["bounding_box (within Document)"]:::core
        D["column_box (within Document)"]:::core
        E["internals (within Document)"]:::core
        F["span (within Document)"]:::core
    end

    subgraph "Text Rendering"
        G["Prawn::Text"]:::text
        H["Text Box & Inline Formatting"]:::text
        I["Formatted Text Modules"]:::text
    end

    subgraph "Graphics and Drawing"
        J["Prawn::Graphics"]:::graphics
        K["Vector Drawing & Transformations"]:::graphics
    end

    subgraph "Fonts and Encoding"
        L["Prawn::Font"]:::fonts
        M["Prawn::Encoding"]:::fonts
        N["Prawn::Fonts"]:::fonts
        O["Font Metric Cache"]:::fonts
    end

    subgraph "Image Handling"
        P["Prawn::Images"]:::images
        Q["Image Handler"]:::images
    end

    subgraph "Security"
        R["Prawn::Security"]:::security
    end

    subgraph "Auxiliary Utilities"
        S["Measurements & Transformation Stack"]:::utilities
        T["Utility Functions"]:::utilities
    end

    subgraph "Manual & Documentation"
        U["Manual & Examples"]:::docs
    end

    subgraph "Tests & Benchmarks"
        V["Spec (Testing)"]:::tests
        W["Benchmarks"]:::tests
    end

    %% Relationships and Data Flow
    A -->|"initiates"| B
    B -->|"calls_text_module"| G
    B -->|"calls_graphics_module"| J
    B -->|"calls_fonts_module"| L
    B -->|"invokes_image_handler"| Q
    B -->|"integrates_security"| R
    G -->|"formats_using_fonts"| L
    G -->|"uses_encoding"| M
    J -->|"renders_vector_drawing"| K
    P -->|"processed_by"| Q
    B -->|"utilizes_utilities"| S
    B -->|"utilizes_utilities"| T
    A ---|"guided_by"| U
    A ---|"validated_by"| V
    A ---|"benchmarked_by"| W

    %% Click Events for Component Mapping
    click B "https://github.com/prawnpdf/prawn/blob/master/lib/prawn/document.rb"
    click C "https://github.com/prawnpdf/prawn/tree/master/lib/prawn/document/"
    click D "https://github.com/prawnpdf/prawn/tree/master/lib/prawn/document/"
    click E "https://github.com/prawnpdf/prawn/tree/master/lib/prawn/document/"
    click F "https://github.com/prawnpdf/prawn/tree/master/lib/prawn/document/"
    click G "https://github.com/prawnpdf/prawn/blob/master/lib/prawn/text.rb"
    click H "https://github.com/prawnpdf/prawn/tree/master/lib/prawn/text/"
    click I "https://github.com/prawnpdf/prawn/tree/master/lib/prawn/text/formatted/"
    click J "https://github.com/prawnpdf/prawn/blob/master/lib/prawn/graphics.rb"
    click K "https://github.com/prawnpdf/prawn/tree/master/lib/prawn/graphics/"
    click L "https://github.com/prawnpdf/prawn/blob/master/lib/prawn/font.rb"
    click M "https://github.com/prawnpdf/prawn/blob/master/lib/prawn/encoding.rb"
    click N "https://github.com/prawnpdf/prawn/blob/master/lib/prawn/fonts.rb"
    click O "https://github.com/prawnpdf/prawn/blob/master/lib/prawn/font_metric_cache.rb"
    click P "https://github.com/prawnpdf/prawn/blob/master/lib/prawn/images.rb"
    click Q "https://github.com/prawnpdf/prawn/blob/master/lib/prawn/image_handler.rb"
    click R "https://github.com/prawnpdf/prawn/blob/master/lib/prawn/security.rb"
    click S "https://github.com/prawnpdf/prawn/blob/master/lib/prawn/measurements.rb"
    click T "https://github.com/prawnpdf/prawn/blob/master/lib/prawn/utilities.rb"
    click U "https://github.com/prawnpdf/prawn/tree/master/manual/"
    click V "https://github.com/prawnpdf/prawn/tree/master/spec/"
    click W "https://github.com/prawnpdf/prawn/tree/master/bench/"

    %% Styles and Colors
    classDef entry fill:#ffcc00,stroke:#333,stroke-width:2px;
    classDef core fill:#66ccff,stroke:#333,stroke-width:2px;
    classDef text fill:#ff9999,stroke:#333,stroke-width:2px;
    classDef graphics fill:#cc99ff,stroke:#333,stroke-width:2px;
    classDef fonts fill:#99ff99,stroke:#333,stroke-width:2px;
    classDef images fill:#ffcc99,stroke:#333,stroke-width:2px;
    classDef security fill:#ff6666,stroke:#333,stroke-width:2px;
    classDef utilities fill:#99ccff,stroke:#333,stroke-width:2px;
    classDef docs fill:#ffff99,stroke:#333,stroke-width:2px;
    classDef tests fill:#cccccc,stroke:#333,stroke-width:2px;
    

```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---