---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/GPGTools/pinentry
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExeHN6eDNuZHkyOG1qN3BqaXhybW1hZWt0dGlvcDdyNWliM2Z1Y2E3MiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/DHqth0hVQoIzS/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# pinentry repo project
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
title: "pinentry repo project"
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
flowchart TD
    subgraph "Build System"
        AC["configure.ac"]:::build
        MA["Makefile.am"]:::build 
        BA["build-aux/"]:::build
        M4["m4/"]:::build
    end

    Client["External Client<br/>(GnuPG)"]
    %% :::external
    libassuan["libassuan"]:::core

    subgraph "pinentry Core"
    %% :::core
        Pmain["pinentry/pinentry.c"]
        Phdr["pinentry/pinentry.h"]
        Argc["pinentry/argparse.c"]
        Argh["pinentry/argparse.h"]
        PcacheC["pinentry/password-cache.c"]
        PcacheH["pinentry/password-cache.h"]
    end

    subgraph Secure_Memory_Manager["Secure Memory Manager<br/>(secmem)"]
        SMc["secmem/secmem.c"]:::core
        SMh["secmem/secmem.h"]:::core
        SMpp["secmem/secmem++.h"]:::core
        SMuh["secmem/secmem-util.h"]:::core
        Utilc["secmem/util.c"]:::core
        Utilh["secmem/util.h"]:::core
    end

    subgraph Frontends["Frontends"]
    %% :::frontend
        subgraph "Text Frontends"
        %% :::frontend
            Curses["curses/pinentry-curses.c"]
            CMake["curses/Makefile.am"]
            TTY["tty/pinentry-tty.c"]
            TMake["tty/Makefile.am"]
            Emac["emacs/pinentry-emacs.c"]
            EMake["emacs/Makefile.am"]
        end
        subgraph "GUI Frontends"
        %% :::frontend
            subgraph "GTK+ 2"
            %% :::frontend
                GTKc["gtk+-2/pinentry-gtk-2.c"]
                GTKm["gtk+-2/Makefile.am"]
            end
            subgraph "GNOME3"
            %% :::frontend
                G33c["gnome3/pinentry-gnome3.c"]
                G33m["gnome3/Makefile.am"]
            end
            subgraph "Qt Variants"
            %% :::frontend
                subgraph "Qt6 (qt)"
                %% :::frontend
                    Qt6_main["qt/main.cpp"]
                    Qt6_dialog["qt/pinentrydialog.cpp"]
                    Qt6_hdr["qt/pinentrydialog.h"]
                    Qt6conf["qt/pinentryconfirm.cpp"]
                    Qt6confh["qt/pinentryconfirm.h"]
                    Qt6_make["qt/Makefile.am"]
                end
                subgraph "Qt4"
                %% :::frontend
                    Qt4_main["qt4/main.cpp"]
                    Qt4d["qt4/pinentrydialog.cpp"]
                    Qt4dh["qt4/pinentrydialog.h"]
                    Qt4cnf["qt4/pinentryconfirm.cpp"]
                    Qt4cnfh["qt4/pinentryconfirm.h"]
                    Qt4_make["qt4/Makefile.am"]
                end
                subgraph "Qt5"
                %% :::frontend
                    Qt5_main["qt5/main.cpp"]
                    Qt5d["qt5/pinentrydialog.cpp"]
                    Qt5dh["qt5/pinentrydialog.h"]
                    Qt5cnf["qt5/pinentryconfirm.cpp"]
                    Qt5cnfh["qt5/pinentryconfirm.h"]
                    Qt5_make["qt5/Makefile.am"]
                end
            end
            subgraph "TQt"
            %% :::frontend
                TQtm["tqt/main.cpp"]
                TQtd["tqt/pinentrydialog.cpp"]
                TQt_make["tqt/Makefile.am"]
            end
            subgraph "FLTK"
            %% :::frontend
                FL_main["fltk/main.cxx"]
                FL_make["fltk/Makefile.am"]
            end
            subgraph "EFL"
            %% :::frontend
                EFLc["efl/pinentry-efl.c"]
                EFLm["efl/Makefile.am"]
            end
            subgraph "macOS"
            %% :::frontend
                Macm["macosx/main.m"]
                Macproj["macosx/pinentry-mac.xcodeproj/"]
            end
            subgraph "Win32"
            %% :::frontend
                W32m["w32/main.c"]
                W32r["w32/pinentry-w32.rc"]
                W32make["w32/Makefile.am"]
            end
        end
    end

    subgraph "Toolkit Libraries"
    %% :::extlib
        NC["ncurses"]
        GTKlib["GTK+2"]
        Qtlib["Qt"]
        Elibs["EFL"]
        FL["FLTK"]
        Cocoa["Cocoa"]
        WinAPI["Win32 API"]
    end

    Client -->|IPC/socket| libassuan -->|"protocol parse"| Pmain
    Pmain -->|"uses secmem"| SMc
    Pmain -->|"calls frontend API"| Curses
    Qt6_main -->|"fallback"| Curses
    GTKc -->|"fallback"| Curses
    AC --> Pmain
    MA --> Pmain
    BA --> Pmain
    M4 --> Pmain
    AC --> Curses
    AC --> Qt6_main
    Pmain --> Frontends
    Frontends --> Toolkit Libraries

    click AC "https://github.com/gpgtools/pinentry/blob/master/configure.ac"
    click MA "https://github.com/gpgtools/pinentry/blob/master/Makefile.am"
    click BA "https://github.com/gpgtools/pinentry/tree/master/build-aux/"
    click M4 "https://github.com/gpgtools/pinentry/tree/master/m4/"
    click Pmain "https://github.com/gpgtools/pinentry/blob/master/pinentry/pinentry.c"
    click Phdr "https://github.com/gpgtools/pinentry/blob/master/pinentry/pinentry.h"
    click Argc "https://github.com/gpgtools/pinentry/blob/master/pinentry/argparse.c"
    click Argh "https://github.com/gpgtools/pinentry/blob/master/pinentry/argparse.h"
    click PcacheC "https://github.com/gpgtools/pinentry/blob/master/pinentry/password-cache.c"
    click PcacheH "https://github.com/gpgtools/pinentry/blob/master/pinentry/password-cache.h"
    click SMc "https://github.com/gpgtools/pinentry/blob/master/secmem/secmem.c"
    click SMh "https://github.com/gpgtools/pinentry/blob/master/secmem/secmem.h"
    click SMpp "https://github.com/gpgtools/pinentry/blob/master/secmem/secmem++.h"
    click SMuh "https://github.com/gpgtools/pinentry/blob/master/secmem/secmem-util.h"
    click Utilc "https://github.com/gpgtools/pinentry/blob/master/secmem/util.c"
    click Utilh "https://github.com/gpgtools/pinentry/blob/master/secmem/util.h"
    click Curses "https://github.com/gpgtools/pinentry/blob/master/curses/pinentry-curses.c"
    click CMake "https://github.com/gpgtools/pinentry/blob/master/curses/Makefile.am"
    click TTY "https://github.com/gpgtools/pinentry/blob/master/tty/pinentry-tty.c"
    click TMake "https://github.com/gpgtools/pinentry/blob/master/tty/Makefile.am"
    click Emac "https://github.com/gpgtools/pinentry/blob/master/emacs/pinentry-emacs.c"
    click EMake "https://github.com/gpgtools/pinentry/blob/master/emacs/Makefile.am"
    click GTKc "https://github.com/gpgtools/pinentry/blob/master/gtk+-2/pinentry-gtk-2.c"
    click GTKm "https://github.com/gpgtools/pinentry/blob/master/gtk+-2/Makefile.am"
    click G33c "https://github.com/gpgtools/pinentry/blob/master/gnome3/pinentry-gnome3.c"
    click G33m "https://github.com/gpgtools/pinentry/blob/master/gnome3/Makefile.am"
    click Qt6_main "https://github.com/gpgtools/pinentry/blob/master/qt/main.cpp"
    click Qt6_dialog "https://github.com/gpgtools/pinentry/blob/master/qt/pinentrydialog.cpp"
    click Qt6_hdr "https://github.com/gpgtools/pinentry/blob/master/qt/pinentrydialog.h"
    click Qt6conf "https://github.com/gpgtools/pinentry/blob/master/qt/pinentryconfirm.cpp"
    click Qt6confh "https://github.com/gpgtools/pinentry/blob/master/qt/pinentryconfirm.h"
    click Qt6_make "https://github.com/gpgtools/pinentry/blob/master/qt/Makefile.am"
    click Qt4_main "https://github.com/gpgtools/pinentry/blob/master/qt4/main.cpp"
    click Qt4d "https://github.com/gpgtools/pinentry/blob/master/qt4/pinentrydialog.cpp"
    click Qt4dh "https://github.com/gpgtools/pinentry/blob/master/qt4/pinentrydialog.h"
    click Qt4cnf "https://github.com/gpgtools/pinentry/blob/master/qt4/pinentryconfirm.cpp"
    click Qt4cnfh "https://github.com/gpgtools/pinentry/blob/master/qt4/pinentryconfirm.h"
    click Qt4_make "https://github.com/gpgtools/pinentry/blob/master/qt4/Makefile.am"
    click Qt5_main "https://github.com/gpgtools/pinentry/blob/master/qt5/main.cpp"
    click Qt5d "https://github.com/gpgtools/pinentry/blob/master/qt5/pinentrydialog.cpp"
    click Qt5dh "https://github.com/gpgtools/pinentry/blob/master/qt5/pinentrydialog.h"
    click Qt5cnf "https://github.com/gpgtools/pinentry/blob/master/qt5/pinentryconfirm.cpp"
    click Qt5cnfh "https://github.com/gpgtools/pinentry/blob/master/qt5/pinentryconfirm.h"
    click Qt5_make "https://github.com/gpgtools/pinentry/blob/master/qt5/Makefile.am"
    click TQtm "https://github.com/gpgtools/pinentry/blob/master/tqt/main.cpp"
    click TQtd "https://github.com/gpgtools/pinentry/blob/master/tqt/pinentrydialog.cpp"
    click TQt_make "https://github.com/gpgtools/pinentry/blob/master/tqt/Makefile.am"
    click FL_main "https://github.com/gpgtools/pinentry/blob/master/fltk/main.cxx"
    click FL_make "https://github.com/gpgtools/pinentry/blob/master/fltk/Makefile.am"
    click EFLc "https://github.com/gpgtools/pinentry/blob/master/efl/pinentry-efl.c"
    click EFLm "https://github.com/gpgtools/pinentry/blob/master/efl/Makefile.am"
    click Macm "https://github.com/gpgtools/pinentry/blob/master/macosx/main.m"
    click Macproj "https://github.com/gpgtools/pinentry/tree/master/macosx/pinentry-mac.xcodeproj/"
    click W32m "https://github.com/gpgtools/pinentry/blob/master/w32/main.c"
    click W32r "https://github.com/gpgtools/pinentry/blob/master/w32/pinentry-w32.rc"
    click W32make "https://github.com/gpgtools/pinentry/blob/master/w32/Makefile.am"

    classDef core fill:#f9f,stroke:#333,stroke-width:2px
    classDef frontend fill:#bbf,stroke:#333,stroke-width:1px
    classDef extlib fill:#bfb,stroke:#333,stroke-width:1px
    classDef build fill:#eee,stroke-dasharray:5 5
    classDef external fill:#fee,stroke:#333,stroke-width:1px
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
