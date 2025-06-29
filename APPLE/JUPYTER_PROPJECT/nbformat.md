---
created: 2025-06-29 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/jupyter/nbformat
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExMjh6cTE3cWZ3Y2d0b2pxanVpcHR4bGVmajE4NWZwbTl3cGZ6dmYzdSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/HdmvfCeOSzG12Non0P/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# nbformat repo project
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



----

```mermaid
---
title: "nbformat repo project"
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
    %% Consumer / CLI Layer
    subgraph "Consumer / CLI Layer"
        direction TB
        CLI["jupyter-trust Script"]:::cli
        NodeWrapper["Node Wrapper (index.js)"]:::cli
    end

    %% Core nbformat API
    subgraph "Core nbformat API"
        direction TB
        Init["__init__.py"]:::api
        ConverterCore["converter.py"]:::api
        Current["current.py"]:::api
        JSONCompat["json_compat.py"]:::api
        NotebookNode["notebooknode.py"]:::api
        Struct["_struct.py"]:::api
    end

    %% I/O Modules
    subgraph "I/O Modules"
        direction TB
        Reader["reader.py"]:::io
        RW_v1["rwbase v1"]:::version
        RW_v2["rwbase v2"]:::version
        RW_v3["rwbase v3"]:::version
        RW_v4["rwbase v4"]:::version
    end

    %% Converter Modules
    subgraph "Converter Modules"
        direction TB
        Conv_v1["convert v1"]:::version
        Conv_v2["convert v2"]:::version
        Conv_v3["convert v3"]:::version
        Conv_v4["convert v4"]:::version
    end

    %% Validator & Signer
    subgraph "Validation & Signing"
        direction TB
        Validator["validator.py"]:::core
        FastJSON["fastjsonschema"]:::external
        JSONSchema["jsonschema"]:::external
        Signer["sign.py"]:::core
    end

    %% Schema / Data Definitions
    subgraph "Schemas & Data Definitions"
        direction TB
        subgraph "Schemas v3"
            Schema_v3["nbformat.v3.schema.json"]:::schema
        end
        subgraph "Schemas v4"
            Schema_v4_0["v4.0 schema"]:::schema
            Schema_v4_1["v4.1 schema"]:::schema
            Schema_v4_2["v4.2 schema"]:::schema
            Schema_v4_3["v4.3 schema"]:::schema
            Schema_v4_4["v4.4 schema"]:::schema
            Schema_v4_5["v4.5 schema"]:::schema
            Schema_v4["v4 schema"]:::schema
        end
        NotebookNodeDS["NotebookNode Structures"]:::api
    end

    %% Test Suite & Corpus
    subgraph "Tests & Corpus"
        direction TB
        Corpus["words.py (corpus)"]:::data
        Tests["tests/"]:::tests
        Tests_v1["tests/v1/"]:::tests
        Tests_v2["tests/v2/"]:::tests
        Tests_v3["tests/v3/"]:::tests
        Tests_v4["tests/v4/"]:::tests
    end

    %% Documentation & CI/CD
    subgraph "Docs & CI/CD"
        direction TB
        Docs["docs/"]:::docs
        API_RST["api.rst"]:::docs
        Conf["conf.py"]:::docs
        Index["index.rst"]:::docs
        FormatDesc["format_description.rst"]:::docs
        Markup["markup.rst"]:::docs
        CI_Tests["tests.yml"]:::ci
        CI_Prep["prep-release.yml"]:::ci
        CI_Publish["publish-release.yml"]:::ci
        CI_Changelog["publish-changelog.yml"]:::ci
        CI_Label["enforce-label.yml"]:::ci
    end

    %% External
    subgraph "External"
        direction TB
        PyPI["PyPI"]:::external
        GitHubActions["GitHub Actions"]:::external
    end

    %% Connections
    CLI -->|"invokes"| Init
    NodeWrapper -->|"calls API"| Init
    Init -->|"uses Reader"| Reader
    Reader -->|"produces NotebookNode"| NotebookNode
    NotebookNode -->|"validate"| Validator
    Validator -->|"uses"| FastJSON
    Validator -->|"or"| JSONSchema
    NotebookNode -->|"convert"| Conv_v1 & Conv_v2 & Conv_v3 & Conv_v4
    Conv_v1 -->|"uses schema"| Schema_v3
    Conv_v2 -->|"uses schema"| Schema_v4_0
    Conv_v2 --> Schema_v4_1 & Schema_v4_2 & Schema_v4_3 & Schema_v4_4 & Schema_v4_5 & Schema_v4
    Conv_v3 -->|"uses schema"| Schema_v4
    Conv_v4 -->|"uses schema"| Schema_v4
    Conv_v1 --> RW_v1
    Conv_v2 --> RW_v2
    Conv_v3 --> RW_v3
    Conv_v4 --> RW_v4
    RW_v1 -->|"writes JSON"| CLI
    RW_v2 -->|"writes JSON"| CLI
    RW_v3 -->|"writes JSON"| CLI
    RW_v4 -->|"writes JSON"| CLI
    Validator --> Signer
    Signer -->|"embeds trust"| CLI

    Tests --> Init
    Tests_v1 --> Conv_v1
    Tests_v2 --> Conv_v2
    Tests_v3 --> Conv_v3
    Tests_v4 --> Conv_v4
    Corpus --> Reader

    Docs --> Init
    CI_Tests --> Tests
    CI_Tests --> Tests_v1 & Tests_v2 & Tests_v3 & Tests_v4
    CI_Prep --> Init
    CI_Publish --> Init
    CI_Changelog --> Init
    CI_Label --> Init
    CI_Tests --> GitHubActions
    CI_Prep --> GitHubActions
    CI_Publish --> GitHubActions
    CI_Changelog --> GitHubActions
    CI_Label --> GitHubActions

    Init --> PyPI

    %% Click Events
    click CLI "https://github.com/jupyter/nbformat/tree/main/scripts/jupyter-trust"
    click NodeWrapper "https://github.com/jupyter/nbformat/blob/main/index.js"
    click Init "https://github.com/jupyter/nbformat/blob/main/nbformat/__init__.py"
    click ConverterCore "https://github.com/jupyter/nbformat/blob/main/nbformat/converter.py"
    click Current "https://github.com/jupyter/nbformat/blob/main/nbformat/current.py"
    click JSONCompat "https://github.com/jupyter/nbformat/blob/main/nbformat/json_compat.py"
    click NotebookNode "https://github.com/jupyter/nbformat/blob/main/nbformat/notebooknode.py"
    click Struct "https://github.com/jupyter/nbformat/blob/main/nbformat/_struct.py"
    click Reader "https://github.com/jupyter/nbformat/blob/main/nbformat/reader.py"
    click RW_v1 "https://github.com/jupyter/nbformat/blob/main/nbformat/v1/rwbase.py"
    click RW_v2 "https://github.com/jupyter/nbformat/blob/main/nbformat/v2/rwbase.py"
    click RW_v3 "https://github.com/jupyter/nbformat/blob/main/nbformat/v3/rwbase.py"
    click RW_v4 "https://github.com/jupyter/nbformat/blob/main/nbformat/v4/rwbase.py"
    click Conv_v1 "https://github.com/jupyter/nbformat/blob/main/nbformat/v1/convert.py"
    click Conv_v2 "https://github.com/jupyter/nbformat/blob/main/nbformat/v2/convert.py"
    click Conv_v3 "https://github.com/jupyter/nbformat/blob/main/nbformat/v3/convert.py"
    click Conv_v4 "https://github.com/jupyter/nbformat/blob/main/nbformat/v4/convert.py"
    click Validator "https://github.com/jupyter/nbformat/blob/main/nbformat/validator.py"
    click Signer "https://github.com/jupyter/nbformat/blob/main/nbformat/sign.py"
    click Schema_v3 "https://github.com/jupyter/nbformat/blob/main/nbformat/v3/nbformat.v3.schema.json"
    click Schema_v4_0 "https://github.com/jupyter/nbformat/blob/main/nbformat/v4/nbformat.v4.0.schema.json"
    click Schema_v4_1 "https://github.com/jupyter/nbformat/blob/main/nbformat/v4/nbformat.v4.1.schema.json"
    click Schema_v4_2 "https://github.com/jupyter/nbformat/blob/main/nbformat/v4/nbformat.v4.2.schema.json"
    click Schema_v4_3 "https://github.com/jupyter/nbformat/blob/main/nbformat/v4/nbformat.v4.3.schema.json"
    click Schema_v4_4 "https://github.com/jupyter/nbformat/blob/main/nbformat/v4/nbformat.v4.4.schema.json"
    click Schema_v4_5 "https://github.com/jupyter/nbformat/blob/main/nbformat/v4/nbformat.v4.5.schema.json"
    click Schema_v4 "https://github.com/jupyter/nbformat/blob/main/nbformat/v4/nbformat.v4.schema.json"
    click Corpus "https://github.com/jupyter/nbformat/blob/main/nbformat/corpus/words.py"
    click Tests "https://github.com/jupyter/nbformat/tree/main/tests/"
    click Tests_v1 "https://github.com/jupyter/nbformat/tree/main/tests/v1/"
    click Tests_v2 "https://github.com/jupyter/nbformat/tree/main/tests/v2/"
    click Tests_v3 "https://github.com/jupyter/nbformat/tree/main/tests/v3/"
    click Tests_v4 "https://github.com/jupyter/nbformat/tree/main/tests/v4/"
    click Docs "https://github.com/jupyter/nbformat/tree/main/docs/"
    click API_RST "https://github.com/jupyter/nbformat/blob/main/docs/api.rst"
    click Conf "https://github.com/jupyter/nbformat/blob/main/docs/conf.py"
    click Index "https://github.com/jupyter/nbformat/blob/main/docs/index.rst"
    click FormatDesc "https://github.com/jupyter/nbformat/blob/main/docs/format_description.rst"
    click Markup "https://github.com/jupyter/nbformat/blob/main/docs/markup.rst"
    click CI_Tests "https://github.com/jupyter/nbformat/blob/main/.github/workflows/tests.yml"
    click CI_Prep "https://github.com/jupyter/nbformat/blob/main/.github/workflows/prep-release.yml"
    click CI_Publish "https://github.com/jupyter/nbformat/blob/main/.github/workflows/publish-release.yml"
    click CI_Changelog "https://github.com/jupyter/nbformat/blob/main/.github/workflows/publish-changelog.yml"
    click CI_Label "https://github.com/jupyter/nbformat/blob/main/.github/workflows/enforce-label.yml"

    %% Styles
    classDef cli fill:#ffeb99,stroke:#aa8800;
    classDef api fill:#cce5ff,stroke:#004085;
    classDef io fill:#e2e3e5,stroke:#6c757d;
    classDef version fill:#d4edda,stroke:#155724;
    classDef core fill:#b8daff,stroke:#0c5460;
    classDef external fill:#f8d7da,stroke:#721c24,stroke-dasharray: 5 5;
    classDef schema fill:#d1ecf1,stroke:#0c5460,stroke-dasharray: 2 2;
    classDef data fill:#e2e3e5,stroke:#6c757d;
    classDef tests fill:#e2e3e5,stroke:#6c757d;
    classDef docs fill:#f0f0f0,stroke:#999999;
    classDef ci fill:#fff3cd,stroke:#856404;

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
