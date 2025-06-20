---
created: 2025-06-20 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/google/gin-config
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



# gin-config repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes (<ins>sometimes, entertainment purposes</ins>), personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


----

```mermaid
---
title: "gin-config repo project"
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
  subgraph User_Layer["User Layer"]
  style User_Layer fill:#F5F2,stroke:#333,stroke-width:2px, color: #FFFF
  direction TB
    UserCode["User Code\n@gin.configurable"]:::user
    ConfigFiles[".gin Config Files"]:::user
  end

  %% Core Layer
  subgraph Core_Gin_Package["Core Gin Package"]
  style Core_Gin_Package fill:#F212,stroke:#333,stroke-width:2px, color: #FFFF
  direction TB
    API["gin.parse_config_files_and_bindings()"]:::core
    config["config.py\nRegistry & @configurable"]:::core
    reader["resource_reader.py"]:::core
    parser["config_parser.py"]:::core
    selector["selector_map.py"]:::core
    utils["utils.py"]:::core
  end

  %% Extension Layer
  subgraph Extension_Modules["Extension Modules"]
  style Extension_Modules fill:#B212,stroke:#333,stroke-width:2px, color: #FFFF
  direction TB

      subgraph TensorFlow_Extension["TensorFlow Extension"]
      style TensorFlow_Extension fill:#C2F2,stroke:#333,stroke-width:2px, color: #FFFF
      direction TB
        tfInit["__init__.py"]:::ext
        tfReg["external_configurables.py"]:::ext
        tfUtils["utils.py"]:::ext
      end
      
      subgraph PyTorch_Extension["PyTorch Extension"]
      style PyTorch_Extension fill:#AFB2,stroke:#333,stroke-width:2px, color: #FFFF
      direction TB
        torchInit["__init__.py"]:::ext
        torchReg["external_configurables.py"]:::ext
    end
  end

    subgraph External_Systems["External Systems"]
    style External_Systems fill:#F2B2,stroke:#333,stroke-width:2px, color: #FFFF
    direction TB
        PythonRuntime["Python Runtime"]:::external
        TensorFlow["TensorFlow"]:::external
        PyTorch["PyTorch"]:::external
    end

  subgraph Tests_and_CI["Tests & CI"]
  style Tests_and_CI fill:#F222,stroke:#333,stroke-width:2px, color: #FFFF
  direction TB

    subgraph Core_Tests["Core Tests"]
    style Core_Tests fill:#22BB,stroke:#333,stroke-width:2px, color: #FFFF
      parserTest["config_parser_test.py"]:::test
      configTest["config_test.py"]:::test
      readerTest["resource_reader_test.py"]:::test
      selectorTest["selector_map_test.py"]:::test
    end
    
    subgraph TF_Tests["TF Tests"]
    style TF_Tests fill:#2BF2,stroke:#333,stroke-width:2px, color: #FFFF
      tfConfigTest["tf/config_test.py"]:::test
      tfRegTest["tf/external_configurables_test.py"]:::test
      tfUtilsTest["tf/utils_test.py"]:::test
    end
    
    subgraph Torch_Tests["Torch Tests"]
    style Torch_Tests fill:#BFF2,stroke:#333,stroke-width:2px, color: #FFFF
      torchTest["torch/external_configurables_test.py"]:::test
    end

    testdata["gin/testdata"]:::test
    runTests["run_tests.sh"]:::script
    pipPkg["pip_pkg.sh"]:::script
  end

  %% Main Flow
  UserCode -->|calls parse| API
  ConfigFiles --> reader --> parser --> selector --> config
  API --> reader
  API --> parser
  API --> selector
  API --> config

  %% Runtime Injection
  UserCode -->|decorated call| config
  config -->|invokes| UserCode

  %% Extensions Registration
  tfReg --> config
  torchReg --> config

  %% External Plugins
  tfReg -->|wrap TF classes| TensorFlow
  torchReg -->|wrap Torch classes| PyTorch
  PythonRuntime --> UserCode

  %% Tests & CI Flows (dashed)
  parserTest -.-> parser
  configTest -.-> config
  readerTest -.-> reader
  selectorTest -.-> selector
  tfConfigTest -.-> tfReg
  tfRegTest -.-> tfReg
  tfUtilsTest -.-> tfUtils
  torchTest -.-> torchReg
  runTests -.-> parserTest
  runTests -.-> configTest
  runTests -.-> readerTest
  runTests -.-> selectorTest
  runTests -.-> tfConfigTest
  runTests -.-> tfRegTest
  runTests -.-> tfUtilsTest
  runTests -.-> torchTest
  pipPkg -.-> runTests

  %% Click Events
  click config "https://github.com/google/gin-config/blob/master/gin/config.py"
  click parser "https://github.com/google/gin-config/blob/master/gin/config_parser.py"
  click reader "https://github.com/google/gin-config/blob/master/gin/resource_reader.py"
  click selector "https://github.com/google/gin-config/blob/master/gin/selector_map.py"
  click utils "https://github.com/google/gin-config/blob/master/gin/utils.py"
  click tfInit "https://github.com/google/gin-config/blob/master/gin/tf/__init__.py"
  click tfReg "https://github.com/google/gin-config/blob/master/gin/tf/external_configurables.py"
  click tfUtils "https://github.com/google/gin-config/blob/master/gin/tf/utils.py"
  click torchInit "https://github.com/google/gin-config/blob/master/gin/torch/__init__.py"
  click torchReg "https://github.com/google/gin-config/blob/master/gin/torch/external_configurables.py"
  click parserTest "https://github.com/google/gin-config/blob/master/tests/config_parser_test.py"
  click configTest "https://github.com/google/gin-config/blob/master/tests/config_test.py"
  click readerTest "https://github.com/google/gin-config/blob/master/tests/resource_reader_test.py"
  click selectorTest "https://github.com/google/gin-config/blob/master/tests/selector_map_test.py"
  click tfConfigTest "https://github.com/google/gin-config/blob/master/tests/tf/config_test.py"
  click tfRegTest "https://github.com/google/gin-config/blob/master/tests/tf/external_configurables_test.py"
  click tfUtilsTest "https://github.com/google/gin-config/blob/master/tests/tf/utils_test.py"
  click torchTest "https://github.com/google/gin-config/blob/master/tests/torch/external_configurables_test.py"
  click testdata "https://github.com/google/gin-config/tree/master/gin/testdata"
  click runTests "https://github.com/google/gin-config/blob/master/run_tests.sh"
  click pipPkg "https://github.com/google/gin-config/blob/master/pip_pkg.sh"

  %% Styles
  classDef core fill:#D1FF,stroke:#333,stroke-width:1px
  classDef ext fill:#D28D,stroke:#333,stroke-width:1px
  classDef user fill:#F2B2,stroke:#333,stroke-width:1px
  classDef external fill:#DDD2,stroke:#333,stroke-width:1px
  classDef test fill:#F112,stroke:#333,stroke-width:1px
  classDef script fill:#E4C4,stroke:#333,stroke-width:1px

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