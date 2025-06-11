---
created: 2025-03-17 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExMjN1b3NuNGM2bHF2cm1pN3kyNzI0cTczcmdqcWluemZvNnZ6NHFtcCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/yv9TitLk3J9bHofwWv/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----



# Kafka Helmsman
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
title: "TESLA - Kafka helmsman"
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
      'textColor': '#F8B229',
      'lineColor': '#F8B229'
    }
  }
}%%
flowchart TD
    subgraph "Java Tools"
        KFCT["Kafka Consumer Freshness Tracker"]:::java
        KTEn["Kafka Topic Enforcer"]:::java
        KQEn["Kafka Quota Enforcer"]:::java
        KCert["Kafka Certificates"]:::java
        KACL["Kafka ACL Enforcer"]:::java
        Common["Common Enforcer Libraries"]:::shared
        Bazel["Bazel Build System (Java)"]:::build

        %% Bazel builds Java tools
        Bazel --> KFCT
        Bazel --> KTEn
        Bazel --> KQEn
        Bazel --> KCert
        Bazel --> KACL

        %% Java tools depend on common libraries
        KFCT -->|"uses"| Common
        KTEn -->|"uses"| Common
        KQEn -->|"uses"| Common
        KACL -->|"uses"| Common
        KCert -->|"may_use"| Common
    end

    subgraph "Python Tools"
        KRoller["Kafka Roller"]:::python
        Tox["tox & build_python.sh"]:::build
        Tox --> KRoller
    end

    KafkaCluster["Kafka Cluster (and optional ZooKeeper)"]:::external

    %% Integration of tools with Kafka Cluster
    KFCT -->|"integrates"| KafkaCluster
    KTEn -->|"integrates"| KafkaCluster
    KQEn -->|"integrates"| KafkaCluster
    KCert -->|"integrates"| KafkaCluster
    KACL -->|"integrates"| KafkaCluster
    KRoller -->|"integrates"| KafkaCluster

    T3rdParty["3rdparty Dependencies (Kafka Clients, Logging)"]:::build
    Bazel -->|"manages"| T3rdParty

    %% Click Events
    click KFCT "https://github.com/teslamotors/kafka-helmsman/tree/master/kafka_consumer_freshness_tracker/"
    click KTEn "https://github.com/teslamotors/kafka-helmsman/tree/master/kafka_topic_enforcer/"
    click KQEn "https://github.com/teslamotors/kafka-helmsman/tree/master/kafka_quota_enforcer/"
    click KCert "https://github.com/teslamotors/kafka-helmsman/tree/master/kafka_certificates/"
    click KACL "https://github.com/teslamotors/kafka-helmsman/tree/master/kafka_acl_enforcer/"
    click KRoller "https://github.com/teslamotors/kafka-helmsman/tree/master/kafka_roller/"
    click Common "https://github.com/teslamotors/kafka-helmsman/tree/master/kafka_enforcer_common/"

    %% Styles
    classDef java fill:#DDEEFF,stroke:#0077CC,stroke-width:2px,color:#000;
    classDef python fill:#FFEEDD,stroke:#CC7700,stroke-width:2px,color:#000;
    classDef external fill:#EEF2AA,stroke:#999900,stroke-width:2px,color:#000;
    classDef build fill:#E8E8E8,stroke:#666666,stroke-width:2px,color:#000;
    classDef shared fill:#FFDDFF,stroke:#990099,stroke-width:2px,color:#000;

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
