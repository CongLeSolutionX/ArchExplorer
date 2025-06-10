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
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExajExNGtobXQzY3QyMHFrdnQ0Z29qeWpzb2t3bHZmaHN5MTlwOXdkMSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/ZLbIkCTHPxt7B1CnvG/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# Sensor Tower - Heatmap
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
title: "Sensor Tower - Heatmap"
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
      'textColor': '#F8B229',
      'lineColor': '#F8B229'
    }
  }
}%%
flowchart TD
    %% Initialization Layer
    subgraph "Initialization Layer"
        CLI["Main Application / CLI"]:::component
    end

    %% Data Ingestion Layer
    subgraph "Data Ingestion Layer"
        Statsd["Statsd Input Interface"]:::component
        Dummy["Dummy Data Generator"]:::component
    end

    %% Data Storage Layer
    subgraph "Data Storage Layer"
        Datastore["In-Memory Datastore"]:::datastore
    end

    %% API Layer
    subgraph "API Layer"
        API["HTTP API & Rendering"]:::api
    end

    %% Cross-Cutting Services
    Monitor["Monitoring & Profiling"]:::monitor
    Log["Logging and Diagnostics"]:::logging

    %% Primary Flow Connections
    CLI -->|"init"| Statsd
    CLI -->|"init"| Dummy
    CLI -->|"init"| Datastore
    CLI -->|"init"| API

    Statsd -->|"input_metrics"| Datastore
    Dummy -->|"inject_dummy"| Datastore
    API -->|"query_data"| Datastore

    %% Monitoring Connections
    Statsd -->|"monitored"| Monitor
    Dummy -->|"monitored"| Monitor
    Datastore -->|"monitored"| Monitor
    API -->|"monitored"| Monitor
    CLI -->|"monitored"| Monitor

    %% Logging Connections (dotted)
    CLI ---|"logs"| Log
    Statsd ---|"logs"| Log
    Dummy ---|"logs"| Log
    Datastore ---|"logs"| Log
    API ---|"logs"| Log
    Monitor ---|"logs"| Log

    %% Click Events for Main Application / CLI
    click CLI "https://github.com/sensortower/heatmap/blob/master/cmd/heatmap/main.go"
    click CLI "https://github.com/sensortower/heatmap/blob/master/main.go"
    click CLI "https://github.com/sensortower/heatmap/blob/master/config.go"

    %% Click Event for Statsd Input Interface
    click Statsd "https://github.com/sensortower/heatmap/blob/master/statsd.go"

    %% Click Events for In-Memory Datastore
    click Datastore "https://github.com/sensortower/heatmap/blob/master/datastore.go"
    click Datastore "https://github.com/sensortower/heatmap/blob/master/ramdatastore.go"
    click Datastore "https://github.com/sensortower/heatmap/blob/master/ramdatastore_test.go"

    %% Click Events for HTTP API & Rendering
    click API "https://github.com/sensortower/heatmap/blob/master/http.go"
    click API "https://github.com/sensortower/heatmap/blob/master/httprender.go"

    %% Click Event for Dummy Data Generator
    click Dummy "https://github.com/sensortower/heatmap/blob/master/dummy.go"

    %% Click Events for Monitoring & Profiling
    click Monitor "https://github.com/sensortower/heatmap/blob/master/memwatch.go"
    click Monitor "https://github.com/sensortower/heatmap/blob/master/memwatch_darwin.go"
    click Monitor "https://github.com/sensortower/heatmap/blob/master/memwatch_linux.go"
    click Monitor "https://github.com/sensortower/heatmap/blob/master/memwatch_other.go"
    click Monitor "https://github.com/sensortower/heatmap/blob/master/pprof.go"

    %% Click Event for Logging and Diagnostics
    click Log "https://github.com/sensortower/heatmap/blob/master/logging.go"

    %% Styles
    classDef component fill:#AED6F1,stroke:#1B4F72,stroke-width:2px;
    classDef datastore fill:#F9E79F,stroke:#B7950B,stroke-width:2px;
    classDef api fill:#A9DFBF,stroke:#1E8449,stroke-width:2px;
    classDef monitor fill:#F5CBA7,stroke:#E67E22,stroke-width:2px;
    classDef logging fill:#D2B4DE,stroke:#8E44AD,stroke-width:2px;


```




---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
