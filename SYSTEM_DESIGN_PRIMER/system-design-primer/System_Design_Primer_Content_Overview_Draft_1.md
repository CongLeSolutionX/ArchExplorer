---
created: 2025-03-09 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://github.com/donnemartin/system-design-primer/blob/master/README.md"
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExM2xodTZzb3owNnM4YThtcGkycjZobmE5czN0ZnhqMHdoNzNqNGZpaSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/lXHwJv89PvdN200Anr/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# System Design Primer - Content Overview
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

The Mermaid diagram below summarizes the key concepts of the System Design Primer, emphasizing its structure, purpose, and core topics.  Each area has been clearly laid out with proper connections and visual distinction.


```mermaid
---
title: "System Design Primer - The Content Overview"
config:
  layout: elk
  look: handDrawn
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%%%%%%% Available curve styles include the following keywords:
%% basis, bumpX, bumpY, cardinal, catmullRom, linear, monotoneX, monotoneY, natural, step, stepAfter, stepBefore.
%%{
  init: {
    "flowchart": { "htmlLabels": false, 'curve': 'linear' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'primaryColor': '#BB28',
      'textColor': '#F8B229',
      'primaryTextColor': '#299',
      'primaryBorderColor': '#7c2',
      'lineColor': '#F8B229',
      'secondaryColor': '#006100',
      'tertiaryColor': '#fff'
    }
  }
}%%
graph LR
    A[System Design Primer] --> B{Purpose};
    B --> C[Learn Large-Scale System Design]:::detail;
    C --> CA[Improve engineering skills by designing scalable systems.];
    C --> CB[Organized collection of resources for building systems at scale.];
    C --> CC[Learn from open-source community contributions.];

    B --> D[Interview Preparation]:::detail;
    D --> DA[Required component of technical interviews at many tech companies.];
    D --> DB[Practice with common system design interview questions.];
    D --> DC[Compare your solutions with sample discussions, code, and diagrams.];
    D --> DD[Utilize resources: study guide, approach guidelines, sample questions & solutions.];

    A --> E{Key Resources};
    E --> F[Anki Flashcards]:::detail;
    F --> FA[Spaced repetition for key concepts.];
    F --> FB[Decks for System Design, Exercises, Object-Oriented Design.];
    F --> FC[Great for learning on-the-go.];
    E --> G[Interactive Coding Challenges]:::detail;
    G --> GA[Sister repo with coding challenges.];
    G --> GB[Additional Anki deck for coding.];

    A --> H{Core System Design Topics};
    H --> I[Scalability]:::detail;
    I --> IA[Vertical vs. Horizontal Scaling];
    I --> IB[Caching, Load Balancing, Database Replication & Partitioning.];
    H --> J[Trade-offs]:::detail;
    J --> JA[Performance vs. Scalability];
    J --> JB[Latency vs. Throughput];
    J --> JC["Availability vs. Consistency (CAP Theorem)"]

    H --> K[Networking & Communication]:::detail;
    K --> KA["Domain Name System (DNS)"]
    K --> KB["Content Delivery Network (CDN): Push vs. Pull"]
    K --> KC["Load Balancers: Active-Passive, Active-Active, Layer 4 & Layer 7"]
    K --> KD["Reverse Proxy (Web Server)"]
    K --> KE["Protocols: TCP, UDP, HTTP (REST, RPC)"]

    H --> L[Application Architecture]:::detail;
    L --> LA["Application Layer (Microservices)"]
    L --> LB["Service Discovery (Consul, Etcd, Zookeeper)"]

    H --> M[Database Systems]:::detail;
    M --> MA["RDBMS (SQL): Replication, Federation, Sharding, Denormalization, SQL Tuning"]
    M --> MB[NoSQL: Key-Value, Document, Wide Column, Graph];
    M --> MC[SQL vs NoSQL trade-offs.];

    H --> N[Caching Strategies]:::detail;
    N --> NA[Client, CDN, Web Server, Database, Application Caching];
    N --> NB[Update Policies: Cache-Aside, Write-Through, Write-Behind, Refresh-Ahead];

    H --> O[Asynchronism]:::detail;
    O --> OA["Message Queues & Task Queues (Redis, RabbitMQ, Amazon SQS, Celery)"]
    O --> OB[Back Pressure to limit queue size.];

    A --> P{Security};
    P --> Q[Basic Security Principles]:::detail;
        Q --> QA[Encryption in transit and at rest.];
         Q --> QB[Sanitize inputs to prevent XSS & SQL injection.];
         Q --> QC[Use parameterized queries.];
         Q --> QD[Principle of Least Privilege.];

    A --> R{Appendix};
    R --> S[Reference Tables]:::detail;
         S --> SA[Powers of Two Table.];
         S --> SB[Latency Numbers for Programmers.];
    R --> T[Additional Questions]:::detail;
         T --> TA[Links to resources and solutions.];

    A --> U{Contributing};
    U --> V[Open Source Project]:::detail;
         V --> VA[Fix errors, improve sections, add new sections, translate.];
         V --> VB[Review contributing guidelines.];

    style A fill:#a2da,stroke:#333,stroke-width:1px
    style C fill:#f2bf,stroke:#333,stroke-width:1px;
    style D fill:#f2bf,stroke:#333,stroke-width:1px;
    style F fill:#a2fa,stroke:#333,stroke-width:1px;
    style G fill:#f2aa,stroke:#333,stroke-width:1px;
    style I fill:#c5cf,stroke:#333,stroke-width:1px
    style J fill:#a5af,stroke:#333,stroke-width:2px
    style K fill:#f2fa,stroke:#333,stroke-width:1px;
    style L fill:#a2fa,stroke:#333,stroke-width:1px;
    style M fill:#a2af,stroke:#333,stroke-width:1px;
    style N fill:#f2bf,stroke:#333,stroke-width:1px;
    style O fill:#a2fa,stroke:#333,stroke-width:1px
    style Q fill:#f2aa,stroke:#333,stroke-width:1px
    style S fill:#c5cf,stroke:#333,stroke-width:1px
    style V fill:#f2aa,stroke:#333,stroke-width:1px
    
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
