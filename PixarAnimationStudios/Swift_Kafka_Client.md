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
> ![Loading...](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExcGdoNmUzdHU1bm9vbnI4OXdldTFpZmEzZ2t0eHFrdXFieWVrbjdmdCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/U7L2cb7zrq2aQZxFTN/giphy.gif)
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
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
