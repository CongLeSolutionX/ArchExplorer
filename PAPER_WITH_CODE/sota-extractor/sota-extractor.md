---
created: 2025-02-18 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExaTF4Mzh3c3QwNnd1Z2tlMGx3enc4OGFrZjVrcDRqaWRzaWh2N3RiOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3xz2BMctq9SRqEWfgQ/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----



# Sota Extractor
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
title: "Papers With Code - Sota Extractor"
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
    "graph": { "htmlLabels": false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#f231',
      'primaryTextColor': '#239',
      'textColor': '#F8B229',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TD
    %% CLI Layer
    subgraph CLI_Layer["CLI Layer"]
        CLI_Entry["CLI Entry Point"]:::cli
        CLI_Cmd["CLI Command Logic"]:::cli
    end

    CLI_Entry --> CLI_Cmd

    %% Scraper Engine Layer
    subgraph Scraper_Engine["Scraper Engine"]
        Scrapers_General["General Scrapers"]:::scraper
        Scrapers_NLP["NLP-progress Scraper"]:::scraper
    end

    %% Data Handling & Serialization Layer
    subgraph Data_Handling_Serialization["Data Handling & Serialization"]
        Serialization["Serialization Logic"]:::data
        TaskDB["Task Database Models"]:::data
    end

    %% Data Storage Layer
    subgraph Data_Storage["Data Storage"]
        Data_Dir["Data Directory & JSON Files"]:::data
    end

    %% Evaluation Module Layer
    subgraph Evaluation_Module["Evaluation Module"]
        Eval_Cmd["Evaluation Command"]:::data
        Eval_Report["Evaluation Report File"]:::data
    end

    %% Utilities Layer
    subgraph Utilities["Utilities"]
        Error["Error Handling Module"]:::util
        Scraper_Utils["Scraper Utility Functions"]:::util
    end

    %% Infrastructure & Testing Layer
    subgraph Infrastructure_and_Testing["Infrastructure & Testing"]
        Build["Build & Setup Files"]:::infra
        Test["Test Suite"]:::test
    end

    %% Connections between layers
    CLI_Cmd -->|"triggers"| Scrapers_General
    CLI_Cmd -->|"triggers"| Scrapers_NLP

    Scrapers_General -->|"provides input"| Serialization
    Scrapers_NLP -->|"provides input"| Serialization

    Serialization -->|"ensures consistency"| TaskDB
    TaskDB -->|"stores data to"| Data_Dir

    Data_Dir -->|"feeds data to"| Eval_Cmd
    CLI_Cmd -->|"can also trigger"| Eval_Cmd
    Eval_Cmd -->|"generates"| Eval_Report

    %% Utilities support
    Error -.-> CLI_Cmd
    Error -.-> Scrapers_General
    Error -.-> Scrapers_NLP
    Scraper_Utils -.-> Scrapers_General
    Scraper_Utils -.-> Scrapers_NLP

    %% Styles
    classDef cli fill:#ce5ff,stroke:#004085,stroke-width:2px
    classDef scraper fill:#d4dda,stroke:#155724,stroke-width:2px
    classDef data fill:#ff3cd,stroke:#856404,stroke-width:2px
    classDef util fill:#f8d7a,stroke:#721c24,stroke-width:2px
    classDef infra fill:#e23e5,stroke:#383d41,stroke-width:2px
    classDef test fill:#decf1,stroke:#0c5460,stroke-width:2px

    %% Click Events
    click CLI_Entry "https://github.com/paperswithcode/sota-extractor/blob/master/sota_extractor/__main__.py"
    click CLI_Cmd "https://github.com/paperswithcode/sota-extractor/blob/master/sota_extractor/commands/cli.py"
    click Scrapers_General "https://github.com/paperswithcode/sota-extractor/tree/master/sota_extractor/scrapers"
    click Scrapers_NLP "https://github.com/paperswithcode/sota-extractor/tree/master/sota_extractor/scrapers/nlp_progress"
    click Serialization "https://github.com/paperswithcode/sota-extractor/blob/master/sota_extractor/serialization.py"
    click TaskDB "https://github.com/paperswithcode/sota-extractor/tree/master/sota_extractor/taskdb/v01"
    click Data_Dir "https://github.com/paperswithcode/sota-extractor/tree/master/data"
    click Eval_Cmd "https://github.com/paperswithcode/sota-extractor/blob/master/sota_extractor/commands/evaluate.py"
    click Eval_Report "https://github.com/paperswithcode/sota-extractor/blob/master/data/eval_all_report.csv"
    click Error "https://github.com/paperswithcode/sota-extractor/blob/master/sota_extractor/errors.py"
    click Scraper_Utils "https://github.com/paperswithcode/sota-extractor/blob/master/sota_extractor/scrapers/utils.py"
    click Test "https://github.com/paperswithcode/sota-extractor/tree/master/sota_extractor/tests"
    
```

---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
