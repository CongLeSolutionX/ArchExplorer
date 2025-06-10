---
created: 2025-03-28 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExOGpuYThjb2N4aDJ2c2I5MHJxaHU2OGd2dnQ4aWZkb2J6ZzY0ZG9iOSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/XgXeYtdhTHsx6smbOx/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Selenium HQ - Selenium
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
title: "Selenium HQ - Selenium"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: base
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Toggle theme value to `base` to activate the initilization below for the customized theme version.
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    'flowchart': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'lineColor': '#F8B229'
    }
  }
}%%
flowchart TD
    %% Top level project
    Project["Selenium Umbrella Project"]:::project

    %% Core Infrastructure
    subgraph "Core Infrastructure"
        WebDriverCore["WebDriver Core (W3C Protocol)"]:::core
    end

    %% Language Bindings
    subgraph "Language Bindings"
        JavaBinding["Java Binding"]:::lang
        PythonBinding["Python Binding"]:::lang
        RubyBinding["Ruby Binding"]:::lang
        DotNetBinding[".NET Binding"]:::lang
        JSBinding["JavaScript Binding"]:::lang
        RustBinding["Rust Binding"]:::lang
        CppBinding["C++ Binding/Driver Integration"]:::lang
    end

    %% Browser Drivers & Integration
    BrowserDrivers["Browser Drivers (Chrome,Gecko,IE,Safari)"]:::driver

    %% Build & CI/Testing
    subgraph "Build & CI/Testing"
        BazelBuild["Bazel Build System"]:::build
        RakeTasks["Rake Tasks"]:::build
        BuildScripts["Build Scripts"]:::build
        TestInfra["Test Infrastructure (CI/CD&LanguageTests)"]:::test
    end

    %% Documentation & Dev Tools
    subgraph "Documentation & Dev Tools"
        Documentation["Documentation"]:::doc
        DevTools["Dev Tools (DevContainers,Gitpod)"]:::doc
    end

    %% External Dependencies
    ThirdParty["Third Party Dependencies"]:::external

    %% Connections from top level project
    Project -->|"contains"| WebDriverCore
    Project -->|"contains"| JavaBinding
    Project -->|"contains"| PythonBinding
    Project -->|"contains"| RubyBinding
    Project -->|"contains"| DotNetBinding
    Project -->|"contains"| JSBinding
    Project -->|"contains"| RustBinding
    Project -->|"contains"| CppBinding

    Project -->|"builds"| BazelBuild
    Project -->|"automates"| RakeTasks
    Project -->|"executes"| BuildScripts
    Project -->|"triggers"| TestInfra
    Project -->|"hosts"| Documentation
    Project -->|"provides"| DevTools
    Project -->|"includes"| ThirdParty

    %% Language Bindings use core
    JavaBinding -->|"uses"| WebDriverCore
    PythonBinding -->|"uses"| WebDriverCore
    RubyBinding -->|"uses"| WebDriverCore
    DotNetBinding -->|"uses"| WebDriverCore
    JSBinding -->|"uses"| WebDriverCore
    RustBinding -->|"uses"| WebDriverCore
    CppBinding -->|"uses"| WebDriverCore

    %% WebDriver Core communicates with Browser Drivers
    WebDriverCore -->|"communicatesWith"| BrowserDrivers

    %% Build system triggers test infrastructure
    BazelBuild -->|"triggers"| TestInfra
    RakeTasks -->|"triggers"| TestInfra
    BuildScripts -->|"triggers"| TestInfra

    %% Style Classes
    classDef project fill:#f9f,stroke:#333,stroke-width:2px;
    classDef core fill:#ccf,stroke:#333,stroke-width:2px;
    classDef lang fill:#cfc,stroke:#333,stroke-width:2px;
    classDef driver fill:#fc9,stroke:#333,stroke-width:2px;
    classDef build fill:#cff,stroke:#333,stroke-width:2px;
    classDef test fill:#ffc,stroke:#333,stroke-width:2px;
    classDef doc fill:#fcc,stroke:#333,stroke-width:2px;
    classDef external fill:#eee,stroke:#333,stroke-width:2px;

    %% Click Events
    click WebDriverCore "https://github.com/seleniumhq/selenium/tree/trunk/common/"
    click JavaBinding "https://github.com/seleniumhq/selenium/tree/trunk/java/"
    click PythonBinding "https://github.com/seleniumhq/selenium/tree/trunk/py/"
    click RubyBinding "https://github.com/seleniumhq/selenium/tree/trunk/rb/"
    click DotNetBinding "https://github.com/seleniumhq/selenium/tree/trunk/dotnet/"
    click JSBinding "https://github.com/seleniumhq/selenium/tree/trunk/javascript/selenium-webdriver"
    click RustBinding "https://github.com/seleniumhq/selenium/tree/trunk/rust/"
    click CppBinding "https://github.com/seleniumhq/selenium/tree/trunk/cpp/"
    click RakeTasks "https://github.com/seleniumhq/selenium/tree/trunk/rake_tasks/"
    click BuildScripts "https://github.com/seleniumhq/selenium/tree/trunk/scripts/"
    click TestInfra "https://github.com/seleniumhq/selenium/tree/trunk/.github/workflows/"
    click Documentation "https://github.com/seleniumhq/selenium/tree/trunk/py/docs/"
    click DevTools "https://github.com/seleniumhq/selenium/tree/trunk/.devcontainer/"
    click ThirdParty "https://github.com/seleniumhq/selenium/tree/trunk/third_party/"
    
```


---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
