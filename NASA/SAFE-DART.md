---
created: 2025-03-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# SAFE-DART
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
title: "CHANGE_ME_DADDY"
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
    'flowchart': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#2ff9',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TD
    subgraph Configuration["Configuration"]
        CONFIG["Configuration File<br>(safedart.ini)"]:::config
    end

    subgraph Core_Library["Core Library<br>(libsafedart)"]
        LIB["SAFE-DART Library<br>(libsafedart)"]:::library
        BUILDER["Builder"]:::library
        CONFIG_COMP["Configuration Components"]:::library
        MODULE_LOADER["Module Loader<br>(LibraryModuleLoader)"]:::library
        REFLECTION["Reflection Utilities"]:::library
    end

    subgraph Executable["Executable<br>(safedart)"]
        EXE["SAFE-DART Executable<br>(safedart)"]:::executable
    end

    subgraph Example_Modules["Example Modules"]
        APP["GreetApplication Module"]:::example
        GREETER["Greeter Module<br>(EnglishGreeter)"]:::example
    end

    subgraph Testing["Testing"]
        TESTS["Tests Suite"]:::testing
    end

    CONFIG -->|"feeds"| EXE
    CONFIG -->|"feeds"| CONFIG_COMP
    EXE -->|"uses"| LIB
    EXE -->|"injects builder"| BUILDER
    CONFIG_COMP -->|"initializes"| BUILDER
    BUILDER -->|"uses reflection"| REFLECTION
    LIB -->|"provides builder to"| APP
    LIB -->|"provides builder to"| GREETER
    LIB -->|"module discovery"| MODULE_LOADER
    MODULE_LOADER -->|"loads"| APP
    MODULE_LOADER -->|"loads"| GREETER
    TESTS -->|"verifies"| LIB
    TESTS -->|"verifies"| EXE

    click LIB "https://github.com/nasa/safe-dart/tree/master/libsafedart/"
    click BUILDER "https://github.com/nasa/safe-dart/blob/master/libsafedart/builder.h"
    click BUILDER "https://github.com/nasa/safe-dart/blob/master/libsafedart/builder.cpp"
    click CONFIG_COMP "https://github.com/nasa/safe-dart/blob/master/libsafedart/configuration.h"
    click CONFIG_COMP "https://github.com/nasa/safe-dart/blob/master/libsafedart/configuration.cpp"
    click CONFIG_COMP "https://github.com/nasa/safe-dart/blob/master/libsafedart/memoryconfiguration.h"
    click CONFIG_COMP "https://github.com/nasa/safe-dart/blob/master/libsafedart/memoryconfiguration.cpp"
    click CONFIG_COMP "https://github.com/nasa/safe-dart/blob/master/libsafedart/settingsconfiguration.h"
    click CONFIG_COMP "https://github.com/nasa/safe-dart/blob/master/libsafedart/settingsconfiguration.cpp"
    click MODULE_LOADER "https://github.com/nasa/safe-dart/blob/master/libsafedart/librarymoduleloader.h"
    click MODULE_LOADER "https://github.com/nasa/safe-dart/blob/master/libsafedart/librarymoduleloader.cpp"
    click REFLECTION "https://github.com/nasa/safe-dart/blob/master/libsafedart/reflectable.h"
    click EXE "https://github.com/nasa/safe-dart/tree/master/safedart/"
    click APP "https://github.com/nasa/safe-dart/tree/master/examples/greet/greetapplication/"
    click GREETER "https://github.com/nasa/safe-dart/blob/master/examples/greet/common/greeter.h"
    click GREETER "https://github.com/nasa/safe-dart/tree/master/examples/greet/englishgreeter/"
    click CONFIG "https://github.com/nasa/safe-dart/blob/master/examples/greet/safedart.ini"
    click TESTS "https://github.com/nasa/safe-dart/tree/master/tests/"

    classDef library fill:#fdf22,stroke:#ff0000,stroke-width:2px
    classDef executable fill:#dff2,stroke:#00aa00,stroke-width:2px
    classDef example fill:#ddf3,stroke:#0000ff,stroke-width:2px
    classDef config fill:#ffc4,stroke:#cccc00,stroke-width:2px
    classDef testing fill:#eCC4,stroke:#999999,stroke-width:2px
    
```







---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---