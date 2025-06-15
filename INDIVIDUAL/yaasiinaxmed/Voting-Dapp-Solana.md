---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/yaasiinaxmed/Voting-Dapp-Solana
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExb2U4aHJnYzZ4dHUyZ2g0a25ja21oM3UxNGo4b3AwNjFqd3VoM2Q3byZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/10zxDv7Hv5RF9C/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----

# Voting-Dapp-Solana repo project
> <ins>📢 **Disclaimer** 🚨</ins>
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
title: "Voting-Dapp-Solana repo project"
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
    subgraph Off_chain_Web_Client["Off-chain Web Client"]
        Layout["layout.tsx"]:::frontend
        HomePage["page.tsx (Home)"]:::frontend
        AccountListPage["account/page.tsx"]:::frontend
        AccountDetailPage["account/[address]/page.tsx"]:::frontend
        ClustersPage["clusters/page.tsx"]:::frontend
        VotingPage["votingdapp/page.tsx"]:::frontend
        APIRoute["api/hello/route.ts"]:::backend
        ReactQueryProvider["react-query-provider.tsx"]:::backend
        SolanaProvider["solana-provider.tsx"]:::backend
    end

    subgraph Anchor_TS_Client["Anchor TS Client"]
        IDL["votingdapp.json"]:::idl
        Types["votingdapp.ts"]:::idl
        ClientExports["anchor/src/index.ts"]:::idl
    end

    subgraph On_chain_Program["On-chain Program<br/>(Rust/Anchor)"]
        Config["Anchor.toml"]:::config
        Program["lib.rs"]:::rust
        Migrations["deploy.ts"]:::scripts
        Tests["votingdapp.spec.ts"]:::tests
    end

    subgraph Solana_Network["Solana Network"]
        Solana["Solana Network"]:::network
    end

    subgraph CI_CD_Pipelines["CI/CD Pipelines"]
        CIAnchor["test-anchor.yml"]:::ci
        CIWeb["test-web.yml"]:::ci
    end

    Layout -->|renders| HomePage
    HomePage -->|uses| ReactQueryProvider
    AccountListPage -->|uses| ReactQueryProvider
    AccountDetailPage -->|uses| ReactQueryProvider
    ClustersPage -->|uses| ReactQueryProvider
    VotingPage -->|uses| ReactQueryProvider
    ReactQueryProvider -->|provides data to| SolanaProvider
    SolanaProvider -->|sends RPC via| ClientExports
    ClientExports -->|reads IDL/types from| IDL
    ClientExports -->|reads IDL/types from| Types
    ClientExports -->|invokes| Program
    Program -->|deploys/contracts on| Solana
    Migrations -->|deploys/upgrades| Program
    Tests -->|deploys to localnet on| Solana
    CIAnchor -->|runs build/test| Program
    CIAnchor -->|runs migrations/tests| Tests
    CIWeb -->|runs build/test| Layout
    APIRoute -->|provides API to| ReactQueryProvider

    click Layout "https://github.com/yaasiinaxmed/voting-dapp-solana/blob/main/src/app/layout.tsx"
    click HomePage "https://github.com/yaasiinaxmed/voting-dapp-solana/blob/main/src/app/page.tsx"
    click AccountListPage "https://github.com/yaasiinaxmed/voting-dapp-solana/blob/main/src/app/account/page.tsx"
    click AccountDetailPage "https://github.com/yaasiinaxmed/voting-dapp-solana/blob/main/src/app/account/[address]/page.tsx"
    click ClustersPage "https://github.com/yaasiinaxmed/voting-dapp-solana/blob/main/src/app/clusters/page.tsx"
    click VotingPage "https://github.com/yaasiinaxmed/voting-dapp-solana/blob/main/src/app/votingdapp/page.tsx"
    click APIRoute "https://github.com/yaasiinaxmed/voting-dapp-solana/blob/main/src/app/api/hello/route.ts"
    click ReactQueryProvider "https://github.com/yaasiinaxmed/voting-dapp-solana/blob/main/src/app/react-query-provider.tsx"
    click SolanaProvider "https://github.com/yaasiinaxmed/voting-dapp-solana/blob/main/src/components/solana/solana-provider.tsx"
    click IDL "https://github.com/yaasiinaxmed/voting-dapp-solana/blob/main/anchor/target/idl/votingdapp.json"
    click Types "https://github.com/yaasiinaxmed/voting-dapp-solana/blob/main/anchor/target/types/votingdapp.ts"
    click ClientExports "https://github.com/yaasiinaxmed/voting-dapp-solana/blob/main/anchor/src/index.ts"
    click Config "https://github.com/yaasiinaxmed/voting-dapp-solana/blob/main/anchor/Anchor.toml"
    click Program "https://github.com/yaasiinaxmed/voting-dapp-solana/blob/main/anchor/programs/voting/src/lib.rs"
    click Migrations "https://github.com/yaasiinaxmed/voting-dapp-solana/blob/main/anchor/migrations/deploy.ts"
    click Tests "https://github.com/yaasiinaxmed/voting-dapp-solana/blob/main/anchor/tests/votingdapp.spec.ts"
    click CIAnchor "https://github.com/yaasiinaxmed/voting-dapp-solana/blob/main/.github/workflows/test-anchor.yml"
    click CIWeb "https://github.com/yaasiinaxmed/voting-dapp-solana/blob/main/.github/workflows/test-web.yml"

    classDef frontend fill:#D5E8D4,stroke:#82B366
    classDef backend fill:#DAE8FC,stroke:#6C8EBF
    classDef idl fill:#FFF2CC,stroke:#D6B656
    classDef config fill:#E1E1E1,stroke:#A8A8A8
    classDef rust fill:#E6E0F8,stroke:#9673A6
    classDef scripts fill:#F5F5F5,stroke:#AAAAAA
    classDef tests fill:#F8CECC,stroke:#B85450
    classDef network fill:#CCCCCC,stroke:#888888,stroke-dasharray: 5 5
    classDef ci fill:#F8CECC,stroke:#B85450,stroke-width:2px
```

----

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