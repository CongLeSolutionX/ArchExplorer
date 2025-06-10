---
created: 2025-03-16 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExczNvNmgxbnE2ZHkwcGw4aDBkZjdtaHI2eDZoYzk5bmVtNGNybGJucyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/OLPQ6z2hlHmwFc4Hso/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# EEFS
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
title: "EEFS"
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
    subgraph EEFS_Core_Libraries["EEFS Core Libraries"]
        core_eepromfs["eepromfs"]:::library
        core_microeefs["microeefs"]:::library
        core_page_window["page window"]:::library
    end

    subgraph Drivers["Drivers"]
        driver_rtems["RTEMS Driver"]:::driver
        driver_standalone["Standalone Driver"]:::driver
        driver_vxworks["vxWorks Driver"]:::driver
    end

    subgraph Development_Tools["Development Tools"]
        tool_eefstool["eefstool"]:::tool
        tool_geneepromfs["geneepromfs"]:::tool
    end

    api_inc["API / Configuration<br>(inc)"]:::api
    doc_doc["Documentation<br>(doc)"]:::doc

    %% Drivers using Core Libraries
    driver_rtems -->|"uses"| core_eepromfs
    driver_rtems -->|"uses"| core_microeefs
    driver_rtems -->|"uses"| core_page_window

    driver_standalone -->|"uses"| core_eepromfs
    driver_standalone -->|"uses"| core_microeefs
    driver_standalone -->|"uses"| core_page_window

    driver_vxworks -->|"uses"| core_eepromfs
    driver_vxworks -->|"uses"| core_microeefs
    driver_vxworks -->|"uses"| core_page_window

    %% Tools building images from Core Libraries
    tool_eefstool -->|"builds"| core_eepromfs
    tool_eefstool -->|"builds"| core_microeefs
    tool_eefstool -->|"builds"| core_page_window

    tool_geneepromfs -->|"builds"| core_eepromfs
    tool_geneepromfs -->|"builds"| core_microeefs
    tool_geneepromfs -->|"builds"| core_page_window

    %% Common API/Configuration used across components
    api_inc ---|"configures"| core_eepromfs
    api_inc ---|"configures"| core_microeefs
    api_inc ---|"configures"| core_page_window
    api_inc ---|"configures"| driver_rtems
    api_inc ---|"configures"| driver_standalone
    api_inc ---|"configures"| driver_vxworks
    api_inc ---|"configures"| tool_eefstool
    api_inc ---|"configures"| tool_geneepromfs

    %% Documentation providing design notes
    doc_doc ---|"documents"| api_inc
    doc_doc ---|"documents"| driver_rtems
    doc_doc ---|"documents"| core_eepromfs

    %% Click Events
    click core_eepromfs "https://github.com/nasa/eefs/blob/master/libraries/eepromfs/eefs_fileapi.c"
    click core_microeefs "https://github.com/nasa/eefs/blob/master/libraries/microeefs/microeefs.c"
    click core_page_window "https://github.com/nasa/eefs/blob/master/libraries/page_window/eeprom_pagewindow.c"
    click driver_rtems "https://github.com/nasa/eefs/blob/master/drivers/rtems_driver/eefsDriver.c"
    click driver_standalone "https://github.com/nasa/eefs/blob/master/drivers/standalone_driver/eefs_filesys.c"
    click driver_vxworks "https://github.com/nasa/eefs/blob/master/drivers/vxworks_driver/eefs_vxworks.c"
    click api_inc "https://github.com/nasa/eefs/blob/master/inc/common_types.h"
    click tool_eefstool "https://github.com/nasa/eefs/tree/master/tools/eefstool"
    click tool_geneepromfs "https://github.com/nasa/eefs/tree/master/tools/geneepromfs"
    click doc_doc "https://github.com/nasa/eefs/blob/master/doc/EEPROM File System Design Notes.docx"

    %% Styles
    classDef library fill:#f9c,stroke:#333,stroke-width:2px
    classDef driver fill:#bbf,stroke:#333,stroke-width:2px
    classDef tool fill:#bfb,stroke:#333,stroke-width:2px
    classDef api fill:#ff9,stroke:#333,stroke-width:2px
    classDef doc fill:#ccf,stroke:#333,stroke-width:2px
    

```






---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
