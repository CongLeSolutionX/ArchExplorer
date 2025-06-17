---
created: 2025-06-12 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/openai/openai-ruby
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExazQxNm9ldjJscWNyYmUwdzFkMnRkZ3BncDV3ZnAxYWh2eTNrZms0aSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/ies0Iqu9Yc5UqpOk6A/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# openai-ruby repo project
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
title: "openai-ruby repo project"
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
    %% Main Runtime Flow
    subgraph "User Code"
        UserApp["User Code (examples or app)"]:::runtime
    end
    UserApp -->|"invokes"| Client

    Client["OpenAI::Client"]:::runtime
    click Client "https://github.com/openai/openai-ruby/blob/main/lib/openai/client.rb"

    Client -->|"uses DSL"| ResDir

    subgraph "Resource DSL"
        ResDir["Resources (DSL)"]:::runtime
        click ResDir "https://github.com/openai/openai-ruby/tree/main/lib/openai/resources/"
        ChatComp["chat.completions"]:::runtime
        click ChatComp "https://github.com/openai/openai-ruby/blob/main/lib/openai/resources/chat/completions.rb"
        ComMsgs["messages"]:::runtime
        click ComMsgs "https://github.com/openai/openai-ruby/blob/main/lib/openai/resources/chat/completions/messages.rb"
        FilesRes["files"]:::runtime
        click FilesRes "https://github.com/openai/openai-ruby/blob/main/lib/openai/resources/files.rb"
        EmbeddingsRes["embeddings"]:::runtime
        click EmbeddingsRes "https://github.com/openai/openai-ruby/blob/main/lib/openai/resources/embeddings.rb"
        FineTuneRes["fine_tuning"]:::runtime
        click FineTuneRes "https://github.com/openai/openai-ruby/blob/main/lib/openai/resources/fine_tuning.rb"
        EvalRes["evaluations"]:::runtime
        click EvalRes "https://github.com/openai/openai-ruby/blob/main/lib/openai/resources/evaluations.rb"
        ResDir --> ChatComp
        ResDir --> FilesRes
        ResDir --> EmbeddingsRes
        ResDir --> FineTuneRes
        ResDir --> EvalRes
        ChatComp --> ComMsgs
    end

    ResDir -->|"builds request"| PR

    subgraph "Transport Layer"
        PR["PooledNetRequester"]:::runtime
        click PR "https://github.com/openai/openai-ruby/blob/main/lib/openai/internal/transport/pooled_net_requester.rb"
        BC["BaseClient"]:::runtime
        click BC "https://github.com/openai/openai-ruby/blob/main/lib/openai/internal/transport/base_client.rb"
        HTTP["net/http"]:::runtime
        PR --> BC --> HTTP
    end

    BC -->|"HTTP request"| ExternalAPI
    HTTP -->|"HTTP request"| ExternalAPI

    ExternalAPI["OpenAI REST API"]:::external

    ExternalAPI -->|"HTTP response"| BC

    subgraph "Type & Model Layer"
        BM["BaseModel"]:::data
        click BM "https://github.com/openai/openai-ruby/blob/main/lib/openai/internal/type/base_model.rb"
        TC["TypeConverters"]:::data
        click TC "https://github.com/openai/openai-ruby/blob/main/lib/openai/internal/type/converter.rb"
        BP["BasePage (auto-pagination)"]:::data
        click BP "https://github.com/openai/openai-ruby/blob/main/lib/openai/internal/type/base_page.rb"
        BS["BaseStream (SSE)"]:::data
        click BS "https://github.com/openai/openai-ruby/blob/main/lib/openai/internal/type/base_stream.rb"
        GM["Generated Models"]:::data
        click GM "https://github.com/openai/openai-ruby/tree/main/lib/openai/models/"
        BM --> GM
        TC --> GM
        BS --> GM
        BC --> BM
        BC --> BS
        GM --> UserApp
        BP --> BP
        GM --> BP
    end

    subgraph "Helpers"
        SO["StructuredOutput"]:::data
        click SO "https://github.com/openai/openai-ruby/blob/main/lib/openai/helpers/structured_output/base_model.rb"
        click SO "https://github.com/openai/openai-ruby/blob/main/lib/openai/helpers/structured_output/json_schema_converter.rb"
        FP["FilePart"]:::data
        click FP "https://github.com/openai/openai-ruby/blob/main/lib/openai/file_part.rb"
    end

    SO --> BM
    FP --> PR

    %% Auxiliary Tooling
    subgraph "Type Definitions"
        RBI["RBI Definitions"]:::tooling
        click RBI "https://github.com/openai/openai-ruby/blob/main/rbi/openai/client.rbi"
        click RBI "https://github.com/openai/openai-ruby/blob/main/rbi/openai/internal/transport/pooled_net_requester.rbi"
        click RBI "https://github.com/openai/openai-ruby/blob/main/rbi/openai/models/all_models.rbi"
        RBS["RBS Definitions"]:::tooling
        click RBS "https://github.com/openai/openai-ruby/blob/main/sig/openai/client.rbs"
        click RBS "https://github.com/openai/openai-ruby/blob/main/sig/openai/internal/type/converter.rbs"
        click RBS "https://github.com/openai/openai-ruby/blob/main/sig/openai/models/audio/speech_create_params.rbs"
    end

    subgraph "CLI & Tooling"
        CLI1["bin scripts"]:::tooling
        click CLI1 "https://github.com/openai/openai-ruby/tree/main/bin/check-release-environment"
        click CLI1 "https://github.com/openai/openai-ruby/tree/main/bin/publish-gem"
        Scripts["scripts/"]:::tooling
        click Scripts "https://github.com/openai/openai-ruby/tree/main/scripts/bootstrap"
        click Scripts "https://github.com/openai/openai-ruby/tree/main/scripts/test"
        click Scripts "https://github.com/openai/openai-ruby/tree/main/scripts/lint"
        RF["Rakefile"]:::tooling
        click RF "https://github.com/openai/openai-ruby/tree/main/Rakefile"
    end

    %% Styles
    classDef runtime fill:#e0f7fa,stroke:#006064,color:#006064;
    classDef data fill:#e8f5e9,stroke:#2e7d32,color:#2e7d32;
    classDef tooling fill:#eceff1,stroke:#455a64,color:#455a64;
    classDef external fill:#ffebee,stroke:#c62828,color:#c62828;

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
