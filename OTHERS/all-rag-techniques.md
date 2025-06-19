---
created: 2025-06-13 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/FareedKhan-dev/all-rag-techniques
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress.
> 
> ![Loading...](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExZmdoYWhxb3c2NmR6OGZoMzN5NWxqNjJmbmVxd3U0NDFobjc4ZHdvNyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/xUA7bjPYcgAvwq5CKc/giphy.gif)
> 
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷

----


# FareedKhan-dev - all-rag-techniques repo project
<details open>
<summary>Click to show/hide the full disclaimer.</summary>
   
> <ins>📢 **Disclaimer** 🚨</ins>
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes (<ins>sometimes, entertainment purposes</ins>), personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.

</details>


----

```mermaid
---
title: "all-rag-techniques repo project"
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
  subgraph "External Services"
    Nebius["Nebius AI API"]:::purple
    OpenAI["OpenAI API"]:::purple
  end

  subgraph "On-Disk Resources"
    Data["data/"]:::blue
    AI["AI_Information.pdf"]:::blue
    Attention["attention_is_all_you_need.pdf"]:::blue
    Quantum["quantum.txt"]:::blue
    Val["val.json"]:::blue
    ValRL["val_rl.json"]:::blue
    Req["requirements.txt"]:::blue
    Readme["README.md"]:::blue
    License["LICENSE"]:::blue
  end

  Data --> AI
  Data --> Attention
  Data --> Quantum
  Data --> Val
  Data --> ValRL

  subgraph "Shared Core Modules"
    Chunker["Chunking Functions"]:::orange
    VectorStore["SimpleVectorStore"]:::orange
    EmbedClient["EmbeddingClient"]:::orange
    LLMClient["LLMClient"]:::orange
  end

  AI --> Chunker
  Attention --> Chunker
  Quantum --> Chunker
  Val --> Chunker
  ValRL --> Chunker

  Chunker -->|"Embed(text chunk)"|EmbedClient
  EmbedClient -->|"API call"|Nebius
  EmbedClient -->|"API call"|OpenAI
  EmbedClient -->|"Store embeddings"|VectorStore
  VectorStore -->|"Retrieve chunks"|EmbedClient

  subgraph "Notebook Pipelines"
    subgraph "Chunking-based Techniques"
      NB1["1_simple_rag.ipynb"]:::green
      NB2["2_semantic_chunking.ipynb"]:::green
      NB3["3_chunk_size_selector.ipynb"]:::green
      NB4["4_context_enriched_rag.ipynb"]:::green
      NB5["5_contextual_chunk_headers_rag.ipynb"]:::green
      NB6["6_doc_augmentation_rag.ipynb"]:::green
    end
    subgraph "Transformer & Reranking"
      NB7["7_query_transform.ipynb"]:::green
      NB8["8_reranker.ipynb"]:::green
      NB9["9_rse.ipynb"]:::green
    end
    subgraph "Compression & Feedback"
      NB10["10_contextual_compression.ipynb"]:::green
      NB11["11_feedback_loop_rag.ipynb"]:::green
      NB12["12_adaptive_rag.ipynb"]:::green
    end
    subgraph "Advanced Techniques"
      NB13["13_self_rag.ipynb"]:::green
      NB14["14_proposition_chunking.ipynb"]:::green
      NB15["15_multimodel_rag.ipynb"]:::green
      NB16["16_fusion_rag.ipynb"]:::green
      NB17["17_graph_rag.ipynb"]:::green
      NB18["18_hierarchy_rag.ipynb"]:::green
      NB19["19_HyDE_rag.ipynb"]:::green
      NB20["20_crag.ipynb"]:::green
      NB21["21_rag_with_rl.ipynb"]:::green
      Best["best_rag_finder.ipynb"]:::green
    end
  end

  EmbedClient -->|"Embed in pipeline"|NB1 & NB2 & NB3 & NB4 & NB5 & NB6 & NB7 & NB8 & NB9 & NB10 & NB11 & NB12 & NB13 & NB14 & NB15 & NB16 & NB17 & NB18 & NB19 & NB20 & NB21 & Best
  NB1 -->|"Retrieve & Generate"|VectorStore
  NB2 -->VectorStore
  NB3 -->VectorStore
  NB4 -->VectorStore
  NB5 -->VectorStore
  NB6 -->VectorStore
  NB7 -->VectorStore
  NB8 -->VectorStore
  NB9 -->VectorStore
  NB10 -->VectorStore
  NB11 -->VectorStore
  NB12 -->VectorStore
  NB13 -->VectorStore
  NB14 -->VectorStore
  NB15 -->VectorStore
  NB16 -->VectorStore
  NB17 -->VectorStore
  NB18 -->VectorStore
  NB19 -->VectorStore
  NB20 -->VectorStore
  NB21 -->VectorStore
  Best -->VectorStore

  subgraph "Evaluation & Visualization"
    Score["JSON Scoring"]:::blue
    Plot["Matplotlib Plots"]:::blue
  end

  NB1 -->Score
  NB1 -->Plot
  NB2 -->Score
  NB2 -->Plot
  NB7 -->Score
  NB7 -->Plot
  NB8 -->Score
  NB8 -->Plot
  NB17 -->Score
  NB17 -->Plot
  Best -->Score
  Best -->Plot

  click Data "https://github.com/fareedkhan-dev/all-rag-techniques/tree/main/data/"
  click AI "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/data/AI_Information.pdf"
  click Attention "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/data/attention_is_all_you_need.pdf"
  click Quantum "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/data/quantum.txt"
  click Val "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/data/val.json"
  click ValRL "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/data/val_rl.json"
  click NB1 "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/1_simple_rag.ipynb"
  click NB2 "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/2_semantic_chunking.ipynb"
  click NB3 "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/3_chunk_size_selector.ipynb"
  click NB4 "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/4_context_enriched_rag.ipynb"
  click NB5 "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/5_contextual_chunk_headers_rag.ipynb"
  click NB6 "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/6_doc_augmentation_rag.ipynb"
  click NB7 "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/7_query_transform.ipynb"
  click NB8 "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/8_reranker.ipynb"
  click NB9 "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/9_rse.ipynb"
  click NB10 "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/10_contextual_compression.ipynb"
  click NB11 "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/11_feedback_loop_rag.ipynb"
  click NB12 "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/12_adaptive_rag.ipynb"
  click NB13 "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/13_self_rag.ipynb"
  click NB14 "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/14_proposition_chunking.ipynb"
  click NB15 "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/15_multimodel_rag.ipynb"
  click NB16 "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/16_fusion_rag.ipynb"
  click NB17 "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/17_graph_rag.ipynb"
  click NB18 "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/18_hierarchy_rag.ipynb"
  click NB19 "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/19_HyDE_rag.ipynb"
  click NB20 "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/20_crag.ipynb"
  click NB21 "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/21_rag_with_rl.ipynb"
  click Best "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/best_rag_finder.ipynb"
  click Req "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/requirements.txt"
  click Readme "https://github.com/fareedkhan-dev/all-rag-techniques/blob/main/README.md"
  click License "https://github.com/fareedkhan-dev/all-rag-techniques/tree/main/LICENSE"

  classDef blue fill:#ADD8E6,stroke:#333,stroke-width:1px
  classDef orange fill:#FFA500,stroke:#333,stroke-width:1px
  classDef green fill:#90EE90,stroke:#333,stroke-width:1px
  classDef purple fill:#DDA0DD,stroke:#333,stroke-width:1px
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
><b>Licenses</b>:
>
>- <b>MIT License</b>:  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
>- <b>Creative Commons Attribution-ShareAlike 4.0 International</b>: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) [![CC BY-SA 4.0](https://licensebuttons.net/l/by-sa/4.0/88x31.png)](https://creativecommons.org/licenses/by-sa/4.0/) - Legal details in [LICENSE-CC-BY-SA-4.0](THE_PAST/LICENSE-CC-BY-SA-4.0) and at [Creative Commons official site](https://creativecommons.org/licenses/by-sa/4.0/).
>
---
