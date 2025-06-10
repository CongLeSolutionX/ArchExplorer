---
created: 2025-03-17 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
---



# Fleet Telemetry
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
title: "TESLA - Fleet Telemetry"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  layout: elk
  look: handDrawn
  theme: dark
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
    %% Vehicle Clients Layer
    subgraph "Vehicle Clients"
        V1("Tesla Vehicles"):::vehicle
    end

    %% Fleet Telemetry Server
    subgraph "Fleet Telemetry Server"
        F1("Main Application"):::server
        F2("WebSocket Handler"):::server
        F3("Middleware Processor"):::server
        F4("Dispatcher Manager"):::server
        F5("Reliable Acknowledgement"):::server
    end

    %% Configuration Service
    subgraph "Configuration Service"
        C1("Configuration"):::config
    end

    %% Dispatcher Modules
    subgraph "Dispatcher Modules"
        D1("Google PubSub Dispatcher"):::dispatcher
        D2("Kafka Dispatcher"):::dispatcher
        D3("Kinesis Dispatcher"):::dispatcher
        D4("MQTT Dispatcher"):::dispatcher
        D5("Simple Logger Dispatcher"):::dispatcher
        D6("ZMQ Dispatcher"):::dispatcher
    end

    %% Logger Services
    subgraph "Logger Services"
        L1("Logger"):::logger
        L2("No-op Logger"):::logger
    end

    %% Metrics & Monitoring
    subgraph "Metrics & Monitoring"
        M1("Metrics Collection"):::monitoring
        M2("Monitoring Endpoints"):::monitoring
    end

    %% Telemetry Schema
    subgraph "Telemetry Schema"
        TS1("Protocol Buffers"):::serialization
        TS2("Messages"):::serialization
    end

    %% External Systems
    subgraph "External Systems"
        EX1("Google PubSub"):::dispatcher
        EX2("Kafka"):::dispatcher
        EX3("Kinesis"):::dispatcher
        EX4("MQTT"):::dispatcher
        EX5("ZMQ"):::dispatcher
        EX6("STDOUT Logger"):::logger
    end

    %% Data Flow Connections
    V1 -->|"WebSocket-connection"| F2
    C1 -->|"TLS/Config"| F2
    F1 --> F2
    F2 --> F3
    F3 --> F4
    F4 -->|"Dispatch"| D1
    F4 -->|"Dispatch"| D2
    F4 -->|"Dispatch"| D3
    F4 -->|"Dispatch"| D4
    F4 -->|"Dispatch"| D5
    F4 -->|"Dispatch"| D6
    D1 --> EX1
    D2 --> EX2
    D3 --> EX3
    D4 --> EX4
    D5 --> EX6
    D6 --> EX5
    F5 -->|"Ack"| V1
    F3 -->|"Log"| L1
    F3 --> M1
    M1 --> M2
    TS1 --> F3
    TS2 --> F3

    %% Click Events for Server Components
    click F1 "https://github.com/teslamotors/fleet-telemetry/blob/main/cmd/main.go"
    click F2 "https://github.com/teslamotors/fleet-telemetry/blob/main/server/streaming/socket.go"
    click F3 "https://github.com/teslamotors/fleet-telemetry/blob/main/server/middleware/wrapped_response_writer.go"
    click F5 "https://github.com/teslamotors/fleet-telemetry/blob/main/messages/stream_ack_message.go"
    click C1 "https://github.com/teslamotors/fleet-telemetry/blob/main/config/config.go"

    %% Click Events for Dispatcher Modules
    click D1 "https://github.com/teslamotors/fleet-telemetry/blob/main/datastore/googlepubsub/publisher.go"
    click D2 "https://github.com/teslamotors/fleet-telemetry/blob/main/datastore/kafka/kafka.go"
    click D3 "https://github.com/teslamotors/fleet-telemetry/blob/main/datastore/kinesis/kinesis.go"
    click D4 "https://github.com/teslamotors/fleet-telemetry/blob/main/datastore/mqtt/mqtt.go"
    click D5 "https://github.com/teslamotors/fleet-telemetry/blob/main/datastore/simple/logger.go"
    click D6 "https://github.com/teslamotors/fleet-telemetry/blob/main/datastore/zmq/zmq.go"

    %% Click Events for Logger Services
    click L1 "https://github.com/teslamotors/fleet-telemetry/blob/main/logger/logger.go"
    click L2 "https://github.com/teslamotors/fleet-telemetry/blob/main/logger/no_op_logger.go"

    %% Click Events for Metrics & Monitoring
    click M1 "https://github.com/teslamotors/fleet-telemetry/tree/main/metrics/"
    click M2 "https://github.com/teslamotors/fleet-telemetry/blob/main/server/monitoring/metrics_server.go"

    %% Click Events for Telemetry Schema
    click TS1 "https://github.com/teslamotors/fleet-telemetry/tree/main/protos/"
    click TS2 "https://github.com/teslamotors/fleet-telemetry/blob/main/messages/tesla/Message.go"

    %% Styling Classes
    classDef vehicle fill:#FAA6,stroke:#000,stroke-width:2px;
    classDef server fill:#2A9D8F,stroke:#000,stroke-width:2px,color:#fff;
    classDef config fill:#264653,stroke:#000,stroke-width:2px,color:#fff;
    classDef dispatcher fill:#E76F51,stroke:#000,stroke-width:2px,color:#fff;
    classDef logger fill:#F4A261,stroke:#000,stroke-width:2px;
    classDef monitoring fill:#ECC6,stroke:#000,stroke-width:2px;
    classDef serialization fill:#FCF4,stroke:#000,stroke-width:2px;


```



---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---
