---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/OpenBB-finance/backends-for-openbb
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExMXVjejV3dnVjc2o5MXd3eXBvcDR1cHlzbHQ1Z2R6YjY0ZHpmdjJ6OCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/hL9q5k9dk9l0wGd4e0/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# backends-for-openbb repo project
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
title: "backends-for-openbb repo project"
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
flowchart TB
    %% Frontend
    UI["OpenBB Workspace UI"]:::frontend

    %% Integration Services
    subgraph "Integration Services"
        direction TB
        demo_risk["demo-risk"]:::service
        dtcc_trade_repository["dtcc_trade_repository"]:::service
        hello_world["hello-world"]:::service
        reference_backend["reference-backend"]:::service

        subgraph "Database Connectors"
            direction TB
            arcticdb["ArcticDB Connector"]:::service
            clickhouse["ClickHouse Connector"]:::service
            elasticsearch["Elasticsearch Connector"]:::service
            mindsdb["MindsDB Connector"]:::service
            snowflake["Snowflake Connector"]:::service
            supabase["Supabase Connector"]:::service
        end

        subgraph "Parameter Types"
            direction TB
            column_and_cell["Column & Cell Rendering"]:::service
            form_parameter["Form Parameter"]:::service
            grouping_widgets["Grouping Widgets"]:::service
            parameters_example["Parameters Example"]:::service
        end

        subgraph "Widget Types"
            direction TB
            advanced_charting["Advanced Charting"]:::service
            chart_widget["Chart Widget"]:::service
            live_grid_widget["Live Grid Widget"]:::service
            markdown_widget["Markdown Widget"]:::service
            metric_widget["Metric Widget"]:::service
            multi_file_viewer["Multi File Viewer"]:::service
            news_widget["News Widget"]:::service
            pdf_widget["PDF Widget"]:::service
            table_widget["Table Widget"]:::service
        end

        prompt_widget["Prompt Widget"]:::service
    end

    %% Data Sources
    subgraph "Data Sources"
        direction TB
        flat_files["Flat Files"]:::files
        external_dbs["External Databases"]:::db
    end

    %% Flows
    UI -->|"GET /widgets.json"| demo_risk
    UI -->|"GET /widgets.json"| dtcc_trade_repository
    UI -->|"GET /widgets.json"| hello_world
    UI -->|"GET /widgets.json"| reference_backend
    UI -->|"GET /widgets.json"| arcticdb
    UI -->|"GET /widgets.json"| clickhouse
    UI -->|"GET /widgets.json"| elasticsearch
    UI -->|"GET /widgets.json"| mindsdb
    UI -->|"GET /widgets.json"| snowflake
    UI -->|"GET /widgets.json"| supabase
    UI -->|"GET /widgets.json"| column_and_cell
    UI -->|"GET /widgets.json"| form_parameter
    UI -->|"GET /widgets.json"| grouping_widgets
    UI -->|"GET /widgets.json"| parameters_example
    UI -->|"GET /widgets.json"| advanced_charting
    UI -->|"GET /widgets.json"| chart_widget
    UI -->|"GET /widgets.json"| live_grid_widget
    UI -->|"GET /widgets.json"| markdown_widget
    UI -->|"GET /widgets.json"| metric_widget
    UI -->|"GET /widgets.json"| multi_file_viewer
    UI -->|"GET /widgets.json"| news_widget
    UI -->|"GET /widgets.json"| pdf_widget
    UI -->|"GET /widgets.json"| table_widget
    UI -->|"GET /widgets.json"| prompt_widget

    demo_risk -->|reads portfolios.xz| flat_files
    dtcc_trade_repository -->|reads swaps_data.xz| flat_files
    dtcc_trade_repository -->|uses store.py| flat_files
    hello_world -->|no data source| flat_files
    reference_backend -->|uses sample.pdf| flat_files

    snowflake -->|connects via connector| external_dbs
    clickhouse -->|connects via clickhouse-driver| external_dbs
    elasticsearch -->|connects via elasticsearch-py| external_dbs
    supabase -->|connects via supabase-py| external_dbs
    mindsdb -->|connects via mindsdb| external_dbs
    arcticdb -->|connects via arcticdb-python| external_dbs

    %% Click Events
    click demo_risk "https://github.com/openbb-finance/backends-for-openbb/blob/main/demo-apps/demo-risk/demo_risk/app.py"
    click dtcc_trade_repository "https://github.com/openbb-finance/backends-for-openbb/blob/main/demo-apps/dtcc_trade_repository/openbb_swaps/main.py"
    click hello_world "https://github.com/openbb-finance/backends-for-openbb/blob/main/getting-started/hello-world/main.py"
    click reference_backend "https://github.com/openbb-finance/backends-for-openbb/blob/main/getting-started/reference-backend/main.py"
    click arcticdb "https://github.com/openbb-finance/backends-for-openbb/blob/main/widget-examples/database-connectors/arcticdb_python/main.py"
    click clickhouse "https://github.com/openbb-finance/backends-for-openbb/blob/main/widget-examples/database-connectors/clickhouse_python/main.py"
    click elasticsearch "https://github.com/openbb-finance/backends-for-openbb/blob/main/widget-examples/database-connectors/elasticsearch_python/main.py"
    click mindsdb "https://github.com/openbb-finance/backends-for-openbb/blob/main/widget-examples/database-connectors/mindsdb_python/main.py"
    click snowflake "https://github.com/openbb-finance/backends-for-openbb/blob/main/widget-examples/database-connectors/snowflake_connector_python/main.py"
    click supabase "https://github.com/openbb-finance/backends-for-openbb/blob/main/widget-examples/database-connectors/supabase_python/main.py"
    click column_and_cell "https://github.com/openbb-finance/backends-for-openbb/blob/main/widget-examples/parameters-types/column_and_cell_rendering/main.py"
    click form_parameter "https://github.com/openbb-finance/backends-for-openbb/blob/main/widget-examples/parameters-types/form_parameter/main.py"
    click grouping_widgets "https://github.com/openbb-finance/backends-for-openbb/blob/main/widget-examples/parameters-types/grouping_widgets/main.py"
    click parameters_example "https://github.com/openbb-finance/backends-for-openbb/blob/main/widget-examples/parameters-types/parameters_example/main.py"
    click advanced_charting "https://github.com/openbb-finance/backends-for-openbb/blob/main/widget-examples/widget-types/advanced_charting/main.py"
    click chart_widget "https://github.com/openbb-finance/backends-for-openbb/blob/main/widget-examples/widget-types/chart_widget/main.py"
    click live_grid_widget "https://github.com/openbb-finance/backends-for-openbb/blob/main/widget-examples/widget-types/live_grid_widget/main.py"
    click markdown_widget "https://github.com/openbb-finance/backends-for-openbb/blob/main/widget-examples/widget-types/markdown_widget/main.py"
    click metric_widget "https://github.com/openbb-finance/backends-for-openbb/blob/main/widget-examples/widget-types/metric_widget/main.py"
    click multi_file_viewer "https://github.com/openbb-finance/backends-for-openbb/blob/main/widget-examples/widget-types/multi_file_viewer/main.py"
    click news_widget "https://github.com/openbb-finance/backends-for-openbb/blob/main/widget-examples/widget-types/news_widget/main.py"
    click pdf_widget "https://github.com/openbb-finance/backends-for-openbb/blob/main/widget-examples/widget-types/pdf_widget/main.py"
    click table_widget "https://github.com/openbb-finance/backends-for-openbb/blob/main/widget-examples/widget-types/table_widget/main.py"
    click prompt_widget "https://github.com/openbb-finance/backends-for-openbb/blob/main/widget_examples/prompt_widget/main.py"

    %% Styles
    classDef frontend fill:#8FBFE0,stroke:#333,stroke-width:1px
    classDef service fill:#A2D39C,stroke:#333,stroke-width:1px
    classDef files fill:#F7DC6F,stroke:#333,stroke-width:1px
    classDef db fill:#D7BDE2,stroke:#333,stroke-width:1px
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