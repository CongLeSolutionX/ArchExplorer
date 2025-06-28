---
created: 2025-06-26 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright © 2025 Cong Le. All Rights Reserved.
source: https://github.com/apple/swift-nio-http2
---

<div align="center">
  <p>⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷</p>
  <i>This is a working draft in progress.</i>
  <br/>
  <img alt="Loading…" src="https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExN2JmOGg3dHo1dTIzeGUxbjkycG9naTB1Z3VxaWtuNG1jMW16YWU1MyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/Jo1Ox5v5pV9g9ati4S/giphy.gif"/>
  <br/>
  <blockquote>
	  <i>gif image is provided by <a href="https://giphy.com">Giphy</a></i>
  </blockquote>
  <p>⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷</p>

</div>


# swift-nio-http2 repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for 👨‍🎓 <ins>educational purposes</ins> 👨‍🎓 (<ins>:trollface:sometimes, entertainment purposes:trollface:</ins>), 📖 <ins> personal study </ins> 📖, and 🔖 <ins> reference </ins> 🔖.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


----

```mermaid
---
title: "swift-nio-http2 repo project"
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
    subgraph Application_Layer["Application Layer"]
        style Application_Layer fill:#f9f,stroke:#333,stroke-width:1px
        AppServer["Example Server"]:::extension
        PerformanceTester["Performance Tester"]:::extension
        FuzzHarness["Fuzz Testing Harness"]:::extension
        IntegrationTests["Integration Test Harness"]:::extension
    end

    %% External Dependency
    SwiftNIO["SwiftNIO Engine<br/>(EventLoop, ChannelPipeline)"]:::external

    %% Package Manifest
    PackageSwift["Package.swift"]:::util

    %% Pipeline Entry
    ChannelPipeline["ChannelPipeline"]:::external

    %% Inbound Flow
    HTTP2FrameParser["HTTP2FrameParser"]:::core
    ConnectionStateMachine["ConnectionStateMachine"]:::core
    StreamMultiplexer["Stream Multiplexer\n(HTTP2StreamMultiplexer)"]:::core
    HPACKDecoder["HPACKDecoder"]:::compression
    AppInbound["Application Inbound"]:::external

    %% Outbound Flow
    AppOutbound["Application Outbound"]:::external
    HPACKEncoder["HPACKEncoder"]:::compression
    HTTP2FrameEncoder["HTTP2FrameEncoder"]:::core
    ChannelPipelineOut["ChannelPipeline"]:::external
    ByteBuffer["ByteBuffer"]:::external

    subgraph Utilities["Utilities"]
        style Utilities fill:#ddd,stroke:#333,stroke-width:1px
        ContentLengthVerifier["ContentLengthVerifier"]:::util
        DOSHeuristics["DOSHeuristics"]:::util
        ErrorAny["Error+Any"]:::util
    end

    %% Connections
    AppServer -->|uses| SwiftNIO
    PerformanceTester -->|uses| SwiftNIO
    FuzzHarness -->|uses| SwiftNIO
    IntegrationTests -->|runs on| SwiftNIO

    SwiftNIO -->|pipeline| ChannelPipeline

    %% Inbound chain
    ChannelPipeline -->|inbound| HTTP2FrameParser
    HTTP2FrameParser -->|parses frames| ConnectionStateMachine
    ConnectionStateMachine -->|stateful routing| StreamMultiplexer
    StreamMultiplexer -->|demux streams| HPACKDecoder
    HPACKDecoder -->|decoded headers| AppInbound

    %% Outbound chain
    AppOutbound -->|outbound| HPACKEncoder
    HPACKEncoder -->|encoded headers| HTTP2FrameEncoder
    HTTP2FrameEncoder -->|frames| ChannelPipelineOut
    ChannelPipelineOut -->|writes| ByteBuffer

    %% Utilities integration
    ConnectionStateMachine -->|uses| ContentLengthVerifier
    ConnectionStateMachine -->|uses| DOSHeuristics
    ConnectionStateMachine -->|wrap errors| ErrorAny

    %% Click Events - Compression
    click HPACKDecoder "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHPACK/HPACKDecoder.swift"
    click HPACKEncoder "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHPACK/HPACKEncoder.swift"
    click DynamicHeaderTable "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHPACK/DynamicHeaderTable.swift"
    click HeaderTables "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHPACK/HeaderTables.swift"
    click HuffmanCoding "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHPACK/HuffmanCoding.swift"
    click HuffmanTables "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHPACK/HuffmanTables.swift"
    click IndexedHeaderTable "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHPACK/IndexedHeaderTable.swift"
    click IntegerCoding "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHPACK/IntegerCoding.swift"
    click StaticHeaderTable "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHPACK/StaticHeaderTable.swift"
    click HPACKErrors "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHPACK/HPACKErrors.swift"

    %% Click Events - Framing
    click HTTP2FrameParser "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2/HTTP2FrameParser.swift"
    click HTTP2FrameEncoder "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2/HTTP2FrameEncoder.swift"
    click HTTP2Frame "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2/HTTP2Frame.swift"
    click HTTP2ErrorCode "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2/HTTP2ErrorCode.swift"
    click HTTP2Settings "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2/HTTP2Settings.swift"

    %% Click Events - State Machine
    click ConnectionStateMachine "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2/ConnectionStateMachine/ConnectionStateMachine.swift"
    click ConnectionStreamsState "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2/ConnectionStateMachine/ConnectionStreamsState.swift"
    click FrameReceivingStates "https://github.com/apple/swift-nio-http2/tree/main/Sources/NIOHTTP2/ConnectionStateMachine/FrameReceivingStates/"
    click FrameSendingStates "https://github.com/apple/swift-nio-http2/tree/main/Sources/NIOHTTP2/ConnectionStateMachine/FrameSendingStates/"
    click StateMachineResult "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2/ConnectionStateMachine/StateMachineResult.swift"

    %% Click Events - Channel Handler & Helpers
    click HTTP2ChannelHandler "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2/HTTP2ChannelHandler.swift"
    click HTTP2PipelineHelpers "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2/HTTP2PipelineHelpers.swift"
    click InboundStreamMultiplexer "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2/HTTP2ChannelHandler+InboundStreamMultiplexer.swift"
    click InlineStreamMultiplexer "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2/HTTP2ChannelHandler+InlineStreamMultiplexer.swift"

    %% Click Events - Multiplexer & Flow Control
    click StreamMultiplexer "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2/HTTP2StreamMultiplexer.swift"
    click CommonInboundStreamMultiplexer "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2/HTTP2CommonInboundStreamMultiplexer.swift"
    click StreamChannelFlowController "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2/StreamChannelFlowController.swift"
    click WatermarkedFlowController "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2/WatermarkedFlowController.swift"
    click ConcurrentStreamBuffer "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2/ConcurrentStreamBuffer.swift"
    click OutboundFlowControlBuffer "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2/OutboundFlowControlBuffer.swift"
    click OutboundFrameBuffer "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2/OutboundFrameBuffer.swift"

    %% Click Events - Utilities
    click ContentLengthVerifier "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2/ContentLengthVerifier.swift"
    click DOSHeuristics "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2/DOSHeuristics.swift"
    click ErrorAny "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2/Error+Any.swift"

    %% Click Events - Extensions & Tests
    click AppServer "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2Server/main.swift"
    click PerformanceTester "https://github.com/apple/swift-nio-http2/blob/main/Sources/NIOHTTP2PerformanceTester/main.swift"
    click FuzzHarness "https://github.com/apple/swift-nio-http2/blob/main/FuzzTesting/Sources/FuzzHTTP2/main.swift"
    click IntegrationTests "https://github.com/apple/swift-nio-http2/blob/main/IntegrationTests/run-tests.sh"
    click PackageSwift "https://github.com/apple/swift-nio-http2/blob/main/Package.swift"

    %% Styles
    classDef external fill:#bbdefb,stroke:#0d47a1,stroke-width:1px
    classDef core fill:#c8e6c9,stroke:#1b5e20,stroke-width:1px
    classDef compression fill:#ffe0b2,stroke:#e65100,stroke-width:1px
    classDef util fill:#eeeeee,stroke:#424242,stroke-width:1px
    classDef extension fill:#f0f4c3,stroke:#827717,stroke-width:1px

```

----

```mermaid
---
title: "❓...CongLeSolutionX....❓"
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
>**Licenses:**
>
>- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
>- **Creative Commons Attribution-ShareAlike 4.0 International**: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) [![CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/88x31.png)](https://creativecommons.org/licenses/by-sa/4.0/) - Legal details in [LICENSE-CC-BY-SA-4.0](THE_PAST/LICENSE-CC-BY-SA-4.0) and at [Creative Commons official site](https://creativecommons.org/licenses/by-sa/4.0/).
>
---
