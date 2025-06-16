---
created: 2025-06-15 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY-SA 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
source: https://github.com/ethereum/ethereum-foundation-website
---


> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷
> 
> This is a working draft in progress
> 
> ![Loading...](https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExanZydm52NDcyNWIwMWtneG9uOWk4aGpseXQ1bHR4b3c1N2x3MnB6bSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/m3XqQ8QhuIUuQau7n5/giphy.gif)
>
> gif image is provided by [Giphy](https://giphy.com)
> 
> ⚠️🏗️🚧🦺🧱🪵🪨🪚🛠️👷


----




# ethereum-foundation-website repo project
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
title: "ethereum-foundation-website repo project"
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
    subgraph Developer_Machine["Developer Machine"]
        DM[("Developer<br>Node.js & npm")]:::dev
        DM -->|"npm run dev"| NextServer
    end

    subgraph Version_Control_and_CI_CD[""Version Control & CI/CD""]
        GH[("GitHub Repo")]:::external
        CI[("CI/CD Pipeline<br/>(Vercel/Netlify)")]:::ci
        GH -->|push/PR triggers| CI
        CI -->|build & deploy| HostingCDN
    end

    subgraph Hosting_and_CDN["Hosting & CDN"]
        HostingCDN[("Vercel/Netlify<br>Static/CDN")]:::cdn
    end

    subgraph Next_js_Server["Next.js Server (SSR/SSG)"]
        NextServer[("Next.js App Server<br>SSR/SSG")]:::server
        subgraph App_Router_Pages_and_Layout["App Router Pages & Layout"]
            Layout["layout.tsx"]:::server
            HeadPage["head.tsx"]:::server
            HomePage["page.tsx"]:::server
            ConflictPage["conflict-policy/page.tsx"]:::server
            EthereumPage["ethereum/page.tsx"]:::server
            InfinitePage["infinitegarden/page.tsx"]:::server
            StoryPage["ourstory/page.tsx"]:::server
            PeoplePage["people/page.tsx"]:::server
            PhilosophyPage["philosophy/page.tsx"]:::server
            EfPage["ef/page.tsx"]:::server
            SilviPage["silviculture-society/page.tsx"]:::server
        end
        NextServer -->|serves HTML| HostingCDN
    end

    %% Static Assets
    subgraph Static_Assets_Store["Static Assets Store"]
        Assets[("public/assets<br>3D Models, Images, PDFs")]:::cdn
    end
    Assets -->|via CDN| HostingCDN

    %% Browser Client
    subgraph Client_Browser["Client Browser"]
        Browser[("Browser<br>React Hydration & WebGL")]:::client
        subgraph Client_Components_and_WebGL["Client Components & WebGL"]
            Content["Content.tsx"]:::client
            HeadComp["Head.tsx"]:::client
            AnimateJS["animate.js"]:::client
            AnimContext["animation-context.tsx"]:::client
            GLSL["animations/*.glsl"]:::client
        end
        subgraph Three_js_Asset_Loaders_and_Shaders["Three.js Asset Loaders & Shaders"]
            GLTF["GLTFLoader.js"]:::client
            EffectComp["EffectComposer.js"]:::client
            Orbit["OrbitControls.js"]:::client
            PassComp["Pass.js"]:::client
            MaskPass["MaskPass.js"]:::client
            RenderPass["RenderPass.js"]:::client
            ShaderPass["ShaderPass.js"]:::client
            UnrealBloom["UnrealBloomPass.js"]:::client
            ShaderJS["shaders/*.js"]:::client
        end
        subgraph Nav_and_Footer["Nav & Footer"]
            NavComp["Nav.tsx"]:::client
            FooterComp["Footer.tsx"]:::client
            LinkComp["Link.tsx"]:::client
        end
        subgraph Client_Hooks["Client Hooks"]
            ScrollUtil["useScrollDirection.ts"]:::client
        end
        Browser -->|loads JS/CSS| HostingCDN
        Browser -->|fetch assets| HostingCDN
    end

    %% Styling
    subgraph Global_Styling["Global Styling"]
        GlobalSCSS["global.scss"]:::style_for_project_style
        ResetSCSS["reset.scss"]:::style_for_project_style
        VarsSCSS["variables.scss"]:::style_for_project_style
        StylesAssets["assets/*"]:::style_for_project_style
    end
    HostingCDN --> GlobalSCSS

    %% Config & Deployment Files
    subgraph Config_and_Deployment["Config & Deployment"]
        NextConfig["next.config.js"]:::config
        TSConfig["tsconfig.json"]:::config
        NetlifyToml["netlify.toml"]:::config
    end

    %% GitHub Templates
    subgraph Repo_Templates["Repo Templates"]
        BugTemp["bug_report.md"]:::external
        FeatureTemp["feature_request.md"]:::external
        PRTemp["PULL_REQUEST_TEMPLATE.md"]:::external
    end
    GH --> RepoTemplates

    %% Flows
    Browser -->|requests HTML/JSON| HostingCDN
    HostingCDN -->|SSR/SSG HTML| Browser
    HostingCDN -->|Static assets| Browser

    GH --> NextServer

    %% Click Events
    click Layout "https://github.com/ethereum/ethereum-foundation-website/blob/master/src/app/layout.tsx"
    click HeadPage "https://github.com/ethereum/ethereum-foundation-website/blob/master/src/app/head.tsx"
    click HomePage "https://github.com/ethereum/ethereum-foundation-website/blob/master/src/app/page.tsx"
    click EthereumPage "https://github.com/ethereum/ethereum-foundation-website/blob/master/src/app/ethereum/page.tsx"
    click Content "https://github.com/ethereum/ethereum-foundation-website/blob/master/src/components/page/Content.tsx"
    click GLTF "https://github.com/ethereum/ethereum-foundation-website/blob/master/src/components/page/assets/GLTFLoader.js"
    click NavComp "https://github.com/ethereum/ethereum-foundation-website/blob/master/src/components/nav/Nav.tsx"
    click GlobalSCSS "https://github.com/ethereum/ethereum-foundation-website/blob/master/src/styles/global.scss"
    click ScrollUtil "https://github.com/ethereum/ethereum-foundation-website/blob/master/src/utils/useScrollDirection.ts"
    click NextConfig "https://github.com/ethereum/ethereum-foundation-website/blob/master/next.config.js"
    click BugTemp "https://github.com/ethereum/ethereum-foundation-website/blob/master/.github/ISSUE_TEMPLATE/bug_report.md"

    %% Styles
    classDef client fill:#e0f7e9,stroke:#27ae60,color:#14522a
    classDef server fill:#e3f2fd,stroke:#2196f3,color:#0d47a1
    classDef cdn fill:#fff3e0,stroke:#fb8c00,color:#e65100
    classDef external fill:#eeeeee,stroke:#9e9e9e,color:#424242
    classDef ci fill:#f3e5f5,stroke:#ab47bc,color:#4a148c
    classDef dev fill:#fff9c4,stroke:#fbc02d,color:#827717
    classDef style_for_project_style fill:#f5f5f5,stroke:#90a4ae,color:#263238
    classDef config fill:#e8f5e9,stroke:#43a047,color:#1b5e20
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