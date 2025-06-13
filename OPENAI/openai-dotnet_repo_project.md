---
created: 2025-06-012 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/openai-dotnet
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExeHJweDB5OWl5NzhrdXR6eDA0ZDZvZXFvbjloNnNnb3ZwbnZxbHVkYSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/wJfZOIx30vMEDm16jz/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# openai-dotnet repo project
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


```mermaid
---
title: "openai-dotnet repo project"
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
flowchart TB
    subgraph "Application Layer"
        App[Client Application]
    end

    subgraph "Client Layer"
        OAC[OpenAI Client]:::main
        click OAC "https://github.com/openai/openai-dotnet/blob/main/src/Custom/OpenAIClient.cs"
        
        Options[Client Options]:::config
        click Options "https://github.com/openai/openai-dotnet/blob/main/src/Custom/OpenAIClientOptions.cs"
    end

    subgraph "Feature Clients"
        Chat[Chat Client]:::feature
        Audio[Audio Client]:::feature
        Image[Image Client]:::feature
        Embed[Embeddings Client]:::feature
        Assist[Assistants Client]:::experimental
        
        click Chat "https://github.com/openai/openai-dotnet/blob/main/src/Custom/Chat/ChatClient.cs"
        click Audio "https://github.com/openai/openai-dotnet/blob/main/src/Custom/Audio/AudioClient.cs"
        click Image "https://github.com/openai/openai-dotnet/blob/main/src/Custom/Images/ImageClient.cs"
        click Embed "https://github.com/openai/openai-dotnet/blob/main/src/Custom/Embeddings/EmbeddingClient.cs"
        click Assist "https://github.com/openai/openai-dotnet/blob/main/src/Custom/Assistants/AssistantClient.cs"
    end

    subgraph "Protocol Layer"
        Rest[REST Client]:::protocol
        Pipeline[Pipeline Policy]:::protocol
        Auth[Authentication]:::protocol
        
        click Rest "https://github.com/openai/openai-dotnet/blob/main/src/Generated/OpenAIClient.RestClient.cs"
        click Pipeline "https://github.com/openai/openai-dotnet/blob/main/src/Utility/GenericActionPipelinePolicy.cs"
        click Auth "https://github.com/openai/openai-dotnet/blob/main/src/Generated/OpenAIClientOptions.cs"
    end

    subgraph "Model Layer"
        BaseModels[Base Models]:::model
        ChatModels[Chat Models]:::model
        AudioModels[Audio Models]:::model
        ImageModels[Image Models]:::model
        ErrorModels[Error Models]:::error
        
        click BaseModels "https://github.com/openai/openai-dotnet/tree/main/src/Generated/Models"
        click ChatModels "https://github.com/openai/openai-dotnet/blob/main/src/Custom/Chat/ChatMessage.cs"
        click AudioModels "https://github.com/openai/openai-dotnet/blob/main/src/Custom/Audio/AudioTranscription.cs"
        click ImageModels "https://github.com/openai/openai-dotnet/blob/main/src/Custom/Images/GeneratedImage.cs"
        click ErrorModels "https://github.com/openai/openai-dotnet/blob/main/src/Custom/OpenAIError.cs"
    end

    subgraph "Utility Layer"
        Telemetry[OpenTelemetry]:::utility
        Streaming[Streaming Support]:::utility
        Binary[Binary Content]:::utility
        Mock[Mock Testing]:::testing
        
        click Telemetry "https://github.com/openai/openai-dotnet/blob/main/src/Utility/Telemetry/OpenTelemetrySource.cs"
        click Streaming "https://github.com/openai/openai-dotnet/blob/main/src/Utility/System.Net.ServerSentEvents.cs"
        click Binary "https://github.com/openai/openai-dotnet/blob/main/src/Utility/MultipartFormDataBinaryContent.cs"
        click Mock "https://github.com/openai/openai-dotnet/blob/main/tests/Utility/MockPipelineTransport.cs"
    end

    subgraph "External"
        API[OpenAI REST API]:::external
    end

    App --> OAC
    OAC --> Options
    OAC --> |Creates| Chat & Audio & Image & Embed & Assist
    Chat & Audio & Image & Embed & Assist --> Rest
    Rest --> Pipeline
    Pipeline --> Auth
    Auth --> API
    Rest --> BaseModels
    Chat --> ChatModels
    Audio --> AudioModels
    Image --> ImageModels
    Rest --> ErrorModels
    Rest --> Streaming
    Rest --> Binary
    Rest --> Telemetry
    Rest -.-> Mock

    classDef main fill:#2196F3,stroke:#1565C0,color:white
    classDef config fill:#90CAF9,stroke:#1565C0,color:black
    classDef feature fill:#4CAF50,stroke:#2E7D32,color:white
    classDef experimental fill:#FF9800,stroke:#EF6C00,color:white
    classDef protocol fill:#FDD835,stroke:#F9A825,color:black
    classDef model fill:#9C27B0,stroke:#6A1B9A,color:white
    classDef error fill:#F44336,stroke:#C62828,color:white
    classDef utility fill:#795548,stroke:#4E342E,color:white
    classDef testing fill:#9E9E9E,stroke:#424242,color:white
    classDef external fill:#607D8B,stroke:#37474F,color:white
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
    
  Link_to_my_profile{{"<a href='https://github.com/CongLeSolutionX/CongLeSolutionX' target='_blank'>Click here if you care about my profile</a>"}}

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
