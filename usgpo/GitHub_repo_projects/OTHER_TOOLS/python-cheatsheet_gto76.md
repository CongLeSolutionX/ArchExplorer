---
created: 2025-06-21 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/gto76/python-cheatsheet
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExOGl5ankxbThqYXF5a2l6Nm0xcm16N2M4dGxzYzNyMzR4aG01MmlpbyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/TncmRRvEGVoVcHgaAb/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# gto76 - python-cheatsheet repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


----

```mermaid
---
title: "gto76 - python-cheatsheet repo project"
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
    %% Developer Workstation
    subgraph "Developer Workstation" 
        direction TB
        DEV["Developer"]:::dev

        subgraph "Source Repository"
            direction TB
            README["README.md"]:::code
            INDEX_HTML["index.html"]:::code
            PARSE_JS["parse.js"]:::code
        end

        subgraph "Web Build Pipeline" 
            direction TB
            CONVERT["convert_table.py"]:::build
            UPDATE["update_plots.py"]:::build
            EMPTY["empty_script.py"]:::build
            CONVERT -->|produces| CASES["covid_cases.js"]:::asset
            UPDATE -->|produces| DEATHS["covid_deaths.js"]:::asset
            UPDATE -->|produces| CONTINENTS["continents.csv"]:::asset
        end

        subgraph "PDF Build Pipeline"
            direction TB
            CREATE_IDX["create_index.py"]:::build
            REMOVE_LNK["remove_links.py"]:::build
            CREATE_IDX -->|produces| PDF_INDEX["index_for_pdf.html"]:::asset
            CREATE_IDX -->|produces| PDF_PRINT["index_for_pdf_print.html"]:::asset
            CREATE_IDX -->|produces| POPUP["popup.html"]:::asset
            REMOVE_LNK -->|cleans| PDF_README["README.md (PDF)"]:::asset
        end

        DEV -->|runs| CONVERT
        DEV -->|runs| UPDATE
        DEV -->|runs| CREATE_IDX
        DEV -->|runs| REMOVE_LNK
        DEV -->|edits| README
        DEV -->|edits| INDEX_HTML
        DEV -->|edits| PARSE_JS
    end

    %% Version Control & Hosting
    subgraph "Version Control & Hosting"
        direction TB
        GIT["Git/GitHub"]:::host
        HOST["GitHub Pages"]:::host
    end

    README -->|commit| GIT
    INDEX_HTML -->|commit| GIT
    PARSE_JS -->|commit| GIT
    CASES -->|commit| GIT
    DEATHS -->|commit| GIT
    CONTINENTS -->|commit| GIT
    PDF_INDEX -->|commit| GIT
    PDF_PRINT -->|commit| GIT
    POPUP -->|commit| GIT
    PDF_README -->|commit| GIT

    GIT -->|deploys| HOST

    %% Browser / Frontend
    subgraph "Client Browser (Runtime)"
        direction TB
        BROWSER["Browser"]:::runtime
        INDEX_HTML_R["index.html"]:::asset
        PARSE_JS_R["parse.js"]:::asset
        CSS["web/style.css, style_dark*.css"]:::asset
        FONTS["web/OnlineWebFonts_COM_*/"]:::asset
        CASES_R["covid_cases.js"]:::asset
        DEATHS_R["covid_deaths.js"]:::asset
        CONTINENTS_R["continents.csv"]:::asset
        PLOTLY["Plotly.js"]:::external
        PDF_INDEX_R["pdf/index_for_pdf.html"]:::asset
        XML["pdf/Acrobat/*.xml"]:::asset

        BROWSER -->|fetch| INDEX_HTML_R
        BROWSER -->|fetch| PDF_INDEX_R
        INDEX_HTML_R -->|loads| PARSE_JS_R
        PARSE_JS_R -->|reads| README
        PARSE_JS_R -->|builds UI| BROWSER
        INDEX_HTML_R -->|loads| CSS
        INDEX_HTML_R -->|loads| FONTS
        INDEX_HTML_R -->|loads| CASES_R
        INDEX_HTML_R -->|loads| DEATHS_R
        INDEX_HTML_R -->|loads| CONTINENTS_R
        INDEX_HTML_R -->|loads| PLOTLY
        PDF_INDEX_R -->|loads| XML
    end

    HOST -->|serves| INDEX_HTML_R
    HOST -->|serves| PDF_INDEX_R
    HOST -->|serves| CSS
    HOST -->|serves| FONTS
    HOST -->|serves| CASES_R
    HOST -->|serves| DEATHS_R
    HOST -->|serves| CONTINENTS_R
    HOST -->|serves| PLOTLY
    HOST -->|serves| XML

    %% Click Events
    click README "https://github.com/gto76/python-cheatsheet/blob/main/README.md"
    click INDEX_HTML "https://github.com/gto76/python-cheatsheet/blob/main/index.html"
    click PARSE_JS "https://github.com/gto76/python-cheatsheet/blob/main/parse.js"
    click CONVERT "https://github.com/gto76/python-cheatsheet/blob/main/web/convert_table.py"
    click UPDATE "https://github.com/gto76/python-cheatsheet/blob/main/web/update_plots.py"
    click EMPTY "https://github.com/gto76/python-cheatsheet/blob/main/web/empty_script.py"
    click CASES "https://github.com/gto76/python-cheatsheet/blob/main/web/covid_cases.js"
    click DEATHS "https://github.com/gto76/python-cheatsheet/blob/main/web/covid_deaths.js"
    click CONTINENTS "https://github.com/gto76/python-cheatsheet/blob/main/web/continents.csv"
    click CREATE_IDX "https://github.com/gto76/python-cheatsheet/blob/main/pdf/create_index.py"
    click REMOVE_LNK "https://github.com/gto76/python-cheatsheet/blob/main/pdf/remove_links.py"
    click PDF_INDEX "https://github.com/gto76/python-cheatsheet/blob/main/pdf/index_for_pdf.html"

    %% Styles
    classDef dev fill:#f9f,stroke:#333,stroke-width:2px
    classDef build fill:#ff9,stroke:#333,stroke-width:2px
    classDef asset fill:#9f9,stroke:#333,stroke-width:2px
    classDef host fill:#9cf,stroke:#333,stroke-width:2px
    classDef runtime fill:#fc9,stroke:#333,stroke-width:2px
    classDef code fill:#ddd,stroke:#333,stroke-width:1px
    classDef external fill:#aaa,stroke:#333,stroke-width:1px,stroke-dasharray: 5 5
```

-----


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
