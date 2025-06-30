---
created: 2025-06-29 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/jupyter/nbconvert-examples
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExaHA3YjU2MW9udHVucXVtdXFiNjZmaHc4Nmc4aTg2YnBldmF2dGJjMCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/2JrSWgKLnbJJrF2lpO/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# nbconvert-examples repo project
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
title: "nbconvert-examples repo project"
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
flowchart LR
    %% Jupyter Notebook Sources
    subgraph "Jupyter Notebook Sources"
        direction TB
        NB1["basic/notebook1.ipynb"]:::notebook
        NB2["basic/notebook2.ipynb"]:::notebook
        CIT1["citations/Tutorial.ipynb"]:::notebook
        CFNB["custom_filter/notebook1.ipynb"]:::notebook
        CPNB["custom_preprocessor/notebook1.ipynb"]:::notebook
        PTNB["pdf/notebook.ipynb"]:::notebook
        SCNB["sphinx_class/notebook1.ipynb"]:::notebook
    end

    %% nbconvert Core Pipeline
    subgraph "nbconvert Core Pipeline"
        direction TB
        NL["NotebookLoader"]:::core
        PRE["Preprocessor Stage"]:::core
        FIL["Filter Stage"]:::core
        TMP["Template Engine"]:::core
        WRI["Writer"]:::core
    end

    %% Outputs
    subgraph "Output Formats"
        direction TB
        HTML["HTML"]:::output
        LATEX["LaTeX"]:::output
        PDF["PDF"]:::output
        SPHINX["Sphinx-ready"]:::output
    end

    %% External Tools
    subgraph "External Tools"
        direction TB
        TEX["LaTeX Toolchain"]:::external
        SPHERE["Sphinx Builder"]:::external
    end

    %% Connections
    NB1 --> NL
    NB2 --> NL
    CIT1 --> NL
    CFNB --> NL
    CPNB --> NL
    PTNB --> NL
    SCNB --> NL

    NL --> PRE
    PRE --> FIL
    FIL --> TMP
    TMP --> WRI

    WRI --> HTML
    WRI --> LATEX
    WRI --> PDF
    WRI --> SPHINX

    LATEX --> TEX
    SPHINX --> SPHERE

    %% Extension Points Attachments
    CFNF["null_highlight_filter.py"]:::extension
    CF_CFG["custom_filter/ipython_nbconvert_config.py"]:::extension
    CFNF --> FIL
    CF_CFG --> FIL

    CP_PP["cheese_preprocessor.py"]:::extension
    CP_CFG["custom_preprocessor/ipython_nbconvert_config.py"]:::extension
    CP_PP --> PRE
    CP_CFG --> PRE

    CIT_TPL["citations/citations.tplx"]:::extension
    CIT_TPL --> TMP

    SC_PP["sphinx_class/sphinx_preprocessor.py"]:::extension
    SC_CFG["sphinx_class/ipython_nbconvert_config.py"]:::extension
    SC_PP --> PRE
    SC_CFG --> PRE

    SC_TPLA["sphinx_class/latex_sphinx_article.tplx"]:::extension
    SC_TPLR["sphinx_class/latex_sphinx_report.tplx"]:::extension
    SC_TPLA --> TMP
    SC_TPLR --> TMP

    %% Click Events
    click NB1 "https://github.com/jupyter/nbconvert-examples/blob/master/basic/notebook1.ipynb"
    click NB2 "https://github.com/jupyter/nbconvert-examples/blob/master/basic/notebook2.ipynb"
    click CIT1 "https://github.com/jupyter/nbconvert-examples/blob/master/citations/Tutorial.ipynb"
    click CFNB "https://github.com/jupyter/nbconvert-examples/blob/master/custom_filter/notebook1.ipynb"
    click CPNB "https://github.com/jupyter/nbconvert-examples/blob/master/custom_preprocessor/notebook1.ipynb"
    click PTNB "https://github.com/jupyter/nbconvert-examples/blob/master/pdf/notebook.ipynb"
    click SCNB "https://github.com/jupyter/nbconvert-examples/blob/master/sphinx_class/notebook1.ipynb"

    click CFNF "https://github.com/jupyter/nbconvert-examples/blob/master/custom_filter/null_highlight_filter.py"
    click CF_CFG "https://github.com/jupyter/nbconvert-examples/blob/master/custom_filter/ipython_nbconvert_config.py"
    click CP_PP "https://github.com/jupyter/nbconvert-examples/blob/master/custom_preprocessor/cheese_preprocessor.py"
    click CP_CFG "https://github.com/jupyter/nbconvert-examples/blob/master/custom_preprocessor/ipython_nbconvert_config.py"
    click CIT_TPL "https://github.com/jupyter/nbconvert-examples/blob/master/citations/citations.tplx"
    click SC_PP "https://github.com/jupyter/nbconvert-examples/blob/master/sphinx_class/sphinx_preprocessor.py"
    click SC_CFG "https://github.com/jupyter/nbconvert-examples/blob/master/sphinx_class/ipython_nbconvert_config.py"
    click SC_TPLA "https://github.com/jupyter/nbconvert-examples/blob/master/sphinx_class/latex_sphinx_article.tplx"
    click SC_TPLR "https://github.com/jupyter/nbconvert-examples/blob/master/sphinx_class/latex_sphinx_report.tplx"

    %% Styles
    classDef core fill:#AED6F1,stroke:#21618C,color:#1B2631
    classDef extension fill:#ABEBC6,stroke:#229954,color:#1B2631
    classDef external fill:#F5CBA7,stroke:#B9770E,color:#1B2631
    classDef output fill:#D2B4DE,stroke:#6C3483,color:#1B2631
    classDef notebook fill:#F9E79F,stroke:#B7950B,color:#1B2631

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
