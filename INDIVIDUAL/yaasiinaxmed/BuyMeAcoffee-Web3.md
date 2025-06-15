---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/yaasiinaxmed/BuyMeAcoffee-Web3
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




# BuyMeAcoffee-Web3 repo project
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
title: "BuyMeAcoffee-Web3 repo project"
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
    subgraph "Client Side"
        Browser["Browser<br/>(Client)"]:::client
    end

    %% Next.js Server
    subgraph "Next.js Server"
        NextServer["Next.js Server<br/>(SSR/SSG)"]:::server
        RootLayout["Root Layout<br/>(app/layout.tsx)"]:::serverComp
        HomePage["Main/Home Page<br/>(app/page.tsx)"]:::serverComp
    end

    subgraph "React Component Layer"
        subgraph "Server Components"
            RootLayout --> HomePage
        end
        
        subgraph "Client Components"
            ConnectWallet["ConnectWallet"]:::clientComp
            Nav["Navigation Bar"]:::clientComp
            Footer["Footer"]:::clientComp
            Profile["Profile Widget"]:::clientComp
            Coffee["Coffee Icon"]:::clientComp
            GameIconsCoffeeCup["GameIconsCoffeeCup"]:::clientComp
        end
    end

    %% Global State & Config
    ContextProvider(("Global State Provider\n(context/index.tsx)")):::config
    ConfigFile(("Configuration<br/>(config/index.tsx)")):::config
    GlobalStyles["Global Styles<br/>(app/globals.css)"]:::styles
    TailwindConfig(("Tailwind Config<br/>(tailwind.config.ts)")):::config
    NextConfig(("Next.js Config<br/>(next.config.js)")):::config

    %% Static Assets
    Public(("Static Assets<br/>(public/)")):::assets

    %% External Services
    ExternalWallet["Blockchain Wallet RPC"]:::external

    %% Connections
    Browser -->|"HTTP GET /"| NextServer
    NextServer --> RootLayout
    NextServer -->|"Serves assets"| Public
    NextServer -->|"Sends HTML + JSON"| Browser
    Browser -->|"Hydrate"| ConnectWallet
    Browser --> Nav
    Browser --> Footer
    Browser --> Profile
    Browser --> Coffee
    Browser --> GameIconsCoffeeCup

    ConnectWallet -->|"RPC call"| ExternalWallet
    ConnectWallet -->|"uses Context"| ContextProvider
    Nav -->|"uses Context"| ContextProvider
    Profile -->|"uses Context"| ContextProvider

    ConnectWallet -->|"reads config"| ConfigFile
    Browser -->|"loads styles"| GlobalStyles
    Browser -->|"loads CSS config"| TailwindConfig
    NextServer --> NextConfig

    %% Click Events
    click RootLayout "https://github.com/yaasiinaxmed/buymeacoffee-web3/blob/main/app/layout.tsx"
    click HomePage "https://github.com/yaasiinaxmed/buymeacoffee-web3/blob/main/app/page.tsx"
    click ConnectWallet "https://github.com/yaasiinaxmed/buymeacoffee-web3/blob/main/app/components/ConnectWallet.tsx"
    click Nav "https://github.com/yaasiinaxmed/buymeacoffee-web3/blob/main/app/components/Nav.tsx"
    click Footer "https://github.com/yaasiinaxmed/buymeacoffee-web3/blob/main/app/components/Footer.tsx"
    click Profile "https://github.com/yaasiinaxmed/buymeacoffee-web3/blob/main/app/components/Profile.tsx"
    click Coffee "https://github.com/yaasiinaxmed/buymeacoffee-web3/blob/main/app/components/Coffee.tsx"
    click GameIconsCoffeeCup "https://github.com/yaasiinaxmed/buymeacoffee-web3/blob/main/app/components/GameIconsCoffeeCup.tsx"
    click Public "https://github.com/yaasiinaxmed/buymeacoffee-web3/tree/main/public/"
    click ContextProvider "https://github.com/yaasiinaxmed/buymeacoffee-web3/blob/main/context/index.tsx"
    click ConfigFile "https://github.com/yaasiinaxmed/buymeacoffee-web3/blob/main/config/index.tsx"
    click GlobalStyles "https://github.com/yaasiinaxmed/buymeacoffee-web3/blob/main/app/globals.css"
    click TailwindConfig "https://github.com/yaasiinaxmed/buymeacoffee-web3/blob/main/tailwind.config.ts"
    click NextConfig "https://github.com/yaasiinaxmed/buymeacoffee-web3/blob/main/next.config.js"

    %% Styles
    classDef client fill:#cce5ff,stroke:#3366cc,color:#000;
    classDef server fill:#d4edda,stroke:#228B22,color:#000;
    classDef serverComp fill:#e2f0cb,stroke:#228B22,color:#000;
    classDef clientComp fill:#fff4cc,stroke:#e69500,color:#000;
    classDef config fill:#f0e68c,stroke:#daa520,color:#000;
    classDef styles fill:#ffe5e5,stroke:#cc0000,color:#000;
    classDef assets fill:#f0f0f0,stroke:#999,color:#000;
    classDef external fill:#ffe4b5,stroke:#ff8c00,color:#000;
```

-----

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