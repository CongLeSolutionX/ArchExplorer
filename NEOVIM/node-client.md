---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/neovim/node-client
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


# node-client repo project
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
title: "node-client repo project"
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
    %% External System
    NeovimBinary["Neovim Binary"]:::external

    %% Core Engine Layers
    subgraph "Transport Layer"
        TransportLayer["TransportLayer"]:::core
    end

    subgraph "API Client"
        BaseAPI["Base.ts"]:::core
        NeovimAPI["Neovim.ts"]:::core
        BufferAPI["Buffer.ts"]:::core
        WindowAPI["Window.ts"]:::core
        TabpageAPI["Tabpage.ts"]:::core
    end

    subgraph "Host & Plugin Loader"
        NvimPluginHost["NvimPlugin.ts"]:::core
        HostFactory["factory.ts"]:::core
        HostIndex["index.ts"]:::core
    end

    subgraph "Plugin API"
        PluginCore["plugin.ts"]:::interface
        CommandDecor["command.ts"]:::interface
        AutoCmd["autocmd.ts"]:::interface
        FuncDecor["function.ts"]:::interface
        PropsDecor["properties.ts"]:::interface
    end

    subgraph "CLI & Scripts"
        CLI["bin/cli.js"]:::core
        ScriptNvim["scripts/nvim.js"]:::core
        ScriptAPI["scripts/api.js"]:::core
        ScriptFind["scripts/findMissingApi.js"]:::core
    end

    subgraph "User Plugins & Examples"
        ExamplePluginPkg["packages/example-plugin"]:::user
        ExamplePluginNode["rplugin/node/test/index.js"]:::user
        ExampleFixture["rplugin/node/test/fixture.js"]:::user
        ExampleDecorators["packages/example-plugin-decorators"]:::user
        ExampleDecoratorsIndex["src/index.js"]:::user
        ExampleScript["examples/rplugin/node/nvim-example/index.js"]:::user
    end

    subgraph "Decorators Helper Library"
        DecoratorsCore["packages/decorators/src/index.ts"]:::user
        DecorCmd["packages/decorators/src/plugin/command.ts"]:::user
        DecorAuto["packages/decorators/src/plugin/autocmd.ts"]:::user
        DecorFunc["packages/decorators/src/plugin/function.ts"]:::user
        DecorPlugin["packages/decorators/src/plugin/plugin.ts"]:::user
        DecorProps["packages/decorators/src/plugin/properties.ts"]:::user
    end

    subgraph "Integration Tests"
        IntegrationIndex["src/index.ts"]:::user
        IntegrationTest["__tests__/integration.test.ts"]:::user
        FactoryTest["src/factory.test.ts"]:::user
        IntegrationPkg["package.json"]:::user
    end

    %% Data Flows
    CLI -->|"attach() call"| TransportLayer
    ScriptNvim -->|"attach() call"| TransportLayer
    TransportLayer -->|"Msgpack-RPC"| NeovimBinary
    TransportLayer <-->|"Msgpack-RPC"| BaseAPI
    BaseAPI --> NeovimAPI
    BaseAPI --> BufferAPI
    BaseAPI --> WindowAPI
    BaseAPI --> TabpageAPI
    BaseAPI --> NvimPluginHost
    NvimPluginHost --> PluginCore
    NvimPluginHost --> HostFactory
    PluginCore --> CommandDecor
    PluginCore --> AutoCmd
    PluginCore --> FuncDecor
    PluginCore --> PropsDecor
    PluginCore -->|"register*()"| ExamplePluginNode
    TransportLayer -->|"RPC Event"| NvimPluginHost
    ExamplePluginNode -->|"calls API"| BaseAPI
    DecoratorsCore --> DecorCmd
    DecoratorsCore --> DecorAuto
    DecoratorsCore --> DecorFunc
    DecoratorsCore --> DecorPlugin
    DecoratorsCore --> DecorProps
    IntegrationIndex -->|"runs full stack"| NeovimBinary
    IntegrationIndex -->|"runs full stack"| TransportLayer
    IntegrationIndex -->|"runs full stack"| ExamplePluginNode

    %% Click Events
    click TransportLayer "https://github.com/neovim/node-client/blob/master/packages/neovim/src/utils/transport.ts"
    click BaseAPI "https://github.com/neovim/node-client/blob/master/packages/neovim/src/api/Base.ts"
    click NeovimAPI "https://github.com/neovim/node-client/blob/master/packages/neovim/src/api/Neovim.ts"
    click BufferAPI "https://github.com/neovim/node-client/blob/master/packages/neovim/src/api/Buffer.ts"
    click WindowAPI "https://github.com/neovim/node-client/blob/master/packages/neovim/src/api/Window.ts"
    click TabpageAPI "https://github.com/neovim/node-client/blob/master/packages/neovim/src/api/Tabpage.ts"
    click NvimPluginHost "https://github.com/neovim/node-client/blob/master/packages/neovim/src/host/NvimPlugin.ts"
    click HostFactory "https://github.com/neovim/node-client/blob/master/packages/neovim/src/host/factory.ts"
    click HostIndex "https://github.com/neovim/node-client/blob/master/packages/neovim/src/host/index.ts"
    click PluginCore "https://github.com/neovim/node-client/blob/master/packages/neovim/src/plugin/plugin.ts"
    click CommandDecor "https://github.com/neovim/node-client/blob/master/packages/neovim/src/plugin/command.ts"
    click AutoCmd "https://github.com/neovim/node-client/blob/master/packages/neovim/src/plugin/autocmd.ts"
    click FuncDecor "https://github.com/neovim/node-client/blob/master/packages/neovim/src/plugin/function.ts"
    click PropsDecor "https://github.com/neovim/node-client/blob/master/packages/neovim/src/plugin/properties.ts"
    click CLI "https://github.com/neovim/node-client/blob/master/packages/neovim/bin/cli.js"
    click ScriptNvim "https://github.com/neovim/node-client/blob/master/packages/neovim/scripts/nvim.js"
    click ScriptAPI "https://github.com/neovim/node-client/blob/master/packages/neovim/scripts/api.js"
    click ScriptFind "https://github.com/neovim/node-client/blob/master/packages/neovim/scripts/findMissingApi.js"
    click ExamplePluginPkg "https://github.com/neovim/node-client/tree/master/packages/example-plugin"
    click ExamplePluginNode "https://github.com/neovim/node-client/blob/master/packages/example-plugin/rplugin/node/test/index.js"
    click ExampleFixture "https://github.com/neovim/node-client/blob/master/packages/example-plugin/rplugin/node/test/fixture.js"
    click ExampleDecorators "https://github.com/neovim/node-client/blob/master/packages/example-plugin-decorators/src/index.js"
    click ExampleScript "https://github.com/neovim/node-client/blob/master/examples/rplugin/node/nvim-example/index.js"
    click DecoratorsCore "https://github.com/neovim/node-client/blob/master/packages/decorators/src/index.ts"
    click DecorCmd "https://github.com/neovim/node-client/blob/master/packages/decorators/src/plugin/command.ts"
    click DecorAuto "https://github.com/neovim/node-client/blob/master/packages/decorators/src/plugin/autocmd.ts"
    click DecorFunc "https://github.com/neovim/node-client/blob/master/packages/decorators/src/plugin/function.ts"
    click DecorPlugin "https://github.com/neovim/node-client/blob/master/packages/decorators/src/plugin/plugin.ts"
    click DecorProps "https://github.com/neovim/node-client/blob/master/packages/decorators/src/plugin/properties.ts"
    click IntegrationIndex "https://github.com/neovim/node-client/blob/master/packages/integration-tests/src/index.ts"
    click IntegrationTest "https://github.com/neovim/node-client/blob/master/packages/integration-tests/__tests__/integration.test.ts"
    click FactoryTest "https://github.com/neovim/node-client/blob/master/packages/integration-tests/src/factory.test.ts"
    click IntegrationPkg "https://github.com/neovim/node-client/blob/master/packages/integration-tests/package.json"

    %% Styles
    classDef core fill:#D0E6FF stroke:#0044CC
    classDef interface fill:#FFE6CC stroke:#CC6600
    classDef user fill:#E6FFCC stroke:#339900
    classDef external fill:#E0E0E0 stroke:#808080
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