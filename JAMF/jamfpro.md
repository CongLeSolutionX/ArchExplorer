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
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExZDJxZWZzZjF4aXkzNnkxMzlyZ21tdnZ0eDJhcjluNm1lZ2VweHU3ciZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/VX7yEoXAFf8as/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Jamfpro
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
title: "JamF - Jamfpro"
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
    'graph': {'htmlLabels': true, 'curve': 'basis' },
    'fontFamily': 'Fantasy',
    'themeVariables': {
      'lineColor': '#F8B229'
    }
  }
}%%
graph TD
    %% Build Process
    subgraph "Build Process"
        DBE["Docker Build Environment"]:::build
        IMG["Docker Image"]:::build
    end

    %% Runtime Container
    subgraph "Runtime Container"
        CON["Container"]:::container
        subgraph "Container Components"
            TOMCAT["Apache Tomcat (non-root)"]:::subcomp
            CONFIG["Custom Configuration Files"]:::subcomp
            LOGGING["Logging Setup"]:::subcomp
            APP["JamfPro Application Deployment (ROOT.war)"]:::subcomp
        end
    end

    %% External Systems
    subgraph "External Systems"
        DB["Remote Database"]:::external
        JMX["Monitoring (JMX)"]:::external
        KUBE["Kubernetes Environment"]:::external
    end

    %% Connections - Build to Runtime
    DBE -->|"builds"| IMG
    IMG -->|"deploys"| CON
    CON -->|"runs"| TOMCAT
    CON -->|"includes"| CONFIG
    CON -->|"includes"| LOGGING
    CON -->|"includes"| APP

    %% Internal Configuration Connections
    CONFIG -->|"overrides"| TOMCAT
    LOGGING -->|"routesLogs"| CON

    %% External Interactions
    TOMCAT -->|"connectsTo"| DB
    TOMCAT -->|"monitoredBy"| JMX
    TOMCAT -->|"clusteredIn"| KUBE

    %% Environment Variables Influence (Annotation)
    DBE -.->|"envVarsApplied"| CON

    %% Click Events for Build Components
    click DBE "https://github.com/jamf/jamfpro/tree/master/Dockerfile"
    click DBE "https://github.com/jamf/jamfpro/blob/master/.dockerignore"
    click DBE "https://github.com/jamf/jamfpro/tree/master/Makefile"

    %% Click Events for Tomcat Component
    click TOMCAT "https://github.com/jamf/jamfpro/blob/master/startup.sh"

    %% Click Events for Custom Configuration Files
    click CONFIG "https://github.com/jamf/jamfpro/blob/master/server.template"
    click CONFIG "https://github.com/jamf/jamfpro/blob/master/configuration.sh"

    %% Click Events for Logging Setup
    click LOGGING "https://github.com/jamf/jamfpro/blob/master/log4j.stdout.replace"
    click LOGGING "https://github.com/jamf/jamfpro/blob/master/log4j2.stdout.appenders.replace"
    click LOGGING "https://github.com/jamf/jamfpro/blob/master/log4j2.stdout.loggers.analytics.replace"
    click LOGGING "https://github.com/jamf/jamfpro/blob/master/log4j2.stdout.loggers.root.replace"
    click LOGGING "https://github.com/jamf/jamfpro/blob/master/log4j2.stdout.loggers.vpp.replace"

    %% Styles
    classDef build fill:#FFD700,stroke:#333,stroke-width:2px;
    classDef container fill:#98FB98,stroke:#333,stroke-width:2px;
    classDef subcomp fill:#ADD8E6,stroke:#333,stroke-width:2px;
    classDef external fill:#FFB6C1,stroke:#333,stroke-width:2px


```





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
