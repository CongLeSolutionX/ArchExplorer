---
created: 2025-06-29 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/jupyter/nbconvert
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExdTN1Z3BtN3BoZXpienYydDJva2NxbGs2enAxOXVnbG50d3BnYm40ayZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/jQbLzuaEu5Wdq8xiWd/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# nbconvert repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for 👨‍🎓 <ins>educational purposes</ins> 👨‍🎓 (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), 📖 <ins> personal study </ins> 📖, and 🔖 <ins> technical reference </ins> 🔖.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>



---

```mermaid
---
title: "nbconvert repo project"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY-SA 4.0"
copyright: "Copyright © 2025 Cong Le. All Rights Reserved."
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
    %% CLI / Main Application
    subgraph "CLI / Main Application"
        CLI_main["__main__.py"]:::core
        CLI_app["nbconvertapp.py"]:::core
    end

    %% Notebook Reader
    Reader["Notebook Reader\n(nbconvert/utils/io.py)"]:::core

    %% Preprocessor Chain
    subgraph "Preprocessor Chain"
        Pre_dir["nbconvert/preprocessors/"]:::core
        Pre_base["base.py"]:::core
    end

    %% Template Renderer
    subgraph "Template Renderer"
        Exp_api["exporter.py"]:::core
        Temp_exp["templateexporter.py"]:::core
        Filters["Filters\n(nbconvert/filters/)"]:::core
    end

    %% Postprocessor Chain
    subgraph "Postprocessor Chain"
        Post_dir["nbconvert/postprocessors/"]:::core
        Post_base["base.py"]:::core
    end

    %% Writer
    subgraph "Writer"
        Writers_dir["nbconvert/writers/"]:::core
        Files["files.py"]:::core
        Stdout["stdout.py"]:::core
    end

    %% Template Store
    Builtin["Built-in Templates\n(nbconvert/templates/)"]:::store
    Shipped["Shipped Templates\n(share/templates/)"]:::store

    %% External Tools
    subgraph "External Tools"
        Pandoc_wrapper["pandoc.py"]:::external
        Pandoc_filter["Pandoc Filter\n(nbconvert/filters/pandoc.py)"]:::external
    end

    %% Data Flow
    CLI_main -->|"calls"| CLI_app
    CLI_app -->|"loads notebook"| Reader
    Reader -->|"produces NotebookNode"| Pre_dir
    Pre_dir --> Pre_base
    Pre_base -->|"preprocessed notebook"| Exp_api
    Exp_api --> Temp_exp
    Filters --> Temp_exp
    Temp_exp -->|"rendered output"| Post_dir
    Post_dir --> Post_base
    Post_base --> Writers_dir
    Writers_dir --> Files
    Writers_dir --> Stdout
    Files -->|"writes file"| Output["Output\n(files or stdout)"]
    Stdout --> Output

    %% Template Store Overrides
    Builtin --> Temp_exp
    Shipped --> Temp_exp

    %% Optional Pandoc Integration
    Temp_exp -->|"shells out"| Pandoc_wrapper
    Pandoc_wrapper --> Pandoc_filter
    Pandoc_filter --> Temp_exp

    %% Click events
    click CLI_main "https://github.com/jupyter/nbconvert/blob/main/nbconvert/__main__.py"
    click CLI_app "https://github.com/jupyter/nbconvert/blob/main/nbconvert/nbconvertapp.py"
    click Reader "https://github.com/jupyter/nbconvert/blob/main/nbconvert/utils/io.py"
    click Pre_dir "https://github.com/jupyter/nbconvert/tree/main/nbconvert/preprocessors/"
    click Pre_base "https://github.com/jupyter/nbconvert/blob/main/nbconvert/preprocessors/base.py"
    click Exp_api "https://github.com/jupyter/nbconvert/blob/main/nbconvert/exporters/exporter.py"
    click Temp_exp "https://github.com/jupyter/nbconvert/blob/main/nbconvert/exporters/templateexporter.py"
    click Filters "https://github.com/jupyter/nbconvert/tree/main/nbconvert/filters/"
    click Post_dir "https://github.com/jupyter/nbconvert/tree/main/nbconvert/postprocessors/"
    click Post_base "https://github.com/jupyter/nbconvert/blob/main/nbconvert/postprocessors/base.py"
    click Writers_dir "https://github.com/jupyter/nbconvert/tree/main/nbconvert/writers/"
    click Files "https://github.com/jupyter/nbconvert/blob/main/nbconvert/writers/files.py"
    click Stdout "https://github.com/jupyter/nbconvert/blob/main/nbconvert/writers/stdout.py"
    click Builtin "https://github.com/jupyter/nbconvert/tree/main/nbconvert/templates/"
    click Shipped "https://github.com/jupyter/nbconvert/tree/main/share/templates/"
    click Pandoc_wrapper "https://github.com/jupyter/nbconvert/blob/main/nbconvert/utils/pandoc.py"
    click Pandoc_filter "https://github.com/jupyter/nbconvert/blob/main/nbconvert/filters/pandoc.py"

    %% Styles
    classDef core fill:#BBE1FA,stroke:#333,stroke-width:1px
    classDef store fill:#C3FDB8,stroke:#333,stroke-width:1px
    classDef external fill:#FFCC99,stroke:#333,stroke-width:1px

```

----

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
    

  Closing_quote ~~~ My_Meme
    
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
