---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/execution-spec-tests
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExenVjbHBkZjg0Zm5kZmFuMGM1NW5qYTBpNndpM2d3cDZqbnEwaThvNSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/doXBzUFJRxpaUbuaqz/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# execution-spec-tests repo project
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
title: "execution-spec-tests repo project"
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
    %% CLI & Entry Points
    subgraph "CLI & Entry Points"
        CLI["CLI & Entry Points"]:::internal
    end
    click CLI "https://github.com/ethereum/execution-spec-tests/tree/main/src/cli"

    %% Configuration & CI
    subgraph "Configuration & CI"
        ConfigModules["Configuration Modules"]:::config
        GitHubConfigs["GitHub & CI Configs"]:::config
        GitHubActions["GitHub Actions Workflows"]:::config
    end
    click ConfigModules "https://github.com/ethereum/execution-spec-tests/tree/main/src/config"
    click GitHubConfigs "https://github.com/ethereum/execution-spec-tests/tree/main/.github/configs"
    click GitHubActions "https://github.com/ethereum/execution-spec-tests/tree/main/.github/actions"

    %% Core Engine Modules
    subgraph "Core Engine Modules"
        BaseTypes["Base Types"]:::internal
        Exceptions["Exceptions"]:::internal
        ExecEngine["Execution Engine"]:::internal
        FixtureGen["Fixture Generation"]:::internal
        Forks["Fork Definitions"]:::internal
        RPC["RPC Interfaces"]:::internal
        Specs["Test Specs"]:::internal
        Tools["Tools & Templates"]:::internal
        Types["Data Types"]:::internal
        VM["VM Utilities"]:::internal
    end
    click BaseTypes "https://github.com/ethereum/execution-spec-tests/tree/main/src/ethereum_test_base_types"
    click Exceptions "https://github.com/ethereum/execution-spec-tests/tree/main/src/ethereum_test_exceptions"
    click ExecEngine "https://github.com/ethereum/execution-spec-tests/tree/main/src/ethereum_test_execution"
    click FixtureGen "https://github.com/ethereum/execution-spec-tests/tree/main/src/ethereum_test_fixtures"
    click Forks "https://github.com/ethereum/execution-spec-tests/tree/main/src/ethereum_test_forks"
    click RPC "https://github.com/ethereum/execution-spec-tests/tree/main/src/ethereum_test_rpc"
    click Specs "https://github.com/ethereum/execution-spec-tests/tree/main/src/ethereum_test_specs"
    click Tools "https://github.com/ethereum/execution-spec-tests/tree/main/src/ethereum_test_tools"
    click Types "https://github.com/ethereum/execution-spec-tests/tree/main/src/ethereum_test_types"
    click VM "https://github.com/ethereum/execution-spec-tests/tree/main/src/ethereum_test_vm"

    %% Pytest Plugins
    subgraph "Pytest Plugins"
        Plugins["Pytest Plugins"]:::internal
    end
    click Plugins "https://github.com/ethereum/execution-spec-tests/tree/main/src/pytest_plugins"


    subgraph External_T8n_Adapters["External T8n Adapters"]
        Adapters["External T8n Adapters"]:::internal
    end
    click Adapters "https://github.com/ethereum/execution-spec-tests/tree/main/src/ethereum_clis"

    %% External Tools
    subgraph "External T8n Tools"
        extEvmt8n[(evm t8n)]:::external
        extEvmone[(evmone-t8n)]:::external
        extSpecEvm[(ethereum-spec-evm)]:::external
        extSolc[(solc)]:::external
    end

    %% Fixtures Output
    Fixtures["Fixtures Output (JSON)"]:::artifact
    click Fixtures "https://github.com/ethereum/execution-spec-tests/tree/main/fixtures/"

    %% Output Consumers
    subgraph "Output Consumers"
        Hive["Hive Framework"]:::external
        Clients["Client Test Harness"]:::external
    end

    %% Data Flows
    CLI -->|"loads config"| ConfigModules
    CLI -->|"invoke core"| ExecEngine
    Plugins -->|"hook into pytest"| ExecEngine
    ExecEngine -->|"generate fixtures"| FixtureGen
    ExecEngine -->|"invoke adapters"| Adapters
    Adapters -->|"invoke"| extEvmt8n
    Adapters -->|"invoke"| extEvmone
    Adapters -->|"invoke"| extSpecEvm
    Adapters -->|"invoke"| extSolc
    extEvmt8n -->|"results"| ExecEngine
    extEvmone -->|"results"| ExecEngine
    extSpecEvm -->|"results"| ExecEngine
    extSolc -->|"results"| ExecEngine
    FixtureGen -->|"write JSON"| Fixtures
    Fixtures -->|"consume"| Hive
    Fixtures -->|"consume"| Clients
    GitHubActions -->|"runs workflows on"| CLI

    %% Styling
    classDef internal fill:#ADD8E6,stroke:#333,stroke-width:1px
    classDef external fill:#FFA500,stroke:#333,stroke-width:1px
    classDef config fill:#90EE90,stroke:#333,stroke-width:1px
    classDef artifact fill:#D3D3D3,stroke:#333,stroke-width:1px

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
