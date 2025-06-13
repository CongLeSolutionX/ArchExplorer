---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/cyclotruc/gitingest
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExZmdoYWhxb3c2NmR6OGZoMzN5NWxqNjJmbmVxd3U0NDFobjc4ZHdvNyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/xUA7bjPYcgAvwq5CKc/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# gitingest repo project
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
title: "gitingest repo project"
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
    %% Clients
    subgraph "Clients"
        U_CLI["CLI Client"]:::client
        U_Browser["Browser UI"]:::client
    end

    %% Compute Layer
    subgraph "Compute"
        subgraph "CLI App"
            entry["entrypoint.py"]:::compute
            cli_file["cli.py"]:::compute
            config_cli["config.py"]:::compute
        end

        subgraph "Web Server (FastAPI)"
            main["main.py"]:::compute
            server_config["server_config.py"]:::compute
            server_utils["server_utils.py"]:::compute

            subgraph "Routers"
                r_index["index.py"]:::compute
                r_download["download.py"]:::compute
                r_dynamic["dynamic.py"]:::compute
            end

            subgraph "Templates"
                t_base["base.jinja"]:::compute
                t_index["index.jinja"]:::compute
                t_git["git.jinja"]:::compute
                t_api["api.jinja"]:::compute
                t_navbar["navbar.jinja"]:::compute
                t_git_form["git_form.jinja"]:::compute
                t_result["result.jinja"]:::compute
                t_footer["footer.jinja"]:::compute
            end

            subgraph "Static Assets"
                s_js["utils.js"]:::compute
                s_robots["robots.txt"]:::compute
            end
        end

        subgraph "Ingestion Library"
            clone["cloning.py"]:::compute
            parse["query_parsing.py"]:::compute
            ingest["ingestion.py"]:::compute
            fmt["output_formatters.py"]:::compute
            schema_ing["schemas/ingestion_schema.py"]:::compute
            util_ing["utils/ingestion_utils.py"]:::compute
            util_git["utils/git_utils.py"]:::compute
            util_qpu["utils/query_parser_utils.py"]:::compute
            schema_fs["schemas/filesystem_schema.py"]:::compute
            util_file["utils/file_utils.py"]:::compute
            util_path["utils/path_utils.py"]:::compute
            util_timeout["utils/timeout_wrapper.py"]:::compute
            util_exc["utils/exceptions.py"]:::compute
        end
    end

    %% Storage & Metadata
    subgraph "Storage & Metadata"
        storage["Cloud Storage (S3)"]:::storage
        metadata["Metadata Store"]:::storage
        cdn["CDN"]:::storage
    end

    %% External Services
    subgraph "External Services"
        git_hosts["Git Remote Hosts"]:::external
        posthog["PostHog Analytics"]:::external
    end

    %% Data Flows
    U_CLI -->|"invoke ingest"| entry
    entry -->|"call ingestion"| ingest
    U_Browser -->|"HTTP request"| main
    main -->|"call ingestion"| ingest
    ingest -->|"clone"| clone
    clone -->|"pull/clone"| git_hosts
    ingest -->|"parse & format"| fmt
    fmt -->|"render HTML"| storage
    storage -->|"store URL"| metadata
    storage -->|"serve content"| cdn
    cdn -->|"deliver HTML"| U_CLI
    cdn -->|"deliver HTML"| U_Browser
    metadata -->|"return link"| entry
    metadata -->|"return link"| main
    main -->|"serve HTML page"| U_Browser
    main -->|"analytics event"| posthog

    %% Click Events
    click entry "https://github.com/cyclotruc/gitingest/blob/main/src/gitingest/entrypoint.py"
    click cli_file "https://github.com/cyclotruc/gitingest/blob/main/src/gitingest/cli.py"
    click config_cli "https://github.com/cyclotruc/gitingest/blob/main/src/gitingest/config.py"
    click clone "https://github.com/cyclotruc/gitingest/blob/main/src/gitingest/cloning.py"
    click parse "https://github.com/cyclotruc/gitingest/blob/main/src/gitingest/query_parsing.py"
    click ingest "https://github.com/cyclotruc/gitingest/blob/main/src/gitingest/ingestion.py"
    click fmt "https://github.com/cyclotruc/gitingest/blob/main/src/gitingest/output_formatters.py"
    click schema_ing "https://github.com/cyclotruc/gitingest/blob/main/src/gitingest/schemas/ingestion_schema.py"
    click util_ing "https://github.com/cyclotruc/gitingest/blob/main/src/gitingest/utils/ingestion_utils.py"
    click util_git "https://github.com/cyclotruc/gitingest/blob/main/src/gitingest/utils/git_utils.py"
    click util_qpu "https://github.com/cyclotruc/gitingest/blob/main/src/gitingest/utils/query_parser_utils.py"
    click schema_fs "https://github.com/cyclotruc/gitingest/blob/main/src/gitingest/schemas/filesystem_schema.py"
    click util_file "https://github.com/cyclotruc/gitingest/blob/main/src/gitingest/utils/file_utils.py"
    click util_path "https://github.com/cyclotruc/gitingest/blob/main/src/gitingest/utils/path_utils.py"
    click util_timeout "https://github.com/cyclotruc/gitingest/blob/main/src/gitingest/utils/timeout_wrapper.py"
    click util_exc "https://github.com/cyclotruc/gitingest/blob/main/src/gitingest/utils/exceptions.py"
    click main "https://github.com/cyclotruc/gitingest/blob/main/src/server/main.py"
    click server_config "https://github.com/cyclotruc/gitingest/blob/main/src/server/server_config.py"
    click server_utils "https://github.com/cyclotruc/gitingest/blob/main/src/server/server_utils.py"
    click r_index "https://github.com/cyclotruc/gitingest/blob/main/src/server/routers/index.py"
    click r_download "https://github.com/cyclotruc/gitingest/blob/main/src/server/routers/download.py"
    click r_dynamic "https://github.com/cyclotruc/gitingest/blob/main/src/server/routers/dynamic.py"
    click t_base "https://github.com/cyclotruc/gitingest/blob/main/src/server/templates/base.jinja"
    click t_index "https://github.com/cyclotruc/gitingest/blob/main/src/server/templates/index.jinja"
    click t_git "https://github.com/cyclotruc/gitingest/blob/main/src/server/templates/git.jinja"
    click t_api "https://github.com/cyclotruc/gitingest/blob/main/src/server/templates/api.jinja"
    click t_navbar "https://github.com/cyclotruc/gitingest/blob/main/src/server/templates/components/navbar.jinja"
    click t_git_form "https://github.com/cyclotruc/gitingest/blob/main/src/server/templates/components/git_form.jinja"
    click t_result "https://github.com/cyclotruc/gitingest/blob/main/src/server/templates/components/result.jinja"
    click t_footer "https://github.com/cyclotruc/gitingest/blob/main/src/server/templates/components/footer.jinja"
    click s_js "https://github.com/cyclotruc/gitingest/blob/main/src/static/js/utils.js"
    click s_robots "https://github.com/cyclotruc/gitingest/blob/main/src/static/robots.txt"

    %% Styles
    classDef compute fill:#ADD8E6,stroke:#333,stroke-width:1px
    classDef storage fill:#90EE90,stroke:#333,stroke-width:1px
    classDef external fill:#FFA500,stroke:#333,stroke-width:1px
    classDef client fill:#D3D3D3,stroke:#333,stroke-width:1px

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
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

  Closing_quote ~~~ My_Meme
  My_Meme animatingEdge@--> Link_to_my_profile
  
  animatingEdge@{ animate: true }

```

---
> **Licenses:**
>
> - **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
> - **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).
> 
---
