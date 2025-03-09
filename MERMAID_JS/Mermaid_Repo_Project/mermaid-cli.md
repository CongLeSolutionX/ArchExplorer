---
created: 2025-03-08 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# mermaid-cli
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
title: "MERMAID-JS - mermaid-cli"
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
    "flowchart": { "htmlLabels": true, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#ffff',
      'primaryTextColor': '#55ff',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
flowchart TD

    %% User Interaction
    UI["User Commands/API Calls"]:::user

    %% CLI Layer
    subgraph CLI_Layer["CLI Layer"]
    style CLI_Layer fill:#c222,stroke:#333,stroke-width:2px
        subgraph CLI_Components["CLI Components"]
            CLI_cli["CLI Interface Component"]:::cliComp
            CLI_index["CLI Interface Component"]:::cliComp
            CLI_version["CLI Interface Component"]:::cliComp
        end
    end

    %% Core Processing Layer
    subgraph Core_Processing["Core Processing"]
    style Core_Processing fill:#c222,stroke:#333,stroke-width:2px
        Config["Configuration Manager"]:::core
        RE["Rendering Engine"]:::core
        FileIO["File I/O Module"]:::core
    end

    %% External Libraries used by Rendering Engine
    subgraph External_Libraries["External Libraries"]
    style External_Libraries fill:#c222,stroke:#333,stroke-width:2px
        Puppeteer["Puppeteer & Mermaid Libraries"]:::external
    end

    %% Testing & CI Pipeline
    subgraph Testing_and_CI_Pipeline["Testing & CI Pipeline"]
    style Testing_and_CI_Pipeline fill:#c222,stroke:#333,stroke-width:2px
        CI["Testing/CI Pipeline"]:::ci
        subgraph CI_Components["CI Components"]
            CI_wf["Workflows (.github/workflows)"]:::ci
            CI_test["Test Runner (run-tests.sh)"]:::ci
            CI_src["Test Scripts (src-test/test.js)"]:::ci
        end
    end

    %% Deployment & Packaging
    subgraph Deployment_and_Packaging["Deployment & Packaging"]
    style Deployment_and_Packaging fill:#c222,stroke:#333,stroke-width:2px
        Deploy["Deployment Module"]:::deploy
        subgraph Deployment_Components["Deployment Components"]
            Dep_Dockerfile["Dockerfile"]:::deploy
            Dep_DockerfileBuild["DockerfileBuild"]:::deploy
            Dep_install["install-dependencies.sh"]:::deploy
            Dep_package["package.json"]:::deploy
            Dep_scriptsVer["scripts/version.js"]:::deploy
        end
    end

    %% Alternative API Usage
    subgraph Alternative_API["Alternative API"]
    style Alternative_API fill:#c222,stroke:#333,stroke-width:2px
        API["Node.js API Entry Point"]:::api
    end

    %% Configuration Files within Configuration Manager
    subgraph Configuration_Files["Configuration Files"]
    style Configuration_Files fill:#c222,stroke:#333,stroke-width:2px
        Config1["puppeteer-config.json"]:::configFile
        Config2["test-negative/config.json"]:::configFile
        Config3["test-negative/puppeteerTimeoutConfig.json"]:::configFile
        Config4["test-positive/config.json"]:::configFile
        Config5["config-deterministic.json"]:::configFile
        Config6["config-noUseMaxWidth.json"]:::configFile
    end

    %% Connections
    UI -->|"Initiate command/API call"| CLI_cli
    UI -->|"Direct API call"| API

    CLI_cli -->|"Parse options"| Config
    CLI_cli -->|"Read input files"| FileIO
    CLI_cli -->|"Invoke rendering"| RE

    Config -->|"Provide settings"| RE
    FileIO -->|"Supply diagram data"| RE
    RE -->|"Generate image outputs"| FileIO

    RE -->|"Utilizes"| Puppeteer

    %% CI Interaction (Testing touches core modules)
    CI -->|"Tests CLI & Core Processing"| CLI_cli
    CI -->|"Tests Rendering and Config"| RE
    CI -->|"Validates File I/O"| FileIO

    %% Deployment is triggered after CI completes
    CI -->|"Deploy build"| Deploy

    %% API entry point also leverages CLI processing
    API -->|"Uses CLI modules for processing"| CLI_index

    %% Click Events for CLI Components
    click CLI_cli "https://github.com/mermaid-js/mermaid-cli/blob/master/src/cli.js"
    click CLI_index "https://github.com/mermaid-js/mermaid-cli/blob/master/src/index.js"
    click CLI_version "https://github.com/mermaid-js/mermaid-cli/blob/master/src/version.js"

    %% Click Event for Rendering Engine configuration
    click Config1 "https://github.com/mermaid-js/mermaid-cli/blob/master/puppeteer-config.json"

    %% Click Events for Configuration Management Files
    click Config2 "https://github.com/mermaid-js/mermaid-cli/blob/master/test-negative/config.json"
    click Config3 "https://github.com/mermaid-js/mermaid-cli/blob/master/test-negative/puppeteerTimeoutConfig.json"
    click Config4 "https://github.com/mermaid-js/mermaid-cli/blob/master/test-positive/config.json"
    click Config5 "https://github.com/mermaid-js/mermaid-cli/blob/master/config-deterministic.json"
    click Config6 "https://github.com/mermaid-js/mermaid-cli/blob/master/config-noUseMaxWidth.json"

    %% Click Events for Testing/CI Pipeline Components
    click CI_wf "https://github.com/mermaid-js/mermaid-cli/tree/master/.github/workflows"
    click CI_test "https://github.com/mermaid-js/mermaid-cli/blob/master/run-tests.sh"
    click CI_src "https://github.com/mermaid-js/mermaid-cli/blob/master/src-test/test.js"

    %% Click Events for Deployment & Packaging Components
    click Dep_Dockerfile "https://github.com/mermaid-js/mermaid-cli/tree/master/Dockerfile"
    click Dep_DockerfileBuild "https://github.com/mermaid-js/mermaid-cli/tree/master/DockerfileBuild"
    click Dep_install "https://github.com/mermaid-js/mermaid-cli/blob/master/install-dependencies.sh"
    click Dep_package "https://github.com/mermaid-js/mermaid-cli/blob/master/package.json"
    click Dep_scriptsVer "https://github.com/mermaid-js/mermaid-cli/blob/master/scripts/version.js"

    %% Click Event for Alternative API Usage
    click API "https://github.com/mermaid-js/mermaid-cli/blob/master/src/index.js"

    %% Styles
    classDef user fill:#2CF5,stroke:#e76f51,stroke-width:2px
    classDef cliComp fill:#29DF2,stroke:#264653,stroke-width:2px
    classDef core fill:#EA22,stroke:#F4A261,stroke-width:2px
    classDef external fill:#2FF62,stroke:#2A9D8F,stroke-width:2px,color:#ffffff
    classDef ci fill:#E7F3,stroke:#264653,stroke-width:2px
    classDef deploy fill:#F2F2,stroke:#264653,stroke-width:2px,color:#ffffff
    classDef api fill:#A2F2,stroke:#457B9D,stroke-width:2px
    classDef configFile fill:#e2f5,stroke:#219ebc,stroke-width:2px

```





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---