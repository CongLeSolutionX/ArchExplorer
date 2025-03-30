---
created: 2025-03-29 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Sourmesen Mesen2
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
title: "Sourmesen - Mesen2"
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
    %% UI Layer
    subgraph "UI Layer"
        UI["UI/Presentation Layer"]:::ui
        Interop["Interop Layer"]:::interop
    end
    UI -->|"communicates"| Interop

    %% Emulation Core Layer
    subgraph "Emulation Core"
        ECore["Emulation Core"]:::core
        Nes["NES Module"]:::core
        Gboy["Gameboy Module"]:::core
        GBA["GBA Module"]:::core
        Snes["SNES Module"]:::core
        PCE["PC Engine Module"]:::core
        SMS["SMS/Game Gear Module"]:::core
        WS["WonderSwan Module"]:::core
        Debugger["Core Debugger"]:::debugger

        ECore --> Nes
        ECore --> Gboy
        ECore --> GBA
        ECore --> Snes
        ECore --> PCE
        ECore --> SMS
        ECore --> WS

        Nes -->|"debugs"| Debugger
        Gboy -->|"debugs"| Debugger
        GBA -->|"debugs"| Debugger
        Snes -->|"debugs"| Debugger
        PCE -->|"debugs"| Debugger
        SMS -->|"debugs"| Debugger
        WS -->|"debugs"| Debugger
    end

    Interop -->|"bridges"| ECore
    Debugger -->|"reports"| UI

    %% Scripting Interface
    LuaScripting["Lua Scripting Interface"]:::scripting
    LuaScripting -->|"scripts"| Debugger

    %% Platform Abstraction Layer
    subgraph "Platform Abstraction"
        WindowsOS["Windows"]:::platform
        LinuxOS["Linux"]:::platform
        MacOS["macOS"]:::platform
        SteamOS["SteamOS Config"]:::platform
    end

    ECore -->|"platformsupport"| WindowsOS
    ECore -->|"platformsupport"| LinuxOS
    ECore -->|"platformsupport"| MacOS
    ECore -->|"platformsupport"| SteamOS

    %% Utility & Supporting Libraries
    subgraph "Utility & Supporting Libraries"
        Utils["Utilities"]:::util
        SevenZipLib["SevenZip"]:::util
        SdlLib["SDL"]:::util
    end

    Utils ---|"supports"| ECore
    SevenZipLib ---|"supports"| ECore
    SdlLib ---|"supports"| ECore

    Utils ---|"supports"| UI
    SevenZipLib ---|"supports"| UI
    SdlLib ---|"supports"| UI

    %% Click Events
    click ECore "https://github.com/sourmesen/mesen2/tree/master/Core"
    click Nes "https://github.com/sourmesen/mesen2/tree/master/Core/NES"
    click Gboy "https://github.com/sourmesen/mesen2/tree/master/Core/Gameboy"
    click GBA "https://github.com/sourmesen/mesen2/tree/master/Core/GBA"
    click Snes "https://github.com/sourmesen/mesen2/tree/master/Core/SNES"
    click PCE "https://github.com/sourmesen/mesen2/tree/master/Core/PCE"
    click SMS "https://github.com/sourmesen/mesen2/tree/master/Core/SMS"
    click WS "https://github.com/sourmesen/mesen2/tree/master/Core/WS"
    click Debugger "https://github.com/sourmesen/mesen2/tree/master/Core/Debugger"
    click LuaScripting "https://github.com/sourmesen/mesen2/tree/master/Lua"
    click UI "https://github.com/sourmesen/mesen2/tree/master/UI"
    click Interop "https://github.com/sourmesen/mesen2/tree/master/InteropDLL"
    click WindowsOS "https://github.com/sourmesen/mesen2/tree/master/Windows"
    click LinuxOS "https://github.com/sourmesen/mesen2/tree/master/Linux"
    click MacOS "https://github.com/sourmesen/mesen2/tree/master/MacOS"
    click SteamOS "https://github.com/sourmesen/mesen2/blob/master/SteamOS.md"
    click Utils "https://github.com/sourmesen/mesen2/tree/master/Utilities"
    click SevenZipLib "https://github.com/sourmesen/mesen2/tree/master/SevenZip"
    click SdlLib "https://github.com/sourmesen/mesen2/tree/master/Sdl"

    %% Styles
    classDef core fill:#8ecae6,stroke:#219ebc,stroke-width:2px;
    classDef ui fill:#ffcc99,stroke:#ff9900,stroke-width:2px;
    classDef interop fill:#f5c8d6,stroke:#f72585,stroke-width:2px;
    classDef debugger fill:#ffe5b4,stroke:#ffb703,stroke-width:2px;
    classDef scripting fill:#caffbf,stroke:#57cc99,stroke-width:2px;
    classDef platform fill:#d8f3dc,stroke:#40916c,stroke-width:2px;
    classDef util fill:#e0fbfc,stroke:#98c1d9,stroke-width:2px;

```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---