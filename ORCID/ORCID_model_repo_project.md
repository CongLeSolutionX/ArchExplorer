---
created: 2025-06-09 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/orcid/orcid-model
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExcHcwcGc0aDlqY2s4NnM5ejZyM3J3dWZicGdzMnRkeXppN3ZydnRldyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/3o6gbchrcNIt4Ma8Tu/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----


# ORCID model repo project
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


## A Diagrammatic Guide 

----

```mermaid
---
title: "ORCID model repo project"
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
    %% External APIs
    subgraph External_ORCID_APIs["External ORCID APIs"]
        ORCID_PUBLIC["ORCID Public API"]:::external
        ORCID_MEMBER["ORCID Member API"]:::external
    end

    %% Maven Build and Code Generation
    subgraph Build_Process["Build Process"]
        MB["pom.xml"]:::build
        plugin["JAXB Code-Generation Plugin"]:::process
    end
    MB --> plugin
    plugin --> codegen["Generate JAXB Java Sources"]:::process

    %% XSD Schemas & Sample Payloads
    subgraph XSD_Schemas_and_Sample_Payloads["XSD Schemas & Sample Payloads"]
        client20["client_2.0"]:::resources
        client21["client_2.1"]:::resources
        client30["client_3.0"]:::resources
        common20["common_2.0"]:::resources
        common21["common_2.1"]:::resources
        common30["common_3.0"]:::resources
        group20["group-id-2.0"]:::resources
        group21["group-id-2.1"]:::resources
        group30["group-id-3.0"]:::resources
        notification20["notification_2.0"]:::resources
        notification21["notification_2.1"]:::resources
        notification30["notification_3.0"]:::resources
        record20["record_2.0"]:::resources
        record21["record_2.1"]:::resources
        record30["record_3.0"]:::resources
        summary30["summary_3.0"]:::resources
    end
    codegen --> client20
    codegen --> client21
    codegen --> client30
    codegen --> common20
    codegen --> common21
    codegen --> common30
    codegen --> group20
    codegen --> group21
    codegen --> group30
    codegen --> notification20
    codegen --> notification21
    codegen --> notification30
    codegen --> record20
    codegen --> record21
    codegen --> record30
    codegen --> summary30

    %% Java Model Packages
    subgraph JAXB_Java_Model_Packages["JAXB Java Model Packages"]
        pm1["org.orcid.jaxb.model.client_v2"]:::code
        pm2["org.orcid.jaxb.model.common"]:::code
        pm3["org.orcid.jaxb.model.message"]:::code
        pm4["org.orcid.jaxb.model.notification"]:::code
        pm5["org.orcid.jaxb.model.record"]:::code
        pm6["org.orcid.jaxb.model.record_v2"]:::code
        pm7["org.orcid.jaxb.model.search_v2"]:::code
        pm8["org.orcid.jaxb.model.statistics"]:::code
        pm9["org.orcid.jaxb.model.v3.release"]:::code
    end
    client20 & client21 & client30 & common20 & common21 & common30 & group20 & group21 & group30 & notification20 & notification21 & notification30 & record20 & record21 & record30 & summary30 --> pm1 & pm2 & pm3 & pm4 & pm5 & pm6 & pm7 & pm8 & pm9

    %% Utility & Supplemental Classes
    subgraph Utility_and_Supplemental_Classes["Utility & Supplemental Classes"]
        util["org.orcid.model.utils"]:::code
        recCorr["org.orcid.model.record_correction"]:::code
        instSign["org.orcid.model.notification.institutional_sign_in_v2"]:::code
        v3notif["org.orcid.model.v3.release.notification"]:::code
    end
    util & recCorr & instSign & v3notif --> pm2 & pm4 & pm9

    %% Artifact Packaging
    subgraph Artifact["Artifact"]
    %% :::artifact
        artifact["orcid-model.jar<br/>(org.orcid:orcid-model)"]:::artifact
    end
    pm1 & pm2 & pm3 & pm4 & pm5 & pm6 & pm7 & pm8 & pm9 & util & recCorr & instSign & v3notif --> artifact

    %% Client Application
    subgraph Downstream_Client["Downstream Client"]
        clientApp["Client Application"]:::external
    end
    clientApp -->|"depends on"| artifact

    %% Runtime Marshalling Flow
    ORCID_PUBLIC -->|"XML/JSON"| Unmarshaller["JAXB Unmarshaller"]:::code
    Unmarshaller -->|"Java Objects"| artifact
    artifact -->|"Marshaller"| Marshaller["JAXB Marshaller"]:::code
    Marshaller -->|"XML/JSON"| ORCID_MEMBER

    %% Unit Tests
    subgraph Unit_Tests["Unit Tests<br/>(Validation Layer)"]
        test1["org.orcid.jaxb.model tests"]:::tests
        test2["org.orcid.record Validate V2 Tests"]:::tests
        test3["org.orcid.record.v3.release tests"]:::tests
        test4["org.orcid.entities.MarshallingTest"]:::tests
    end
    test1 & test2 & test3 & test4 --> client20 & client21 & record20 & record21 & record30 & summary30
    test1 & test2 & test3 & test4 --> pm1 & pm2 & pm3 & pm4 & pm5 & pm6 & pm7 & pm8 & pm9

    %% Click Events
    click MB "https://github.com/orcid/orcid-model/blob/main/pom.xml"
    click plugin "https://github.com/orcid/orcid-model/blob/main/pom.xml"
    click client20 "https://github.com/orcid/orcid-model/blob/main/src/main/resources/client_2.0"
    click client21 "https://github.com/orcid/orcid-model/blob/main/src/main/resources/client_2.1"
    click client30 "https://github.com/orcid/orcid-model/blob/main/src/main/resources/client_3.0"
    click common20 "https://github.com/orcid/orcid-model/blob/main/src/main/resources/common_2.0"
    click common21 "https://github.com/orcid/orcid-model/blob/main/src/main/resources/common_2.1"
    click common30 "https://github.com/orcid/orcid-model/blob/main/src/main/resources/common_3.0"
    click group20 "https://github.com/orcid/orcid-model/blob/main/src/main/resources/group-id-2.0"
    click group21 "https://github.com/orcid/orcid-model/blob/main/src/main/resources/group-id-2.1"
    click group30 "https://github.com/orcid/orcid-model/blob/main/src/main/resources/group-id-3.0"
    click notification20 "https://github.com/orcid/orcid-model/blob/main/src/main/resources/notification_2.0"
    click notification21 "https://github.com/orcid/orcid-model/blob/main/src/main/resources/notification_2.1"
    click notification30 "https://github.com/orcid/orcid-model/blob/main/src/main/resources/notification_3.0"
    click record20 "https://github.com/orcid/orcid-model/blob/main/src/main/resources/record_2.0"
    click record21 "https://github.com/orcid/orcid-model/blob/main/src/main/resources/record_2.1"
    click record30 "https://github.com/orcid/orcid-model/blob/main/src/main/resources/record_3.0"
    click summary30 "https://github.com/orcid/orcid-model/blob/main/src/main/resources/summary_3.0"
    click pm1 "https://github.com/orcid/orcid-model/tree/main/src/main/java/org/orcid/jaxb/model/client_v2"
    click pm2 "https://github.com/orcid/orcid-model/tree/main/src/main/java/org/orcid/jaxb/model/common"
    click pm3 "https://github.com/orcid/orcid-model/tree/main/src/main/java/org/orcid/jaxb/model/message"
    click pm4 "https://github.com/orcid/orcid-model/tree/main/src/main/java/org/orcid/jaxb/model/notification"
    click pm5 "https://github.com/orcid/orcid-model/tree/main/src/main/java/org/orcid/jaxb/model/record"
    click pm6 "https://github.com/orcid/orcid-model/tree/main/src/main/java/org/orcid/jaxb/model/record_v2"
    click pm7 "https://github.com/orcid/orcid-model/tree/main/src/main/java/org/orcid/jaxb/model/search_v2"
    click pm8 "https://github.com/orcid/orcid-model/tree/main/src/main/java/org/orcid/jaxb/model/statistics"
    click pm9 "https://github.com/orcid/orcid-model/tree/main/src/main/java/org/orcid/jaxb/model/v3/release"
    click util "https://github.com/orcid/orcid-model/tree/main/src/main/java/org/orcid/model/utils"
    click recCorr "https://github.com/orcid/orcid-model/tree/main/src/main/java/org/orcid/model/record_correction"
    click instSign "https://github.com/orcid/orcid-model/tree/main/src/main/java/org/orcid/model/notification/institutional_sign_in_v2"
    click v3notif "https://github.com/orcid/orcid-model/tree/main/src/main/java/org/orcid/model/v3/release/notification"
    click test1 "https://github.com/orcid/orcid-model/tree/main/src/test/java/org/orcid/jaxb/model"
    click test2 "https://github.com/orcid/orcid-model/tree/main/src/test/java/org/orcid/record"
    click test3 "https://github.com/orcid/orcid-model/tree/main/src/test/java/org/orcid/record/v3/release"
    click test4 "https://github.com/orcid/orcid-model/blob/main/src/test/java/org/orcid/entities/MarshallingTest.java"

    %% Styles
    classDef external fill:#FFA500,stroke:#333,stroke-width:1px;
    classDef resources fill:#ADD8E6,stroke:#333,stroke-width:1px;
    classDef process fill:#FFFF99,stroke:#333,stroke-width:1px;
    classDef code fill:#90EE90,stroke:#333,stroke-width:1px;
    classDef artifact fill:#D3D3D3,stroke:#333,stroke-width:1px;
    classDef tests stroke-dasharray: 5 5,fill:none,stroke:#333;

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
    
  My_Meme ~~~ Closing_quote
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

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
