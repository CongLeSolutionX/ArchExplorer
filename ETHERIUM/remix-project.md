---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/remix-project
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExanZydm52NDcyNWIwMWtneG9uOWk4aGpseXQ1bHR4b3c1N2x3MnB6bSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/m3XqQ8QhuIUuQau7n5/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# remix-project repo project
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
title: "remix-project repo project"
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
    %% CI/CD & Build System
    subgraph "CI/CD & Build System"
        NxCLI["Nx CLI\n(root)"]:::build_ci
        Lerna["Lerna\n(root)"]:::build_ci
        PackageJSON["package.json\n(root)"]:::build_ci
        CircleCI["CircleCI\n(.circleci/config.yml)"]:::build_ci
        GitHubActions["GitHub Actions\n(.github/workflows/)"]:::build_ci
    end

    %% Shared Libraries
    subgraph "Shared Libraries"
        coreEngine["remix-lib\n(libs/remix-lib/)"]:::shared_lib
        pluginAPI["remix-api\n(libs/remix-api/)"]:::shared_lib
        corePlugin["remix-core-plugin\n(libs/remix-core-plugin/)"]:::shared_lib
        uiLib["remix-ui\n(libs/remix-ui/)"]:::shared_lib
        solWrap["remix-solidity\n(libs/remix-solidity/)"]:::shared_lib
        simulator["remix-simulator\n(libs/remix-simulator/)"]:::shared_lib
        debugEngine["remix-debug\n(libs/remix-debug/)"]:::shared_lib
        analyzer["remix-analyzer\n(libs/remix-analyzer/)"]:::shared_lib
        testsLib["remix-tests\n(libs/remix-tests/)"]:::shared_lib
        fileServerLib["remixd\n(libs/remixd/)"]:::shared_lib
    end

    %% Host Applications
    subgraph "Host Applications"
        browserIDE["Browser IDE\n(React, TypeScript)\napps/remix-ide/"]:::host_app
        desktopIDE["Desktop IDE\n(Electron)\napps/remixdesktop/"]:::host_app
        circuit["Circuit Compiler UI\napps/circuit-compiler/"]:::host_app
        contractVerif["Contract Verification UI\napps/contract-verification/"]:::host_app
        debuggerUI["Debugger UI\napps/debugger/"]:::host_app
        docGen["Documentation Generator\napps/doc-gen/"]:::host_app
        docViewer["Documentation Viewer\napps/doc-viewer/"]:::host_app
        quickDapp["Quick DApp UI\napps/quick-dapp/"]:::host_app
        learnEth["Learn-Eth Tutorial\napps/learneth/"]:::host_app
        solhint["Solhint Plugin UI\napps/solhint/"]:::host_app
        solidityCompilerUI["Solidity Compiler UI\napps/solidity-compiler/"]:::host_app
        vyperUI["Vyper Compiler UI\napps/vyper/"]:::host_app
        noirUI["Noir Compiler UI\napps/noir-compiler/"]:::host_app
        universalDapp["Universal DApp\napps/remix-dapp/"]:::host_app
        e2e["E2E Test Runner\napps/remix-ide-e2e/"]:::host_app
    end

    %% CLI Tools & Services
    subgraph "CLI Tools & Services"
        remixdService["remixd File Server\n(libs/remixd/)"]:::service
        remixTestsCLI["remix-tests CLI\n(libs/remix-tests/)"]:::service
        remixDebugCLI["remix-debug CLI\n(libs/remix-debug/bin/)"]:::service
    end

    %% External Services
    subgraph "External Services"
        ethRPC["Ethereum JSON-RPC\n(Infura/Alchemy/Ganache/Hardhat)"]:::external
        ipfs["IPFS/Swarm"]:::external
        gitStorage["GitHub/dGit"]:::external
        inference["Inference Server"]:::external
    end

    %% Build Dependencies
    NxCLI -->|orchestrates builds| coreEngine
    NxCLI -->|orchestrates builds| pluginAPI
    NxCLI -->|orchestrates builds| corePlugin
    NxCLI -->|orchestrates builds| uiLib
    NxCLI -->|orchestrates builds| solWrap
    NxCLI -->|orchestrates builds| simulator
    NxCLI -->|orchestrates builds| debugEngine
    NxCLI -->|orchestrates builds| analyzer
    NxCLI -->|orchestrates builds| testsLib
    NxCLI -->|orchestrates builds| fileServerLib
    CircleCI -->|CI pipelines| NxCLI
    GitHubActions -->|CI pipelines| NxCLI

    %% Runtime Interactions
    browserIDE -->|"Plugin API"| pluginAPI
    browserIDE -->|"Plugin API"| corePlugin
    pluginAPI -->|"loads plugins"| corePlugin
    corePlugin -->|"uses core engine"| coreEngine
    coreEngine -->|"calls compiler"| solWrap
    coreEngine -->|"runs simulation"| simulator
    coreEngine -->|"runs debugger"| debugEngine
    coreEngine -->|"runs analysis"| analyzer
    solWrap -->|"JSON-RPC"| ethRPC
    simulator -->|"JSON-RPC"| ethRPC
    browserIDE -->|"WebSocket"| remixdService
    desktopIDE -->|"Electron IPC"| browserIDE
    desktopIDE -->|"Electron IPC"| remixdService
    e2e -->|"WebDriver"| browserIDE

    %% Click Events
    click NxCLI "https://github.com/ethereum/remix-project/blob/master/nx.json"
    click Lerna "https://github.com/ethereum/remix-project/blob/master/lerna.json"
    click PackageJSON "https://github.com/ethereum/remix-project/blob/master/package.json"
    click CircleCI "https://github.com/ethereum/remix-project/blob/master/.circleci/config.yml"
    click GitHubActions "https://github.com/ethereum/remix-project/tree/master/.github/workflows/"
    click coreEngine "https://github.com/ethereum/remix-project/tree/master/libs/remix-lib/"
    click pluginAPI "https://github.com/ethereum/remix-project/tree/master/libs/remix-api/"
    click corePlugin "https://github.com/ethereum/remix-project/tree/master/libs/remix-core-plugin/"
    click uiLib "https://github.com/ethereum/remix-project/tree/master/libs/remix-ui/"
    click solWrap "https://github.com/ethereum/remix-project/tree/master/libs/remix-solidity/"
    click simulator "https://github.com/ethereum/remix-project/tree/master/libs/remix-simulator/"
    click debugEngine "https://github.com/ethereum/remix-project/tree/master/libs/remix-debug/"
    click analyzer "https://github.com/ethereum/remix-project/tree/master/libs/remix-analyzer/"
    click testsLib "https://github.com/ethereum/remix-project/tree/master/libs/remix-tests/"
    click fileServerLib "https://github.com/ethereum/remix-project/tree/master/libs/remixd/"
    click browserIDE "https://github.com/ethereum/remix-project/tree/master/apps/remix-ide/"
    click desktopIDE "https://github.com/ethereum/remix-project/tree/master/apps/remixdesktop/"
    click circuit "https://github.com/ethereum/remix-project/tree/master/apps/circuit-compiler/"
    click contractVerif "https://github.com/ethereum/remix-project/tree/master/apps/contract-verification/"
    click debuggerUI "https://github.com/ethereum/remix-project/tree/master/apps/debugger/"
    click docGen "https://github.com/ethereum/remix-project/tree/master/apps/doc-gen/"
    click docViewer "https://github.com/ethereum/remix-project/tree/master/apps/doc-viewer/"
    click quickDapp "https://github.com/ethereum/remix-project/tree/master/apps/quick-dapp/"
    click learnEth "https://github.com/ethereum/remix-project/tree/master/apps/learneth/"
    click solhint "https://github.com/ethereum/remix-project/tree/master/apps/solhint/"
    click solidityCompilerUI "https://github.com/ethereum/remix-project/tree/master/apps/solidity-compiler/"
    click vyperUI "https://github.com/ethereum/remix-project/tree/master/apps/vyper/"
    click noirUI "https://github.com/ethereum/remix-project/tree/master/apps/noir-compiler/"
    click universalDapp "https://github.com/ethereum/remix-project/tree/master/apps/remix-dapp/"
    click e2e "https://github.com/ethereum/remix-project/tree/master/apps/remix-ide-e2e/"
    click remixdService "https://github.com/ethereum/remix-project/tree/master/libs/remixd/"
    click remixTestsCLI "https://github.com/ethereum/remix-project/tree/master/libs/remix-tests/"
    click remixDebugCLI "https://github.com/ethereum/remix-project/tree/master/libs/remix-debug/bin/"

    %% Styles
    classDef build_ci fill:#fde4c2,stroke:#f29e4c
    classDef shared_lib fill:#d2e5fd,stroke:#4a90e2
    classDef host_app fill:#d8f3d8,stroke:#6bbf6b
    classDef service fill:#fff4c2,stroke:#f2d94c
    classDef external fill:#eeeeee,stroke:#999999
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