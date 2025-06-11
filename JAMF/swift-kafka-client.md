---
created: 2025-03-23 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---

> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExbGNlamVyMjdlODA2ODM2dGdpMzQ2bjdyeDdkY2h2aWxtOHJncGsyeiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/IzigGVSs9fHjug20Mq/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----



# Swift Kafka Client
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
title: "Swift Kafka Client"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: default
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
    subgraph "Swift API Layer"
        direction TB
        A["KafkaConfiguration"]:::config
        B["Utility Modules"]:::utility
        C["Service Lifecycle Manager"]:::service
        D["KafkaProducer"]:::swift
        E["KafkaConsumer"]:::swift
    end

    subgraph "Integration Layer"
        direction TB
        F["RDKafka Client"]:::integration
        G["Crdkafka"]:::integrationDotted
        H["COpenSSL"]:::integrationDotted
    end

    I["Apache Kafka Broker"]:::external
    J["Docker Compose Environment"]:::docker

    A --> D
    A --> E
    B --> D
    B --> E
    C --> D
    C --> E
    D --> F
    E --> F
    F -->|"sends/receives"| I
    F --> G
    F --> H
    J --> I
    J --> C

    click D "https://github.com/swift-server/swift-kafka-client/blob/main/Sources/Kafka/KafkaProducer.swift"
    click E "https://github.com/swift-server/swift-kafka-client/blob/main/Sources/Kafka/KafkaConsumer.swift"
    click A "https://github.com/swift-server/swift-kafka-client/tree/main/Sources/Kafka/Configuration"
    click B "https://github.com/swift-server/swift-kafka-client/tree/main/Sources/Kafka/Utilities"
    click F "https://github.com/swift-server/swift-kafka-client/tree/main/Sources/Kafka/RDKafka"
    click G "https://github.com/swift-server/swift-kafka-client/tree/main/Sources/Crdkafka"
    click H "https://github.com/swift-server/swift-kafka-client/tree/main/Sources/COpenSSL"
    click J "https://github.com/swift-server/swift-kafka-client/tree/main/docker"

    classDef swift fill:#cce5ff,stroke:#004085,stroke-width:2px;
    classDef config fill:#d4edda,stroke:#155724,stroke-width:2px;
    classDef utility fill:#fff3cd,stroke:#856404,stroke-width:2px;
    classDef service fill:#f8d7da,stroke:#721c24,stroke-width:2px;
    classDef integration fill:#d1ecf1,stroke:#0c5460,stroke-width:2px;
    classDef integrationDotted fill:#e2e3e5,stroke:#6c757d,stroke-width:2px,stroke-dasharray: 5 5;
    classDef external fill:#fefefe,stroke:#818182,stroke-width:2px,stroke-dasharray: 3 3;
    classDef docker fill:#e0f7fa,stroke:#006064,stroke-width:2px

```




---

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
